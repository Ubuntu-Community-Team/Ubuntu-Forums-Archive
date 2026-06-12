---
title: "GRUB/LILO single boot with XP"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by Asday on 2012-02-13
I've gotten in a bit of a weird situation.

My HDD died, (there are posts about it somewhere), and I reinstalled windows to a new HDD that arrived.

I didn't take the old HDD out, as it occasionally semi-works, and getting some more files off it would be cool.

Windows XP, in all its glory, decided that even though I'm installing to the new HDD, it should write the MBR to the old one.  Or append an entry to it or something.  I'm not exactly at home with knowing this.

Now, I've been googling from a livedisc for a fair while, and read fixboot;fixmbr posts, but they require a recovery console, (press "R" at some point when booting from the installation CD), but my windows disc doesn't have that.  I have an option for Automated System Recovery (what), but that asks for a floppy, and it's 2012.

I can't burn a new windows CD that I could get from legitimate sources, as I only have one CD drive, and Ubuntu doesn't like it when I remove its brain, and hangs before burning images.

SO.

I turned to LILO/GRUB.

Back in the days of my laptop working, I broke the MBR somehow on that, and managed to recover my Vista install, that I needed to keep the warranty alive, with LILO fairly easily.  I don't remember how I did it.

I tried installing LILO, (sudo lilo -M /dev/sdwhatever mbr), but that just gets rid of the BIOS throwing a fit 'cause there are no MBRs around, and instead LILO (I think) complains about NTLDR not being there; likely due to the windows installer being glorious.

I was about to install GRUB, but I figured that I have no idea how to use it, and LILO seems to work, so doing more stuff may mess it up.

Instead, I come here, to the endless fountain of knowledge and awesomeness, to plead.

Thanks for your eyes.

