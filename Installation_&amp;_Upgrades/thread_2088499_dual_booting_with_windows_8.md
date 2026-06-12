---
title: "dual booting with windows 8"
date: 2012-11-26
forum: Installation &amp; Upgrades
---

### Post by Bigneil on 2012-11-26
Ok, so I need a little advice. 
My wonderful wife just bought me an early Christmas present,  an ASUS K55A notebook. (I'm a lucky guy, this is my first ever NEW computer).

It comes with windows 8 pre-insalled so normally I would just wipe windows and install ubuntu, I have been using ubuntu since Fiesty Fawn came out and used it almost exclusively since hardy heron . However, on this occasion I would like to keep windows 8 and dual boot.

So, I did what i always do, and popped in an ubuntu CD and this time installed it along side windows. All seemed to go very smoothly, so when prompted I popped out the disk and restarted only to be met with a message something like "no OS found" I can't remember the wording, sorry.

It reminds me of the time I once ruined GRUB. lol 

So I was wondering if anybody else has tried ubuntu along side W8, and did you have any troubles? or was it a success?  did you have trouble then fiure it out?

The only thing I can think of right now is that windows was split into 2 parts, OS, and storage.... could it be that ubuntu needs to be installed on one rather than the other? 

anyway, at the moment I am running the reset function  on the new computer to put it back to factory pre-set, Then I can start over again once I have armed myself with knowledge.

Thanks for reading?


P.S I almost forgot to say It was 12.04

---

### Post by oldfred on 2012-11-26
If you have a new secure boot system which all pre-installed Windows 8 systems are, you can only install Ubuntu 12.10 which has the very new grub2 2.00 if you want secure boot. They are going to add grub2 2.00 to 12.04 with the next point upgrade in Jan. Or we are testing grub2 2.00 before they add it to the LTS. :)
12.10 has worked for some with secure boot on or off. But others have issues as the vendors have not all implemented UEFI per standard.

       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

Windows 8 systems are all UEFI boot also. 

Did you turn secure boot off?  If so you can convert 12.04 to UEFI install. It will not work with secure boot on but has worked with those who installed Windows 7 or Windows 8 manually. And some were UEFI. 

