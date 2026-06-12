---
title: "To Install Ubuntu, do I need to burn a CD? Can't I just mount?"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by Nehmo on 2010-10-04
I'm familiar with Windows, but not Linux, and I have Win 7 Home Premium 32 bit on this laptop. I want to additionally install Ubuntu, and I've downloaded ubuntu-10.10-rc-desktop-i386.iso . The next step according to the instructions is to burn to a CD. 

But is that necessary? Can't I just mount the iso using Virtual clone drive or something similar? 

What's the point of using a physical CD? Or is there a point?

...
I tried it. That is, I mounted and I ran wubi.exe -> got the box of options: 1 Demo and Full, leave CD in; 2 Install inside, no dedicated partition; 3 More info.

I think I want to install alongside, the 1 Demo and Full option. It seems after I reboot, I can then install like a duel boot arrangement. Is there some reason I wouldn't want a dedicated partition?

Option 2 Install inside, seems to degrade performance with no compensating benefit.

I had better do the more info option. But is 1 Demo and Full the way to go? (By the way, Demo usually means a trial or crippled version. This doesn't seem to be the case. So why use the term "Demo"?)

  ~~ Nehmo

---

### Post by tgm4883 on 2010-10-04
> **Nehmo said:**
> I'm familiar with Windows, but not Linux, and I have Win 7 Home Premium 32 bit on this laptop. I want to additionally install Ubuntu, and I've downloaded ubuntu-10.10-rc-desktop-i386.iso . The next step according to the instructions is to burn to a CD. 

But is that necessary? Can't I just mount the iso using Virtual clone drive or something similar? 

What's the point of using a physical CD? Or is there a point?

...
I tried it. That is, I mounted and I ran wubi.exe -> got the box of options: 1 Demo and Full, leave CD in; 2 Install inside, no dedicated partition; 3 More info.

I think I want to install alongside, the 1 Demo and Full option. It seems after I reboot, I can then install like a duel boot arrangement. Is there some reason I wouldn't want a dedicated partition?

Option 2 Install inside, seems to degrade performance with no compensating benefit.

I had better do the more info option. But is 1 Demo and Full the way to go? (By the way, Demo usually means a trial or crippled version. This doesn't seem to be the case. So why use the term "Demo"?)

  ~~ Nehmo

Because demo is short for demonstration. Not trial or crippled version.

---

### Post by oldfred on 2010-10-06
If your computer will boot USB, I would suggest that. Follow the links to instructions on USB installs.

Also has links to alternative install -text mode & not liveCD, CD & USB install instructions
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by Nehmo on 2010-10-07
> **oldfred said:**
> If your computer will boot USB, I would suggest that. Follow the links to instructions on USB installs.

Also has links to alternative install -text mode & not liveCD, CD & USB install instructions
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

~~ Nehmo

---

### Post by gnush on 2010-10-07
I suppose the CD/USB has an advantage of being able to partition harddrives, since you can't partition a harddrive if you're using an OS placed on the harddrive you want to partition.


> **Nehmo said:**
> ~~ Nehmo

What's the point of posting a quotation? :?

---

### Post by Nehmo on 2010-10-08
> **gnush said:**
> I suppose the CD/USB has an advantage of being able to partition harddrives, since you can't partition a harddrive if you're using an OS placed on the harddrive you want to partition.

What's the point of posting a quotation? :?

I don't know how it happened, but the quote went through, but what *I* wrote didn't. I was asking *why* use a removable storage device. What's the advantage? Gnush, or you, offered an  explanation.

  ~~ Nehmo

---

### Post by lisati on 2010-10-08
One advantage of using a USB in preference to a CD is that the USB device is reusable once the content has served its purpose.

The advantage of using a CD or USB device is that it can be used to run Ubuntu without actually installing Ubuntu. This is good for getting a basic idea of how Ubuntu works and can give you a head start figuring out if Ubuntu works with your setup.

Another advantage is that if you need to resize an existing partition as part of the installation process, it can go more smoothly if the partition is not in use by the OS you are currently using.

---

### Post by Nehmo on 2010-10-08
Those reasons are ok, but I already have the downloaded copy and I can mount it. I don't even have a blank CD. I don't see how any harm can come from mounting and installing from there. We'll see.
   ~~ Nehmo

---

### Post by Nehmo on 2010-12-23
When trying to install inside of Windows, I get an error: Invalid argument
Here's the end of the log:
"
...
12-23 10:44 DEBUG  TaskList: ## Finished copy_installation_files
12-23 10:44 DEBUG  TaskList: ## Running get_iso...
12-23 10:44 DEBUG  TaskList: New task copy_file
12-23 10:44 DEBUG  TaskList: ### Running copy_file...
12-23 10:45 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
12-23 10:45 DEBUG  TaskList: # Cancelling tasklist
12-23 10:45 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
12-23 10:45 DEBUG  TaskList: New task check_iso
12-23 10:45 ERROR  CommonBackend: CD check failed, but ignoring because CD is Release Candidate
12-23 10:45 DEBUG  TaskList: ## Finished get_iso
12-23 10:45 DEBUG  TaskList: # Finished tasklist

" end of log
  ~~ Nehmo

---

### Post by dino99 on 2010-12-23
[http://translate.google.com/#fr|en|http%3A%2F%2Fwww.jellykernel.org%2Fgeek%2Finstaller-ubuntu-sans-cd-ni-cle-usb-ubuntu-netinstall%2F](http://translate.google.com/#fr|en|http%3A%2F%2Fwww.jellykernel.org%2Fgeek%2Finstaller-ubuntu-sans-cd-ni-cle-usb-ubuntu-netinstall%2F)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Nehmo on 2010-12-24
@ dino99

Are you saying the answer is in one of those links? 

I didn't read everything, but I didn't find my particular issue addressed. However, your second link is a previous post by you saying how to partition the drive for a Duel Boot arrangement. So you are advocating a duel boot arrangement instead of installing inside of Windows?

I could do that (assuming everything works), but I chose the installation inside Windows because it seems less risky. I've installed lots of programs inside of Windows and I'm familiar with the procedure. But I've never re-partitioned the drive on which the OS lives. And, so far, I've never been successful making a duel boot system. 

In my current effort, I tried installing inside Windows. Looking at the log, I suppose the problem is indicated by the line:

IOError: [Errno 22] Invalid argument

Searching on this error produced
[https://answers.launchpad.net/ubuntu/+question/82914](https://answers.launchpad.net/ubuntu/+question/82914) 
and marcobra (Marco Braida) said on 2009-09-16 that I should

"...install Ubuntu NOT using Wubi.

If you have installed Ubuntu via Wubi please uninstall it read
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php) and [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Installing Ubuntu using Wubi make Ubuntu less robust and all problems that you will have to Windows can be affect your Ubuntu partition file.

I strongly suggest you to install Ubuntu+Windows in dual mode creating a real Ubuntu ext3 or ext4 partition.
In this mode you can use Ubuntu and Windows ad usual and then using installed Ubuntu you can save or repair damaged (due viruses or other issue) Windows partitions data.

- Here the steps to install Ubuntu 9.04 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) "

The installation iso I used was ubuntu-10.10-rc-desktop-i386.iso at 254 MB. On [http://forum.lowyat.net/topic/1061302](http://forum.lowyat.net/topic/1061302) ,
dkk cautions that a package under 600 MB is not the full program and requires an internet connection to complete the package. I wasn't connected to the internet when I tried the install. Maybe that's the problem.

So, now I have some more reading to do.

  ~~ Nehmo

---

### Post by Syed75 on 2010-12-24
No I never had problems with wubi.

---

### Post by kansasnoob on 2010-12-24
I did not read all of the responses but it's my opinion that someone should have a known "working" Linux Live medium before installing any Linux system!

Wubi has ongoing problems:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

With no Live CD I certainly couldn't deal with that :o

The 10.10 Live Installer also has major bugs:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

So IMHO you should be sure and have some known "working" Linux live media so you can fix things if something goes wrong!

---

