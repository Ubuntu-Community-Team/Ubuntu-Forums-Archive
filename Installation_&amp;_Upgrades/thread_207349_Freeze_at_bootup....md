---
title: "Freeze at bootup..."
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by jsimmons on 2006-07-01
System: ASRock 939 dual sata2, amd64 3599, 1gb ram, a new nVidia 7900gtx, using onboard sound and onboard NIC, a new 200gb seagate EIDE harddrive a couple of SATA-1 drives, a new lite-on dvd writer, and a 19-inch LCD monitor. The SATA drives are running in SATA-1 mode, and I'm not using RAID (and SATA2 mode is disabled).

1) Booted CD, and selected "Install" on the desktop.
2) Used the entire hard drive for Ubuntu.
3) Everything appeared to install fine.
4) Clicked Restart Now button on "Installation Complete" dialog.
5) Hangs on message "Shutting down LVM volume groups..." (hard drive lightis i on steady the whole time).

After about 5 minutes, I got bored and did a hard reset.  The system starts to boot into Ubuntu, but freezes at the point where it's...

"Loading hardware drivers..."

The harddrive light stays on steady for about a minute and then turns off, but the system is still sitting at the status message shown above.

Does anyone have any ideas?

I then tried to install Breezy, and it choked on the network configuration, and then after detecting hardware, it froze at an empty blue screen.  After waiting about 10 minutes at the empty blue screen, I tried rebooting and it would go past the first grub message.

---

### Post by jsimmons on 2006-07-01
bump

---

### Post by jsimmons on 2006-07-02
I tried installing with the alternate CD and it froze during installation of system files at 97% with the status being "Cleaning up"

I'm going to try debian itself and see if that installs.  In the meantime, where's that support that the Ubunutu community is so famous for?

---

### Post by zasf on 2006-07-02
Same problem here on my server but laptop works.

I read a few threads, some people advise to remove 'splash' from kernel parameters in /boot/grub/menu.lst or to reinstall udev package. Neither of the two worked for me.

I'm trying to upgrade the system to the latest packages.. lets see.

---

### Post by jsimmons on 2006-07-02
I just tried burning the cd at 24x, and that didn't help (the first cd i burned at 48X).  I guess i'll try 12x and see what happens...

---

### Post by jsimmons on 2006-07-02
I didn't have a 12x burn option, so I tried it at 8x. That didn't work either. 

Knoppix 4.02 installed fine (except it couldn't find an "acceptable driver" for my video card), but that's not the distro i want to run.

---

### Post by jsimmons on 2006-07-03
Bump!

---

### Post by audaz on 2006-07-03
Both of my computers also freeze up while booting. They get to the loading hardware drivers and hang there for a while. My desktop will not boot it at all from this point.

On my laptop, I eventually get a text version of the login screen. When I put in my username and password, it says a few things really fast and then puts a bunch of lines that say 

-bash: /dev/null: Permission denied

What the heck is going on here? This is not the experience I have had with Ubuntu (I have installed every version since Warty on several machines!). Is Dapper just crappy?

---

### Post by jsimmons on 2006-07-03
[QUOTE=audaz]Both of my computers also freeze up while booting. They get to the loading hardware drivers and hang there for a while. My desktop will not boot it at all from this point.

On my laptop, I eventually get a text version of the login screen. When I put in my username and password, it says a few things really fast and then puts a bunch of lines that say 

-bash: /dev/null: Permission denied

What the heck is going on here? This is not the experience I have had with Ubuntu (I have installed every version since Warty on several machines!). Is Dapper just crappy?[/QUOTE]

Maybe it should have been called Deplorable Drake...

The part I don't understand is that the live CD boots up fine, yet the installer appears to be  brain dead...

---

### Post by jsimmons on 2006-07-03
Updated my machine's BIOS to the latest - 1.21 (or something like that). Tried again to install, and no joy. It hangs at various places during the removal process. Sometimes it gets stuck at ntsprogs, and sometimes other places, but it doesn't seem to want to go beyond 97%.

C'mon Ubuntu team. At least let me know that you're looking into the problem.

---

### Post by jsimmons on 2006-07-04
Bump

---

### Post by jsimmons on 2006-07-04
To recap:

**My system (a desktop system)**
ASROCK 939 Dual SataII, BIOS 2.27 dated 06/20/2006
AMD64 3500 Winchester
1gb (2x512mb) PC3200 RAM
eVGA 7900GTX PCIe video card
EIDE drives: Primary master= 200gb Seagate, slave=80gb Western Digital
SATA1 drives: 2x 160gb
SATA2 drives: NONE
1 Lite-On 48x DVD burner


**Other Notes:**
1) I'm not running RAID
2) I don't have any PCMCIA cards
3) SATA1 drives are set in the bios to behave like IDE drives.  
4) SATA2 controller is disabled
5) Using the onboard LAN and sound components
6) Nothing is overclocked.
7) I am NOT dual booting.
8 ) I'm trying to install Ubuntu onto the 200gb IDE drive.
9) The 2nd IDE drive has three FAT32 partitions
10) The 1st SATA1 drive has a single NTFS partition
11) The 2nd SATA1 drive has five FAT32 partitions
12) I can swap my boot drives out (this allows me to avoid dual-booting issues). These aren't hot-swappable or aything like that.


