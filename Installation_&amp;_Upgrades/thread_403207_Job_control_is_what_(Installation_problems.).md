---
title: "Job control is what? (Installation problems.)"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by Halfling Rogue on 2007-04-06
Hey there, I'm a relatively new user who started using Ubuntu a number of months ago; my latest laptop kicked it in terms of hardware, and I got a used IBM ThinkPad to replace it (which had Windows 98 on it). However, I'm encountering a problem when I try to install Dapper from the desktop cd. It starts just fine, and when I select 'start or install Ubuntu' it begins the process like it's supposed to. But then partway through the second step I get this:

> Uncompressing Linux... Ok, booting the kernel.

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#ls

bin      etc    linuxrc   proc     sbin    tmp      var
dev     lib      mnt      root     sys      usr

#

I thought it might be Windows interfering, so I had the primary partition wiped, but I'm still getting the error message when I try to install. I can access commands from that point (I tried ls and got a listing), but I have no idea what I should do to get it working. Help?

---

### Post by Halfling Rogue on 2007-04-06
**ETA:** I found [this]("http://www.linuxquestions.org/questions/showthread.php?t=474493") and [this]("http://www.uclibc.org/FAQ.html#job_control") via Google but I don't know enough about coding to understand most of the suggestions, and ones I *do* understand require actually being able to get to the desktop, which I can't do. Should I just try for another laptop or what?

---

### Post by Halfling Rogue on 2007-04-06
Right, so, I tried messing around a bit. I was able to change directories to /bin and so on, but if I tried to move any further I'd get the error **cd: 24 can't cd to /busybox**. The number changed depending on which dir I was trying to change to. Eventually I tried the exit command and got this:

> #exit
cp: unable to open 'root/var/log/': No such file or directory
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

r
BusyBox v1.01 etc. etc. (same as first post)

Then I tried ejecting the CD, and when I did I got this message:

> #[   102.490768] irq 15: nobody cared (try booting with the "irqpoll" option)
[  102.500603] handlers:
[  102.510003] [<c02521a0>] (ide_intr+0x0/0x200)
[  102.519601] Disabling IRQ #15

And then it went back to the "/bin/sh: can't access tty" message. No idea if this helps anyone understand what's going on, because I sure don't.

---

### Post by wpshooter on 2007-04-06
Rogue:

What version of Ubuntu are you trying to install ?  Dapper, Edgy or Feisty ?

If it is Feisty, I would suggest that you (for now) move back to either Dapper or Edgy.

I have gotten the error you are referring to at various times while I was test installing the Feisty BETA versions.

I have inquired numerous times regarding this error and have yet to get a satisfactory explanation as to the cause which makes any sense.  There are a number of threads on these forums regarding this error type and it has been reported as a bug by me and I am sure a number of other parties.

Good luck.

---

### Post by Halfling Rogue on 2007-04-06
wpshooter:

Nope, it's Dapper, not Feisty or Edgy. I guess I'll just have to try another laptop.

---

### Post by Halfling Rogue on 2007-04-06
. . . Or, as it turns out, my supplier doesn't *have* another used laptop in my range. So I guess I'll keep trying with this one. Here's more documentation, for all that it might help somebody (although at this point I'm mostly recording it on the off chance that I get the thing to work).

> #sh init
mkdir: Cannot create directoy '/sys': File exists
mkdir: Cannot create directoy '/proc': File exists
mkdir: Cannot create directoy '/tmp': File exists
mount: Mounting none on /sys failed: Device or resource busy
mount: Mounting none on /proc failed: Device or resource busy

BusyBox v1.01 etc. etc.

**ETA:** Getting a *lot* of "not found" listings for mounts, devices, cpuinfo, partitions, stat, etc. in /proc, as well as casper.log. I'm also getting a heck of a lot of syntax errors in /bin. The one I get most often is **Syntax error: "(" unexpected**, but I also got **")" unexpected** and **Syntax error: word unexpected (expecting ")")** in a few places like gzip and casper-md5check.

Also in bin, when I tried sh casper-reconfigure, I got the error **casper-reconfigure: package ' ' is not installed.** In sys/module/cdrom/sections, running sh __versions, I got **__versions: 1: 0xd0892ae0: not found**. If I try the tty command in the main dir I get **"/dev/console/"**, which according to [this]("http://www.linuxquestions.org/questions/showthread.php?p=2554669#post2554669") and especially [this]("http://www.uclibc.org/FAQ.html#job_control") it isn't supposed to be doing.

Another thing I noticed is that after attempting the 'exit' command and getting sent back to the main directory, two new directories show up on the ls, called "cow" and "rofs", and they don't seem to have anything in them. I can get rid of rofs with rmdir, but if I try to remove cow it says the device or resource is busy. Also, there's nothing in my /root dir, which I'm pretty sure is wrong, and the only thing in /var is "lock".

I also noted that when I'm in the graphical interface for installation, if I hit F6 for additional info, it displays a line for the installation command that states "root=/dev/ram rw quiet splash--". Which I'm *assuming* is important, because that one guy mentioned an almost identical command line [here]("http://www.linuxquestions.org/questions/showthread.php?p=2603828#post2603828").


**ETA2:** Okay, before when I was running ls in /dev, I was getting a huge list of tty listings. I tried sh tty1, then ran init, and while it took me back to the first error message, when I entered /dev the listing had cut down to twelve. The twelve being console, null, fb0, and tty0 through to tty8.

**ETA3:** Trying to run the 'Check CD for defects' gets the same error as running the 'Start or Install' option. Also, I've got the huge list of ttys back in /dev and can't seem to get rid of them this time.

---

### Post by bapoumba on 2007-04-07
@ Halfling Rogue: I'm going to delete your duplicate thread in the Beginner Team forum (which is not for support questions ;)).

---

### Post by Halfling Rogue on 2007-04-07
My bad, I realized that after I made it and then realized I couldn't delete the post. XD;

---

### Post by bapoumba on 2007-04-07
> **Halfling Rogue said:**
> My bad, I realized that after I made it and then realized I couldn't delete the post. XD;
No problem :)

---

### Post by sgardne on 2007-04-13
Okay, I was having this same problem and discovered that if I manually mounted the cd by typing 

mount -t iso9660 /dev/scd0 /cdrom

I could mount the cd, but now I am kinda stuck because I have no idea what to do. How do I make the installer start up again now that the cd is properly mounted?

---

### Post by Halfling Rogue on 2007-04-13
Try running sh init from the main directory?

---

### Post by sgardne on 2007-04-13
> **Halfling Rogue said:**
> Try running sh init from the main directory?
Doing that I get a bunch of errors:

> 
mount: Mounting none on /sys failed: Device or resource busy
mount: Mounting none on /proc failed: Device or resource busy
Begin: Loading essential drivers... ...
Done.
Begin: Running /scripts/init-premount ...
udevd[2832]: init_udevd_socket: bind failed: Address already in use
error initializing udevd socket
udevd[2832]: main: error initializing udevd socket
Done.
Begin: Mounting root file system... ...

Then it dumps me back to the BusyBox shell. casper.log now contains about 100 lines similar to this one:

init: init: 1: cannot open /dev/sr0: No such file

The /dev/* is different for each line but they are otherwise the same, then at the very end is:

Unable to find a medium containing a live file syste

---

