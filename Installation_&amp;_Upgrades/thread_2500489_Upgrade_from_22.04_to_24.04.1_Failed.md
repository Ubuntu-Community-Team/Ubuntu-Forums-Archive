---
title: "Upgrade from 22.04 to 24.04.1 Failed"
date: 2024-09-03
forum: Installation &amp; Upgrades
---

### Post by vw16v on 2024-09-03
Hello, yesterday my 22.04 LTS prompted me for the upgrade to 24.04.1. I reviewed some information online before proceeding. The installation essentially got all the way to the end and then it failed right after it found my boot loader and Dual boot/Windows configuration. 
These were the messages it failed with. It mainly appeared that "Thunderbird" was causing all the issues. I have since removed Thunderbird since I do not use it. 

Here's the first error that popped up and then it proceeded quite a ways after this error.

```
Could not install '/tmp/apt-dpkg-install-xQMYRJ/00-thunderbird_2%3a1snap1-0ubuntu3_amd64.deb'

The upgrade will continue but the '/tmp/apt-dpkg-install-xQMYRJ/00-thunderbird_2%3a1snap1-0ubuntu3_amd64.deb' package may not be in a working state. Please consider submitting a bug report about it.
new thunderbird package pre-installation script subprocess returned error exit status 1
```

For some reason it said it completed but it definitely did not completed and upgrade. I was able to boot back into 22.04 so that's a relief.

```
Upgrade complete

The upgrade has completed but there were errors during the upgrade process.
```

After I got back in I removed thunderbird and wanted to try to update again. However, I'm unable to get the prompt to come up to upgrade and system updater just shows my system as up to date. 

I also tried this command but it will not allow me to upgrade.

```
do-release-upgrade
Checking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS development release 
set Prompt=normal in /etc/update-manager/release-upgrades.
```

I also ran these commands in hope that it would purge any data it pulled down during the upgrade which was basically all 1700 packages.

apt-get update
apt-get autoremove
NOTE : this removed over 800MB!
apt-get clean
 
UNUSCONF=$(dpkg -l|grep "^rc" | awk '{print $2}')
apt-get remove --purge $UNUSCONF
(this Purged a bunch of STUFF/Kernels)

NEWKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')

ADDKERNEL="linux-(image|headers|ubuntu-modules|restricted-modules)"

METAKERNEL="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"


Here's some example output of the thunderbird failures.

```
var/log/dist-upgrade$ grep fail main.log 
2024-09-02 19:11:00,482 DEBUG running apport_pkgfailure() thunderbird: new thunderbird package pre-installation script subprocess returned error exit status 1
2024-09-02 19:16:53,735 DEBUG running apport_pkgfailure() thunderbird-locale-en: dependency problems - leaving unconfigured
2024-09-02 19:17:03,918 DEBUG running apport_pkgfailure() thunderbird-locale-en-us: dependency problems - leaving unconfigured

```
[B]
Thanks for any help on how I can get the update to come up again. I'm hoping after removing thunderbird this will complete. Appreciate any assistance. [/B]

---

### Post by tomho on 2024-09-04
In my case, update to 24.04 was offered yesterday 3rd Sep. but today I get the same message, that "There is no development version of an LTS available."
&#55358;&#56631;*&#9792;&#65039;

---

