---
title: "Assistance Needed: Grub Install To Wrong Root Patch Bug"
date: 2008-07-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-07-17
Ok, so there is a serious bug with both ubiquity and alternate installers in some cases of machines having multiple HDDs where grub gets installed for the wrong root. Its an easy fix for experienced users, but once fixed it then becomes an annoyance with any kernel uprade overwriting the menu.lst grub paths again. For new users, its a deal breaker resulting in Ubuntu not working out of the box.

I reported this bug:

[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/243803](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/243803)

However the installer log lzma archive is corrupted. I tried to attach a new installer archive however by mistake I attached a working systems logs. Now I dont have four HDDs anymore and the hardware I have access too only has one HDD so I cant replicate the bug and give logs.

This is an important bug so can I please appeal to folk to test this and provide logs. I know this bug occurs on Intrepid, Hardy and Gutsy.

---

### Post by BwackNinja on 2008-07-17
I can confirm that I saw this too in my menu.lst, but I immediately changed it myself before I even tried booting it. I can try to help and do basically whatever you'd need me to do to help confirm and get it fixed though.

---

### Post by Nullack on 2008-07-17
Thanks, we need to get logs in /var/log/installer all tarred up including subdir and attached to the bug.

---

### Post by BwackNinja on 2008-07-17
Hmmm.... I tried to tar it all up using my account and it gave me some blank error (I'd assume) message. I tried it running "sudo nautilus /var/log/" and do it from there, but it still didn't work, and somehow it has completely destroyed my install...

I could no longer run any programs, my wallpaper was gone (though I still had my desktop icons), all my icons on my panels were missing and replaced with a document-like icon with a red "x" on it, my time is randomly all screwed up too. I'd attatch a screenshot, but that would require gnome-screenshot to have been working right then. I had to hard-boot it to restart and when I logged out, instead of text, I had a series of boxes instead. Now it doesn't even boot. I'll reinstall tomorrow.... I would seriously like to have problems that I can actually fix with less than a full reinstall...

---

### Post by ronacc on 2008-07-17
I have never had good luck with Ubuntus grub installer getting things right so I don't let it install grub unless it is the first distro I install on the box . With that said on my new install of intrepid A2 it did write a /boot/grub/menu.lst  even though it didn't install grub and it clearly points to the wrong root as you said ( root   (hd0,0)   should read  root    (hd4,0) )  should I go ahead and send in my /var/log/installer  + menu.list as written + the correct boot stanza ?

---

### Post by Nullack on 2008-07-17
BwackNinja there must be some other problem with your install. To tar up the contents of /var/log/installer, grab all the files except initial-status.gz as that is a zero length file. Make sure to grab the subdir files as well in the subdir cdebconf. There should not be anything related to tarring up a few files and having your whole system die.

ronacc its probably worth attaching those logs to the bug along with an explanation as to your custom install, since it still shows the issue.

Thanks for all your support - I see it as an important mission to fix this bug before Intrepid is out.

---

### Post by BwackNinja on 2008-07-17
I guess there would be something else wrong.... but I didn't do any tweaking past basic ui changes (background, theme colors, compiz settings). I over-tweak my stable install and I've never had anything happen that has made me reinstall. As I said before, this isn't just the first time, it is the second. Something's up and I don't know what or how.

---

### Post by ronacc on 2008-07-17
hmm I may have found a bug in nautilus , I nuked my upgraded hardy when I tried to access something I had copied as root , well I just nuked my A2 install by trying to use archive manager to
tar a copy of my /var/log/installer that I had made as root for that purpose . I think copying something as root somehow screws the permissions on the whole partition .

---

### Post by Nullack on 2008-07-17
Im sorry guys. All I can say is that today I tarred up my /var/log/installer using file roller without having anything go wrong. I guess a positive is if we preserver we can isolate the bugs, report with logs and devs can fix them. I cant physically test this bug anymore but I will help anyone who can test it to make sure the right logs are attached to the bug report.

---

### Post by ronacc on 2008-07-17
I can still tar the thing using another install and send it in , I'm going to poke around some more and try to figure out whats going wrong with operate on a file as root from the description the same thing got BwackNinja , I also got a blank error ? message .

---

### Post by Gina on 2008-07-18
Something odd here - I have installed various versions of Ubuntu dozens of times and I don't recall ever having a grub install problem.  That includes one machine with two SATA drives with WinXP and a data ext3 partition on the first and several Ubuntus on the second - multi-boot.  I don't install development versions on this at least until beta release.  Another desktop and laptop only have one drive - though I could always stick a 2nd IDE drive in my old desktop for testing.  These are all 32 bit systems.

I also have an AMD64 system which now has two drives - one IDE 250GB and one SATA2 500GB (new).  I had several Ubuntu systems installed on the IDE when I added the SATA and installed Ubuntu-Studio Hardy followed by Ubuntu Intrepid on my new SATA drive - using the installer to create the partitions required (each new system had it's own new **/home** partition on the new drive).  In both installs the grub install seemed to be correct - I can run either the new systems on the SATA or the older ones on the IDE.  I used the Alternate CD to install the systems on the new drive - I generally use the Alt, though I have installed from Live CD and the mini.iso several times.

This is my main test machine so I'd be happy to test anything (even wiping the lot and installing several different versions). I have no other OSs than various versions of Ubuntu installed.  ATM I cannot see anything particularly different that I'm doing from the members here having problems.

---

### Post by philinux on 2008-07-18
my rig has 2 HD's and has Hardy on hd0.

I tried pclos and mint on hd1 and in both cases grub was installed to hd0.

When I installed Intrepid to hd1 it too correctly installed grub to hd0.

N.B. there is always the problem of dual boot 2hd's linux/linux where the menu.lst on hd0 doesn't get updated with new kernels for the install on hd1. I've since installed grub to hd1 and chainload from hd0.

---

### Post by ronacc on 2008-07-18
in my case it was not where grub would have been installed had I let it but the drive designator it wrote into the boot stanza for itself , for example the root line the grub installer wrote was root      (hd0,0)  
when it should have read   root      (hd4,0)    the uuid was correct . and in the past I have had problems with ubuntus grub installer (or grub itself) not finding all the installs on my box , it often finds only one other than itself when I may have 4 or 5 all on different drives .

---

### Post by Gina on 2008-07-18
Ah, I see.  I always have the first partition of the first drive as boot and thats where grub installs so that is probably why I've never had a problem.  If you have a special setup, you can tell grub where to install using the Advanced option in the Ubuntu installer.  But as I said, hd(0,0) has always been correct for my machines.

---

### Post by Nullack on 2008-07-25
Cmon folks :) Its been a week now and no one has added any relevant logs to the bug. Unfortunately I cannot test this anymore due to my hardware configuration.

This is an important bug to fix so that novice users dont have a non working system after install.

Please, lets move this along.

---

### Post by Gina on 2008-07-27
I've just installed Alpha 3 on my AMD 64 and at the same time changed the boot drive from the older IDE drive to my new 500GB SATA2, installing Intrepid on that.  That went fine and I'm using it now.

However, after that I installed 8.04.1 64bit on new partitions on the SATA drive using XFS format for **/** (root) and **/home** and separate ext3 for **/boot** (as per another thread) and the grub install didn't seem to work.  I'm investigating... It may or may not be related to this thread.  I'll report back when I have more info.

---

### Post by ronacc on 2008-07-27
added my comments and my installer logs to your bug .

---

### Post by Nullack on 2008-07-27
Legend mate :) Thanks alot, next step I am doing my luck rain dance and salt throwing for it to be picked up for code fixing.

---

