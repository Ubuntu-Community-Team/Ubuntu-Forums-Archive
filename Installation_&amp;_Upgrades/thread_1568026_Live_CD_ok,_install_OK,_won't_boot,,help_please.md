---
title: "Live CD ok, install OK, won't boot,,help please"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by fatcatbaz on 2010-09-04
Hello Sorry for the noob question. My daughter really wants Ubuntu installed alongside windows vista on her PC. We tested the live cd and that all worked fine. we then repartitioned the C: drive through the Ubuntu installation process and installed Ubuntu, all ok. When we reboot you get the choices of Ubuntu and windows, when we select Ubuntu it starts to load and then comes up with a low graphics message and a check box asking to run in low graphics mode once. We we select O it moves on and then  and comes to a stop. A couple of times it reached a login screen and asked for login-Pword but stopped after that. I can't work out how to delete Ubuntu and start again. Any help or advise would be gratefully received.

---

### Post by -kg- on 2010-09-04
Please boot to the Live CD to the desktop, launch the terminal from "Applications/Accessories/Terminal" and run the following command:

```
sudo fdisk -l
```
(That's a lower case "-L", not the number one)

That command will show what partitions exist and what you're dealing with.  From that point we'll be able to suggest further steps to take.  What kind of computer it is and installed hardware would also be nice, especially what graphics card/chipset it is using, since the problem seems to be graphics related.

One thing; when you shrink a Vista partition, it's always better to shrink it using Vista's "Disk Management" rather than GParted.  There have been issues using GParted (which is what the installer uses) to shrink a Vista OS partition (and Windows 7, I would assume).  But done is done.  If you are still able to boot to Vista, no harm done.

Let's see what you have in the way of partitions, then go from there.

---

### Post by fatcatbaz on 2010-09-04
Firstly, many thanks for your very prompt response.

The partition is as follows:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25228   202641155+   7  HPFS/NTFS
/dev/sda2           29461       30401     7558582+   7  HPFS/NTFS
/dev/sda3           25228       29460    33995777    5  Extended
/dev/sda5           25228       29281    32551936   83  Linux
/dev/sda6           29281       29460     1442816   82  Linux swap / Solaris


The pc is a HP Compaq SR5219UK

AMD 64 Dualcore 4400+ 2.3 ghz

2GB ram

32bit

Graphics card nvida GeForce 6150se nForce430

It looks like we got away with using Gparted this time, windows vista still boots and runs.

Again many thanks for your help with this…

---

### Post by -kg- on 2010-09-04
The way it looks, it should work.  I don't know if there are any problems with that nVidea chipset, but I have an nVidea card in my desktop and have had no problems.  I also can't find any specific problems concerning it.

You might try a re-install...the first one might not have installed as expected.  You have two methods to do this.  The first method would be to launch the installer and, when you get to the Partitioning section, select "Manual Partitioning" from the selections.

When you are setting up the partitions, first select sda5 from the list, then select "Edit".  When you get that Window, you will need to select to reformat that partition to ext4, then you need to select the mount point as "/".

You shouldn't need to do anything with the swap partition.  It should be automatically used.

Then just run it through the rest of the installation as normal.  It should format sda5 and (re)install, and you'll soon see if it worked.

The second method would be to boot to the Live CD to the desktop, launch "System/Administration/GParted", and delete sda5 and sda6.  Once that is done, launch the installer and, when you get to the Partitioning section, select "Install to largest contiguous free space."  It will pick up the space inside the Extended partition and automatically create the "/" and swap partitions and install in them.

Use whatever method is more comfortable to you.

---

### Post by jeight on 2010-09-04
The only time I have run into a problem with low graphics mode on install was when the hard drive was failing. In your case though I would suggest that you partition your hard drive in Windows rather than using Gparted. To do this follow these steps.

1. Defrag windows. Make sure you defrag good. Sometimes using a free trial program like Perfect Disk works better.

2. Click start then go to computer but right click on it instead of left click. Choose manage.

3. I don't have a windows computer in front of me, but after that you should click something on the left side that refers to partitions.

4. Right click on current partition and select shrink volume.

Now after all this go ahead and try to install Ubuntu. Go ahead and use Gparted to install the systems side by side or using the biggest free space available.

---

### Post by JBAlaska on 2010-09-04
Before you try a reinstall:
Boot to the grub screen, press the e key, using arrow keys navigate to and delete quiet and splash and type the word ```
nomodeset
``` in their place
Press Ctrl and X to boot.

If Ubuntu boots, Install the latest recommended video driver in System, Administration, Hardware Drivers.

If Ubuntu does not boot, note any error messages and post them here.

---

### Post by fatcatbaz on 2010-09-04
I really appreciate the response from you all. It’s now 10:30 pm in the UK and my daughter is asleep, so we will pick this up again in the morning.

I just wanted to say thanks for your help….

---

### Post by fatcatbaz on 2010-09-05
Hi Guys

I followed the instructions regarding pressing “e” at the boot screen and replacing quiet and splash with “nomodeset”

This then ran though to a login and Pword prompt, after I entered the details it ran on and finished in the text screen with the following:

0 packages can be updated
0 updates are security updates

-bash: cannot create tempfile for here – document : no space left on device

lucy@lucy – desktop:~$

---

### Post by dino99 on 2010-09-05
hi,

as i've understood, now you can boot but got a low graphic issue, right ? Is it with Lucid & gnome or something else ? 

there you will find a little help about how to install ubuntu:
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

then into a console:

as actual kernel directly deal with X, remove your xorg.conf

sudo rm -f /etc/X11/xorg.conf

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

the next step is: reboot then check diver activation into: system admin additional driver, nvidia-current might be activated (nvidia-glx-173 in your case)

---

### Post by fatcatbaz on 2010-09-05
Hi

The Ubuntu version that I am trying to load  is 10.04 LTS Desktop edition. This is from a cd issued with PC Pro (UK) magazine Oct 2010 . The CD is branded Ubuntu and solely contains this version of Ubuntu. The live CD option works fine.

I have installed Ubuntu alongside Windows Vista using the options on the installation disk.

The boot screen loads up with the choice of Linux or windows. If I select Windows it loads and runs ok.

In the boot window I have 4 options for choosing Linux :

Linux 2.6.32.24 Generic, Linux 2.6.32.24 recovery, Linux 2.6.32.21 Generic, Linux 2.6.32.24 Recovery,




When I select Ubuntu  Linux 2.6.32.24 Generic,

It starts to load and displays the Ubuntu Logo with the dots below. The screen flashes on and off, followed by the message “your screen, graphics card and input device could not be detected. I click the OK button in the message box and another box appears asking to run in low graphics mode, I click Ok and a text screen appears. It starts checking a few items, however it then hangs after checking battery status.

- By  choosing the recovery version at the boot screen and then selecting continue with clean install, I get to a text based login, that works and appears to load the command line

I tried following the instructions in the previous posting, but I get an error message after typing:  sudo rm –f/etc/X11/xorg.conf

It tells me to check help for rm 

I guess the next step will be to delete the installation and try again.

Many Thanks for the replies. I am determined to get this working..

---

### Post by cwhamsun on 2010-09-06
I would think that video card would be sufficient, I have ubuntu running on far older nvidia cards. How large is your hard drive, and what size are each of those partitions you listed? 

Also, partition 3 being extended might cause some issues. You can have up to 4 primary partitions, so 4 would be the extended one. Having the kernel/boot directory in an extended partition can cause some problems.

---

### Post by -kg- on 2010-09-07
> **cwhamsun said:**
> Also, partition 3 being extended might cause some issues. You can have up to 4 primary partitions, so 4 would be the extended one.

Actually, he has three Primary partitions...sda1, sda2, and sda3, which is the Extended partition with sda5 and sda6 as Logical partitions within it.  Whenever you create Primary partitions, they are created using the lowest available designator, in this case sda3.  Position on disk has nothing to do with this, either.

In the case of Logical partition designators, it does.  If you have 3 Logical partitions, sda5, sda6, and sda7, and you delete sda6, sda7 will then become sda6, and if you create another partition in the free space left by the deleted (former) sda6, it will become sda7, regardless of order on the disk.

Not so with Primary partitions, though.  Once named, they remain that name. sda3 will remain sda3, even if you create a 4th Primary partition on the disk.

> Device Boot Start End Blocks Id System
/dev/sda1 * 1 25228 202641155+ 7 HPFS/NTFS
/dev/sda2 29461 30401 7558582+ 7 HPFS/NTFS
/dev/sda3 [COLOR="Red"]25228 29460[/COLOR] 33995777 5 Extended
/dev/sda5 [COLOR="Red"]25228[/COLOR] 29281 32551936 83 Linux
/dev/sda6 29281 [COLOR="Red"]29460[/COLOR] 1442816 82 Linux swap / Solaris

Note above that the start of sda5 is at the start of the Extended partition, and the end of sda6 is the same as the end of the Extended partition.

> **cwhamsun said:**
> Having the kernel/boot directory in an extended partition can cause some problems.

I don't know what problems it would cause.  Every single one of my three installed Linux OSes (Ubuntu, Fedora, and OpenSUSE) are installed completely in Logical partitions (which are contained within an Extended partition, which the OP's is, also. You cannot format or copy data to an Extended partition itself.), and I've had not a bit of problem with any of them.