### Post by tomho on 2024-09-05
See also [https://ubuntuforums.org/showthread.php?t=2500509](https://ubuntuforums.org/showthread.php?t=2500509)

---

### Post by Dennis N on 2024-09-05
Using Ubuntu 22.04:

With Software & Updates utility's Updates tab set to "Notify me of a new Ubuntu version" set to "For long-term support versions":
```
dmn@Sydney-vm:~$ do-release-upgrade -c
Checking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS development release 
set Prompt=normal in /etc/update-manager/release-upgrades.
```
With Software & Updates utility's Updates tab set to "Notify me of a new Ubuntu version" set to "For any new version"
```
dmn@Sydney-vm:~$ do-release-upgrade -c
Checking for a new Ubuntu release
New release '24.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

```
Clearly something seems amiss, but perhaps using the "For any new version" setting, your upgrade will be processed? Try it.

---

### Post by xav42 on 2024-09-05
It looks to me that Canonical intentionally stopped the automatic upgrade process from 22.04 to 24.04 for some reason (most probably upgrade bugs).

So I would not try to force the upgrade until it's officially enabled again, but that's just me...

---

### Post by vw16v on 2024-09-10
> **Dennis N said:**
> Using Ubuntu 22.04:

With Software & Updates utility's Updates tab set to "Notify me of a new Ubuntu version" set to "For long-term support versions":
```
dmn@Sydney-vm:~$ do-release-upgrade -c
Checking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS development release 
set Prompt=normal in /etc/update-manager/release-upgrades.
```
With Software & Updates utility's Updates tab set to "Notify me of a new Ubuntu version" set to "For any new version"
```
dmn@Sydney-vm:~$ do-release-upgrade -c
Checking for a new Ubuntu release
New release '24.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

```

Clearly something seems amiss, but perhaps using the "For any new version" setting, your upgrade will be processed? Try it.

Thanks for the updates everyone! I haven't had a chance to mess with  this again since Sept 2nd when I posted this. I'll check the links  provided but might hold off for a little while as suggested by @ xav42. If anyone can confirm what xav42 mentioned  regarding Canonical intentionally stopped the automatic upgrade process from 22.04 to 24.04 for some reason (most probably upgrade bugs). Let me know or I'll search around some more. 

I might give this a try if I still get the "To upgrade to the latest non-LTS development release." when running do-release-upgrade without any switches. 

I actually did check Software & Updates last time I got this message. My setting are currently set to the following under the "updates" tab.
Subscribe to: All updates
Automatically check for updates: Daily
When there are security updates: Download and install auto
When there are other updates: Display weekly
**Notify me of a new Ubuntu version**: For long-term support versions. 

I haven't tried to push any updates since I booted up today but it hasn't prompted any updates either. 
Also, when I updated the installer said the following: 
"Some 3rd part entries in my sources.lists were disable. You can re-enable them after the upgrade with 'software-properties' tool or your package manager"

So, I also re-enabled quite a few things in Software & Updates under "Other Software" tab since all of them appeared to be unchecked. 
Also, everything is checked under "Ubuntu Software" table in Software & Updates.

Appreciate any other people that mentioned having issues and what the resolutions was while I look up the thread posted among other things. I'd like to get upgraded since I've seen lots of great stuff in the latest 24.04 LTS!

I'll also report back if I change it to "For any new version" in Software & Updates or anything else I try to remediate.

---

### Post by vw16v on 2024-09-24
Update! 
 I just noticed a Crash and took screen shots and it said Ubuntu 24.04 has experienced an error! I won't bother posting this but it took me off guard since based on the errors I saw during the upgrade I could of sworn the upgrade failed! My desktop and everything looked the same so it also made me think I was still on 22.04 because it looked the same. I have a bunch of output below showing I'm definitely on 24.04 (noble). ***What's odd is my Linux kernel is old.*** When I check version and it shows me on 24.04 but with old kernel that's from August before I attempted the upgrade. I've been receiving updates since I had issues with the upgrade to 24.04. I had no idea how it shows me 24.04! If anyone can confirm the Kernel I should be on I would appreciate it. I would assume the newer distro should be running a newer kernel correct?

```
 uname -a
Linux 6.8.0-44-generic #44-Ubuntu SMP PREEMPT_DYNAMIC Tue Aug 13 13:35:26 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux


```

And release output:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 24.04.1 LTS
Release:    24.04
Codename:    noble
$ uname -a
Linux yoga9i 6.8.0-44-generic #44-Ubuntu SMP PREEMPT_DYNAMIC Tue Aug 13 13:35:26 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

cat /etc/issue
Ubuntu 24.04.1 LTS \n \l

cat /etc/os-release
PRETTY_NAME="Ubuntu 24.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.1 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo

```

---

