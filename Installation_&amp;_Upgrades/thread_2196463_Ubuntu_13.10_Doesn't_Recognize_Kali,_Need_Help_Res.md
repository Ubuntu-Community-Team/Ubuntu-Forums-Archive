---
title: "Ubuntu 13.10 Doesn't Recognize Kali, Need Help Resizing Partitions"
date: 2013-12-29
forum: Installation &amp; Upgrades
---

### Post by VicariousToast on 2013-12-29
Hey guys, I'm having some problems installing Ubuntu 13.10. A few days ago I finished building a computer, and decided to check out Kali Linux just to see what it was like. I actually like it, even though I don't have the knowledge required to use the pentesting tools. I would like to keep it installed, but I decided to dual-boot Ubuntu alongside Kali, and use Ubuntu for casual stuff and gaming, while using Kali for programming and the like, and for pentesting in the future. 

I used UNetBootin to make a bootable USB for installing Ubuntu, which worked fine. When I got to the partitioning step, it did not recognize another OS (it still recognized my partitions). So the only option given to me is to format my partitions, which I don't want to do. I tried to resize my partition with GParted, (I had some minor issues with the Kali install, and ended up using a single "/" partition, without a seperate "/home" partition. I figured I didn't really need a seperate /home partition, since I don't plan to install and uninstall different distros much.), but I couldn't resize it. I tried doing it via a live cd, but I still got the same result. 

I would prefer not to format the hard drive and re-install kali, because it was a pain in the ass to get my wireless card's drivers working (the process itself wasn't hard, it's just that my computer is in the basement, so I had to unplug everything and take it upstairs to plug it into the modem so I had internet access, and then take it back downstairs again.), so can someone please help me out with resizing my partitions? I will attach a few screenshots of GParted so that I don't have to explain in further detail (I would just cause unnecessary confusion).

---

### Post by oldfred on 2013-12-30
You have a LVM install which is a full drive install. You can only resize with LVM tools. But then you lose the advantages of LVM.

Gparted does not work on LVM partitions although I thought I saw the very newest release may, but that is only directly downloaded not in any distribution yet.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay

    
I think the above is the extent of my LVM knowlege. :)

---

### Post by VicariousToast on 2013-12-30
Thank you for the reply oldfred.

I'll try to resize the partition with lvm then, and see what happens. I have another question related to my Ubuntu install though. I have a wireless card that requires the drivers to be installed manually. It isn't much of a problem, all I had to do was install linux-headers-generic or build-essential through apt-get. I already had one of them installed, but I can't remember which. I think build-essential was the one that was already installed. Anyway, I want to download the files and install them manually, so that I don't have to take my computer upstairs again. Where would I download the files from? I found a few websites, but there were differences among the files, so I don't know what I need to download.

---

### Post by oldfred on 2013-12-30
Does wired Ethernet work? Usually then you can download directly from repository.

 Offline Updates:
[https://launchpad.net/keryx/+download](https://launchpad.net/keryx/+download)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
[https://help.ubuntu.com/community/Rsyncmirror](https://help.ubuntu.com/community/Rsyncmirror)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

These are probably more than you need. But is upstairs connected to your computer?

Setting up your own APT repository with upload support - 2005
 [http://www.debian-administration.org/articles/286](http://www.debian-administration.org/articles/286)
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[https://help.ubuntu.com/community/LocalAptGetRepository](https://help.ubuntu.com/community/LocalAptGetRepository)

---

### Post by VicariousToast on 2013-12-30
Thanks, that should be much easier than the way I was prepared to do it.

> These are probably more than you need. But is upstairs connected to your computer?

No, my computer is downstairs, I am using a wireless card to connect to my wi-fi network. When I first installed Kali, I had to take it upstairs so I could install linux-headers-generic, so that I could install my drivers. Now I decided to install Ubuntu, so I will need to install the drivers for Ubuntu as well. I don't have a long enough ethernet cable to run all the way downstairs, so I had to take it upstairs and plug it into the router, and then move it back downstairs when I was done. My mother's computer is in that room, and there wasn't much space. It was kind of annoying having to go through that process. That's why I want to install it offline, that way I can keep my computer in the basement.

---

### Post by VicariousToast on 2014-01-02
Well, I succesfully installed Ubuntu. I'm having some problems with installing my wireless card drivers now, but I think that would belong in it's own thread.

Thank you for the help oldfred, I really appreciate it.

---

