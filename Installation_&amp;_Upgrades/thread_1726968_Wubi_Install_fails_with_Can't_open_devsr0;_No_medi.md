---
title: "Wubi: Install fails with Can't open /dev/sr0; No medium found"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by defaria on 2011-04-11
I've been trying to install wubi 10.04 and when I do I get:

```
/scripts/casper_premount/20_ISC_scan
  Line 46 Can't open /dev/sr0; No medium found
Couldn't find ISO /ubuntu/install/ubuntu-10.04.2-desktop-i386-iso
```

The error message goes on to say try rebooting and doing a chkdsk /r, reboot to Windows again then it should work. One problem. It doesn't work! It doesn't do anything different. Same problem, same error message.

Oh and for some odd reason if I just run wubi by itself it download the 64 bit version of 10.10. But I have only a 32-bit machine! I learned of the --32bit option and have been using that to get the 32 bit version. Still after downloading the ISO I fail to install with the above message. Even let it download the 64 bit version and same error message essentially.

Also I need 10.04 as I want to install Clearcase from Rational and Rational doesn't support 10.10 yet.

I found an older wubi that would download 10.04 but it would only download 10.04.01. Then it would reboot and look for 10.04.02! 

Found that problem reported and it offered a wubi version that would correctly download 10.04.02 iso. However the error message reported above persists. 

Why is this so difficult?

---

### Post by bcbc on 2011-04-11
The wubi.exe on releases.ubuntu.com/lucid is incorrect - it's set at 10.04.1. This is a known bug, but we're waiting for someone at canonical to fix it.
In the meantime you can get it from here: [http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe](http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe)

I would run a md5sum on your CD to make sure that it's OK. I've seen some comments on this error that disabling your floppy drive in the bios fixes it, but ... most people don't have floppies so I suspect it's some other error.

Re. 32 bit vs 64 bit. Wubi chooses the 64bit by default if you computer supports it (many computers shipped with 32bit Windows are 64bit capable. You already found how to override that...

---

### Post by defaria on 2011-04-15
I did the wubi-r191 thing already. Didn't change the result.

You speak of a CD. What CD? I have no CD. Last time I used wubi it  downloaded an iso file and use that with no need for a CD. 

This is a Dell laptop. I don't think there is any floppy to disable.

Regarding 64bit - I only have a 32bit CPU. How could 64bit stuff work?

Other ideas?

---

### Post by bcbc on 2011-04-16
Yeah I think I was half asleep now that I reread what I posted ;)

