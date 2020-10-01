# Template - PCF Field Component

This template generates the repo for a PCF Field Component. The name of the repo is used as the name of the PCF Component.

# How does it work

This template has two actions:

1. pcfinit.yml - This workflow runs one time and scaffolds out your new PCF repo. It is deleted after the repo is initialised.
2. build.yml - This is your workflow for building the project and releasing the solution.

In order for the pcfinit workflow to scaffold out the repo properly please name your repo using this convention: pcf-COMPONENTNAME-component. If you do not have the hyphens, you will get this error below:

_Error: Not able to add reference to a project with same name as CDS project with name: reponame._

For example if you named your repo pcf-autocomplete-component, below will be the folder structure.

```
\
|   .gitignore
|   package-lock.json
|   package.json
|   pcf-autocomplete-component.pcfproj
|   pcfconfig.json
|   README.md
|   tsconfig.json
|   
+---.github
|   \---workflows
|           build.yml
|           
+---pcfautocompletecomponent
|       ControlManifest.Input.xml
|       index.ts
|       
\---Solution
    \---pcfautocompletecomponent
        |   .gitignore
        |   pcfautocompletecomponent.cdsproj
        |   
        \---src
            \---Other
                    Customizations.xml
                    Relationships.xml
                    Solution.xml
  ```                  

build.yml workflow can also be run manually, as it has a workflow_dispatch trigger. This workflow also runs automatically, if the commit contains a tag that begins with "v" e.g. v1.5.
