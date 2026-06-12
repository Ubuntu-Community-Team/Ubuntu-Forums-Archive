---
title: "Virtualbox and dpkg --configure -a problems"
date: 2018-06-03
forum: Installation &amp; Upgrades
---

### Post by esaksager on 2018-06-03
I have been trying to install Virtualdrive somedays ago.

Today I attempted to update and upgrade ubuntu (sudo apt-get upgrade && sudo apt-get update -y), this command results in the answer
[I]"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem"
[/I]
When I follow the instructions and enter sudo dpkg --configure -a, the following happens:

*"Setting up virtualbox-dkms (5.2.10-dfsg-6) ...**Removing old virtualbox-5.2.10 DKMS files...*

*-------- Uninstall Beginning --------*
*Module:  virtualbox*
*Version: 5.2.10*
*Kernel:  4.15.0-22-generic (x86_64)*
*-------------------------------------*

*Status: This module version was INACTIVE for this kernel.*
*depmod...*

*DKMS: uninstall completed.*

*------------------------------*
*Deleting module version: 5.2.10*
*completely from the DKMS tree.*
*------------------------------*
*Done.*
*Loading new virtualbox-5.2.10 DKMS files...*
*Building for 4.15.0-22-generic*
*Building initial module for 4.15.0-22-generic*
[I]"
[/I]And here it freezes and nothing more happens. I have been trying apt remove and apt-purge virtualbox etc., but I can not find a solution to this.

---

### Post by ajgreeny on 2018-06-03
I'm not sure you need the **virtualbox-dkms** package in the host, which I think is what you're saying, and I don't have it installed on my system where VBox works with no problems. I do have the relevant guest-additions installed however.

I do, however, have the **dkms** package installed in my host, and that is required in order to build the virtualbox kernel modules when a new kernel arrives in normal updates.

---

### Post by astram on 2018-06-04
I am experiencing the exact same issue on Ubuntu 18.04. I tried "apt-get install virtualbox", which ended up hanging. Now when I try to run "dpkg --configure -a" to clear the issue, that command freezes at the "Building initial module for 4.15.0-22-generic*" *step as well. I am unable to terminate the process via CTRL+C, and have to reboot.

---

### Post by ajgreeny on 2018-06-04
Are you using the standard Ubunturepos or have you enabled the VBox repos as detailed in the vvirtual box site itself?
I have not tried to install VBox 5.2 in my install of 18.04 yet but will try today and report back as I wonder if this is a specific kernel problem.

---

### Post by astram on 2018-06-04
I was able to salvage my apt/dpkg system using the following commands:

# dpkg --remove --force-remove-reinstreq virtualbox-qt
# dpkg --remove --force-remove-reinstreq virtualbox
# dpkg --remove --force-remove-reinstreq virtualbox-dkms
# dpkg --configure -a

I will hold off on trying to re-install VirtualBox until this issue is resolved.

---

### Post by astram on 2018-06-04
> **astram said:**
> I was able to salvage my apt/dpkg system using the following commands:

# dpkg --remove --force-remove-reinstreq virtualbox-qt
# dpkg --remove --force-remove-reinstreq virtualbox
# dpkg --remove --force-remove-reinstreq virtualbox-dkms
# dpkg --configure -a

I will hold off on trying to re-install VirtualBox until this issue is resolved.


I was eventually able to get VirtualBox installed by doing the following:

1) # apt install dkms
2) Disabling secure boot in my BIOS
3) # apt install virtualbox-5.2

---

### Post by helloannali on 2018-06-05
yes,i have the same problem. i tried so many times, but still failed. Did you solve it?

---

