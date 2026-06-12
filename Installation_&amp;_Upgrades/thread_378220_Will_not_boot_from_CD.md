---
title: "Will not boot from CD"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by aggierandy on 2007-03-07
I am trying to run the live CD for 6.10 and when i put it in my laptop it gives me this screen

1133 Mhz Mobile Celeron CPU
Intel Processor Update Rec 01Dh Complete
External Cache: 256K Installed
Boot CD-ROM Type: Non Emulation Booting
ISOLINUX 3.11 Debian-2006-03-16 isolinux: Image checksum error, sorry...

Boot Failed: press a key to retry.


I want to preserve my Windows setup but I still want to be able to run  ubuntu. I thought it might be the CD so I ran it on another computer and the live CD worked fine. What do I do? Thanks. 

P.S. This is the 3rd PC i have tried to install Ubuntu on and I have nad no luck

---

### Post by Sef on 2007-03-07
A couple of questions:

1) Did you md5sum the download to verify it correctly downloaded?

2) Did you burn the iso at 4x or less?  Greater can cause a bad burn.

---

### Post by aggierandy on 2007-03-07
Well I made sure to burn it at 4x but I did not md5sum the download because I have no idea what that is. :-k I think I might have deleted the iso download can I run md5sum on the CD itself?  Thanks

---

### Post by Kateikyoushi on 2007-03-07
Here are some tools to verify the download. [LINK]("http://check-md5-sum-utility.qarchive.org/")

You could also check the disc on the machine which can boot it, at startup select the check disc from the menu. I have never seen that error so on 2 machines it is most likely the disc.

---

### Post by aggierandy on 2007-03-07
Im sorry my description was not clear. The other machine would boot Ubuntu to the menu but on this machine I cannot. I get that message as soon as the machine goes to run from the CD, like the system doesnt want to boot from there at all. On my dell laptop I can run the live CD just fine but on my hp machine it won't load. 

Ok so I have downloaded a checker now how do I use it. I have never used an MD5 checker. The principal is it will compare the download to a file and it will verify that it is intact. Well I found the MD5 file on my disc but now what do I do?

Sorry I have so little experience. I am trying to learn

---

### Post by Kateikyoushi on 2007-03-07
Download the ISO again if you deleted it and this softare as well [LINK]("http://www.midwavi.com/md5.zip"). Extract the MD5 checker paste to the top field the MD5 checksum from the download site and browse to the ISO, select the verify radio button at the bottom this should do.

---

### Post by aggierandy on 2007-03-07
Ok while I am waiting on that to download, maybe you could help me with my other PC. I tried to install and it was acting really funny. Nothing on the forums seemed similar. There is a possibility the hard drive is no good but I really don't know. Anyways I described it here. 

[http://ubuntuforums.org/showthread.php?t=376507](http://ubuntuforums.org/showthread.php?t=376507)

At first it wouldnt run at all and then I entered the irqpoll boot command and it got me to the desktop. But every time I try to install it get logged back out. Dunno whats going on....is it the disc.?? I guess we will see in a minute!

---

### Post by aggierandy on 2007-03-07
wow I guess no one really has any idea what to say about that thread. I guess I have an unsolvable problem! Well I checked out the iso with md5 and it says they do not match....but I dunno what I did wrong? I have no idea where to go from here. Any ideas? I am still convinced it is not the disc.

---