EDIT:  I also have this.  Not sure if it helps.  [http://paste.ubuntu.com/840755/](http://paste.ubuntu.com/840755/)

---

### Post by Quackers on 2012-02-13
Is the 1500GB drive the new one? 
You don't appear to have any Windows boot files on either disc.
Is your bios set to boot from the new drive, or still from the old one?

I would suggest temporarily disconnecting your original drive and try re-installing Windows again to the new drive, making sure the bios is set to boot from that drive.

---

### Post by Asday on 2012-02-13
> **Quackers said:**
> Is the 1500GB drive the new one? 
You don't appear to have any Windows boot files on either disc.
Is your bios set to boot from the new drive, or still from the old one?

I would suggest temporarily disconnecting your original drive and try re-installing Windows again to the new drive, making sure the bios is set to boot from that drive.

500 has a primary partition with windows on it.

I believe the boot files are on the broken drive, which is unusable.

The BIOS is booting from the right disk.

Reinstalling is something I would very *very* much prefer to avoid.

EDIT:  The broken drive is now disconnected completely, by the way.  From now on, I'm regarding it as dead.

---

### Post by Quackers on 2012-02-13
Sorry, things aren't clear for me.
Is the broken drive the 500GB drive in the bootinfor script, or is it the 1500GB drive, or is it another drive entirely?
Which drive is your bios trying to boot?
When you "re-installed" Windows to the new drive, how did you do that please? With a Windows installation disc,or some other means.

---

### Post by Asday on 2012-02-13
> **Quackers said:**
> Sorry, things aren't clear for me.
Is the broken drive the 500GB drive in the bootinfor script, or is it the 1500GB drive, or is it another drive entirely?
Which drive is your bios trying to boot?
When you "re-installed" Windows to the new drive, how did you do that please? With a Windows installation disc,or some other means.

I have 2 drives pertaining to the situation.  There is the 500GB drive shown there, which is working, and has windows installed.  There is a 500GB drive not connected, which is broken, and contains boot information of some sort.  The 1500GB drive is unrelated.

The BIOS is trying to boot the 500GB, which has LILO on it, which complains about no NTLDR.

I installed windows to the new 500 while the old 500 was still in the PC.  As it had a windows install on it, I assume the install disc just elected to use the existing MBR on the faulty 500 (which is now dead), instead of writing it to where it should; the new 500.

EDIT:  And while I'm here, why am I not getting email notifications of posts in this thread?

---

### Post by oldfred on 2012-02-13
Grub normally defaults the install of the boot loader to sda. Windows seems a tad smarter in that it installs its boot loader to the drive you have set in BIOS to boot from which again is usually sda but not always.

Windows can only boot from one active (boot flag) partition, so it literally moves the boot files from a second install to the first and updates the BCD (for Vista/7) or boot.ini (XP) to allow booting either install.

You may be able to move the boot files from your nonworking drive if you can to the working install.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Most of XP can be repaired from Ubuntu. chkdsk is one thing you have to run from a Windows repair console.

How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Herman on booting XP in logical
[http://ubuntuforums.org/showthread.php?p=4701367#post4701367](http://ubuntuforums.org/showthread.php?p=4701367#post4701367)

---

### Post by Quackers on 2012-02-13
To get email notifications you need to click on the Thread Tools near the top of this page and select "subscribe to this thread". 
If you have already done that it can sometimes be a while before emails are received.

Lilo is not showing as being installed in the MBR of /dev/sda. It shows Syslinux MBR. I've not personally used Lilo, but, from memory if it's installed I think it should show as Lilo, not Syslinux (but I could be wrong).
How did you install Lilo?
Was it like the method in post #4 here?
[http://ubuntuforums.org/showthread.php?t=1911968&highlight=lilo](http://ubuntuforums.org/showthread.php?t=1911968&highlight=lilo)

Even if Lilo is installed to the MBR, Windows will not boot without NTLDR, and NTLDR is not showing on your system as being installed.

EDIT  And see above post :-)
Have a look at the section headed "Corrupt NTLDR or NTDETECT.COM file" for the XP users in the link below.
[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

---

### Post by Asday on 2012-02-13
> **oldfred said:**
> Grub normally defaults the install of the boot loader to sda. Windows seems a tad smarter in that it installs its boot loader to the drive you have set in BIOS to boot from which again is usually sda but not always.

Windows can only boot from one active (boot flag) partition, so it literally moves the boot files from a second install to the first and updates the BCD (for Vista/7) or boot.ini (XP) to allow booting either install.

You may be able to move the boot files from your nonworking drive if you can to the working install.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Most of XP can be repaired from Ubuntu. chkdsk is one thing you have to run from a Windows repair console.

How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Herman on booting XP in logical
[http://ubuntuforums.org/showthread.php?p=4701367#post4701367](http://ubuntuforums.org/showthread.php?p=4701367#post4701367)

Right, my dead HDD works around once every 8 power cycles, (like, turn it off, then on), so I'll do that in a few reboots.

In the meantime, are they mildly generic files?  Can I, if those are unaccessible, download some off the internet somewhere, and just change a few things to point to wherever they need to on my setup?

> **Quackers said:**
> To get email notifications you need to click on the Thread Tools near the top of this page and select "subscribe to this thread". 
If you have already done that it can sometimes be a while before emails are received.

Lilo is not showing as being installed in the MBR of /dev/sda. It shows Syslinux MBR. I've not personally used Lilo, but, from memory if it's installed I think it should show as Lilo, not Syslinux (but I could be wrong).
How did you install Lilo?
Was it like the method in post #4 here?
[http://ubuntuforums.org/showthread.php?t=1911968&highlight=lilo](http://ubuntuforums.org/showthread.php?t=1911968&highlight=lilo)

Even if Lilo is installed to the MBR, Windows will not boot without NTLDR, and NTLDR is not showing on your system as being installed.

EDIT  And see above post :-)
Have a look at the section headed "Corrupt NTLDR or NTDETECT.COM file" for the XP users in the link below.
[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

I installed it with "lilo -M /dev/sdsomething mbr".

I think I understand more about the problem now, thanks to you and Oldfred.

I'll be back in a few.

EDIT:  Ok, first time's the charm, it seems.  here's how my drives look, now:

[http://i.imgur.com/8zmHA.png](http://i.imgur.com/8zmHA.png)

There are 4 other files that I didn't have on hope (the new one); autoexec, config, io, and msdos.

While I have the drive alive, in whatever small measure, should I copy those over, too?  Or at least back them up somewhere more readily accessible?

EDIT2:  Sorry for the image confuddles.  I linked the wrong one.

---

### Post by darkod on 2012-02-13
OK, here is a suggestion:
1. Temporarily disconnect the 1.5TB disk so it doesn't get into the way.
2. Leave only the 500GB disk, or even better move it to the first sata port on your board, it might be called SATA0 or SATA1, depending.
3. The boot flag is already on the first partition of your 500GB, don't touch it.
4. From ubuntu live mode install the lilo boot process on the 500GB disk, it doesn't seem installed right now. You install it with the command you already mentioned:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

5. Again from live mode, visit this post:
[http://ubuntuforums.org/showpost.php?p=5082723&postcount=1](http://ubuntuforums.org/showpost.php?p=5082723&postcount=1)

and towards the bottom download the attachment. It has all three XP files you need, for a standard setup (XP installed on the first disk on the first partition). Should work without any changes for you. Extract that archive and copy all three files to /dev/sda1.

Restart without the ubuntu cd and see if it worked. It should.

---

### Post by Asday on 2012-02-13
> **darkod said:**
> OK, here is a suggestion:
1. Temporarily disconnect the 1.5TB disk so it doesn't get into the way.
2. Leave only the 500GB disk, or even better move it to the first sata port on your board, it might be called SATA0 or SATA1, depending.
3. The boot flag is already on the first partition of your 500GB, don't touch it.
4. From ubuntu live mode install the lilo boot process on the 500GB disk, it doesn't seem installed right now. You install it with the command you already mentioned:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

5. Again from live mode, visit this post:
[http://ubuntuforums.org/showpost.php?p=5082723&postcount=1](http://ubuntuforums.org/showpost.php?p=5082723&postcount=1)

and towards the bottom download the attachment. It has all three XP files you need, for a standard setup (XP installed on the first disk on the first partition). Should work without any changes for you. Extract that archive and copy all three files to /dev/sda1.

Restart without the ubuntu cd and see if it worked. It should.

I've just pulled those three files from my faulty HDD, so hopefully they'll work too.

Why isn't LILO installed if I used the right command?  The only message it came up with was something about being configured, but for reasons I forget, I dismissed that as something of a side-effect of being run from a livedisc.

Also, are you sure?  I get a different message from the BIOS now, from before I ran the command.  ("DISK BOOT FAILURE, PRESS ANY KEY TO RESART" became "NTLDR is missing, bro.  You should check that out.  Feels weird.")

---

### Post by darkod on 2012-02-13
The message about lilo not being configured should be ignored, it's normal since you will only be using part of lilo that you need.

I am not 100% sure that lilo is not installed but according to the link you posted, it said Syslinux is installed on /dev/sda. For lilo it should literary say "lilo is installed on /dev/sda".

At least that's how it was earlier. I would install it again, it can't hurt.

Whether your XP files will work or not also depends if your disk was first, second, etc. But copy them and lets see.

---

### Post by Asday on 2012-02-13
> **darkod said:**
> The message about lilo not being configured should be ignored, it's normal since you will only be using part of lilo that you need.

I am not 100% sure that lilo is not installed but according to the link you posted, it said Syslinux is installed on /dev/sda. For lilo it should literary say "lilo is installed on /dev/sda".

At least that's how it was earlier. I would install it again, it can't hurt.

Whether your XP files will work or not also depends if your disk was first, second, etc. But copy them and lets see.

```
ubuntu@ubuntu:~$ sudo lilo -M /dev/sdc mbr
Backup copy of /dev/sdc in /boot/boot.0820
The Master Boot Record of  /dev/sdc  has been updated.
ubuntu@ubuntu:~$ liloconfig
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "config": could not write /var/cache/debconf/config.dat-new: Permission denied
ubuntu@ubuntu:~$ sudo liloconfig
ubuntu@ubuntu:~$ 

```

Both runnings of liloconfig resulted in the same message about fstab being unwritable, or something.  As to be expected.

Ok, here we go.  Wish me luck.

---

### Post by darkod on 2012-02-13
We just said to ignore any messages about the config, just run the one command.
And why are you installing on /dev/sdc?

---

### Post by Asday on 2012-02-13
> **darkod said:**
> We just said to ignore any messages about the config, just run the one command.
And why are you installing on /dev/sdc?

Was just running config to see what would happen.  As far as I could tell, it wouldn't do anything without further action, so no harm in having an explore.

Installing on /dev/sdc 'cause it picked up the drives in a weird order that boot.  Broken drive was sdb, the storage drive was sda, and the boot drive was sdc.

I booted up again, and it complained about hal.dll being missing.

Being the genius I am (that can't work out how to copy ntldr without excessive amounts of help :-&), I diagnosed that this wasn't due to it actually being missing, but that the boot.ini from my old drive was still referring to things from the old drive as it was no longer connected.

Gedit helped me solve that fairly painlessly, and I'm back in windows now.  Time to play some SC2.

Thanks for all your help, guys, I really appreciate it.

---