### Post by Jammyjamjamman on 2018-06-08
I had a similar problem when installing nvidia-390 dkms stuff recently. I described a workaround here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1775526](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1775526) based on [https://devtalk.nvidia.com/default/topic/1036167/linux/stuck-trying-to-intall-nvidia-390-ubuntu-18-04-lts-/](https://devtalk.nvidia.com/default/topic/1036167/linux/stuck-trying-to-intall-nvidia-390-ubuntu-18-04-lts-/)

Just to re-iterate the problem, a dialogue for creating a password (for secureboot stuff) should popup, but doesn't. Switching off secureboot did not get rid of this for me.

The workaround is to type in a new password "blindly" in the terminal with the "frozen" update and press return. In theory, you need to repeat this step at least twice, but I had to repeat it about 4 times to get it to work (I'm not really sure why).

---

### Post by ssm1985 on 2018-06-10
> **Jammyjamjamman said:**
> I had a similar problem when installing nvidia-390 dkms stuff recently. I described a workaround here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1775526](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1775526) based on [https://devtalk.nvidia.com/default/topic/1036167/linux/stuck-trying-to-intall-nvidia-390-ubuntu-18-04-lts-/](https://devtalk.nvidia.com/default/topic/1036167/linux/stuck-trying-to-intall-nvidia-390-ubuntu-18-04-lts-/)

Just to re-iterate the problem, a dialogue for creating a password (for secureboot stuff) should popup, but doesn't. Switching off secureboot did not get rid of this for me.

The workaround is to type in a new password "blindly" in the terminal with the "frozen" update and press return. In theory, you need to repeat this step at least twice, but I had to repeat it about 4 times to get it to work (I'm not really sure why).

I'm not sure why but this seems hit or miss with me. I've been running into the same problem messing with the nvidia drivers and it seemed to work once or twice, but the last few times I've done it nothing happens. It could also be because I'm fairly new to Ubuntu and I don't know what I'm doing...

---

### Post by morten-fyhn-amundsen on 2018-06-11
> **astram said:**
> I was able to salvage my apt/dpkg system using the following commands:

# dpkg --remove --force-remove-reinstreq virtualbox-qt
# dpkg --remove --force-remove-reinstreq virtualbox
# dpkg --remove --force-remove-reinstreq virtualbox-dkms
# dpkg --configure -a

I will hold off on trying to re-install VirtualBox until this issue is resolved.

Thank you!

---

### Post by rpgmorpheus on 2018-06-26
This helped me as well!
Just gave up on virtual box for the time being.

---

### Post by ashcanconsortia on 2018-06-27
> **Jammyjamjamman said:**
> 
Just to re-iterate the problem, a dialogue for creating a password (for secureboot stuff) should popup, but doesn't. Switching off secureboot did not get rid of this for me.

The workaround is to type in a new password "blindly" in the terminal with the "frozen" update and press return. In theory, you need to repeat this step at least twice, but I had to repeat it about 4 times to get it to work (I'm not really sure why).

Thanks for the hint about it being secure boot. Out of curiosity I tried turning off secure boot in the BIOS and then just running "dpkg --configure -a" again, and it worked for me without the bit about typing the password in the terminal, so it might work for some other folk's systems as well.

---

### Post by ferranaris on 2018-06-28
> **astram said:**
> I was eventually able to get VirtualBox installed by doing the following:

1) # apt install dkms
2) Disabling secure boot in my BIOS
3) # apt install virtualbox-5.2

Thanks astram, worked for me.

Secure boot was the problem, just disabling in BIOS let me go ahead without problems.

---

### Post by mlloyd on 2018-06-30
This worked for me, to make the installer available again.

I finally got virtualbox installed, but it was necessary to disable secure boot to get it to work.

---

### Post by jorislambrechts on 2018-07-07
> **astram said:**
> I was eventually able to get VirtualBox installed by doing the following:

1) # apt install dkms
2) Disabling secure boot in my BIOS
3) # apt install virtualbox-5.2

Had the same issue and resolved it using both steps suggested by **@astram**

1. Remove installed packages
 
[COLOR=#000000]*# dpkg --remove --force-remove-reinstreq virtualbox-qt*[/COLOR]
[COLOR=#000000]*# dpkg --remove --force-remove-reinstreq virtualbox*[/COLOR]
[COLOR=#000000][I]# dpkg --remove --force-remove-reinstreq virtualbox-dkms

2. Disable secure boot in BIOS 

3. Install virtualbox

# apt install virtualbox[/I][/COLOR]

---

### Post by hopeinformer on 2018-07-23
This worked perfectly for regaining my apt-get system. Thank you so very much.

---