I ***always*** install my Linux OSes in Logical partitions.  Linux runs from them...it's Windows that has to run from Primary partitions (in most cases).  In any event, it wouldn't cause graphic problems.

> **cwhamsun said:**
> How large is your hard drive, and what size are each of those partitions you listed? 

According to his fdisk -l output, he's got all kinds of room for the installation in sda5.  I just checked his output with the output for my Fedora installation, which is a little small, but quite sufficient, and he has roughly 4 times the space in his sda5.  It should be plenty.

---

### Post by fatcatbaz on 2010-09-11
Hi, I have reloaded Ubuntu by following the instructions: 

“You might try a re-install...the first one might not have installed as expected. You have two methods to do this. The first method would be to launch the installer and, when you get to the Partitioning section, select "Manual Partitioning" from the selections.

When you are setting up the partitions, first select sda5 from the list, then select "Edit". When you get that Window, you will need to select to reformat that partition to ext4, then you need to select the mount point as "/".

You shouldn't need to do anything with the swap partition. It should be automatically used.

Then just run it through the rest of the installation as normal. It should format sda5 and (re)install, and you'll soon see if it worked.”

The installation appeared to work fine with no errors etc

It boots to the bootloader screen OK and I select Ubuntu. It loads but there is no graphical interface. I get a request to enter - user and password (all via a text based screen).

