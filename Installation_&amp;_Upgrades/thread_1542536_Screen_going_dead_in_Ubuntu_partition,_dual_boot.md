---
title: "Screen going dead in Ubuntu partition, dual boot"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by Nick_Jinn on 2010-07-30
This is weird. This is an HP desktop that comes with an install disk that does its custom setup....factory defaults dont allow any partitioning or custom setup. 

So when I try to install Ubuntu or Mint the screen 'goes to sleep' and wont let me install.....However, this does NOT happen when I use Knoppix live disk and I also seem to be able to install GOS Gadgets and it works and loads perfect. Ubuntu wont however.....Suse will let me install, which is better than Ubuntu, but the same dead screen comes up when I log in or try to.....Only GOS and Knoppix seem to be working so far, but I really want Mint or Ubuntu on this PC, not GOS or Suse. Im not sure how Knoppix would be as a full time desktop.....Are there any good Knoppix based operating systems out there?

Anyway, I would like to trouble shoot this. Could the problem be because I tried doing the manually installation with the custom partitioning? I read this can cause problems. Should I delete the partitions, expand the NTFS partition again then try again only with the shrinking and installing side by side option? Or should I reinstall Windows all over again and install either with Wubi or with the side by side option?

I wonder if I could isntall mint if I remove Windows entirely. They said they are not attached to it, but i would prefer giving them the option just in case they were attached to something windows only.

---

### Post by Nick_Jinn on 2010-07-30
I deleted Windows entirely, and the same problem is happening on a clean installation on an empty hard drive. The screen goes dead or says its going to sleep, but I cant wake it up by typing or using the mouse. Its like there is no X desktop environment to be found. I have tried using multiple disks. This is only happening on this one HP machine.

Why would Knoppix and GOS work but not Ubuntu or Mint?

---

### Post by arpanaut on 2010-07-30
Spec's of machine might be helpful...

---

### Post by Nick_Jinn on 2010-07-30
2.something ghrz dual core Athlon 64
1gb of RAM, or it shows up as 960 rather than 1gb.
I dont know anything about the graphics card. I guess I could plot in a live disk to find out.

The graphics is Nvidia 6150 LE.

PC model number is a1600N


I wonder if the recovery partition for windows is hidden. Its still showing up as 180gb out of 200 even after I deleted everything.

---

### Post by Nick_Jinn on 2010-07-31
Still not solved.


Any idea why some distros show up on the moniter while others produce a blank screen and the PC goes to sleep?

---

### Post by oldfred on 2010-07-31
I have a newer nvidia and had to do this. My monitor would go to sleep but the install was still working as my USB was still flashing.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I edited my grub.cfg as I use grub to boot ISO on USB, or in other USB's syslinux.cfg or text.cfg(
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

---

### Post by Nick_Jinn on 2010-08-01
Its the damndeset thing, but Ubuntu Jaunty and even Karmic worked (But the equal version of Mint didnt work). 10.04 based systems dont work. 

Thank you for the help....I am a noob so I might need a more step by step run down of some of your tips.




Is there still a problem with video card drivers no longer working when you upgrade? Could I use a previous version then upgrade if I use one of the programs that lets you install the proprietary drivers not from the repositories?


There needs to be a solution to these repository conflicts. There needs to be a way to make them backwards compatible.

---

### Post by Nick_Jinn on 2010-08-01
My client wants Mint, since its just a little easier than Ubuntu for noobs...basically it is Ubuntu...Anyway, I dont see a 'nomodset' option. 

I cant even seem to get it installed due to the screen going to sleep.

---

### Post by Nick_Jinn on 2010-08-01
Maybe if I install from USB drive, copy the USB drive to the hand drive to the internal hard drive with the driver already installed....would that work?


I hope this bug is addressed in future installations. I almost think this warrants updating the main image since this cant be fixed by update if you cant even install.

---

### Post by oldfred on 2010-08-01
I install from a USB flash drive but not the standard version as I use grub2 and I edit the grub.cfg to include the nomodeset. 
I think with the more standard Flash drive with syslinux there is a syslinux.cfg or text.cfg that is like the grub menu and you can directly edit it to include the nomodeset command on the kernal line and/or replace the quiet splash commands.

---

### Post by Nick_Jinn on 2010-08-01
I bet your right, but I am still learning all this :)


I am looking for a solution that is more fool proof and less technical, even if it takes longer. I dont care if I have to upgrade twice in a row and install all the updates 3 times, or install a Fluxbox version then add the Gnome environment with Aptitude.....I just want to work within the skill sets I have or have some dummy proof instructions.

---

