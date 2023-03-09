# integrate-terraformcloud-sentinel

Configure Workspace
This integration enables Bridgecrew to scan misconfigurations in your Infrastructure-as-code files and detect secrets exposed in your code. Supported formats and environments include: AWS Cloud Formation, HashiCorp Terraform, Azure Resource Manager, Kubernetes and Docker.

1. In Terraform Cloud go to your workspace.
2. Navigate to Settings > General.
3. Under General Settings you should find you Workspace ID and Workspace Name.

Create 'sentinel.hcl'
1. Create a new file named "sentinel.hcl" (locally or in your VCS)
2. Copy the following code snippet into the new file.
Note that {PATH_TO_FILE} should be replaced with the actual path
policy "bridgecrew" {
        source            = "{PATH_TO_FILE}"
        enforcement_level = "hard-mandatory"
}


Create 'bridgecrew.sentinel'
1. Create another file under the same path named "bridgecrew.sentinel"
2. Copy the following code snippet into the new file.

Connect Policy Set
In Terraform Cloud:
1. Under Settings, Policy sets, press Connect a New Policy Set.
2. Connect to the VCS and the specific repository where your new policy files are located or, if local, select No VCS connection.
3. Enter a Policy Name and Description. Then select the scope of policies to be enforced only on the integrated workspace.
4. Under Policy Set Settings, press "Sentinel Parameters", and click on Add parameter. Set the key as BC_API_KEY with the API token given in the previous step and check the Sensitive option.
5. Press Connect Policy Set.