Check this thread out: [http://ubuntuforums.org/showthread.php?t=795706](http://ubuntuforums.org/showthread.php?t=795706)
From post #8 it looks like the same error you're getting.

If you can create an ubuntu CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") it should give a bit more diagnostic info. If you like you can capture your logs and post a bug report.

To capture your logs:
when you get the error hit CTRL+ALT+F2 to drop to a terminal
run
```
sudo sh /host/ubuntu/install/custom-installation/hooks/failure-command.sh
```

Then when you reboot into Windows your logs will be in \ubuntu\installation-logs.zip and you can attach these to the bug report.

---

### Post by lmarmisa on 2011-04-16
Consider to use an alternative solution based on virtualization.

I recommend to install [VirtualBox]("http://www.virtualbox.org/") on your Windows system and then create a virtual machine for Ubuntu 10.04. This works really great.

---

### Post by bcbc on 2011-04-16
> **lmarmisa said:**
> Consider to use an alternative solution based on virtualization.

I recommend to install [VirtualBox]("http://www.virtualbox.org/") on your Windows system and then create a virtual machine for Ubuntu 10.04. This works really great.
How do you find it compares to Wubi? On my machine I only have 1GB of RAM so when I run Ubuntu on Virtual box it pretty much kills both Windows and Ubuntu: it's way slower and the screen size is limited. The only benefit is I can run Ubuntu without rebooting, but since I pretty much have to close down all the apps on Windows to get it to run, and it's still really slow... it's not a very good experience. Hardly a good way to sell Ubuntu to a new user, in my opinion.

---

### Post by lmarmisa on 2011-04-16
> **bcbc said:**
> How do you find it compares to Wubi? On my machine I only have 1GB of RAM so when I run Ubuntu on Virtual box it pretty much kills both Windows and Ubuntu: it's way slower and the screen size is limited. The only benefit is I can run Ubuntu without rebooting, but since I pretty much have to close down all the apps on Windows to get it to run, and it's still really slow... it's not a very good experience. Hardly a good way to sell Ubuntu to a new user, in my opinion.

My experience with VirtualBox is very positive. My machine is about 4 years old and it is not very powerful at all. I have a modest dual core CPU with 2 Gbytes of RAM. My wife and my daughter have affordable laptops (3 and 1 years old) and they also use VirtualBox with no problem. BTW, they are Ubuntu users because they have installed VirtualBox with Ubuntu virtual machines in their computers. And of course, there is no limitation about the size of the screen on VirtualBox.

Many persons of the Ubuntu forums use virtualization and they like it. There is a specific forum for virtualization in ubuntuforums.org: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

So, I recommend virtualization because I believe that it is an excellent solution for many people. I accept that your had a bad experience with VirtualBox but this is not the general case.

---

### Post by bcbc on 2011-04-16
> **lmarmisa said:**
> My experience with VirtualBox is very positive. My machine is about 4 years old and it is not very powerful at all. I have a modest dual core CPU with 2 Gbytes of RAM. My wife and my daughter have affordable laptops (3 and 1 years old) and they also use VirtualBox with no problem. BTW, they are Ubuntu users because they have installed VirtualBox with Ubuntu virtual machines in their computers. And of course, there is no limitation about the size of the screen on VirtualBox.

Many persons of the Ubuntu forums use virtualization and they like it. There is a specific forum for virtualization in ubuntuforums.org: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

So, I recommend virtualization because I believe that it is an excellent solution for many people. I accept that your had a bad experience with VirtualBox but this is not the general case.
I wouldn't say I had a bad experience - it was useful if I wanted to check something out without having to reboot. But it wouldn't be my first choice to recommend someone trying out Ubuntu - the performance isn't even close to what you get with Wubi.

I know it would be better with more RAM... but I think a lot of people run Ubuntu on low ram, e.g. my other computer has 512MB RAM and it runs 10.04 fine.

---

### Post by defaria on 2011-04-17
> **lmarmisa said:**
> Consider to use an alternative solution based on virtualization.

I recommend to install [VirtualBox]("http://www.virtualbox.org/") on your Windows system and then create a virtual machine for Ubuntu 10.04. This works really great.

Thanks but I really don't want to run in a VM - I want to ultimately replace Windows! 

And I'm not a new user, I run Ubuntu 64 bit on my desktop at home, my laptop and my server. I run Win 7 only in a vmware session on the laptop and that's only for 1 program - Playon. I have about 25 years of working with Unix and Linux.

This is my work laptop. I'm a Linux guy. My current client is largely Linux oriented but like most business IT hands out Windows laptops and says "Here's Outlook and your Exchange server - there's MS Office here so of course you're all set up!". I already have Cygwin installed, use Chrome, Thunderbird, etc. and I don't use any of the "normal" Corporate Windows crap. I'd be more comfortable in Linux anyway.

Usually the hard part is getting Thunderbird to talk to Exchange, etc. Recently I found software named DavMail. It's Java and takes all of the non-standard Exchange crap and converts it to standard IMAP/SMTP/WebDAV/etc/ standards. So I'm relatively happy. But I got to thinking that DavMail also runs on Linux so I could install Wubi on a dual boot, get everything set up and running then simply boot into Ubuntu and use that for the rest of the time that I'm there, never to see Windows again.

(And if I was gonna run it in a VM I'd use vmware).

I'll need to check out that thread tomorrow... Thanks bcbc.

Looked over the thread. Doesn't seem to apply to me. They said something about /dev/scd0 probably indicating a CD. Mine was /dev/sr0. Remember I'm not using a CD. I'm not even sure if the work laptop has a CD writer. I have one at home but then there's still the issue of which 10.04 do I get? It seems to want to download a 64bit one but I have only a 32bit CPU. They also talk about not being able to boot and a faulty boot partition. I don't have that problem. Besides this should just work.

Oh and another thing - my job involves using IBM/Rational's Clearcase. I saw that Rational finally supports Ubuntu @ 10.04 but not at 10.10. It might just work in 10.10, I don't know. But I'd prefer to get 10.04. If I can get the dual boot Wubi installed Ubuntu 10.04 to use DavMail and connect up Thunderbird for "corporate communications" and if I can get Clearcase running then I'm all set to abandon Windows. That'd be nice and that's my goal here.

---

### Post by bcbc on 2011-04-18
/dev/sr0 is the cd-rom.

I'm sure it's a bug in ubiquity (that it's looking for the cd-rom). But there must something upsetting ubiquity on that computer, that isn't very common. 

I've installed wubi dozens of times from 8.04 to 11.04 and I know it doesn't need or refer to the cd-rom... but I did get a similar error was when I was testing the "CD boot helper" option with Wubi (in this case it requires the CD be present)... and the message was:
> stdin: error 0
/init: line 7: can't open /dev/sr0: no medium found
/init: line 7: unable to find a medium containing a live file system I created a [bug report]("https://bugs.launchpad.net/wubi/+bug/759352") about it because I found it confusing and not well-handled.

Anyway... that's a bit off topic. This is what I'd suggest. If the machine has a cd drive, try booting an Ubuntu CD in live CD mode (or use a USB otherwise). Then run [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). This is often good at showing things that could cause boot problems (e.g. a mix of GPT and MBR partition table info, or leftover fakeraid metadata - I don't think these are the issue, but maybe simply running "sudo fdisk -l" will spit out some diagnostic message). You could also install and run testdisk as suggested in that thread and see what it indicates.

---

### Post by defaria on 2011-04-18
But I don't have an Ubuntu CD! I have an AMD 64 bit Desktop CD (that I used for my 64 Bit desktop) and a 32 bit server CD for 9.10.

Do I just download a 32bit ISO of 10.04 and use that?

---

### Post by bcbc on 2011-04-18
What makes you so sure that it's 32 bit? Wubi figured it was 64bit. If there was a bug in wubi we'd see a lot of failed installs.

What chip do you have?

But whatever chip it is, downloading 10.04 32-bit will work. Or if you have a leftover \ubuntu directory it's saved there already ( pre-install as \ubuntu\install\installation.iso, and post-install as a hidden file \ubuntu\install\.fuse_hidden400000001 (something like that).

---

### Post by defaria on 2011-04-18
According to: [http://support.microsoft.com/kb/827218](http://support.microsoft.com/kb/827218)

> 

Windows XP
If you have Windows XP, there are two methods to determine whether you are running a 32-bit or a 64-bit version. If one does not work, try the other.
Method 1: View System Properties in Control Panel
Click Start, and then click Run.
Type sysdm.cpl, and then click OK.
Click the General tab. The operating system is displayed as follows:
For a 64-bit version operating system: Windows XP Professional x64 Edition Version < Year> appears under System.
For a 32-bit version operating system: Windows XP Professional Version <Year> appears under System.
Note <Year> is a placeholder for a year.
Method 2: View System Information window
Click Start, and then click Run.
Type winmsd.exe, and then click OK.
When System Summary is selected in the navigation pane, locate Processor under Item in the details pane. Note the value.
If the value that corresponds to Processor starts with x86, the computer is running a 32-bit version of Windows.
If the value that corresponds to Processor starts with ia64 or AMD64, the computer is running a 64-bit version of Windows.

It was my assumption that if I was running a 32-bit version of Windows that it was because I couldn't run a 64-bit verison. Silly me!

The CPU is listed simply as "Intel(R) Core(TM) 2CPU T7400 @ 2.16GHz 2.16 GHz, 2.00 GB of RAM" and that's usually as much of hardware I care to dig into. After all I'm a software guy! :-)

Ah [http://ark.intel.com/Product.aspx?id=27256](http://ark.intel.com/Product.aspx?id=27256) says it has the "64-bit instruction set". Who woulda thunk it!

As for the iso image being on the disk, I've seen that before. When you run Wubi however it "uninstalls" it. Doesn't really matter however as @ work I don't have a CD ROM burner - I have one at home. So I'll download the 64 bit one since my processor will apparently run it, and burn it onto the CD then bring that to work. Stay tuned...

---

### Post by defaria on 2011-04-19
Well this is a big no-go unfortunately. Like many corporate environments they are using drive encryption (pointsec) and as such I can't install Ubuntu because of it. References: 
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=712234](http://ubuntuforums.org/showthread.php?t=712234)
[*][https://bugs.launchpad.net/wubi/+bug/119607](https://bugs.launchpad.net/wubi/+bug/119607)
[/LIST]

It seems like all that is needed is a driver for such encrypted drives.

UGH, this sucks!

---

