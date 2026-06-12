---
title: "Recovering Previously Installed Apps after major Version UPGRADE"
date: 2022-03-25
forum: Installation &amp; Upgrades
---

### Post by n2te on 2022-03-25
I did a major version upgrade of Ubuntu 18.04 to 20.04 on TWO different PC's *VIA THE COMMAND LINE* and what a nightmare and headache. Never again. LOL. All kinds of strange and weird things happened. Then out of frustration, I did a "CLEAN" iso install from DVD and 20.04 then worked fine. No problems. My motivation however for attempting to upgrade to v20 via the command line was to _*keep*_ my existing _*installed applications*_ intact and not have to re-install all of them when finished. So I opted for the risky upgrade via command line. Big mistake. The installed 20.04 system was rampant with problems. So now, with an error-free 20.04 installed from a "clean" install, I have to go back and download and re-install _*ALL*_ of my previously installed apps from 18.04 which is what I was hoping to avoid. 

So do I understand correctly that when doing a *major* upgrade from version to version that there is NO WAY to avoid this time consuming task of re-installing one's previously installed apps? I can't seem to find an answer to this question online. (I must be searching for the wrong thing.) Is there any utility that has been developed by someone (i.e. open source, or even paid, ???) that automates this time consuming post-upgrade task? Or are there just too many version related dependencies with each of these individual previously installed apps which would make automating this task impractical? I sort of recall seeing something once before about such an automated time-saving utility but I can't find it. Is this just something that everyone who upgrades must endure or is there a solution to what I have described here? Suggestions? Thanks.

---

### Post by oldfred on 2022-03-25
Part of your backup should be an export of installed apps. You still have to reinstall them, but then it can be automated.
All your user settings for apps (unless a server app) are in /home, so restoring /home restores those settings.

My rsync backup script file includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

compare script  MAFoElffen
[https://ubuntuforums.org/showthread.php?t=2470869&page=2](https://ubuntuforums.org/showthread.php?t=2470869&page=2)

---

### Post by grahammechanical on 2022-03-25
> So do I understand correctly that when doing a *major* upgrade from  version to version that there is NO WAY to avoid this time consuming  task of re-installing one's previously installed apps?

The applications that come as part of a default install of Ubuntu do get upgraded. But applications that we install ourselves do not always get upgraded because the developers of those applications may not have upgraded their software to the new version.

If we have a separate /home partition then when we do a fresh install it is possible to fresh install or re-install Ubuntu into the root partition (mark the partition to be formatted) and mark the separate home partition as /home (do not mark the partition to be formatted) and our user configuration files will remain untouched then the re-installed applications will find their configuration files.

Remember, the online upgrade from one Ubuntu version to a new Ubuntu version works best between default installations of Ubuntu. When we add applications to the installation and modify the desktop and user interface then we are changing the installation in a way that the Ubuntu developers cannot possibly foresee or take into account.

Regards

---

### Post by DuckHook on 2022-03-25
> **n2te said:**
> &#8230;Or are there just too many version related dependencies with each of these individual previously installed apps which would make automating this task impractical? I sort of recall seeing something once before about such an automated time-saving utility but I can't find it. Is this just something that everyone who upgrades must endure or is there a solution to what I have described here? Suggestions? Thanks.I have one install which I have network upgraded since 12.04. Mind, they were all LTS upgrades, so it was only done every two years but, still, that's an appreciable number of upgrades without the problems that you ran into.

I've also had installs that cratered at the first network upgrade. But I know what I did that led to the failure, so that came as no surprise.

Here are the factors that I've found over the years that lead to good success (versus almost guaranteed failure):

[LIST=1]
[*]Keep your base system as close to its default state as possible. The key to success here is to hive all of your apps and customizations off to containers or VMs. This allows the bare metal install to remain pristine.
[*]Do NOT add PPAs, third party repos or standalone apps to your base install. Aside from the security concerns, doing so drags in tons of dependencies that can mess up your dpkg database. Even if the database is not immediately compromised, it becomes very fragile. A network upgrade, which will change almost every library in your system, will have a devil of a time accounting for the special little accommodations that you forced the system to make for each of those apps.
[*]I used to have three (and only three) third party repos added to my base install: WINE, Virtualbox and Brave. These days, I have zero. Since discovering LXD and working out its quirks, I now have these three needed platforms running from their own containers. Steam is in a container. So is my Windows VM. Essentially, anything that might force the system to depart from a default state is confined to a container where it can make its demands without impacting my base system. Network upgrades are now a breeze.
[*]Do not make big changes to the system configurations. Too many people fall for the various extensions, modifications, bells and whistles that turn their systems into little customized city states. How is a network upgrade supposed to anticipate such modifications or work around them?
[*]Stick with boring, run&#8209;of&#8209;the&#8209;mill hardware. Anything that requires OEM drivers or oddball post install tweaking is bad news when it comes to network upgrades. Bleeding edge HW is often unsupported. Even new stuff that is supported will often be buggy or suffer from regressions. Tried and true HW rarely gives problems.
[*]As a corollary to the above (and this will raise a few objections), avoid nVidia. I've never had problems with AMD GPUs because they have a bigger commitment to Linux. nVidia is notorious for its indifference to Linux.
[*]Last but not least, don't try to upgrade from within a graphical environment. I've been burned a number of times doing that. Sometimes, the GUI will die mid-upgrade. Sometimes, it freezes, taking with it both mouse and keyboard. No recovery possible except restart, which is guaranteed to bork your install. Instead, leave the GUI at the login screen and switch to a TTY session using <Ctrl> <Alt> <F2-6>. Then, do your do-release-upgrade from there. Far less chance of a frame buffer switchover killing your GUI and with it your whole install.
[/LIST]
Though I may be jumping to conclusions, I suspect that your problems arose because you departed big time from the above rules. The more you "customize" the more you make simple upgrades impossible.

---