It then stops at a flashing cursor that is proceeded with “desktop:~$

I’m not really sure what else to do…..

---

### Post by -kg- on 2010-09-14
Sorry that I just got back to this...I've been having a few issues of my own to resolve.

One thing you mentioned:

> **fatcatbaz said:**
> It boots to the bootloader screen OK and I select Ubuntu. It loads but there is no graphical interface. I get a request to enter - user and password (all via a text based screen).

It then stops at a flashing cursor that is proceeded with “desktop:~$

I’m not really sure what else to do…..

When you say you "select Ubuntu," how are you doing that?  You should see the GRUB menu, hit <Enter> and it should boot right in to Ubuntu without problem.

If, by saying you "select" it, you mean that you use the down arrow key to select it, then you are moving one selection down to the "Recovery" entry.  That would take you to a screen like you describe, which is a Command Line screen (with no GUI "Desktop").

Your GRUB menu should (approximately) show:

> Ubuntu 10.04.....
Ubuntu 10.04 (Recovery)....
Mem Test.....
Windows

Four selections, the first of which should already be highlighted and is the one you want.  You can also auto-boot into it by doing nothing when the GRUB menu comes up.  It will automatically boot into it after the timeout (10 seconds, I think).

That's the only thing I can think of that would take you to the display you describe.  If I misinterpreted your statements, then there are other problems causing the DE GUI not to load.

NEXT!...

I have just re-read the whole thread, and found that you listed all the selections in your GRUB menu, and what each got you, so you likely have other problems.

> I tried following the instructions in the previous posting, but I get an error message after typing: sudo rm –f/etc/X11/xorg.conf

Did you type it exactly as you posted?  There should be a space between "-f" and "/etc..."  If there wasn't, that would explain the error message.  If there's no space, the path and file would be included as an argument to the command rather than the target /directory/file. naturally, there's no such argument, so the system would tell you to check the help files for rm for it's proper usage.

The Live CD shows the desktop, so I can see no reason that the DE wouldn't be installed, loaded and run.  If it still takes you to the command line screen, you might try running the command "startx" (I can't remember whether it has to be run with sudo or not...if so, it would be "sudo startx") and see what that does.

---