Best to see exactly where you are at. But you probably installed in BIOS mode, not UEFI mode. Boot repair can convert by uninstalling grub-pc and installing grub-efi.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

       [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
       Dual-boot Windows 8 and Ubuntu 12.10 on UEFI hardware
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

    
       Acer V5-571P-6815 secure boot off worked
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

Not Windows 8 but UEFI.
       Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
    Even older as install was more difficult, new versions much better
       efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

---

### Post by Bigneil on 2012-11-27
Thank you for a great answer. although at this stage, I have never heard of a UEFI lol. All the info I need is there and I am sure I'll be able to figure it out from your info :)

---

### Post by Bigneil on 2012-11-27
right, I turned off the fancy booting options in the bios screen and ran an installation of 12.10 64 bit and ubuntu is working nicely, however there is a new issue I need to fix.

the startup option are like this.
[IMG]http://i704.photobucket.com/albums/ww46/blueb4sunrise/DSC_0030-1.jpg[/IMG]

If I try to choose windows 8 (loader) this happens.
[IMG]http://i704.photobucket.com/albums/ww46/blueb4sunrise/DSC_0031-1.jpg[/IMG]

would a program like "bootrepair" work or make it worse?

---

### Post by Bigneil on 2012-11-27
LOL, I'm far too impatient. I couldn't resist just diving in and running boot-repair.

All is good and I can now use 'buntu or windows.:guitar:

---

### Post by offgridguy on 2012-11-27
Glad to see you didn't wipe a perfectly good OS{win 8}.

---

### Post by mhpathfinder on 2012-11-27
> **Bigneil said:**
> Ok, so I need a little advice. 
My wonderful wife just bought me an early Christmas present,  an ASUS K55A notebook. (I'm a lucky guy, this is my first ever NEW computer).
It comes with windows 8 pre-insalled so normally I would just wipe windows and install ubuntu, I have been using ubuntu since Fiesty Fawn came out and used it almost exclusively since hardy heron . However, on this occasion I would like to keep windows 8 and dual boot.
So, I did what i always do, and popped in an ubuntu CD and this time installed it along side windows. All seemed to go very smoothly, so when prompted I popped out the disk and restarted only to be met with a message something like "no OS found" I can't remember the wording, sorry.
It reminds me of the time I once ruined GRUB. lol
So I was wondering if anybody else has tried ubuntu along side W8, and did you have any troubles? or was it a success?  did you have trouble then fiure it out?
The only thing I can think of right now is that windows was split into 2 parts, OS, and storage.... could it be that ubuntu needs to be installed on one rather than the other?
anyway, at the moment I am running the reset function  on the new computer to put it back to factory pre-set, Then I can start over again once I have armed myself with knowledge.
Thanks for reading

P.S I almost forgot to say It was 12.04

I bought a refurbished ASUS K54C w/ Win7.  One hardware note: I swapped out the 320gb hard drive for a Crucial M4 solid state drive.  Everything is so fast with it.
I went to ASUS site, upgraded all drivers and BIOS to Win8 64 bit. I DISABLED UEFI in BIOS after my BIOS update.  This may be important for you.  For more info on UEFI and when to disable or enable it for dual boot a post from 
Bhaismachine's Blog:
[http://bhaismachine.wordpress.com/2012/06/01/how-to-disable-uefi-and-dual-boot-ubuntu-and-windows-on-an-uefi-enabled-laptop/](http://bhaismachine.wordpress.com/2012/06/01/how-to-disable-uefi-and-dual-boot-ubuntu-and-windows-on-an-uefi-enabled-laptop/)
and
AskUbuntu.Com
[http://askubuntu.com/questions/130392/how-to-install-ubuntu-on-uefi-enabled-hp-pavilion-hpe-h9-tower](http://askubuntu.com/questions/130392/how-to-install-ubuntu-on-uefi-enabled-hp-pavilion-hpe-h9-tower)

I then upgraded Window 7 to Windows 8 Pro via the $39 upgrade download offer through Microsoft's site.  Smooth install and set up.

A few days later, I installed Ubuntu 12.10, creating my own partions with mount points / and /home and 5gb swap partition.  Smooth and fast install.
Rebooted.  Grub works--boots to either system.  No snags or crashes.
Everything works great in both systems.
Only one hitch:  I have to completely shut down Windows 8 after a Windows session, because it will not sleep while in Windows 8.  This is not an issue if I am in Ubuntu 12.10.  Sleep mode functions perfectly.  Minor hitch, because I work in Ubuntu most of the time.

I hope that some of this is helpful.  
MH
P.S. I'll have more on how these two systems function on a dual boot machine at [http://mhpathfinder.wordpress.com](http://mhpathfinder.wordpress.com).
I hope to learn a bit more about EFI and UEFI, and their differences.

---

### Post by Bigneil on 2012-11-27
That's an interesting thing about the SS drive .. I haven't been keeping with the times. I bought a 1TB pocket size external drive the other day, and couldn't believe how cheap it was, must be because every one wants SS drives now. I would certainly consider upgrading to one, the stock drive is pretty slow.

@ offgridguy. I actually wish i could safely get it to take up a lot less room though. this machine has a 1TB drive and 1/2 of it has all windows and windows backups and restore disks n stuff.

I partionioned off 100gb for ubuntu then shrunk the ntfs section called "DATA" and used the left overs to make a separate ntfs partion that I intend to be a storage area that both OS's can use safely without hurting the other.

and thanks again for the helpful replies.

---

### Post by rreyes3713 on 2013-01-03
> **Bigneil said:**
> LOL, I'm far too impatient. I couldn't resist just diving in and running boot-repair.

All is good and I can now use 'buntu or windows.:guitar:
So how did you fix it? I'm encountering the same problem. Only way I recover Window 8 is going through the bios and setting enabling  the "secure" boot but then there's no grub.

I could accept this because 85% of the time I'm using Ubuntu. The other 15% my girlfriend is using Window 8.

---

### Post by oldfred on 2013-01-03
You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)


If you installed in BIOS mode Boot-Repair will uninstall grub-pc and install grub-efi converting it to UEFI boot. And grub has  a bug on chain entries which Boot-Repair will also fix. Or you can manually add chain entries as shown in bug report.



       
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


       
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by moparfreak426 on 2013-01-23
i have the asus k55a and upgraded to windows8, it had windows 7 on it when bought. I just went back to 7 and finally got all my drivers downloaded and such.... i tried burning 64 bit 12.10 ubuntu to dvd, and installing... it said everything went well, however, it doesnt give me the option to boot ubuntu. i've read about disabling fastboot, and such.... it only gives me boot options when i hit esc on boot up.... someone wanna help? I REALLY wanna dual boot this thing? why do they make it so hard to do so? Thank you...

---

### Post by oldfred on 2013-01-23
@moparfreak426
You asked this in another thread & I created a new thread.

Please do not ask same question in mutiple threasd as we all are volunteers and need to see what others have already suggested. Generally best to have your own threads.
[http://ubuntuforums.org/showthread.php?t=2108008](http://ubuntuforums.org/showthread.php?t=2108008)

---