**The CD's I Have**
I've downloaded the 32-bit live cd, and burned it at three different speeds (48X, 24x, and 8X).

I've downloaded the 32-bit alternate CD, and burned it at 8x.

I've downloaded the 64-bit CD, and burned it at 8x.


**Problems**

1) The install has "completed" just 2 times.  Once with the 48x 32-bit, and once with the 24x CD.  By "completed", I mean it actually presented me with the dialog box that had the "Restart Computer" button.  In BOTH of those instances, the system was shutting things down, but hung up at the "Closing LVM Volumn Groups..." prompt (it had a status of "[ok]", but it just sat there with the hard disk light on steady).

At this point, the system was completely unresponsive. I could not use Ctrl-Alt-Del to reset the system, so I did a hard reset, and removed the CD at the earliest possible point so the system would boot from the hard drive.  Booting proceeded until it got to the "Loading hardware drivers..." prompt, and then hung at that point. Once I tried to Ctrl-C past this point, but it hung up on the next driver loading phase (I don't recall exactly what that status message said), but at that point, the entire system became unresponsive, requiring me to turn the machine off in order to swap my windows boot drive back into the system.

2) More often than not, the OS wouldn't finish installing at all. It almost always hung up when it reached the 97% point (removing unneeded packages).   Most of the time, it hangs up at "Completely removed ntfsprogs...", and other times it hangs up at various stages of the "removal" process.

I spent ALL DAY SUNDAY on the Ubuntu IRC channel, and nobody had anything there either, although one guy stuck with me almost the entire time trying to get me going (thanks, Jack-Sparrow, whoever you are).

**Comments**

Ya know, I've done everything I can think of, and posted here everytime I've tried something new.  I've spent four days of my time trying to install Ubuntu, and NOTHING HAS WORKED.  Even worse, I haven't seen a SINGLE RESPONSE from anyone directly (or even REMOTELY) connected with the OS.  I haven't even seen anyone say "hey we're looking into it...".

I hate to say it, but WHAT A LOAD OF CRAP!

Oh yeah - the thread has been read 171 times at the time I wrote this, but all I've seen is a mee-too post.

---

### Post by jsimmons on 2006-07-04
This post is being made from the live CD, so I know without a doubt that Ubuntu can handle my hardware...  I also hear the boot sound when the live CD boots.

---

### Post by jsimmons on 2006-07-04
I completely disconnected my SATA1 drives, and Ubuntu installs and boots up fine.  It seems that the kernel isn't prepared to deal with the ULI M1567 SATA Controller.

The next logical step is to putrchase a Linux-compatible SATA controller card ( I won't buy another motherboard just install Linux when Windows works fine with it), but I'm concerned that the kernel does not yet directly support a motherboard SATA controller that's at least a year old.

---

### Post by houstonbofh on 2006-07-04
[QUOTE=jsimmons]This post is being made from the live CD, so I know without a doubt that Ubuntu can handle my hardware...  I also hear the boot sound when the live CD boots.[/QUOTE]
You found the problem.  SATA is buggy on a lot of OS's.  (Some Windows implimentations require a dead chicken...)  If it is installing, but failing on shutdown, I have no help for you.  However, if it installs, but fails on reboot, you need a boot image with that driver.  The best post for this was for a DAC-960 raid controler at [http://www.ubuntuforums.org/showthread.php?t=79529](http://www.ubuntuforums.org/showthread.php?t=79529)

---

### Post by jsimmons on 2006-07-04
[QUOTE=houstonbofh]You found the problem.  SATA is buggy on a lot of OS's.  (Some Windows implimentations require a dead chicken...)  If it is installing, but failing on shutdown, I have no help for you.  However, if it installs, but fails on reboot, you need a boot image with that driver.  The best post for this was for a DAC-960 raid controler at [http://www.ubuntuforums.org/showthread.php?t=79529](http://www.ubuntuforums.org/showthread.php?t=79529)[/QUOTE]

I have another motherboard that had the same drives connected (2 IDE and 2 SATA1), and Linux installs just fine on that motherboard without having to disconnect the drives.

---

