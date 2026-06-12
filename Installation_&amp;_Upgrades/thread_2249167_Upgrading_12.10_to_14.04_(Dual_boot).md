---
title: "Upgrading 12.10 to 14.04 (Dual boot)"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by enumaris88 on 2014-10-20
Hello, 

I own a sony vaio and I currently have it set up to dual boot ubuntu 12.10 and windows 7. I rarely use the ubuntu OS because I am just more familiar with windows; however, I need to use it to run some coding I wrote in Fortran because it's much easier to do through the terminal on Ubuntu than it is to do in windows. 

Because I don't use ubuntu very often at all, I only just recently found out that 12.10 is no longer supported, and I need to upgrade to the newest version so that I can keep my software up to date (some of which I need for the code). The thing is, since ubuntu 12.10 is no longer supported, my software updater/manager won't work there anymore because it just keeps giving me "404" errors when I start it up and it just automatically shuts off. 

I have therefore downloaded ubuntu 14.04 and burned it into a flash drive so that I may install it from the flash drive. The thing is, I don't see any option to upgrade ubuntu 12.10, I only see an option to install the new ubuntu "alongside my other operating systems" or to replace my operating systems (which I certainly DON'T want), or to do some sort of custom installation. 

Since I am not super tech savvy, I am afraid of messing up my computer when I am installing ubuntu (last time I did it, when I set up the dual boot in the first place, my computer failed to boot for the longest time...I can't remember how I solved that problem). I have no more use of ubuntu 12.10, and am OK with replacing that with 14.04, including all the data that is used over there, and I can simply reinstall all the necessary packages later (again, since I don't use ubuntu very often, I have very little data there). But I want to make sure I DON'T delete any data that I have access to through windows, and it would be easier of course if I could just upgrade 12.10 to 14.04 without having to reinstall all the packages I've downloaded, etc. I can't find the option to do so; however.

Should I install 14.04 into the partition marked "ubuntu 12.10" when I click on the "custom installation" tab? Will that erase 12.10 and replace it with 14.04? Is that my best option at this point? 

I'd appreciate some help. Thanks!

---

### Post by Bucky Ball on 2014-10-20
Welcome. Best to choose 'Something Else' at the partitioning section and partition manually. You will get to something that looks like Gparted. There, you will see the existing 12.10 install. It will be at the mountpoint /. Simply install to there. Make sure the /swap partition and /home, if you have one, are set to 'Use' but also, and most importantly, to DON'T FORMAT! This is important.

The Win install will be on an NTFS partition, clearly visible. Make sure it is set to 'Don't Use' and 'Don't Format'. Same with any other NTFS partitions. 

Go ahead with the install. When finished your existing /swap will be used by the new install and so will your existing /home partition, if you have one. Any data in the /home partition will be intact, as it was before the install (theoretically!).

Needless to say, backup anything you don't want to lose prior to commencing your adventure in case things should go pear-shaped. You should be fine if you take it slooooow. Good luck. ;)

PS: Pretty sure the upgrade option only applies to the last release, for 14.04 LTS that would be 13.10. LTS releases can be upgraded to the next LTS via the Software Updater, i.e. 12.04 LTS>14.04LTS. Handy. Judging by how you use Ubuntu, you're probably better off with a five year support LTS release.

---

### Post by enumaris88 on 2014-10-20
I see. I will try this out! Thanks!

---

### Post by grahammechanical on 2014-10-20
Ubuntu 12.10 was the last interim release to have 18 months support. Ubuntu 13.04 and 13.10 only had 9 months support. That is why there is no option to upgrade to 13.04. There is a way to do an End of Life upgrade. Here is the link.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

But you may find the fresh install using the Something Else option to be easier. By the way, some have found that using the Replace Ubuntu option actually replaces everything on the hard disk. So, it is good that you did not get a Replace Ubuntu option and were not tempted to use it.

If you going the upgrade route, then revert the user interface back to its default state, use the open source video driver, disable any PPAs and remove any applications that were not installed through the Ubuntu Software Centre. That is my advice.

Regards.

---

### Post by enumaris88 on 2014-10-20
> **Bucky Ball said:**
> Welcome. Best to choose 'Something Else' at the partitioning section and partition manually. You will get to something that looks like Gparted. There, you will see the existing 12.10 install. It will be at the mountpoint /. Simply install to there. Make sure the /swap partition and /home, if you have one, are set to 'Use' but also, and most importantly, to DON'T FORMAT! This is important.

The Win install will be on an NTFS partition, clearly visible. Make sure it is set to 'Don't Use' and 'Don't Format'. Same with any other NTFS partitions. 

Go ahead with the install. When finished your existing /swap will be used by the new install and so will your existing /home partition, if you have one. Any data in the /home partition will be intact, as it was before the install (theoretically!).

Needless to say, backup anything you don't want to lose prior to commencing your adventure in case things should go pear-shaped. You should be fine if you take it slooooow. Good luck. ;)

PS: Pretty sure the upgrade option only applies to the last release, for 14.04 LTS that would be 13.10. LTS releases can be upgraded to the next LTS via the Software Updater, i.e. 12.04 LTS>14.04LTS. Handy. Judging by how you use Ubuntu, you're probably better off with a five year support LTS release.

Hi, I've finally gotten around to trying to install, and I think I understood your post more poorly than I previously thought. I clicked on the "Something Else" option and am directed to this page:

