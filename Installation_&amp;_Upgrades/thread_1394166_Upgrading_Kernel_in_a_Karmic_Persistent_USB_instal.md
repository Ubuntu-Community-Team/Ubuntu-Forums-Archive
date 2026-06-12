---
title: "Upgrading Kernel in a Karmic Persistent USB installation"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by octaedro7 on 2010-01-30
Hello,
I've upgraded the generic kernel of my Xubuntu Karmic AMD64 persistent USB installation with the ubuntustudio realtime kernel (2.6.31.9.10). 
The thing is that the generic kernel is still loading as default and I don't have the option on the boot menu to choose the new one. I don't know how to edit this Grub2 version (grub-pc 1.97 beta 4).
I haven't found a GUI package for this either. 
Does anybody know how to do this?

Thanks in advance

Regards

---

### Post by C.S.Cameron on 2010-01-30
I think that if you want to be able to upgrade a pendrive installation you need to do a full install, (using Install Ubuntu option from the Live CD or USB).
The Persistent Installs, (UNetbootin or usb-creator), boot a file named filesysten.squashfs. The kernel is locked inside this file and can not be easily changed.

---

### Post by octaedro7 on 2010-01-30
Thanks Cameron,
I've installed the rt kernel through synaptic, so it is there, somewhere in the loop file. I've updated many other packages successfully. I realize that a kernel might be totally different situation.
Hopefully there's a solution because there is no ubuntu live version bundled with rt kernel that I know of.
Seeing all the "magic" that has been done with live installations, all its flexibility I really keep the faith ;)
Are you positive that is not possible?

---

### Post by C.S.Cameron on 2010-01-30
I understand that the kernel is the first thing booted, the casper-rw file or partition does not get opened until the boot is underway, (I figure).
I've been sucker punched before by things in Ubuntu that I thought I was absolutely sure about.

Do you have a problem with doing a FULL install to your flashdrive?
It takes up a little more room but you can do anything you can do installing to an internal HDD.

---

### Post by octaedro7 on 2010-01-31
Thanks again Cameron.
The thing I like about persistent live installations is that they run in a plain fat32 partition thus making transfer of files quite easy between ubuntu and a windows PC. I know that there are other ways of accesing files from one to the other, it's just that is way simpler like this.
I guess I'll have to go for a regular install.
Anyway I'll leave the question floating, perhaps there's a way ;)

---

### Post by kolya_m on 2010-02-01
Hi,

I'm currently running Karmic with the RT Kernel off a liveUSB stick with persistent storage. I did this by making my own custom live iso by following [these instructions]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") (note that the repo url is different for Karmic as mentioned [here]("http://geekconnection.org/remastersys/forums/index.php?topic=354.0")). I then used the Create A USB Startup Disk in the Ubuntu 'System' menu, and told it to use my custom iso. Hey presto!

Obviously, this is no good if you want to update the kernel without having to start afresh, but I thought I'd share anyway.

Kolya

---

### Post by octaedro7 on 2010-02-03
Thanks kolya_m
Actually I've been struggling too much IMHO doing a regular install on the pendrive and after 4 failed attempts (first the device got locked and then grub refused to be installed on the pendrive,giving a fatal error, happened with both ubuntustudio and ubuntu mini cd) 
I managed to install xubuntu x86 karmic from a live CD but installation is not flawless ([http://ubuntuforums.org/showthread.php?t=1397302](http://ubuntuforums.org/showthread.php?t=1397302))
I'm more into the persistant live installation, because of all this problems but also because the OS being loaded into Ram its noticeably faster.

I`ll definitively give your info a try!! 

:popcorn:

---

### Post by octaedro7 on 2010-02-05
> **kolya_m said:**
> Hi,

I'm currently running Karmic with the RT Kernel off a liveUSB stick with persistent storage. I did this by making my own custom live iso by following [these instructions]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") (note that the repo url is different for Karmic as mentioned [here]("http://geekconnection.org/remastersys/forums/index.php?topic=354.0")). I then used the Create A USB Startup Disk in the Ubuntu 'System' menu, and told it to use my custom iso. Hey presto!

Obviously, this is no good if you want to update the kernel without having to start afresh, but I thought I'd share anyway.

Kolya
I'm finishing my customizations and I'm about to make an iso with Remastersys. I've read, said by the very same Remastersys author, that none of the applications like unetbootin works for persistent live USBs, that one has to do it manually.
[http://geekconnection.org/remastersys/forums/index.php?topic=463.0](http://geekconnection.org/remastersys/forums/index.php?topic=463.0)
Can you explain how did you accomplish it?
I would really appreciate your guide

I have an extra challenge, that I'm counting on surpass, that is that my custom installation is in VMware WS. I've never been good at praying, this might be a good chance to practice ;-)

---

### Post by C.S.Cameron on 2010-02-05
I usually install as you mention in your other post however I retain some FAT32 as the first partition so I can save stuff in Windows.

With a "Persistent" install, persistence is saved in a file named casper-rw. I'm not sure if it will compress if you include it in a squashfs file.

You can also make partitions named casper-rw and home-rw. I think you can use almost any file system, (except FAT32), for these persistent partitions.

You can trigger persistence by pressing F6 at the first screen after language preference and typing <space>persistent after ...quiet splash --.

Or you can edit text.cfg thus:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent.

With an UNetbootin install you edit syslinux.cfg the same way.

I have never ever had any luck with a mini.iso install to flash drive.

---

### Post by octaedro7 on 2010-02-17
I just wanted to report back my advances and failures, but first thank you both guys as I ended up using both tips.

I created a Xubuntu x86 virtual machine in vmware and customized it, including linux-rt kernel (I keeped the generic kernel as well just in case). 
I installed remastersys and did a full backup iso. I created the custom live-usb using the specific xubuntu usb creator application from pendrivelinux.com as it was the only one that allowed me to set a persistent loop on it. I don't know why but all other windows tools for creating usb-live installs didn't like the fact that the iso was named custombackup.iso, so they either didn't allow to select it or didn't allow to add persistence to the installation.   
Then I modified the syslinux.cfg adding the persistence part at the end of the boot commands.
Everything went fine except:
-I'm a bit surprised on how unstable is the karmic installation (both actual and live installs). I ended up several times without access to the installation after installing packages, especially after kernel installs. I was not messing up with any system file, simply installing things from official ubuntu's repos. It happened with regular ubuntu, ubuntustudio and xubuntu. Happened in virtual installs as well. The most common issue was, after installing the RT kernel and rebooting, the login start up splash shows up and after entering the user and password it sort of goes through the authentication process and it reverts you back to the login screen. Impossible to login there after. Note that the login splash shouldn't be there in the first place. I'm not an expert, so perhaps a more knowledgeable person would sort this out but definitively not a regular user.

-I wonder if one can get rid of the prompt that tells you to remove the cd and hit enter when you reboot or shutdown the computer. 

I'll keep on trying to finally make it work. At least remastersys works like a charm, so I have my own customized copy of xubuntu which makes me happy :p 
I'll come back with mi findings

---

