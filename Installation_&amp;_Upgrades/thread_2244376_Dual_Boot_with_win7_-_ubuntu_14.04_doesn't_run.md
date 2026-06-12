---
title: "Dual Boot with win7 - ubuntu 14.04 doesn't run"
date: 2014-09-15
forum: Installation &amp; Upgrades
---

### Post by wbrokow1 on 2014-09-15
I have a 64 AMD machine with windows dual booting with ubuntu.
Never had any problems for years.
When I did the 12.04 to 14.04 from within ubuntu, ubuntu stopped working and bought me to a screen with busybox on it and a bunch of commands to use.
To be honest I have no Idea how to fix this and don't want to reinstall ubuntu for the fear of screwing up the windows 7 pro installation.

I am able to run win7 pro without a problem when I pick it from the list at boot time.
But when I pick ubuntu it goes to that busybox error screen and just sits.
i am able to type but don't know how to repair it.
Any help is appreciated.
I did create a 14.04 live CD but did not have the nerve to reinstall ubuntu!
Thanks for any help. I would like to just repair ubuntu if possible.

---

### Post by fantab on 2014-09-15
Run [**boot-repair**]("https://help.ubuntu.com/community/Boot-Repair") and '*Create a BootInfo summary*'... note down the url link to the file and paste the link here.
Don't run any repairs just yet.

---

### Post by wbrokow1 on 2014-09-16
Do I boot from the live cd and run 'boot-repair'?
or from the location where I crash to when I attempt to boot the ubuntu already installed.
i will try both
Thanks

---

### Post by wbrokow1 on 2014-09-16
Ok I tried at the ubuntu error screen, in the livecd at a command prompt and in a windows command prompt.
Nothing happened.
What did I do wrong?

---

### Post by oldfred on 2014-09-16
You have to install Boot-Repair into your live installer. Intructions on installing it are in link above.

If you do not boot then you cannot run Boot-Repair from your install. 
And you may have just a grub command line which is very limited to a few grub commands or you may be booting to a command line only but no gui.
Have you tried recovery mode or second boot option in grub? Or do you not even get to grub menu?

---

### Post by fantab on 2014-09-16
> **wbrokow1 said:**
> Do I boot from the live cd and run 'boot-repair'?
or from the location where I crash to when I attempt to boot the ubuntu already installed.
i will try both
Thanks

Yes, you will have to boot with LiveCD and 'Try Ubuntu' (without installing). This loads a working ubuntu-desktop.
Connect to internet. Download and install Boot-Repair tool. Run Boot-Repair to 'create a bootinfo summary'.

---

### Post by wbrokow1 on 2014-09-20
I ran Boot-repair from the live cd 

Here is the summary link.

Any help is appreciated.

[http://paste.ubuntu.com/8391047](http://paste.ubuntu.com/8391047)

Thanks for any help

---

### Post by yancek on 2014-09-20
It might have been useful to indicate that you had three separate hard drives along with the flash.  You referred to dual-booting but never made mention of multiple drives.  If you look at the very top of the boot repair output, you will see that you have windows boot code installed to the master boot record of all the drives.  You will also note that you do not have any Linux filesystems on any of the partitions.  The only reference to Ubuntu anywhere is the wubi entries on sda2.  WUBI installs Ubuntu inside a windows partition as a program similar to  virtual software.  My understanding is that WUBI puts an entry in the windows bootloader to chainload to its Grub but there is no grub.cfg file shown nor is there a windows boot file.  I've never used wubi, so someone who has may have a suggestion for you.  Just so you know, WUBI is no longer being developed and is not supported.

---

### Post by wbrokow1 on 2014-09-20
All did was the upgrade from 12.04 to 14.04 and it wipes itself out?
Should I follow the suggestion at the bottom of the report?to execute the recommended repair?
Thanks

---

### Post by oldfred on 2014-09-20
12.04 was the last supported version of wubi.

 Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

With multiple drives you can easily create a partition for Ubuntu on one of your other drives and install grub to that drive. 

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by hakuna_matata on 2014-09-21
> **wbrokow1 said:**
> I
When I did the 12.04 to 14.04 from within ubuntu, ubuntu stopped working and bought me to a screen with busybox on it and a bunch of commands to use.

IMHO this is known bug [1317437]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437")  (message "Serious errors were found while checking the disk drive for /", possible keys are "I", "S", "M" )

Solution: Try [this post]("http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696") and use **gksudo** as I wrote [here]("http://ubuntuforums.org/showthread.php?t=2217829&p=13035996#post13035996")

---

