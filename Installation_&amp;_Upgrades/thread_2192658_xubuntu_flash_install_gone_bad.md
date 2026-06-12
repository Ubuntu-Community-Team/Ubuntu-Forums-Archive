---
title: "xubuntu flash install gone bad"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by natebaux on 2013-12-09
im trying to get a new machine going....again. i had it running, and after an unfortunate  reboot, will no longer boot into the flash drive like it once did.

i used unetbootin to install xubuntu 12.10-64 to a new 8 gig sandisc cruzer drive. this drive was going to install to another identical drive. after the tragic reboot, neither the newly installed drive, nor the installer, would boot to anything other than the grub 2.0 ubuntu screen. i tried to use another drive to install the livecd to, but the result is the same. grub.

 on occasion, for a nano-second, i can see the message "secure boot not enabled" before the grub screen appears. before all this i had full access to the livecd, and the new install flash drive.

ive tried to make the installer flash drive using unetbootin a few more times and the result is always the same. no desktop, only the grub screen. no menus or selections. a black screen that says with a prompt "grub_".

it worked the first time, as i had the menu choices of install or try xubuntu. i survived at least 20 reboots with no problem. well, once i made the appropriate settings in the uefi. i thought maybe my iso became corrupted, so i deleted and tried again. same result. no desktop, only grub.

why wont my livecd get to instillation? 

the first time making the livecd with unetbootin, the one that worked and was able to issue a successful install to another drive, it was performed on a windows 7 machine. 

the new machine, the one i can no longer get to boot from a xubuntu live cd,  is an asrock 970 extreme 4
seasonic 1250 gold
semperon 145
asus r9 280x
crucial ddr3 1333 1x4 gig

if ive left anything out, or been unclear, feel free to ask.

---

### Post by ajgreeny on 2013-12-09
> **natebaux said:**
> im trying to get a new machine going....again. i had it running, and after an unfortunate  reboot, will no longer boot into the flash drive like it once did.

[COLOR=#ff0000]1)- i used unetbootin to install xubuntu 12.10-64 to a new 8 gig sandisc cruzer drive.[/COLOR] this drive was going to install to another identical drive. after the tragic reboot, neither the newly installed drive, nor the installer, would boot to anything other than the grub 2.0 ubuntu screen. i tried to use another drive to install the livecd to, but the result is the same. grub.

 on occasion, for a nano-second, i can see the message "secure boot not enabled" before the grub screen appears. before all this i had full access to the livecd, and the new install flash drive.

ive tried to make the installer flash drive using unetbootin a few more times and the result is always the same. no desktop, only the grub screen. no menus or selections. a black screen that says with a prompt "grub_".

it worked the first time, as i had the menu choices of install or try xubuntu. i survived at least 20 reboots with no problem. [COLOR=#ff0000]2)- well, once i made the appropriate settings in the uefi.[/COLOR] i thought maybe my iso became corrupted, so i deleted and tried again. same result. no desktop, only grub.

why wont my livecd get to instillation? 

[COLOR=#ff0000]3)- the first time making the livecd with unetbootin[/COLOR], the one that worked and was able to issue a successful install to another drive, it was performed on a windows 7 machine. 

the new machine, the one i can no longer get to boot from a xubuntu live cd,  is an asrock 970 extreme 4
seasonic 1250 gold
semperon 145
asus r9 280x
crucial ddr3 1333 1x4 gig

if ive left anything out, or been unclear, feel free to ask.
I'm a little confused, so here are three questions back to you about your comments I've shown in red.

1)  Was this a full installation to the flash drive or did you just make a live USB system?
2)  What exactly were these changes you made to UEFI, and why did you make them after managing to use the drive previously?
3)  Are you sure you used unetbootin to make a live CD?  I thought it was only for making live USBs, but I don't know if things are different when using Windows.

---

### Post by natebaux on 2013-12-09
1) i used unetbootin to make a bootable flash drive to install xubuntu to an identical flash drive, that would stay on the machine.

2) correction. i changed the settings in the uefi to allow the machine to boot from the flash drive. choices were usb, and uefi-usb. i also set it to accept legacy support. these changes were made before, not after i successfully booted then installed to another flash drive. as of now, i can only get it to boot to the flash drive with uefi set to uefi-usb.

3) my bad, you are correct, i made a live usb, containing xubuntu 12.10 desktop amd64. my intention was to use it to boot the new machine, and install xubuntu to the 2nd flash drive. which i successfully did. now, after the new rig froze and i had to do a manual power reset, it no longer boots into desktop, even with a live usb. not the old one, not a new one. ive made several since then, reformatting the drives and starting over. it boots to the gnu grub 2.0-7ubuntu11, a black screen, with this message (minimal BASH-like line editing is supported. for the first word, TAB lists possible command completions. anywhere else TAB lists possible device or file completions.) then the following prompt, grub>_.

---

### Post by ajgreeny on 2013-12-09
> As of now, i can only get it to boot to the flash drive with uefi set to uefi-usb.
I think this points to the probability that your machine is set to the wrong UEFI booting system for the flash drive that you've made.

Have you read and followed all the info at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") as this is the "bible" for using UEFI with Ubuntu, in my opinion.  I suggest you use UEFI if it is possible as it is the way forward, and in the long run will solve many potential problems.

---

### Post by natebaux on 2013-12-09
> **ajgreeny said:**
> I think this points to the probability that your machine is set to the wrong UEFI booting system for the flash drive that you've made.

Have you read and followed all the info at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") as this is the "bible" for using UEFI with Ubuntu, in my opinion.  I suggest you use UEFI if it is possible as it is the way forward, and in the long run will solve many potential problems.

im going to say you were partially correct. any settings that were not uefi, resulted in a disc read error. even the uefi settings would not fix the problem, which was the lack of a efi partition. im not sure why my first attempt contained one, and the subsequent ones did not. they were all constructed using Unetbootin and the same iso. i even deleted the iso and Unetbootin, on the chance the dl was corrupted.

 my solution was after determining that i was lacking an efi partition, was to use Rufus. ole' Ruffie will take care of you. when i booted, it still booted to the grub menu, but unlike the prompt i was experiencing earlier, this a was a menu, giving me the choice to try or install. installation is currently underway. but, it still was not like the FIRST time, with the pretty colored background, just a black and white, no frills menu. 

Troops, i know its hard. i know its frustrating. you just might have to walk away for a while. come back later when you arent as likely to flame out, and throw everything out the window. i see traces of frustration turning to rage in some posts. ive been there. read, listen, learn.

 "Fdisc this! im moving where there is no electricity. problem solved!"

---

### Post by natebaux on 2013-12-09
sudo apt-get thank-you

---

### Post by ajgreeny on 2013-12-10
I presume from your timing of the thanks that you did get eventually the system working properly; correct?

This UEFI is causing a lot of difficulties for new users most of whom are used to legacy BIOS, but as I said, once you get the few bits and pieces such as the EFI partition on the system sorted out as they should be, it does have some advantages over the legacy system, such as increased speed and an unlimited number of primary partitions on disk, (OK, I know there **is** a limit, but I doubt many users will ever get to it).

---

