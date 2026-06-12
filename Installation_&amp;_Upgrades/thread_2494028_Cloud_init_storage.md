---
title: "Cloud init storage"
date: 2024-01-03
forum: Installation &amp; Upgrades
---

### Post by kleijheeg on 2024-01-03
Since a few month we use cloud init in combination with ipxe to  install ubuntu 22 on our baremetal desktops. 
It is working great but we  have baremetal desktops with different kind of storage.


 Most computer are having SSD disks and our new desktops are having NVME disks. The cloud init is working fine with the NVME disks but now I want to try to config the SSD aswell.
Also some baremetal machine need to be configured with RAID mirror.


 Is there an option to create a if statement or something else to  configure the storage in one user-data file? or do I have to create a  new user-data for the different kinds of disks.


 I have search on the internet if there is a kind of if statement but  have not found any. Then I tried to search if it is possible to change the name of the path  within cloud-init for the storage to have one uniform name for both the  ssd and nvme disks.

 From both of them I could not get any usefull information.

---

### Post by MAFoElffen on 2024-01-03
Sort of... curtin, cloud-inti & yaml are tied together.

Since somewhere around 2021, I started seeing YAML ${{ if }} and ${{ else }} statements being supported in AZURE via YAML... If I look in the yaml docs at GitLab in the CI/CD YAML syntax reference ([https://docs.gitlab.com/ee/ci/yaml/](https://docs.gitlab.com/ee/ci/yaml/)), I see this:
```

job1:
  variables:
    DEPLOY_VARIABLE: "job1-default-deploy"
  rules:
    - if: $CI_COMMIT_REF_NAME == $CI_DEFAULT_BRANCH
      variables:                                   # Override DEPLOY_VARIABLE defined
        DEPLOY_VARIABLE: "job1-deploy-production"  # at the job level.
    - when: on_success                             # Run the job in other cases
  script:
    - echo "Run script with $DEPLOY_VARIABLE as an argument"
    - echo "Run another script if $IS_A_FEATURE exists"

job2:
  script:
    - echo "Run script with $DEPLOY_VARIABLE as an argument"
    - echo "Run another script if $IS_A_FEATURE exists"

```
And their explanation of it
> 
When the branch is the default branch:

    job1&#8217;s DEPLOY_VARIABLE is job1-deploy-production.
    job2&#8217;s DEPLOY_VARIABLE is deploy-production. 

When the branch is feature:

    job1&#8217;s DEPLOY_VARIABLE is job1-default-deploy, and IS_A_FEATURE is true.
    job2&#8217;s DEPLOY_VARIABLE is default-deploy, and IS_A_FEATURE is true. 

When the branch is something else:

    job1&#8217;s DEPLOY_VARIABLE is job1-default-deploy.
    job2&#8217;s DEPLOY_VARIABLE is default-deploy. 

Additional details:

    workflow:rules:variables become global variables available in all jobs, including trigger jobs which forward variables to downstream pipelines by default. If the downstream pipeline uses the same variable, the variable is overwritten by the upstream variable value. Be sure to either:
        Use unique variable names in every project&#8217;s pipeline configuration, like PROJECT1_VARIABLE_NAME.
        Use inherit:variables in the trigger job and list the exact variables you want to forward to the downstream pipeline. 

Also this: [https://integrationworkz.antiohne.nl/2020/12/make-steps-conditional-in-multi-stage.html](https://integrationworkz.antiohne.nl/2020/12/make-steps-conditional-in-multi-stage.html)

But I am not sure if that can be used back in curtin and cloud-init... But I do know that the installer itself does take triggers to apply different installer scripts, so I believe those hooks are there... Just not publicly documented.

---

