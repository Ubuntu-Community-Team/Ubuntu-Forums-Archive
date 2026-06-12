---
title: "Guide me on installing on my low RAM PC...!"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by bimaljr on 2006-12-20
Hi,
I am a very newbie in Linux and I want to try first the Ubuntu
I am very familiar with Windows and know much more... (just for info)

I get CDs from ShipIt and want to install it.
My System Info : 
Intel P4 3.06Ghz
Intel 102 Ggc Motherbord
256 DDR Ram
Two HDD :
1) 80GB with four partition for windowsXP
        C:    NTFS   WinXP
        D:    FAT32  for Data
        E:    FAT32  for Data
        F:    FAT32  for Data
2) 10GB for Linux  (reserved for Ubuntu)

 (LG DVD writer for booting Live CD)
(my system is Intel x86 based)

I had booted the Live Ubuntu CD and get the live desktop too.
But when I clicked INSTALL from desktop icon, it takes so much time to load. Then I click  "Forward", it takes more than 20 min to load the map window (still not fully loaded)

I have posted a thread for this problem, but I get reply that I have to download the **Alternate install CD**... I cannot download this full cd, I have too slow internet connection :( 

Now, I see a thread for my probem at here :
[http://www.ubuntuforums.org/showthread.php?t=218036](http://www.ubuntuforums.org/showthread.php?t=218036)

And I think this will be done by this way... but anoter problem I cannot understand what it says. I want to install Ubuntu on my second 10GB HDD (It's empty). I also don't know more about fdisk.

**If you anyone can guide me for this I can install it, I just need help for this.**

Thanks for support

---

### Post by Haegin on 2006-12-20
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
Thats for low memory systems but compared to some that that guide works for - your pc is a monster - I installed kubuntu with ease from the alternate install cd on a p3 1.0GHz, 256MB Ram, 7GB hdd with ease - ran beautifully.

---

### Post by bimaljr on 2006-12-20
> Ubuntu version 6.06.1

To install a base system, boot from the alternate (install) CD and choose "Install a server."

it also points to install server I want to install as Desktop PC.. It's also pointing me to install from alternate CD :(

---

### Post by aysiu on 2006-12-20
"Install a server" from the Alternate CD doesn't mean you're actually installing a server (in fact, it uses a different kernel from the Server CD)--it's just a way to get a barebones installation that you can then add a desktop to.

---

### Post by bimaljr on 2006-12-20
But I want to know where to start? I get free cd from ShipIt

Please reply stap by stap info...

---

### Post by aysiu on 2006-12-20
Step by step info:

Download the Alternate CD from here:
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/edgy/ubuntu-6.10-alternate-i386.iso](http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/edgy/ubuntu-6.10-alternate-i386.iso)

If you don't live in the US and would like a local mirror or if you'd like to use BitTorrent instead of a direct download, this page has a list of other mirrors and download options you can use:
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Since you have a slow connection, I'd **highly** recommend using BitTorrent over a straight download.

Use the appropriate CD burning application to burn your ISO as a **disk image** (not as *data*). This will walk you through that process:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Then a good dual boot guide for the Alternate CD is here:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

Since you have 256 MB of RAM, your system isn't really that low RAM a PC... it's just too low to install Ubuntu from the Desktop CD. You can still run Ubuntu. However, if you have any concerns about speed (Gnome will be usable with 256 MB of RAM, but it won't fly), you can also check out Xubuntu (which also has an Alternate CD available):
[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by bimaljr on 2006-12-20
> 
Download the Alternate CD from here:
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/edgy/ubuntu-6.10-alternate-i386.iso](http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/edgy/ubuntu-6.10-alternate-i386.iso)

 - Hey... I cannot download 700MB file. My net connection speed is just 4 to 5 KB (real speed) per second. I am from India


> 
If you don't live in the US and would like a local mirror or if you'd like to use BitTorrent instead of a direct download, this page has a list of other mirrors and download options you can use:
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Since you have a slow connection, I'd **highly** recommend using BitTorrent over a straight download.

 - There is no link for bittorent for alternative cd on this page :(

---

### Post by aysiu on 2006-12-20
Here's a Xubuntu torrent:
[http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-i386.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-i386.iso.torrent)

There don't appear to be an Indian mirrors, but here's a torrent for Ubuntu from China:
[http://mirror.lupaworld.com/ubuntu/releases/edgy/ubuntu-6.10-alternate-i386.iso.torrent](http://mirror.lupaworld.com/ubuntu/releases/edgy/ubuntu-6.10-alternate-i386.iso.torrent)

---

### Post by bimaljr on 2006-12-20
Any other way that doesn't require this download... why don't you guide me with this help : 
[http://www.ubuntuforums.org/showthread.php?t=218036](http://www.ubuntuforums.org/showthread.php?t=218036)

Please do so...

---

### Post by aysiu on 2006-12-20
> **bimaljr said:**
> Any other way that doesn't require this download... why don't you guide me with this help : 
[http://www.ubuntuforums.org/showthread.php?t=218036](http://www.ubuntuforums.org/showthread.php?t=218036)

Please do so...
Why? Because that looks complicated, and I've never done anything like that before.

---

### Post by bimaljr on 2006-12-20
OK... I will try to download this.

---

### Post by bimaljr on 2006-12-22
I have downloaded and install UBUNTU 6.06.. wow great... The download takes 2 days (48 hours) to download it.. but anyway... great things takes some time..

**One problem : **I don't know root password, so I cannot login. The installer asked to input any user and I gave it the user **bimal** and set password too. I can login as user, but not as root. Is there any fix password for ubuntu? The installer don't asked me for any root password at installation time...!

Thanks

---

### Post by aysiu on 2006-12-23
> **bimaljr said:**
> I have downloaded and install UBUNTU 6.06.. wow great... The download takes 2 days (48 hours) to download it.. but anyway... great things takes some time..

**One problem : **I don't know root password, so I cannot login. The installer asked to input any user and I gave it the user **bimal** and set password too. I can login as user, but not as root. Is there any fix password for ubuntu? The installer don't asked me for any root password at installation time...!

Thanks
Ubuntu doesn't use root. It uses *sudo*. Read more here:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

