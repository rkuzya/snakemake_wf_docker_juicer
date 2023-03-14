This workflow contains one rule:

all:
Specifies the output file(s) that are required to consider the workflow run as successful. In this case, it is the final Hi-C matrix in the .hic format.
call_juicer:Runs Juicer inside a Docker container on the raw fastq file to generate the final Hi-C matrix in the .hic format in the final/hic directory.
The rule specifies the following arguments to Juicer:

-s: Specifies the path to the input fastq file.

-g: Specifies the path to the genome file.

-e: Specifies the restriction enzyme used in the experiment.

-r: Specifies the path to the restriction enzyme cutting site file.

-c: Specifies the path to the chromosome sizes file.

-o: Specifies the output file name and location.

The config.yaml file specifies the paths to the genome, restriction enzyme cutting sites, and chromosome sizes. You will need to modify the paths to match your system.

The workflow is automated using GitLab CI/CD. In the .gitlab-ci.yml file, the conda package manager is used to install the necessary dependencies, including Snakemake and Juicer. Then, the Snakemake workflow is executed inside a Docker container with the required dependencies.

To run the workflow, replace /path/to/raw/hic/sample.fastq.gz with the path to your raw HIC data file in the call_juicer rule. Then, clone the repository and push it to a GitLab repository. Finally, create a new pipeline in GitLab. The pipeline will automatically execute the Snakemake workflow inside a Docker container with the required dependencies.

In summary, this workflow runs Juicer inside a Docker container with the specified genome, restriction enzyme cutting sites, and chromosome sizes to generate the final Hi-C matrix in the .hic format from your raw HIC data. The workflow is automated using Snakemake and GitLab CI/CD.

JUICER DOCKER CONTAINER TO BE USED:
https://hub.docker.com/r/aidenlab/juicer
