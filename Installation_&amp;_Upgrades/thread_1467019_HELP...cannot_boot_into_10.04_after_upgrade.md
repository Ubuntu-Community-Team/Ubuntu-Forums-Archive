---
title: "HELP...cannot boot into 10.04 after upgrade"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by chaman1 on 2010-04-30
Hi, this is my first time upgrading Ubuntu - from 9.10 to 10.04.  I'm a beginner at Linux, so I'd appreciate help that is easy to understand.
 
I made a mistake while upgrading the GRUB options - when choosing "install the maintainer's version vs. keep the local version"...in the drop down menu, I chose the **local version option**.  On reboot, GRUB works, but I can't boot into 10.04.  My old entries (kernels) are still there, but when I choose them, there's an error that says something like "disk not found".  However, I am able to boot into Vista.
 
So do I solve this problem by fixing GRUB?  If so, how? I have a Live CD of 9.10, would that be necessary to use it to solve this problem?
 
Please refer to [www.ubuntu.com/getubuntu/releasenotes/1004]("http://www.ubuntu.com/getubuntu/releasenotes/1004"), under GRUB.menulst: maintainer's version vs. keep the local version.  I read it afterwards (I should've read it before), but I have no idea what it means and if it is describing my problem.

---

### Post by Esau on 2010-04-30
Somewhat of the same issue.

I upgraded from 9.10 and since then have not been able to boot into any new kernels. It starts the process but then gives me a blank screen. Only way to login is to go to an older entry, and as of right now i'm using kernel 2.6.31-21-generic.

Any help would be appreciated.

Thanks

---

### Post by chaman1 on 2010-04-30
> **Esau said:**
> Somewhat of the same issue.
 
I upgraded from 9.10 and since then have not been able to boot into any new kernels. It starts the process but then gives me a blank screen. Only way to login is to go to an older entry, and as of right now i'm using kernel 2.6.31-21-generic.
 
Any help would be appreciated.
 
Thanks
 
I can't even log in to the older kernel (2.6.31-21-generic), I think it may have been removed. (Blank black screen, with a message saying no disk image or something like that).

---

### Post by hudi on 2010-04-30
I'm having similar issues. After the update to 10.04 my system didn't boot (Kubuntu on a Dell Inspiron). First I got error messages about b43legacy drivers that were not found. I tried disabling the WLAN card in the BIOS. Now after some messages (too fast to read) I get a blank screen. End of story

Choosing an older kernel was a good hint: now I can login.

I never had any problems updating Kubuntu on this laptop. Any ideas/ hints on how to find out what's wrong would be greatly appreciated!

---

### Post by chaman1 on 2010-04-30
I can't even boot into linux right now :(

---

### Post by kooljester on 2010-04-30
Having the same problem, I guess we get what we pay for:guitar:

---

### Post by arepaking on 2010-04-30
Hello,
Do the following and you will be in no time working in Lucid.

a) Insert Ubuntu Live CD (It does not matter which version).
b) Backup your home folder (and any other user home folder).
c) Perform a fresh installation of Lucid.
d) Restore your backup.

Trust me, this is the best way to ensure that your system is properly configured. BTW, when restoring your backup, do not copy/merge your home folder. Go inside and take what you need. Docs, pictures, data, etc... 

Hope it helps!
-AK

---

### Post by manoynmonic on 2010-04-30
I had the same issue - old kernels worked, but the newer one wouldn't.  What worked for me was to boot into the older kernel, and install a kernel from the ppa (a few notches newer than the one that ships with the Lucid iso).

I got it from the index here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/)

There is one that came out yesterday that is newer than the link above, but I know 2.6.34 works perfectly (for me).

-mn

---

### Post by chaman1 on 2010-05-01
> **manoynmonic said:**
> I had the same issue - old kernels worked, but the newer one wouldn't. What worked for me was to boot into the older kernel, and install a kernel from the ppa (a few notches newer than the one that ships with the Lucid iso).
 
I got it from the index here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/)
 
There is one that came out yesterday that is newer than the link above, but I know 2.6.34 works perfectly (for me).
 
-mn
 
...which ones do i need to download?

---

### Post by manoynmonic on 2010-05-01
> **chaman1 said:**
> ...which ones do i need to download?

The link I gave was to rc5 kernel, I just tried rc6, it works as well.  Get the package called linux-image.  If you use a 64bit system, get the amd64 package, if you are 32 bit (if you don't know which, then you probably have 32), get the one with i386 in the name.

---

### Post by axelsvag on 2010-05-01
Thank you the r6 saved me also. Totally impossible to boot from 2.6.32.22

---

### Post by Esau on 2010-05-01
Thank you manoynmonic!  Worked for me as well.

---

### Post by chaman1 on 2010-05-01
Haha thanks, finally worked...but now my new problem is that the boot splash doesn't work.  I only have a black screen.  Any ideas?

---

### Post by manoynmonic on 2010-05-01
> **chaman1 said:**
> Haha thanks, finally worked...but now my new problem is that the boot splash doesn't work.  I only have a black screen.  Any ideas?

Glad it's working.  Lots of guys having trouble with the splash...  Try the noveau driver (and another thread :P).

---

### Post by chaman1 on 2010-05-01
> **manoynmonic said:**
> Glad it's working.  Lots of guys having trouble with the splash...  Try the noveau driver (and another thread :P).

Alright, thanks!!!

---

### Post by TyTiger on 2010-05-03
> **arepaking said:**
> Hello,
Do the following and you will be in no time working in Lucid.

a) Insert Ubuntu Live CD (It does not matter which version).
b) Backup your home folder (and any other user home folder).
c) Perform a fresh installation of Lucid.
d) Restore your backup.

Trust me, this is the best way to ensure that your system is properly configured. BTW, when restoring your backup, do not copy/merge your home folder. Go inside and take what you need. Docs, pictures, data, etc... 

Hope it helps!
-AK

And if you need to back up a databse from MySQL?

---

### Post by parovelb on 2010-06-04
Zdravo!

I did experienced the same issue. Thank you for the solution. 

Currently running [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-rc1-lucid/") on a Dell Latitude D400 notebook ;)

---

