---
title: "installer in 6.06 desktop cd: a huge disappointment"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by wsonguci on 2006-08-07
Hi, 

I've been long-time redhat/fedora user and recently I started to use ubuntu.  Several months ago, I installed ubuntu 5.10 and it's pretty impressive. Now 6.06 came out and I was eager to install it.

So I downloaded the desktop cd (ubuntu-6.06-desktop-i386.iso) and booted it up on my ubuntu 5.10 PC (pentium III 1Ghz, 512M memory). To make sure the CD has no problem, I selected 'Disk Test' first, and it reported 0 failure. Then I went ahead to run the 'installer'. Afte selecting a few options such as time zone and keyboard etc, it got into the partition screen. I selected 'Erase entire disk' for /dev/hda. The installer started to run  the partitioning but reported 'failed to create the filesystem' and it got stuck on 15% of the 'installing system' progress bar. I tried the same process on my laptop and it unbelievably had the same problem!

So I searched the forum and found that other people run into the same 15% stuck problem also and people suggest we install the alternate CD instead.

However, according to the release notes of 6.06:

The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of CD is what most people will want to use.

For me, it's a huge disappointment for 6.06: if the installer doesn't work, just don't put it on the desktop. For a Linux distribution boasting best for the desktop users, it's even unacceptable.

That made me really hesistant to switch to ubuntu permanently, which I was almost ready to.

---

### Post by hopstah on 2006-08-07
that disk checker isn't always 100% accurate.  i just read a thread about somebody's install stopping at 14% every time, and he checked the disc and had zero errors, but it turns out that the disk was smudged and after a cleaning everything worked fine.  i have used the installer about a half dozen times due to my learning of linux, and haven't had a problem with it yet.

---

### Post by orb9220 on 2006-08-08
Mine has installed on three machines and complete installs from disks 6 or 7 times. The installer always worked. But I did to a manual config of partitions instead of the auto. 

Try going to manual edit then pick the partition and mount points.

---

### Post by Caepio on 2006-08-26
Hello

My experience with 6.06 has been terrible. Since this is my first Linux experience, I am exceptionally skeptical that this OS can ever be useful except to a few hard core devotees.

My purpose in looking into 6.06 was to find a workable substitute for Microsoft for a major deployment in another country, but with this software being so unreliable, I must rule it out. Terribly unfortunate.

I have had nothing but problems and frustrations with 6.06, and if I can't get this to work as a dual boot or stand alone, I don't see any hope of my customer being able to use this.

After multiple reloads, repartioning, reformatting, and rebuilding the test laptop, I now have 6.06 installed over itself (2 installs) with no graphics or any other functionality.

This is a failure and a waste of time. Unfortunately, I have to go with Microsoft.  [-X [-X

---

### Post by az on 2006-08-26
> **wsonguci said:**
>  For a Linux distribution boasting best for the desktop users, it's even unacceptable.


D'uh!  It's a bug.

Have you tried the 6.06.1 release?  It fixed a few installer bugs.

---

### Post by Tomosaur on 2006-08-26
This kind of thing really irks me. You say 'if it doesn't work, don't include it'. Well, it worked flawlessly for me, and thousands of other people. You are an exception - part of a minority group. You come for support - people know about the bug, but there isn't currently anything that can be done, so you get a friendly suggestion to try something else, but you go ahead and complain anyway. What's the point? It's a confirmed bug, and I'm sure the devs are working on it right now. I'm sorry you had a bad experence - but as a 'long-time redhat/fedora user', you really should know that there are bugs - things which go wrong for a minority of people that aren't caught by the pre-release testing. There are other ways to install Ubuntu, and you were pointed in the right direction. Why make a thread complaining about it?

---

### Post by alsenior on 2006-08-26
i used the installed under vmware and the disc installed was fine on a blank vmware disk. it might of had problems with the other installation on the disk.

---

