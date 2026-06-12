---
title: "Password for Wubi?"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by hpng on 2010-11-27
Helloz:   Downloaded Wubi on Win 7- 64 bit. ran it,a nd it asked for password. I gave it my Ubuntu account password a d it did not work. I also gave it my PC's password, it still does not work...  Help.  Thanks.

---

### Post by hpng on 2010-11-27
I wonder if there is somewhere I can delete / reset password and user name saved by Wubi.

---

### Post by hpng on 2010-11-27
I forgot to mention when I start Wubi, it never asked for me to do account setup.
it only asked me to enter a password (with no confirmation box to reenter same password for new install) and it has the same user name as I have for win 7, as if I already install before.  Just does not make any sense.

I did tried to install version Ubuntu 10.10, but abandon it when I realize that I cannot install it due to partition limits, i.e. I already have 4 partitions dedicated and cannot change it.
It was a clean "abandon" in the fact that I click Cancel and finally Quit before any partitionw ere created.


So, now I am wondering may be the installer somehow create password without me knowing.  so does anyone out there knows how to reset or delete the password associated with Wubi?


Thanks

---

### Post by wilee-nilee on 2010-11-27
First check the MD5SUM of the ISO or CD your installing with.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

No secret password no partitioning.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Since it is a fresh install just remove it, make sure you have a good download and look at the Wubi guide.

---

### Post by hpng on 2010-11-28
Hello:

First check the MD5SUM of the ISO or CD your installing with.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[COLOR=Teal]Response: 
I am just running Wubi.  There is no ISO file yet.
Wubi is suppose to download it after "new" account setup.[/COLOR]

[COLOR=Teal]I just checked with WinMD5Sum for ISO and Wubi file.
Both are correct.[/COLOR]

No secret password no partitioning.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Since it is a fresh install just remove it, make sure you have a good download and look at the Wubi guide.

[COLOR=Teal]Response:
Wubi is just an exe file.  Wubi was never installed since it just ran as an exe file.
I already deleted and downloaded it three times!  And it still has the same problem, i.e.
it only display boxes for username and password as if account has already being setup.

I also do not see any Wubi install under Control Panel's Programs that were installed.
[/COLOR] 

So I am still lost!

---

### Post by wilee-nilee on 2010-11-28
> **hpng said:**
> Hello:

First check the MD5SUM of the ISO or CD your installing with.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[COLOR=Teal]Response: 
I am just running Wubi.  There is no ISO file yet.
Wubi is suppose to download it after "new" account setup.[/COLOR]

[COLOR=Teal]I just checked with WinMD5Sum for ISO and Wubi file.
Both are correct.[/COLOR]

No secret password no partitioning.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Since it is a fresh install just remove it, make sure you have a good download and look at the Wubi guide.

[COLOR=Teal]Response:
Wubi is just an exe file.  Wubi was never installed since it just ran as an exe file.
I already deleted and downloaded it three times!  And it still has the same problem, i.e.
it only display boxes for username and password as if account has already being setup.

I also do not see any Wubi install under Control Panel's Programs that were installed.
[/COLOR] 

So I am still lost!

A regular download of Maverick has the wubi installer in it download that burn it to a cd and use it I think that will work. You have to be in the admin account to install.
[http://www.ubuntu.com/](http://www.ubuntu.com/)

Really one of the best insurance plans for a MS only or a setup with Wubi is a Ubuntu or various other open source cd available it has so many uses like recovery resetting the bootloader Ubuntu or a MD compatible, do you get what I'm saying here.

I have tried the wubi download method your using and found it to be problematic. You do the math; your down loading a foreign install and installing at the same time, in a perfect world it should work but there a bit to many outliers.

When you downloaded wubi there was a ISO file it is the installer that is .exe

---

### Post by hpng on 2010-11-28
Did a google search and found out the problem.
One new user has the same problem.
The problem is poor display of confirmation password box 
below the top password box.
I have to tilt the LCD screen to see it.
Cost me several hours here!
Now it is installing.. Cross my fingers....

---

### Post by wilee-nilee on 2010-11-28
> **hpng said:**
> Did a google search and found out the problem.
One new user has the same problem.
The problem is poor display of confirmation password box 
below the top password box.
I have to tilt the LCD screen to see it.
Cost me several hours here!
Now it is installing.. Cross my fingers....

Hey good job.;)

---

