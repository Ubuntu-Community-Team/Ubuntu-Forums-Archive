---
title: "CDCheck Fails but MD5 is Correct! 8.04"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Jaiinus on 2008-04-25
Trying to install: 8.04 Heron Server LTS (ubuntu-8.04-server-i386 w/ MD5 of c3162b21757746c64a0a22cdd060b164)

So I burned the first one with default settings after MD5'ing the image and confirming it came down the pipe correctly. I put it into a server running VMWare Server 1.0.5 on Red Hat Enterprise 5. VMWare is set to cough up the physical drive to the VM. I make a new VM, set it to ubuntu, and then boot it up and do a media check. It says it fails on ./dists/hardy/main/binary-i386/packages.gz so I go back to my computer, slow down the burner after double checking the ISO MD5, and try the process again. It fails on the SAME file.

So my process from there was to open up the MD5 file on the CD, dig up the file in question, and then MD5 it on a working system. The MD5 matches (d442c09a3b1e5e16d0b3a95397568312). So I figure I have no idea what's going on with that and try, in vain, to install it and get a "can't read from the disc, file or cd is corrupt" which is to be expected. I have checked the MD5 sum from the host OS (RHEL5) and it matches as well.

So, in summary:
ISO MD5 matches on Burning system
Packages.gz MD5 matches on Burning system and Host OS
Packages.gz FAILS MD5 through media check during install

I'm really at a loss at what's going on. It's the end of the business day so I'm heading home, but I imagine the next step of "just get it done" will be to burn the iso file itself and try a virtual mount, but I'm still infinitely curious of why this is happening.

---

### Post by Pumalite on 2008-04-25
First suspect is your burner. Clean the lens or change it. Burn at 4x or less. You can download IngBurn that allows burn at 4 or 1x.

---

### Post by BoogieKnight on 2008-04-25
I had an identical experience burning the 64bit desktop ISO from within Windows using Nero (set a slowest speed)... burned it 3 times and got errors on all 3. I booted into Ubuntu 7.10 and burned the same ISO and everything checked out perfectly... go figure.

I'm really puzzled why I kept getting coasters burning from within Windows as I never have any issues like that when I burn other stuff.

I remember having similar issues when the 7.10 ISOs came out... maybe it's some obscure Nero issue with Ubuntu ISO files... who knows. I have yet to try a different burning software within Windows but it might be worth a try just to see what happens.

---

### Post by Jaiinus on 2008-04-28
I could understand that its my burner because I don't get a choice about the burning software I use (work). However, it doesn't make any sense to me that the host OS can read the file and do a MD5 and get a correct result but when I use a guest OS it fails that MD5. It's not like I'm using a different CD drive to read it with the host, it's the same CD drive, same CD, and Hardy is failing the file when it is actually being read "fine". I'm going to try to transfer it over to the system as a .iso file and see if that works.

---

### Post by Pumalite on 2008-04-28
This might help:
[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

---

### Post by Jaiinus on 2008-04-28
I used the host system and SCP'd it over as a iso and that worked. This is why I have a stack of good media at home :D

Thanks for the help though, and the cool new way to ubuntize a system that I didn't know about. I'll have to try that one on my own time at some point.

---

### Post by Pumalite on 2008-04-28
Something to get you started:
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

