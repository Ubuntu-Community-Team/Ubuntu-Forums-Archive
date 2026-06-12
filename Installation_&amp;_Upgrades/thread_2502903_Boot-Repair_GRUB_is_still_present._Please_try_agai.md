---
title: "Boot-Repair GRUB is still present. Please try again["
date: 2024-12-04
forum: Installation &amp; Upgrades
---

### Post by soma56 on 2024-12-04
[https://paste.ubuntu.com/p/43gZ2HqtCN/](https://paste.ubuntu.com/p/43gZ2HqtCN/)

I swapped out my windows 11 hd that was in hibernation mode with my Ubuntu 22.04.1 and this is what started my login issues. Several hours later I have have boot repair installed on a usb thumb drive that I'm able to log into and create the above report. While I've tried various things online in attempt to resolve this issue I believe I've made things worse. While boot repair initially looked promising I can't get past the following error message: 

```
GRUB is still present. Please try again
```

Boot repair has a list of commands in terminal that it asks the uesr to input - I did receive this error - perhaps it's relevant? 

```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

Instead of potentially making things worse I'm hoping someone here can assist. Thank you in advanced for your help.^

---

### Post by soma56 on 2024-12-04
Not sure if this is also relevant but I thought I would post it here for good measure. One suggestion was to repair the filesystem using fsck command, however, sudo doesn't work within GRUB, recovery screen crashes and my only access to a terminal is through the USB stick with Boot-Repair.
 
```

mint@mint:~$ blkid
/dev/sda1: UUID="12E4-D300" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="3442d9cf-e5f1-4325-a068-240abd71713a"
/dev/sda2: UUID="01d64bdc-d66f-47f8-b164-16401ffdc95d" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="abc10a7e-b1d3-4855-b27e-5a626b78391b"
/dev/sdb1: LABEL="BOOT-REPAIR" UUID="2EF0-291B" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="0281a0c6-01"
/dev/loop0: TYPE="squashfs"

mint@mint:~$ fsck /dev/sda2
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
fsck.ext2: Permission denied while trying to open /dev/sda2
You must have r/w access to the filesystem or be root
```

I'm assuming you can use the Boot-Repair USB stick to repair the boot-loader on (sda2?), however, I'm uncertain on how to do this.

---

### Post by oldfred on 2024-12-04
I have not seen grub is still present. Are you running the system uninstall or a total reinstall of grub?
Report looks complete.

With one install, you normally do not get grub menu. Can you press escape key just after vendor logo & before grub menu appears.

I am seeing more of this setting, default was always 10 sec & I change to 3, 0 gives no time to get grub menu:
See line 156, 
> 
GRUB_TIMEOUT=0


If you cannot boot, you cannot easily change /etc/default/grub as you then have to also update grub. You can do all that with a chroot.
But you can edit grub.cfg which at top says do not edit. Any changes get replaced  with a grub update, so you normally would not edit it.
Change timeout to 10 and change style, my settings.
```
[FONT=monospace][COLOR=#000000]GRUB_TIMEOUT_STYLE=menu [/COLOR]
GRUB_TIMEOUT=3
[/FONT]
```
[FONT=monospace] But because grub & Boot-Repairs report look ok, the issue may be something after grub.
Change to menu will show boot process. Same info as in log files for boot.
[/FONT]

---

### Post by grahammechanical on 2024-12-05
There are things in your post that I do not understand.

> I swapped out my windows 11 hd that was in hibernation mode with my Ubuntu 22.04.1

Were you dual booting Windows 11 and Ubuntu with Windows on one drive and Ubuntu on another? And then there is this:

> While I've tried various things online in attempt to resolve this issue

What issue? What were the login issues that you were having? @oldfred has pointed out the BOOT Repair summary that you show us doesn't show that anything is wrong with the Ubuntu boot files on sda. In my opinion, sda should boot and should load Ubuntu. What is the present issue?

> mint@mint:~$ fsck /dev/sda2fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
fsck.ext2: Permission denied while trying to open /dev/sda2
You must have r/w access to the filesystem or be root

You ran the wrong command:

```
sudo fsck /dev/sda
```

Is the right command. Enter your user password when required to do so. This problem is not relevant. What makes you think that a file system check will fix the issue?

Regards

---

### Post by yancek on 2024-12-05
Could you explain the 'swapped out' you refer to in your original post?  Did you simply remove the windows hard drive then attach the Ubuntu hard drive to the same connector?  different connector?

What specific action got the message Grub is still present?  As you reported, trying different things you do not understand often does make things worse, bad idea.  Also, how did you get the error regarding broken packages, what were you doing?

---

### Post by soma56 on 2024-12-05
> **oldfred said:**
> I have not seen grub is still present. Are you  running the system uninstall or a total reinstall of grub?


> **grahammechanical said:**
> There are things in your post that I do not understand. ... 
Were you dual booting Windows 11 and Ubuntu with Windows on one drive and Ubuntu on another? ... What issue? What were the login issues that you were having? ... What is the present issue?


> **yancek said:**
> Could you explain the 'swapped out' you refer to  in your original post?  Did you simply remove the windows hard drive  then attach the Ubuntu hard drive to the same connector?  different  connector?

Thank you so much for replying (all of you) and so quickly as well. Yes, and I apologies as perhaps I should have provided some more clarity initially. I have a Panasonic Toughbook cf-54. I have two hard drive caddys associated with this laptop that are easily accessible through a simple release switch and have two different operating systems - Windows 11 and the other being Ubuntu 22.04.1 respectively. This error started yesterday when I removed  my Windows 11 hd caddy from the laptop and shoved in the Ubuntu hd caddy with the problem being (I think) that it was still in hibernation mode (as per Windows). This is instead of being completely off* before *loading the other hard drive. After I pressed the power button the laptop woke up from a hibernation status in (what it thought was) a Windows environment which was instead my Ubuntu hd. This is when the problems started. 

Ubuntu has never loaded properly since. The specific error or issue I was receiving was a blank screen upon powering on (no GUI/logo). I am able to hold the shift key and access a 'grub' menu of sorts with a variety of options, however, I'm still hitting a dead end as the system 'crashes' when attempting recovery options and/or attempting anything else to load the OS. 

> **grahammechanical said:**
> You ran the wrong command:

```
sudo fsck /dev/sda
```

Is the right command...What makes you think that a file system check will fix the issue?


Good question. My limited education of Ubuntu coupled with trying what the internet suggests seemed like a good idea.

> **yancek said:**
> What specific action got the message Grub is  still present?  As you reported, trying different things you do not  understand often does make things worse, bad idea.  Also, how did you  get the error regarding broken packages, what were you doing?

Ironically  using the Windows machine now. I'm going to shut this machine down and  report back with exactly what happens when I attempt to load Ubuntu. I  hope everyone has some better clarity with respect to what's going  (apologies for lack of clarity initially).

---

### Post by soma56 on 2024-12-05
When turning on the laptop I'm greeted with gnu grub 2.12. Here are the option results (when I click them). 
[B]
*Ubuntu[/B]
Results in error (freezes): 
0.4010601 Initramfs unpacking failed: invalid magic in start of ...

** Advanced Options -> *Ubuntu with Linux _6.8.0-49_ Generic**
Results in error (freezes): 
0.4020731 Initramfs unpacking failed: invalid magic in start of ...

** Advanced Options -> *Ubuntu with Linux _6.8.0-49_ Generic (Recovery Mode)**
Results in error  (freezes after loading many files):
0.5899381 ? __pfx-kernal_init?0x10/0x10

** Advanced Options -> *Ubuntu with Linux _6.8.0-48_ Generic**
Operating system loads, however: 
1. I am greeted with the welcome screen (as if it were a fresh install) 
2. My files are gone
3. My programs are present but don't work/load
4. I receive an error pop-up stating multiple issues
5. the mouse/keyboard/visuals/ extremely buggy (inoperable at times). 

** Advanced Options -> *Ubuntu with Linux _6.8.0-48_ Generic (Recovery Mode) -> Resume (to OS)**
Operating system loads, however, same issues as previous/above. 

###############################################

Additional options within *Advanced Options -> *Ubuntu with Linux *_6.8.0-48_* Generic (Recovery Mode)*
are as follows: 
Resume (already tried - see above)
Clean
DPKG
FSCK
GRUB
NETWORK
ROOT
SYSTEM SUMMARY

I did play with some of the options here in an effort to repair my OS. My rabbit hole of Google searches was suggesting to repair the boot loader amongst other things,  however, I may have made things worse? With that said I will wait to hear on what you folks think I should try next - before I make things worse *worse*. TIA

---

### Post by grahammechanical on 2024-12-05
I can give you some information about the recovery menu.

Select NETWORK and you should get a network (internet) connection using settings in the OS. You will end up back at the recovery menu. Select Root and you will end up at a root shell prompt where you can run commands such as

```
apt update
apt upgrade
```

the prefix sudo is not needed. Update/upgrade might bring in some improvements. To get back to the recovery menu type exit and press enter. If you get error messages about broken packages the you can run DPKG - that will fix broken packages.

I am not sure but you might need to re-install a Linux kernel. I do not know how to do that. It is possible that update/upgrade might bring in a newer kernel that actually works.

Regards

---

### Post by oldfred on 2024-12-05
Are you attempting to repair an Ubuntu install with a Mint live installer?
You need to be using the Ubuntu live installer that is the same version you have installed.

Windows hibernation will not effect your Linux install. Windows hibernation/fast startup will lock NTFS partitions as the Linux NTFS driver will not mount read/write to prevent loss of data when hibernation restored by Windows boot.

Boot-Repair has an advanced mode that lets you choose to totally reinstall grub2 but also to install the most recent kernel. That sometimes fixes things.

---

### Post by soma56 on 2024-12-06
> **oldfred said:**
> Are you attempting to repair an Ubuntu install with a Mint live installer?

No. I don't necessarily wish to install, reinstall the OS, etc. unless this is required. I'm nor sure what Mint live installer - the only 3rd party software I played with was boot-repair (detailed below). 

> **oldfred said:**
> Windows hibernation will not effect your Linux install. Windows hibernation/fast startup will lock NTFS partitions as the Linux NTFS driver will not mount read/write to prevent loss of data when hibernation restored by Windows boot.

Boot-Repair has an advanced mode that lets you choose to totally reinstall grub2 but also to install the most recent kernel. That sometimes fixes things.

This is great information (thank you). I did see a Windows splash 'crash' screen when I powered up the laptop with the Ubuntu hd (relevant/ce?). I suppose I need to determine whether or not grub2 needs to be reinstalled (as well as the kernel) - but if you're suggesting this might be good practice either way and in consideration of my circumstances - I will try it.

I did try Boot-Repair ([https://sourceforge.net/p/boot-repair-cd/home/Home/](https://sourceforge.net/p/boot-repair-cd/home/Home/)) on a usb stick in an attempt to repair the boot processes associated with Ubuntu (as per Internet suggestions and logically this made sense - booting is 'broken', everyone praises 'this corrected their issues').

However, after loading Boot-Repair the 'recommended repair' didn't work as it returned error. This led to other searches and trying other fixes that obviously made things worse it seems. I have not tried the advanced mode/option as per your suggestion - speaking of which - is there a tutorial specific to this that you're aware of? I'm afraid  of Google and Linux solutions based on my kindergarten level of  knowledge on the Linux OS. I will look over the boot-repair website in the interim. 

> **grahammechanical said:**
> 

You ran the wrong command:

```
sudo fsck /dev/sda
```

Is the right command...this problem is not relevant. What makes you think that a file system check will fix the issue?



What made me think to try this? Google searches leading down rabbit holes in my attempts to resolve this issue. Having run the incorrect command I hope it didn't have an adverse/negative affect.

> **grahammechanical said:**
> Select NETWORK ... and you will end up at a root shell prompt where you can run commands such as
```
apt update
apt upgrade
```


I will try this and report back here. Thanks to both of you for your replies here.

---

### Post by oldfred on 2024-12-06
Shows some of the screens you see with advanced mode. Did you try that.
Best to run Boot-Repair from Ubuntu live installer of version you have installed. The Boot-Repair live ISO is not as current as the ppa most of the time.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You run fsck or e2fsck on formatted partitions like sda2, not a drive like sda unless you formatted an entire drive which is not recommended.
There also is dosfsck for FAT32.
See
man fsck
man e2fsck
man dosfsck

---

