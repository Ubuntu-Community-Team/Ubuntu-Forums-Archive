---
title: "Upgrade Ubuntu 22.04 to 24.04 -"
date: 2024-08-24
forum: Installation &amp; Upgrades
---

### Post by penguinpages2 on 2024-08-24
```
cat /etc/os-release 
PRETTY_NAME="Ubuntu 22.04.4 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.4 LTS (Jammy Jellyfish)"
```

Error 

```


E:The repository 'https://apt.kubernetes.io kubernetes-xenial 
Release' no longer has a Release file., W:Updating from such a 
repository can't be done securely, and is therefore disabled by 
default., W:See apt-secure(8) manpage for repository creation and 
user configuration details., W:An error occurred during the signature 
verification. The repository is not updated and the previous index 
files will be used. GPG error: 
[https://packages.gitlab.com/runner/gitlab-runner/ubuntu](https://packages.gitlab.com/runner/gitlab-runner/ubuntu) jammy 
InRelease: The following signatures were invalid: EXPKEYSIG 
3F01618A51312F3F GitLab B.V. (package repository signing key) 
<packages@gitlab.com> 
```

I made posting to upgrade team assuming this was some upgrade script with core OS issue
[https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2076561](https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-6.5/+bug/2076561)

But the response I think is to imply one of my channels outside ubuntu is creating the conflict

```

[COLOR=#000000][FONT=&quot]Check the *.sources files in /etc/apt/sources.list.d/ for any that are disabled and re-enable them if you want them back.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]$ grep '^Enabled' /etc/apt/sources.list.d/*.sources[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Also check any *.list.distUpgrade files in the same directory that you might want to reenable.[/FONT][/COLOR]


[email]root@pandora:/etc/apt/sources.list[/email].d# ls /etc/apt/sources.list.d/
ansible-ubuntu-ansible-jammy.list                                    archive_uri-https_packages_microsoft_com_repos_edge-jammy.list              azure-cli.sources           helm-stable-debian.list.distUpgrade  microsoft-edge-dev.list.distUpgrade  runner_gitlab-runner.list.distUpgrade
ansible-ubuntu-ansible-jammy.list.distUpgrade                        archive_uri-https_packages_microsoft_com_repos_edge-jammy.list.distUpgrade  hashicorp.list              kubernetes.list                      plexmediaserver.list
archive_uri-https_apt_releases_hashicorp_com-jammy.list              azure-cli.list                                                              hashicorp.list.distUpgrade  kubernetes.list.distUpgrade          plexmediaserver.list.distUpgrade
archive_uri-https_apt_releases_hashicorp_com-jammy.list.distUpgrade  azure-cli.list.distUpgrade                                                  helm-stable-debian.list     microsoft-edge-dev.list              runner_gitlab-runner.list
[email]root@pandora:/etc/apt/sources.list[/email].d# 
[email]root@pandora:/etc/apt/sources.list[/email].d# grep '^Enabled' /etc/apt/sources.list.d/*.list.distUpgrade
[email]root@pandora:/etc/apt/sources.list[/email].d# grep '^Enabled' /etc/apt/sources.list.d/*.sources
[email]root@pandora:/etc/apt/sources.list[/email].d# cat * |grep -i enable
[email]root@pandora:/etc/apt/sources.list[/email].d# 

```

Response I am not sure if it maps to issue.  I this is trying to list "Enabled" channels that have been added to the 22.04 distro but the content of these files are just URLs to repos.

Any suggestions on error on upgrade is and next debug steps.  My thought is to disable all third party repos for now. Run upgrade then re-enable against new 24.04 channel.  But not sure how to do that, and if that maps to proper upgrade workflow.

---

### Post by grahammechanical on 2024-08-24
All third party repositories should be disabled before doing an online upgrade from one Ubuntu LTS to the next Ubuntu LTS. This is because third party repositories are not always updated to the new LTS version. In fact, some third party software might be discontinued by its developers. Therefore, the repository will not have a valid internet address for the latest Ubuntu LTS release.

Open Software and Updates>Other Software tab and untick the software repositories listed. After the upgrade is completed successfully you can either re-enable them or change the internet address to match the code name on the new LTS release. If the maintainers of the third party software have created an repository for the new LTS release.

I have Ubuntu 24.04 LTS (noble) but I need keyboard drivers from the supplier of my laptop. So, in my Other Software tab I have an internet address for the Ubuntu 20.04 LTS (focal) repository of the laptop supplier. I am able to get access to the repository of the laptop supplier and install the keyboard drivers as they are not present in Linux firmware (drivers).

Regards

---

