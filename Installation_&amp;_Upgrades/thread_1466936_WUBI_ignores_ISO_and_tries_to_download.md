---
title: "WUBI ignores ISO and tries to download"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by ramasan on 2010-04-30
I have downloaded the 10.04 release install iso DVD - all 4G worth. I am now trying to install in my Win 7 x64 desktop.

No matter what I try, Wubi doesn't seem to see the iso and goes to:
Downloading ubuntu-10.04-desktop-amd64.iso.torrent

Grr.

I have tried:
extract iso and run wubi
  - with the 4G iso in the root directory
  - with the 4G iso in the same directory as wubi (and the rest of the extracted iso)
place *just* wubi.exe and the iso in the same dirctory
place *just* wubi.exe with iso in root directory

nothing works, it wants to download every time.

i noticed the iso wubi seems to want to download and the current iso name is different
ubuntu-10.04-desktop-amd64.iso vs
ubuntu-10.04-dvd-amd64.iso

i tried a noob hack and renamed my 4G iso to what wubi seems to be looking for and that didnt work.

would it be so hard to have a "source" select on the wubi screen? seems like a lot of people have trouble with this.

---

### Post by northrup on 2010-04-30
I'm pretty sure Wubi has to use the standard LiveCD (the 700 MB one).  DVD and alternate .iso's aren't supported.  Although, if it's on the DVD itself, I would think it wouldn't need to download a new .iso file.

Regardless, try it a regular LiveCD (NOT a LiveDVD) and see if it will install without re-downloading.

---

### Post by ramasan on 2010-04-30
[IMG]http://img514.imageshack.us/img514/2653/wubiinstallfail.png[/IMG]

downloaded iso. ran wubi from same directory.

same result.

---

### Post by pecazp on 2010-05-27
Same thing like in the post above. Has something being done to fix/enable this method of installation?
In my case, installation would last at least two full days and that is unacceptable (impossible).

Thanks

---

### Post by dino99 on 2010-05-27
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by darkod on 2010-05-27
> **pecazp said:**
> Same thing like in the post above. Has something being done to fix/enable this method of installation?
In my case, installation would last at least two full days and that is unacceptable (impossible).

Thanks

I'm confused. In the first case when DVD ISO was used, lets say it wants to download the CD ISO.
But when wubi.exe and the CD ISO are in the same folder, it should definitely work. I can't find the exact page right now but I clearly remember on the Ubuntu website it said: if wubi.exe and the ISO are placed in the same folder, when you start wubi.exe it will not try to download over the internet, it will use the ISO.

And to make sure you are using the same version wubi.exe it's best to extract it from the ISO itself. The unpacked ISO and wubi.exe need to be in the same folder.
And it should work.

---

### Post by pecazp on 2010-05-27
> **darkod said:**
> 
But when wubi.exe and the CD ISO are in the same folder, it should definitely work. I can't find the exact page right now but I clearly remember on the Ubuntu website it said: if wubi.exe and the ISO are placed in the same folder, when you start wubi.exe it will not try to download over the internet, it will use the ISO.

I have also read this part, so i downloaded cd iso of version i wanted to install.
I guess problem is with version, mine not being "live".:)
Wubi is not to be found inside this iso.

[IMG]http://i128.photobucket.com/albums/p164/drpager/wubi.png[/IMG]

Do i have to download different version or there's some way to make this one work?

Thanks again for your time.

---

### Post by darkod on 2010-05-27
> **pecazp said:**
> I have also read this part, so i downloaded cd iso of version i wanted to install.
I guess problem is with version, mine not being "live".:)
Wubi is not to be found inside this iso.

[IMG]http://i128.photobucket.com/albums/p164/drpager/wubi.png[/IMG]

Do i have to download different version or there's some way to make this one work?

Thanks again for your time.

Yes, in your case that is a different ISO. It has to be the desktop version, it has -desktop- in the name. And that ISO has the wubi.exe inside which you need to extract and them place the wubi.exe and the unpacked ISO in the same folder and start wubi.exe like that.

---

### Post by pecazp on 2010-05-27
Wow, that was fast. :)
Well i better go and download right one.
 
 Thanks again.

---

### Post by steveneddy on 2010-05-27
The Ubuntu Live CD **_IS_** an .iso - FYIs

You will have a better experience by partitioning and installing Ubuntu on that partition or using a virtual machine like [VirtualBox]("http://www.virtualbox.org/wiki/Downloads"). It's free and very easy to use.

cheer

---

### Post by pecazp on 2010-05-27
To be honest, i've tried to install version that you see in the image above. Made partitions (swap, root) and gone trough whole process of installing. When it finished, i couldn't boot neither Windows 7 nor Ubuntu. 
Win7 startup repair didn't do the job and i tried something i don't remember from Ubuntu CD but with same result.
I've read somwhere that it's about version of GRUB or something.
But it was no real damage since i was already long procrastinating reinstallation of windows.
And that is something entirely off topic. 

ubuntu-10.04-desktop-amd64.iso ...downloading... :cool:

---

### Post by vinaykumar on 2010-08-21
Disconnect the network (internet connection) and try to install, that did the trick for me,

---

### Post by Tohayaseen on 2010-12-23
> **ramasan said:**
> [IMG]http://img514.imageshack.us/img514/2653/wubiinstallfail.png[/IMG]

downloaded iso. ran wubi from same directory.

same result.

dude visit this problem solved
[http://www.youtube.com/watch?v=CrnhymdXJ1g](http://www.youtube.com/watch?v=CrnhymdXJ1g)

---

### Post by Tohayaseen on 2010-12-23
IF u have redownloading problem visit 
[http://www.youtube.com/watch?v=CrnhymdXJ1g](http://www.youtube.com/watch?v=CrnhymdXJ1g)
problem solved

---

### Post by psusi on 2010-12-23
ISOs are for burning to disc, not extracting on your hd.  You need to burn it to a disc, and preferably boot from it and do a real install instead of using wubi.

---

### Post by Tohayaseen on 2010-12-23
[http://www.youtube.com/watch?v=CrnhymdXJ1g](http://www.youtube.com/watch?v=CrnhymdXJ1g)
this vid shows how to solve the problem

---

### Post by Tohayaseen on 2010-12-23
> **ramasan said:**
> [IMG]http://img514.imageshack.us/img514/2653/wubiinstallfail.png[/IMG]

downloaded iso. ran wubi from same directory.

same result.

[http://www.youtube.com/watch?v=CrnhymdXJ1g](http://www.youtube.com/watch?v=CrnhymdXJ1g)

---

