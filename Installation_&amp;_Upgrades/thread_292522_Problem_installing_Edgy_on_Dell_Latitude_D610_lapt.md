---
title: "Problem installing Edgy on Dell Latitude D610 laptop"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by trmiv on 2006-11-03
Last night I downloaded the desktop iso of edgy and burned it, but I can't get to the install. When I boot to the CD the screen comes up with the various options, I select the first one to install Ubuntu. It launches that splash screen with Ubuntu on it with the progress bar. I can hear the CD drive spinning up and down. Eventually I get an error that says:

Buffer I/O Error on device sr0 logical block 357564

When I got to work today I burned the exact same iso download to another CD, and installed it on a Latitude D600 and it worked fine. I was able to install and do everything perfectly.  I took the exact CD that I used today at work that installed fine and tried it at home. It gives me the exact same error as I got last night "Buffer I/O Error on device sr0 logical block 357564". 

I also got a new CD-rom drive and tried the disc in that, and it still gives me the error. So apparently it's not the disc or the drive. The weird thing is, this exact same CD installed just fine today at work on a D600. Only difference is my laptop is a D610. I'm confused. The drive works fine in Windows, and works fine installing windows, but refuses to work with ubuntu.

---

### Post by scb147 on 2006-11-03
I'm having the exact same problem with my Latitude D610.

Never did this with Dapper.  This may be one reason why my upgrade from Dapper to Edgy was such a disaster...

---

### Post by scb147 on 2006-11-03
The first CD I burnt was a CD-RW, so I tried again using a CD-R, no luck with either.  Both of them give me the Buffer I/O Errors.  The checksum matches as well.

Back to Dapper for me.

---

### Post by trmiv on 2006-11-04
Good to know I'm not alone.  Weird that it works on the D600 and not the D610.  Sucks that I ordered a CD of edgy thinking maybe the download was screwed up.

---

### Post by trmiv on 2006-11-05
I'm done messing around with it.  I installed 6.06 which went fine, but now I'm having a nightmare of a time getting my Intel 2200 wireless card to work.  I'm reading all the documentation on it, but at this point I'm just about fed up with this whole thing.

---

### Post by no_one on 2006-11-07
Hey all!

I'm having the exact same problem on my Inspiron 9400. 6.06 worked great, Intel ProWireless 3945 worked too. The wifi and bluetooth LED's actually worked properly. 

Anyway, it's good to see that I'm not along with this error. Switching back to 6.06 :mad:

---

### Post by trmiv on 2006-11-14
So I figured this out.  I ended up buying an edgy disc on the internet, and that worked fine.  I then wanted to try Kubuntu and ran into the exact same error.  So that got me thinking, the discs that I burned that didn't work we're all burned on the same computer.  So I stuck the images on another computer and burned them (with nero again), and they worked!  The odd thing is, the "bad" images will work on a D600, just not a D610.

---

### Post by no_one on 2006-11-14
Wow, that is very strange. good news is that I got 6.10 working finally. this is what I did: 
1. reformat partition
2. install 6.06
3. edit sources.list with [these ]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Repositories")repositories
4. reboot into recovery mode and the usual: 
apt-get update
apt-get upgrade
apt-get dselect-upgrade

and it magically works, just takes hours of downloading updates. good luck to all!

---

### Post by kchung on 2006-11-17
I'm also receiving this problem on a Dell Inspiron 4000 series notebook. I've burned the disc on two different computers/burners, and on two different brand media and I still get nearly the same error:
```
Buffer I/O error on device hdc, logical block 357564
```

It goes on for a while and then drops me to Busybox.

---

### Post by mormith on 2006-12-01
I wonder if 6.10 is able to boot on any newer dell laptops...
My Latitude D810 fails but the old C600 is able to boot.

---

### Post by shareMenaPeace on 2006-12-31
On d620 i get the same error but can install. I used 6.10

---

### Post by scaryant on 2006-12-31
Hi,

I found this thread for you, sounds like these guys had exactly the same issue with their laptops and resolved it with the instructions included in [thread.]("http://ubuntuforums.org/showthread.php?p=1919513")

If that still doesn't resolve the issue you can try loading Ubuntu via the network, I recently did this using another Windows machine providing you have a PXE Bootable machine. FYI I prepared [HOWTO]("http://ubuntuforums.org/showthread.php?t=327597") to guide people through...

HTH - Cheers

---

### Post by knelafina on 2007-02-17
Two days ago I bought a new laptop, a Toshiba A100-999 (core 2 duo, sata HD 120 GB, Nvidia 7300, DVD-RW Pioneer DVR-k17A) and I wanted to install edgy on it, but when I load the LiveCD I'm having the same error (Buffer I/O error on device Sr0, logical block 357564) booting. 

It appears 4 times after ubuntu splash and then the livecd continue to load.  I can load edgy with the livecd but I am scared to install it and get a big error. I actually have a partition with xp (necessary for my studies) and stop me to try it too...

Any sugestions?

---

### Post by thelizardreborn on 2008-05-01
From research in other places on the internet, it seems this error is caused by faults on the CD, which is why official CDs tend to be more likely to work. The thread [here]("https://answers.launchpad.net/ubuntu/+question/19682") suggests burning your own ubuntu (or kubuntu etc) discs at a lower speed, like 4x.

---

