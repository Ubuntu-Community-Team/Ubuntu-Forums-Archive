---
title: "Ubuntu Freezing and grup corrupting"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by sazhagianambi on 2012-09-05
Hi, 

I installed ubuntu 12.04 along with Windows 8 as dual boot system on Sony Vaio F11 laptop. 

When I run Flash video (youtube, espn3) ubuntu seems freezing the whole system..I happened to do cold reboot few times which allows me to get back to ubutu...Then later I was reading about Magic Recovery Key ( Alt+PrntScreen+R+E+I+S+U+B) and tried when it frozen again.. This time it restarted but shows up message as "Operating SYstem Not Found"...

Later I was able to restore grub using Live CD + Boot Recovery tool..here is the dump [http://paste.ubuntu.com/1188086/](http://paste.ubuntu.com/1188086/)...

I just want to understand what went wrong, or I am not suppose to use Alt+PrntScreen+R+E+I+S+U+B rather than cold reboot..

I hope I posted the question in correct forum...Thank you very much...

-Nambi

---

### Post by sazhagianambi on 2012-09-06
Seems I spoken too soon...Now every time I restart machine it seems hit and miss for boot menu showing up...couple of times I see "No Operating system found" and some times I see dual boot options fine....

What could be issue? Can some one please advise me as what would be best option now? any help is appreciated...

additional info is I do uses SSD(crucial m4, 128GB)...

---

### Post by darkod on 2012-09-06
1. There are no linux partitions shown in the results summary. And no 128GB neither.

2. There is no win8 recognized by the script. Not sure if it's not able to detect win8, or you have some weird win8 installation.

---

### Post by sazhagianambi on 2012-09-06
> **darkod said:**
> 1. There are no linux partitions shown in the results summary. And no 128GB neither.

2. There is no win8 recognized by the script. Not sure if it's not able to detect win8, or you have some weird win8 installation.

Thank you for having look on this. I happened to have connected multiple external disks which is showing up in that log isn't much helpful. I'll try to get the log again with my internal HD alone and post in evening..

I don't know why its not showing up 128GB there, but I have three partitions there...103 GB for Windows 8 (which is upgraded from Win7), 17 GB where Ubuntu 12.04 got installed and another GB for swap...

please let me know what info needed more, I'll try to run Boot repair tool for log again after removing all my external HDs in evening and post back (ie, hoping I am able to get into system fine)..

---

### Post by sazhagianambi on 2012-09-06
[http://paste.ubuntu.com/1189843/](http://paste.ubuntu.com/1189843/) here is my updated Boot-Repair Log..This will have only the SSD i used...I see there is some info about ext4 partition recommended, I don't think I done this...any help is appreciated..

---

### Post by darkod on 2012-09-07
I have no idea why right now, but win8 is not getting detected. Yes, it detects the boot files and creates the win8 loader entry, but the actual OS is not detected.

Look at the top of the results, under sda2:
Operating System : nothing

Look under sda3:
OS : Ubuntu 12.04.1 LTS

It is not detecting it as an OS. This might be due to win8, or not.

---

### Post by sazhagianambi on 2012-09-07
ha, I see what you taking about now...Its been too much freezing things up going on both Ubuntu and Windows 8 and then I happened(forced) to wipe the whole SSD and re-install from start...

I looked on the [Guide]("http://www.linuxbsdos.com/2012/06/06/how-to-dual-boot-linux-mint-13-cinnamonmate-and-windows-7/2/") posted here and formatted the drive accordingly ( sda3 for MBR(/boot) with 500 MB, sda5 for / with 8 GB, sda6 for /home with 12 GB and 2 GB for swap[system has 8 GB ram, so not sure its needed though] )....Now both seems OKAY at moment...I haven't installed Boot-Repair tool yet for log, will post it later when I get chance (not sure its recognized win8 this time though)...

Is there something else I have to make sure? I read some stuff about RAID and SSD but not sure as I have to do something...

Thanks for all inputs...

---

