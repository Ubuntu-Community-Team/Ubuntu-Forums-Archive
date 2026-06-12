---
title: "Problem with Installing Unbuntu AMD64"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by davidor on 2006-11-19
I have a 120gb with Windows XP sp2 in 80gb partition trying to add Unbuntu AMD64 to the 30gb partition.

I boot to the Unbuntu x64 CD and try to select Install for Text mode.  When that happens it loads the linux kernel then stops and freezes at Booting Kernel.

I really do not understand what is going on.  

I have tried other CD's i have burned and still it did not work.

---

### Post by taurus on 2006-11-19
How fast did you burn those CDs?  If you used the default speed, try to burn one again but this time, try 4x...

---

### Post by vibhu on 2006-11-19
I too am having a problem with AMD installation. Here's my system config: 

AMD64 3700+
2GB Ram
200GB SATA Hard Disk (Seagate)
Nvidia 7900GT

Here's what happened : 
In my 5.06 install i clicked on upgrade system. It started to download the binaries. Then something happened and the system froze. Since nothing was happening, I had to press the reset button. Next thing I know I cannot reboot into linux, though the Games partition (windows) is working fine. Using the ext plugin, I can even access the linux partition, but booting just does not work. I get an error : 
> /etc/mdadm/mdadm.conf : File not found
Waiting for root file system.

I downloaded the desktop 64 iso. Nope . Does not work. Freezes as soon as it boots into the graphical screen. 

I had [same issues in the last release of ubuntu]("http://ubuntuforums.org/showthread.php?t=201653"), so i tried the same steps again. 

So, I downloaded the alternate 64 bit Ubuntu, and tried to install from there. The problem is that it wants a root partition now ( I just have a swap and ext3 partition). If I want to create that I need to delete my ext3 partition, which I don't want to do. 

Why is Ubuntu so frustrating to install ?

---

### Post by vibhu on 2006-11-19
> **davidor said:**
> 
I boot to the Unbuntu x64 CD and try to select Install for Text mode.  When that happens it loads the linux kernel then stops and freezes at Booting Kernel.

I really do not understand what is going on.  


Did you download the desktop 64 iso or the alternate 64 iso ? Try the alternate 64 iso. Also if the ISO is giving problems, try to download from some other source, as that ISO may be corrupted.

---

### Post by rigol on 2006-11-20
Did you try booting with "noapic"?

---

### Post by davidor on 2006-11-20
I have tried to burned at 4x the Alt 64 version i got from this site and it kept freezing at booting kernel.

I tried although i am a novice about putting commands in i just type noapic or disableapic.

Neither work.  

I am going to see if i can get another Unbunbtu some where.  I did not say this but I tried a copy of Ununtu that somebody else had and it did the same thing.  I have even tried 32 bit ones and no go on that.  I did a memtest and passed.

---

### Post by davidor on 2006-11-20
Alt 64 from the torrent of this site is not working.  Gives me the same thing.

---

### Post by taurus on 2006-11-20
See if you can boot from x86 alternate CD?

---

