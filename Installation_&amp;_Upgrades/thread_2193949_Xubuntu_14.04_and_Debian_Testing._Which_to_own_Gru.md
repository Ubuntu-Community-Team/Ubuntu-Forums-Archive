---
title: "Xubuntu 14.04 and Debian Testing. Which to own Grub2 Which will safely see the other?"
date: 2013-12-15
forum: Installation &amp; Upgrades
---

### Post by mikodo on 2013-12-15
Hi,

I had a situation in the past where one distro, that owned Grub2, stopped being able to see my other distro. Maybe the original kernel or userspace became too old to see the other OS's newer one. (Everything is on the same drive, different partitions).

I use xubuntu LTS's and want to install [Xubuntu 14.04 with its kernel 13.3 or 13.14]("http://news.softpedia.com/news/Ubuntu-14-04-LTS-Final-Might-Be-Based-on-Linux-Kernel-3-13-402283.shtml"), for the 3 years ***once it is released.* <- EDIT**

Also, I want to have [Debian Testing (xfce), installed which is kernel version 3.11.10-1]("http://packages.qa.debian.org/l/linux.html") With Debian Testing being a semi-rolling release the kernel may change later when it is updated, I don't know ...

Question. 

Which distro, Xubuntu 14.04 or Debian Testing should I attach Grub2 and which of the two is going to continue to see the other? (userspace may make issues, too.)

**So, which distro** **will continue** **to see the other safely?**

Thanks.

---

### Post by oldfred on 2013-12-15
Moved to Ubuntu + 1 forum. Moved back to Installation & Upgrades after edit & users request. Not really 14.04 yet.

I do not know about Debian.

Do you not have a stable install? I think just about all of us with Ubuntu+1 install that to a second drive, flash drive, or at least a second partition and boot from our stable install whether 12.04 or 13.10 or other distribution.

I have several hard drives all with different boot loaders, plus several flash drives to either boot a full install (my larger one) or repair ISOs. Somewhat like having a belt and suspenders just to be safe.

---

### Post by mikodo on 2013-12-15
deleted, see below

---

### Post by mikodo on 2013-12-15
> **oldfred said:**
> Do you not have a stable install? 

Duh, I meant to say I plan to install Xubuntu 14.04, when it is released this spring.

---

### Post by mikodo on 2013-12-15
I think I will just go ahead and use Xubuntu 14.04 for grub2, as it will have a newer kernel and cross my fingers.

Thanks.

---

### Post by oldfred on 2013-12-15
The booting with grub has nothing do do with kernel. That is before grub starts to boot system. So as long as you have a stable version of grub2 it should not matter.
But do not attempt to share a /boot partition.

---

### Post by mikodo on 2013-12-15
> **oldfred said:**
> The booting with grub has nothing do do with kernel. That is before grub starts to boot system. So as long as you have a stable version of grub2 it should not matter.
But do not attempt to share a /boot partition.

Thanks, Fred   :D

I'll just let them share the *boot drive*. I may have messed that up before, when I lost the ability to boot Debian, on a kernel update (Debian's). t'was a long time ago.

---

### Post by fantab on 2013-12-15
I had also had to face a similar conundrum, which Disto should be allowed to control GRUB when I have multiple distros?

I have Ubuntu Development Release, Ubuntu Studio, and Arch Linux.

The question I asked myself, which Distro is likely to be there all the time (theoretically at least).
Arch is a rolling distro, and its package versions are latest and comparable to Debian Sid. It is likely to receive Grub version upgrade sooner than Debian Testing or Ubuntu.
Ubuntu's are changed every 6 months, not in case of an LTS, however. 

So I stick with Arch Grub.

If you use 'os-prober' then another question you need to ask is which of the two distros, xubuntu or Debian testing is likely to receive more kernel upgrades? Because after every kernel upgrade you may have to upgrade-grub if the grub you are using, is from other distro. Suppose you use Grub from Xubuntu, and each time there is a kernel upgrade in Debian then you have to login to Xubuntu and run 'update-grub'. 

Debian testing is likely to get more kernel upgrades than Xubuntu LTS once its released. If I were you I would use Debian's Grub. Just to make things easier for me.
Also if there is Grub version upgrade, Debian testing is likely to get it first.

I hope you get the drift of what I am saying.

My two cents....

---

### Post by mikodo on 2013-12-15
Thank you fantab.

I agree with your advice. The only thing  that worries me about it is, that  Xubuntu 14.04 is going to start with a much newer kernel than Debian Testing, or for that matter Debian Unstable. That worries me. If I ran with grub2 attached to Debian Testing or Unstable, would their kernel or userspace always see Xubuntu 14.04?

