---
title: "another grub error 15"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by redfox on 2005-08-15
HP laptop 20 GB HD partitioned with knoppix in order to have 6 GB or so for a Ubuntu dual boot.  First install didn't come out right (ShipIt CD).  The main sign in screen was all screwy and I couldn't get the password to go through.  Reinstalled with another ShipIt disk, deleted partitions (keeping the 13 GB XP partition), let the install automatically format the 6 GB or so.  Install hung shortly thereafter.

Turned the computer on again.  It started to dawn on me that I should've been told to take the CD out.  GRUB error 15.  Jump into BIOS.  BIOS shuts down on me.  I'm now a little worried that the BIOS is fried.  Can't boot off the Ubuntu disk.  I start to get a little freaked out.

After sitting around thinking about the problem, both Ubuntu and XP disks boot.  I decide to get into XP recovery and rewrite the MBR so I can get into XP and back up some stuff (oh the horrors of not backing up).

Now I get a line that says "error loading operating system."

So..., how deep am I in?  The fact I'm a n00b doesn't help.

Edit: This should actually be on the HH installation help board.  Can I get it moved?

---

### Post by amohanty on 2005-08-15
Download a win98se boot disk from [www.bootdisk.de](www.bootdisk.de). Boot up with it. AT the command prompt type:
fdisk /mbr

Reboot into Ubuntu recovery mode and reinstall grub in mbr.

HTH
AM

---

### Post by redfox on 2005-08-16
Why download the 98 boot disk instead of an XP boot disk?

---

### Post by amohanty on 2005-08-17
Its simpler, only one floppy instead of four, although it does not recognize ntfs, it doesnt matter because it simply resets the MBR to a stable state from which the XP recovery can ... well recover.

AM

---

### Post by aaRonm on 2005-08-17
Well just do this, insert knoppix and fixed up the grub and then boot up from there

---

### Post by redfox on 2005-08-17
What I need most is to fix the MBR to get back to XP.  I'm pretty sure whatever Ubuntu I have on the other partitions is screwed up enough to not be worth saving.  So I'm going to try to get back to Windows, save some data, and then clean install both.

Hopefully I'll have two clean OSs up by tomorrow evening.

Thanks for the help.

---

### Post by redfox on 2005-08-17
:sad:  Well, that didn't work.  I'm still getting the error loading operating system line.  I've been wondering about my A drive for a while, but I haven't tested it in a stable condition.  The boot disk works on another computer.  The A drive must be toast.

Does anybody know how to use the XP install disk to rescue files off the inaccessible windows partition?  The command line recognizes the partition.  I've deleted the linux partitions, and just want to save two or three files before I nuke everything and get the dual boot straight.

---

### Post by amohanty on 2005-08-18
If you have a usb drive just boot into knoppix (as aaRonm suggested), mount the ntfs drive, copy the files over. Or if you have a LAN, do the same, mount a remote drive via smbfs and copy the files off to that.

AM

---

### Post by redfox on 2005-08-18
Sounds like a good plan.  I'll give it a shot.

---

### Post by Jedi on 2005-09-10
[QUOTE=amohanty]If you have a usb drive just boot into knoppix (as aaRonm suggested), mount the ntfs drive, copy the files over. Or if you have a LAN, do the same, mount a remote drive via smbfs and copy the files off to that.

AM[/QUOTE]

How do you do that?  I'm in a similar situation but don't know how do get to NTFS drive from Knoppix

---

### Post by Game master pro on 2005-09-10
This happened to me on a windows 98 computer, what i did was re install windows but i only selected the option to overright system files, so i kept all my data, after that i reinstall ubuntu again, worked fine with me

---

### Post by iansstar on 2007-08-01
To be able to get into your windows X P  just reinstall ubuntu and it will reinstall your grub boot loader. iansstar

---

### Post by push_harder on 2008-01-23
I tried this, but at 69% is said HDD is either faulty or disk is faulty.
So i burnt a new copy of ubuntu at the slowest speed and the same thing.
I have seriously tried alot of methods, even force mounting, but i just can't seem to access the drive with out useing TestDisk, even then, that's stone age Terminal and it's ******* hard to do.

I'm about to give up

I have a full Vista partition now and running off Live CD

My problem began when i just reformatted the ubuntu partition because i needed the space. and i rebooted and got error 17.
Then i used TestDisk and it lowered it to error 15.

Makeing little progress.

Any ideas?

---

### Post by push_harder on 2008-01-23
Anyone?

---

### Post by push_harder on 2008-01-23
This is doing my Fuc**** head in.
UGH!.

Ha.

---

### Post by Sam Lars on 2008-02-01
When this has happened to me before, I think it's always been that I'd forgotten to properly seat the IDE cable on the HD or MB.
I found this code [here]("http://www.linuxquestions.org/questions/fedora-35/new-fc5-installation-grub-error-15-429075/"):

```
chroot /mnt/sysimage
grub-install --recheck /dev/hda
exit
exit
```

I'm not sure if that would work, but it should give you the idea...

---

### Post by bronxbomberz41 on 2008-02-16
Hi,

I am trying to reinstall Ubuntu (gutsy) and I am having issues.  The reason i am reinstalling is because i was trying to burn some DVDs and there was some sort of error and my computer froze.  Upon restart I could not load Ubuntu.  I tried using an Xubunut live CD to look at my hard drive and see if I could mount it and I could not.  One of my friends who happens to know more about both computers and linux in general than i do looked at it and after playing with it for about a week he says he was able to use a live cd to locate and mount my hd.  He gave me an Ubuntu live CD and I assumed i could handle a reinstall from there.  Now when I am trying to reinstall ubuntu i get the Error 15 message.  I don't have any partitions or other OSes on the computer.  I don't have a USB drive with something like Knoppix or something on it.  Is there anything I can do?  I am not as savvy as some of you on here might be so bare with me.  This is really frustrating for me and I don't know what to do.  PLEASE HELP!!!!

Thanks!!:)

---

### Post by hchanman on 2008-02-28
is it bad if i tried to reinstall kubuntu and i got a "fatal error, grub failed to install" or something similar

---

### Post by Sam Lars on 2008-02-29
Is that during the setup?  Try running the setup again (and again, etc.).  Sometimes errors like that on install don't come up later.

---

### Post by bronxbomberz41 on 2008-04-28
for anyone out there who may be wondering I got it working about a month or two ago...i used the Super Grub Disk and was able to repair the grub on my computer.  I then used the Xubuntu disk I had for my gf (didn't have an ubuntu disk) and then was able to download all the gnome packages and desktop and got rid of the xfce desktop.

---

