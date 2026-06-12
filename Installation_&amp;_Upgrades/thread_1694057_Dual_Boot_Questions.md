---
title: "Dual Boot Questions"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by SquigglesXX on 2011-02-23
Hello,

I have recently taken an interest in making my desktop system into a dual boot system with Windows 7 (Currently on it) and Ubuntu. Have have done some research but it is hard to find what i am looking for. My current system is 

OS: Windows 7 Pro 64-bit
Processor: AMD Phenom II X4 965 3.40 GHz
Memory: G.SKILL DDR3 x2 4GB (8GB)
Motherboard: ASUS M4A89GTD PRO/USB3
SSD:[COLOR=Black] Crucial C300 64GB (For Windows 7 and soon to be Ubuntu)
Hard Drive: x4 Western Digital Caviar Black 640GB set up in RAID 10 (for data)

What I would ideally like it to be able to keep all my data and windows 7 stuff how it is and install Ubuntu on the SSD and have it recognize the RAID 10 for data. I have found a couple of tutorials for installing Windows 7 and Ubuntu as dual boot but am having issues with how it will work after it get Ubuntu installed in regards to RAID 10. If you have any tips or experiences for me I would appreciate it. If you could direct me to any links that might be helpful.

I am a Computer Science major and have used Linux at school so i know my way around but i definitely don't know it all.

If there is any more information you need to help me just let me know and if something like this has been posted sorry and could you redirect me there.

Thanks
[/COLOR]

---

### Post by YesWeCan on 2011-02-23
Hmm.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

You have a fast system with plenty of RAM. You could install VirtualBox and run Ubuntu out of that. Then you can access the RAID.

---

### Post by ronparent on 2011-02-23
Three factors:

1) You don't appear to be installing the OS to the raid but to the ssd. In that case the fakeraid howto doesn't apply.

2) You don't say which distro you are installing. But with either 10.04 or 10.10 dmraid (the software that permits you to access raid partitions) won't be automatically installed. You have to install dmraid after completing your system install. The raid partitons should then be automatically accessed provided raid 10 is suported.

3) You should verify that dmraid supports the raid 10 level for your raid chip set. Just type dmraid -l in a live cd terminal (dmraid is included on the desktop cd's for the last three releases). Which raid chipset is the raid 10 plugged into?
 
As another aside, not all ssd's are automatically recognized by gparted. It is an alignment issue. If that is the case you will have to resolve it before you can install Ubuntu to an ssd with Win7 (gparted must be able to recognize the partitioning on the drive you are installing to).  

You may have no problems at all but do post if you need more guidance. Good luck.

---

### Post by SquigglesXX on 2011-02-23
ronparent,
thank you for that information. I am installing the OS to a SSD and the hard drives are in a separate RAID 10.

I am still getting familar with terms. what is distro? And if it is what version i am installing i was hoping to get any recommendations.

Is dmraid included with the OS and just needs to be installed after?

Which raid chipset is the raid 10 plugged into? I feel like i should know this but how can i check? and the dmraid -l command will give a list of supported ones?

Thank You

---

### Post by YesWeCan on 2011-02-23
Yes, my mistake. That link does not apply.

---

### Post by ronparent on 2011-02-23
Disto is distribution - ie in the case of Ubuntu 9.10. 10.04, 10.10 etc. Dmraid is included on the desktop cd with any of these three 'distro's'.

Because you are not installing to the raid you will find that dmraid is not installed with the OS install but has to be separately installed when you first boot it after the install. Don't forget to then run sudo update-grub in a terminal to rescan your computer and pick up the win 7 on the raid.
 
You should check the MB documentation for the raid chip set. There are often two different sets on the computer and it depends which one your disks are plugged into. If the raid bios screen displays during boot that can tell you also. Not all raid 10 chip sets that work with windows are supported by dmraid. And yes dmraid -l will give you a list of supported ones.

---

### Post by ronparent on 2011-02-23
Disto is distribution - ie in the case of Ubuntu 9.10. 10.04, 10.10 etc. Dmraid is included on the desktop cd with any of these three 'distro's'.

Because you are not installing to the raid you will find that dmraid is not installed with the OS install but has to be separately installed when you first boot it after the install. Don't forget to then run sudo update-grub in a terminal to rescan your computer and pick up the win 7 on the raid.
 
You should check the MB documentation for the raid chip set. There are often two different sets on the computer and it depends which one your disks are plugged into. If the raid bios screen displays during boot that can tell you also. Not all raid 10 chip sets that work with windows are supported by dmraid. And yes dmraid -l will give you a list of supported ones.

---

### Post by SquigglesXX on 2011-02-24
Looks like i am going for 10.10 so i am downloading it now.

One thing that confused me was your "run sudo update-grub in a terminal to rescan your computer and pick up the win 7 on the raid." comment because I currently have my Win 7 on my C drive (SSD) and i have changed all the default paths for data to do on my D drive (RAID 10). I would like to set up the same thing with ubuntu.

I have an AMD SB850 which from what i herd is supported but will just check when I get the ubuntu downloaded.

Also I was wondering how I will need to set up the partitions. It looks like i will need a root for all the ubuntu OS files? and a swap for the memory. How big should i make the partitions? I have read the swap should be at least as big as the memory so 8 GB for me.

My SSD is 59.4 GB space and I have filled 27.7 with windows stuff so far. 
Will there be an easy way to set up the paths for the programs on Ubuntu to go on the RAID.

Thanks for all the help i am slowly getting there.

---

### Post by ronparent on 2011-02-24
> One thing that confused me was your "run sudo update-grub in a terminal to rescan your computer and pick up the win 7 on the raid." comment because I currently have my Win 7 on my C drive (SSD) and i have changed all the default paths for data to do on my D drive (RAID 10). I would like to set up the same thing with ubuntu.
Disregard my comment - only trying to account for why original scan with install didn't pickup your win 7. It's fixable anyway if the same problem persists.
> I have an AMD SB850 which from what i herd is supported but will just check when I get the ubuntu downloaded.
Supported as pdc.

> Also I was wondering how I will need to set up the partitions. It looks like i will need a root for all the ubuntu OS files? and a swap for the memory. How big should i make the partitions? I have read the swap should be at least as big as the memory so 8 GB for me.
The swap might make do with as little as 2 or 3 Gb and it could be placed on the raid during install. The same for the /home. The location and sizes of these partitions are determined during the manuall partitioning step.

ie 10 Gb for home on ssd
   3 Gb for swap on raid
   20 Gb for /home on raid

I don't think you would want to squeeze windows any more than you have to - windows tends to expand to occupy more and more space as it ages. 

Designating the /, swap and /home during install should allow all of them to be found on boot. I think if you install portions to the raid that dmraid will automatically install. If not, we can figure a way to fix it afterwards.

---