[Debian current kernels]("http://packages.qa.debian.org/l/linux.html")

Testing    3.11.10-1

Unstable  3.11.10-1

Experimental  3.12.3-1~exp1

[Xubuntu 14.04 is going to use kernel 3.13 or 3.14]("http://news.softpedia.com/news/Ubuntu-14-04-LTS-Final-Might-Be-Based-on-Linux-Kernel-3-13-402283.shtml")

[Arch Linux uses kernel 3.12.5-1 (a much newer kernel, than Debian versions)]("https://www.archlinux.org/packages/core/x86_64/linux/")

Possibly, by the time Xubuntu 14.04 freezes, Debian Stable will catch up in kernel versions and/or surpass it by then.


Let me think about your advice. Again, thank you!

---

### Post by oldfred on 2013-12-15
With Debian based installs there are links to the newest (and 2nd newest) kernel in the /. And you can directly boot the links, so you do not have to update your main working install. I turn os-prober off and use 40_custom. I learned from user Ranch hand and Cavsfan further documented it. 

 Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   gksudo gedit /etc/grub.d/40_custom
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}


 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

 Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by fantab on 2013-12-16
> **mikodo said:**
> The only thing  that worries me about it is, that  Xubuntu 14.04 is going to start with a much newer kernel than Debian Testing. That worries me. If I ran with grub2 attached to Debian testing, would it always see Xubuntu 14.04?


Ubuntu is built with and upon Debian 'Testing'. So it will take the latest kernel that is in the Debian 'testing' repos, but at some point in Ubuntu14.04's development cycle, there will be a 'kernel freeze'. Meaning no newer kernels will be used from testing anymore.
So it is unlikely that Ubuntu's release will see a newer kernel than the one in Debian 'testing'. At best they both will have same basic kernel version at time of 14.04 release.

---

### Post by mikodo on 2013-12-16
> **fantab said:**
> Ubuntu is built with and upon Debian 'Testing'. So it will take the latest kernel that is in the Debian 'testing' repos, but at some point in Ubuntu14.04's development cycle, there will be a 'kernel freeze'. Meaning no newer kernels will be used from testing anymore.
So it is unlikely that Ubuntu's release will see a newer kernel than the one in Debian 'testing'. At best they both will have same basic kernel version at time of 14.04 release.

I think you are right. Also, eventually, Debian Testing is going to have a newer kernel and has the potential to provide a newer Grub2.

Thanks.

---

### Post by mikodo on 2013-12-16
Extra post.

---

### Post by mikodo on 2013-12-16
extra post.

---

### Post by mikodo on 2013-12-16
> **oldfred said:**
> With Debian based installs there are links to the newest (and 2nd newest) kernel in the /. And you can directly boot the links, so you do not have to update your main working install. I turn os-prober off and use 40_custom. I learned from user Ranch hand and Cavsfan further documented it. 

 Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   gksudo gedit /etc/grub.d/40_custom
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}


 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

 Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Thanks Fred. Yes, Ranch Hand, we haven't seen him around here. I did see him on another forum though!

Thanks for the advice. I will read your links, and decide what to do. Just as I am getting used to following your advice to do this, after kernel updates.

```
sudo grub-install /dev/sda

Then sudo update-grub on primary install to set it.

```
My best to you.

---

### Post by fantab on 2013-12-16
Yes, setting up your grub menu with 40_custom will be a better option than 'os-prober'; os-prober can have bugs and other performance issues.

Also, I forgot to mention earlier; Debian, at the time of installation, gives you an option to NOT install Grub, Ubuntu does not.

---

### Post by mikodo on 2013-12-16
> **fantab said:**
> Yes, setting up your grub menu with 40_custom will be a better option than 'os-prober'; os-prober can have bugs and other performance issues.

Also, I forgot to mention earlier; Debian, at the time of installation, gives you an option to NOT install Grub, Ubuntu does not.


As it stands now, I think I will install Debian Untstable (Sid), and attach Grub2 to it. For more stable, I will be using Xubuntu 14.04. (I often have 3 or so other installs in different partitions, just for fun, too!).

I've never usedr 40_custom, but I will look at solidifying things with it. I have os-prober installed and didn't know it. <- EDIT

You and oldfred have been great.

Thanks guys, for all the help and advice.

EDIT: Something oldfred taught me before today, and I confirmed while installing different distros. One can install the Grub2 to the drive you want, so when I install the Xubuntu 14.04 I have to install Grub2, I can install it to /dev/sda, just like I will with Debian Sid. In effect, like like not installing it anywhere.

---

