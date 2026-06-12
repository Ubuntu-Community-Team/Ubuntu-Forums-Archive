---
title: "At a loss as to how to proceed"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2014-07-30
I have Ubuntu 12.04.4 installed.  My Update Manager shows "New hardware is available."  If I select Install I get the following:> Your current Hardware Enablement Stack (HWE) is going out of support
on 2014-08-07.  After this date security updates for critical parts (kernel
and graphics stack) of your system will no longer be available.issues

For more information, please see:
[http://wiki.ubuntu.com/1204_HWE_EOL](http://wiki.ubuntu.com/1204_HWE_EOL)If I select Upgrade, I get the following:> Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.If I choose Details, I get> The following packages have unmet dependencies:

libgl1-mesa-glx-lts-trusty: Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but 10.1.3-0ubuntu0.1~precise1 is to be installed
                            Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.4.99.1-0ubuntu2.2 is to be installedissues
                            Depends: libxdamage1 (>= 1:1.1) but 1:1.1.3-2build1 is to be installed
xserver-xorg-lts-trusty: Depends: xserver-xorg-core-lts-trusty (>= 2:1.11) but 2:1.15.1-0ubuntu2~precise1 is to be installed
From a terminal> uname -r
3.5.0-54-generic
and > grep prompt= /etc/update-manager/release-upgrades
prompt=lts
and >  sudo apt-get install linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty
[sudo] password for butch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:unmet
 libgl1-mesa-glx-lts-trusty : Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but it is not going to be installed
 xserver-xorg-lts-trusty : Recommends: xserver-xorg-input-all-lts-trusty but it is not going to be installed
                           Recommends: xserver-xorg-video-all-lts-trusty but it is not going to be installed
                           Recommends: x11-xserver-utils-lts-trusty but it is not going to be installed
                           Conflicts: libglapi-mesa:i386 (>= 0~)
E: Unable to correct problems, you have held broken packages.
and > sudo do-release-upgrade
Checking for a new Ubuntu release
No new release found
So, I am not sure where things stand nor what to do to upgrade.  I have read many posts concerning issues about HWE and upgrading bugs.  I noticed the two (2) bugs related to the LTS upgrade had been fixed.  I do want to do an upgrade that will leave my /home alone.  Anyone?

---

### Post by TheFu on 2014-07-30
Before any major upgrade like this, please, please, please perform a backup for anything you don't want to risk loosing.

If it were me, I'd start over with a fresh install and avoid the update process which seems to be looking to fail. If you've ever installed any packages without using the package manager (i.e. from a .deb file directly), that could lead to dependency issues.
> E: Unable to correct problems, you have held broken packages.  tells me that is the situation.

---

### Post by cscj01 on 2014-07-30
I do have a current backup of /home.  If I were to do a fresh install of 14.04.1, wouldn't me copying my /home to the new install that cause some issues with what is there from the install?  Also, is there a way to find out what the broken packages are?  I used Synaptic's Fix Broken Packages, but that gave me nothing.  By the way, I also ran this from a terminal> apt-cache policy update-manager-coreupdate-manager-core:
  Installed: 1:0.156.14.16
  Candidate: 1:0.156.14.16
  Version table:
 *** 1:0.156.14.16 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:0.156.14.5 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main amd64 Packages
     1:0.156.14 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main amd64 Packagesand this > hwe-support-status --verbose

Your current Hardware Enablement Stack (HWE) is going out of support
on 2014-08-07.  After this date security updates for critical parts (kernel
and graphics stack) of your system will no longer be available.

For more information, please see:
[http://wiki.ubuntu.com/1204_HWE_EOL](http://wiki.ubuntu.com/1204_HWE_EOL)

To upgrade to a supported (or longer supported) configuration:

* Upgrade from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS by running:
sudo do-release-upgrade 

OR

* Install a newer HWE version by running:
sudo apt-get install linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty

and reboot your system.
As I indicated earlier, I also ran the last install in the above to no avail.

I don't know what HWE I have (don't know the command to find out), but I believe it is the one associated with 13.10.  All of that said, I am still confused as to why the HWE update won't work.

---

### Post by grahammechanical on 2014-07-30
On the 7th August Ubuntu 12.04 will get another point release. It will be 12.04.5 and doing an normal update will bring it in. What you are being offered is an upgrade to your present Hardware Enablement Stack which is not the same thing as an upgrade to a point release or to the next LTS release.

Some on have reported on this forum that accepting the upgrade of the HWE broke the system. but when I put in an install of 12.04.4 and ran the HWE upgrade everything went fine. Mind you I am using the open source video driver. Not sure if that makes any difference. I am now waiting until 7th August to see how the upgrade to 12.04.5 goes. You could wait until then, yourself.

Personally I do not see the point of pushing out an upgrade to a new HWE when there is going to be a point release upgrade a day before support ends that will include the new HWE.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

> 
[LIST=1]
[*]The original 12.04 stack in Precise will remain supported for the usual 5yr life cycle of the LTS release.
[/LIST]


From the charts in that link it seems that you are being offered an early preview of the HWE stack that is coming in 12.04.5. See Ubuntu Kernel Support and that EP = Early Preview.

Regards.

---

### Post by cscj01 on 2014-07-31
> **grahammechanical said:**
> On the 7th August Ubuntu 12.04 will get another point release. It will be 12.04.5 and doing an normal update will bring it in. What you are being offered is an upgrade to your present Hardware Enablement Stack which is not the same thing as an upgrade to a point release or to the next LTS release.

Some on have reported on this forum that accepting the upgrade of the HWE broke the system. but when I put in an install of 12.04.4 and ran the HWE upgrade everything went fine. Mind you I am using the open source video driver. Not sure if that makes any difference. I am now waiting until 7th August to see how the upgrade to 12.04.5 goes. You could wait until then, yourself.

Personally I do not see the point of pushing out an upgrade to a new HWE when there is going to be a point release upgrade a day before support ends that will include the new HWE.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)



From the charts in that link it seems that you are being offered an early preview of the HWE stack that is coming in 12.04.5. See Ubuntu Kernel Support and that EP = Early Preview.

Regards.
If I understand you correctly, the update from 12.04.4 to 12.04.5 should resolve these problems I am having as well as update the HWE to the Trusty stack.  If that happens, I presume I would get the LTS upgrade notification from Update Manager in the usual manner.

---

### Post by kansasnoob on 2014-07-31
Best to be patient and wait until about the 7th. There have been problems encountered regarding both the HWE EOL updates and Precise -> Trusty release upgrades which are only partially resolved ATM. Just keep applying the regular updates - do not use the proposed repos - and remember the date:

> Your current Hardware Enablement Stack (HWE) is going out of support on **[COLOR="#FF0000"]2014-08-07[/COLOR]**.

The devs can get a lot of things fixed in a week ;)

---

### Post by cscj01 on 2014-08-10
The upgrade to 12.04.5 fixed my problem.  The HWE installed with no problems.

---