[http://i.imgur.com/TlwAFPP.png](http://i.imgur.com/TlwAFPP.png)

As you can see volume 4 is the one with ubuntu 12.10 installed on it. But I don't know what I should do now. Surely it's not as easy as just highlighting that volume and clicking "install"?

Highlighting that volume, I can click "change" and it gives me a bunch of options for "use as" including "ext4 journaling system" "fat16 file system" etc., right now it's on "do not use partition". After changing the option from "do not use partition" to "ext4 journaling system" I am asked to select a "Mount point" which includes "/" "/home" "/boot" etc. Could you give me a step by step on what I should do on this page of the installation process? I'm really not very good at this. 

Should I change the "device for boot loader installation"? 

Thanks!

EDIT: I tried an install without messing with the "bootloader" and I got an error "Sorry, an error occured and it was not possible to install the bootloader at the specified location". So what location should I specify, the same 12.10 location?

---

### Post by Bucky Ball on 2014-10-20
> **enumaris88 said:**
> 

As you can see volume 4 is the one with ubuntu 12.10 installed on it. But I don't know what I should do now. Surely it's not as easy as just highlighting that volume and clicking "install"?


More or less is that easy. The 12.10 install will be on the mountpoint / already. Mark that partition to use and format and install 14.04 LTS there. Mark the /swap to use, but you don't need to format that. All other partitions, if you want to keep them, mark as 'do not use' and DON'T format them.

Bootloader generally goes on sda, but you can change that. One thing I have no idea about is how your partitions are marked. Is this an encrypted drive? Something else? With that many partitions I'd say you are using UEFI. That might make things trickier and I have little experience with it. Know nothing about /dev/mapper and the rest of that. I also see no /swap partition. You should have one.

Hopefully someone could chime in who knows about the mapper stuff.

Once again, backup anything you don't want to lose prior to doing anything further.  

That's about it. Good luck. ;)

---

### Post by enumaris88 on 2014-10-20
> **Bucky Ball said:**
> More or less is that easy. The 12.10 install will be on the mountpoint / already. Mark that partition to use and format and install 14.04 LTS there. Mark the /swap to use, but you don't need to format that. All other partitions, if you want to keep them, mark as 'do not use' and DON'T format them.

Bootloader generally goes on sda, but you can change that. One thing I have no idea about is how your partitions are marked. Is this an encrypted drive? Something else? With that many partitions I'd say you are using UEFI. That might make things trickier and I have little experience with it. Know nothing about /dev/mapper and the rest of that. I also see no /swap partition. You should have one.

Hopefully someone could chime in who knows about the mapper stuff.

Once again, backup anything you don't want to lose prior to doing anything further.  

That's about it. Good luck. ;)

Ok, I tried to install. I set the partition where 12.10 was where to install it, and mount "/". At first the installer said it was unable to install the bootloader at the default /dev/sda so I changed the location for the bootloader to where 12.10 was. The installation went on without much more error. I restarted my computer, and now GRUB loads automatically (previously grub only loaded when I selected to boot up ubuntu) and there is no more windows 7 option. In addition, selecting the ubuntu option, I am met with a black screen and the following error:

[http://i.imgur.com/3sCbLwe.jpg](http://i.imgur.com/3sCbLwe.jpg)

I am now forced to boot using the flashdrive and am now using the preview version of ubuntu... I checked the partitions again, and 14.04 has indeed replaced 12.10, but I just can't boot to there. Some help would be appreciated. Thanks.

---

### Post by Bucky Ball on 2014-10-20
Some progress. Try Boot Repair and let's see if that fixes. 

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Looks like the UUID you have in your /etc/fstab file is wrong (the UUID of a paritition can change with a new install). Perhaps Boot Repair can remedy that. Boot Repair can create a bootinfo output. Create one, note the address of that and put it here (Boot Repair will give you a link with your bootinfo when finished). We can then have a closer look if it doesn't fix things.

---

### Post by enumaris88 on 2014-10-20
> **Bucky Ball said:**
> Some progress. Try Boot Repair and let's see if that fixes. 

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Looks like the UUID you have in your /etc/fstab file is wrong (the UUID of a paritition can change with a new install). Perhaps Boot Repair can remedy that. Boot Repair can create a bootinfo output. Create one, note the address of that and put it here (Boot Repair will give you a link with your bootinfo when finished). We can then have a closer look if it doesn't fix things.

I ran the utility, at the end of it all I got this message:
An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/8609782/](http://paste.ubuntu.com/8609782/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 

You can now reboot your computer.
Please do not forget to make your BIOS boot on mapper/isw_bfhhiijdaa_Volume0 (256GB) disk!

I'm posting it here to keep this information. Hopefully restarting will work...

EDIT: It worked! Now I can boot up both ubuntu and windows! That's like a magic application! Haha. Thanks a bunch! :D

---

### Post by Bucky Ball on 2014-10-21
Great news! Yes, Boot Repair is your friend. Glad it's working. Please mark thread as solved by following the second link in my signature and don't hesitate to post a new thread for any further issues/comments. Enjoy and good luck with it. ;)

---

### Post by enumaris88 on 2014-10-21
Thanks! It's done. :)

---

### Post by Bucky Ball on 2014-10-21
Good job. Hey, I think I discovered totally by accident this afternoon what the /dev/mapper/etc. is all about. Are you running RAID? Apparently that uses that format for the partitions instead or the regular /dev/sda1 etc. 

Live and learn. ;)

---

