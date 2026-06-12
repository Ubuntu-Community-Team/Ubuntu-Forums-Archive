---
title: "[SOLVED] Help with Intel 945"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by newbeeman on 2008-03-08
I am trying hard to install a dual boot Ubuntu but failing miserably.
The first attempt went on for hours till I finally quit.
I then decided to format C to remove windows completely, reinstalled without adding any other programs.
Tried to use the Live CD, but it starts then the drive keeps rolling without imput. Read somewhere on this forum to try Alternate CD, that wouldn't even start.
I am really struggling to get this going. 
I run Ubuntu successfully as a dual boot on my machine.
PLEASE help me before this b.... machine goes out the window:(:confused:.

---

### Post by Pumalite on 2008-03-08
First clean your drive. DBan:[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Delete anything left in your drive (if any). Make new large partition of your whole hard drive, formatted ext3. Then install Ubuntu. Less than 512 MB of RAM or a rare video card, better use the Alternate CD to install.

---

### Post by newbeeman on 2008-03-08
[QUOTE=Pumalite;4477737. Then install Ubuntu. Less than 512 MB of RAM or a rare video card, better use the Alternate CD to install.[/QUOTE]

I believe my problem is the chipset.
I did try all you suggested, deleted the partitions, formatted the drive during windows install.
Now the drive keeps running and doesn't come to a stop, so I cannot install correctly.
Please advise.

---

### Post by Pumalite on 2008-03-08
Is that drive one large partition, formatted ext3?

---

### Post by Pumalite on 2008-03-08
Ubuntu has no problems with Intel 945 chipset.

---

### Post by newbeeman on 2008-03-08
> **Pumalite said:**
> Is that drive one large partition, formatted ext3?

My original post states a dual boot required, so format whole disc to ext3 would create more problems?

I now have partitioned the drive 35gbs for win and the same for Ubuntu.
I have just tried another install, same thing. The CD runs part way, allows to check disc etc, all OK, but then it just keeps running without completing the install.
Any further help?

---

### Post by Pumalite on 2008-03-08
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by newbeeman on 2008-03-08
> **Pumalite said:**
> [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

I did do a lot of reading before I came here, in fact I recognise the ones you quote. But now where can I find anything about a constant running disc drive.
Any other comments would be appreciated.

---

### Post by Pumalite on 2008-03-08
Test your drive with TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Or rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Maybe it's going south.
If you are referring to your CD-DVD Drive, that's an entirely different matter.

---

### Post by newbeeman on 2008-03-08
> **Pumalite said:**
> Test your drive with TestDisk: [
If you are referring to your CD-DVD Drive, that's an entirely different matter.

You might be right, but at the same time I have just re-installed windows without a problem.
So what would cause this problem? Does it not prove my hardware is OK?

---

### Post by louieb on 2008-03-08
The whole install takes 20 min to an hour depending on how fast your pc and just as important how fast is CD drive. 
There are several screens that come up during the install. 
Can you describe the last screen you saw or maybe the screen that it seem to be stalling on.

---

### Post by Pumalite on 2008-03-08
Yes. Then, burn a new Ubuntu CD after doing md5sum on your iso, burn at 4x or less, check for CD integrity after burn and before install.

---

### Post by newbeeman on 2008-03-08
> **louieb said:**
> The whole install takes 20 min to an hour depending on how fast your pc and just as important how fast is CD drive. 
There are several screens that come up during the install. 
Can you describe the last screen you saw or maybe the screen that it seem to be stalling on.

I have installed Ubuntu on 3 machines before this one. 
The last screen I have is at the install icon, but the mouse is irratic and the cd-rom is still running after about 20 mins.
I have used this Live Cd before so know that is OK.

---

### Post by louieb on 2008-03-08
Still could be the CD its self. I've had them go bad on me. But if it is the chipset. THe only thing I can think to do is try is boot options that have to do with drive access. Here is a couple of lists for Debian based distros.
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")

---

### Post by newbeeman on 2008-03-08
> **louieb said:**
> .
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")

Sorry this is all beyond me.
I have just tried to install Kubuntu and ended up with an error after it ran for some time.
"The process for the file protocol died unexpectedly"
I am beginning to think I have an un-installable box. 
Where do I go from here? Chuck it out and start with another machine?

---

### Post by Pumalite on 2008-03-08
Louieb's idea of boot parameters is something that you definitely have to try. All OS's have a learning curve.

---

### Post by newbeeman on 2008-03-08
> **Pumalite said:**
> Louieb's idea of boot parameters is something that you definitely have to try. All OS's have a learning curve.

I have experimented with another alternative, a 'Mini Install'.
This is only a 10mb installer, takes a great deal of pressure off the Cd-rom and Ram as it downloads all the packages off the repositories.
It ran very well but again stuck at 90% which is about where the Live CD stopped.
So, I'm giving it best until I can get the hardware checked out by my Guru.
Thank you all for the advice, I will mark this one as solved.

---

