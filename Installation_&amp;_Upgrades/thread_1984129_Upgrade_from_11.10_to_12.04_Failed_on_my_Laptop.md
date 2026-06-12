---
title: "Upgrade from 11.10 to 12.04 Failed on my Laptop"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by sonicrock786 on 2012-05-21
Today when I logged in to my system I have got prompt to upgrade my system and I thought let me upgrade it.

When I did it, it took long time to download all the packages and then started installing.

I was watching everything it was doing in terminal window and after some time, It said installation/setup halted due to too many errors and it was asking me to reboot the computer.

I reboot the system and this time on my log on screen, I can not see any small icons e.g. language, power option icons.

When I logged in to my account, I can only see blank screen and nothing else. I tried Ctrl + Alt + Del to log off and shut it down.

What should I do in this situation ? How can I repair and get it back to normal.

I AM A NOOB AT UBUNTU.

My pc is a SONY VAIO laptop with Win 7 x64 Installed as primary OS and I have installed Ubuntu on different partition but as Windows Program. I installed Ubuntu from Windows. In case it helps.

I am currently running Win7 to use my laptop but I still want to have my Ubuntu back.

Please help me. Thanks in advance.

---

### Post by sonicrock786 on 2012-05-21
Please help me so that at least I can get backup of my data and delete and reinstall whole ubuntu from beginning if there isn't any other way to get it back to normal.

Thanks.

---

### Post by sonicrock786 on 2012-05-21
Seriously ?? No one ???

---

### Post by cortman on 2012-05-21
We're all volunteers here. Be patient. :)

Recovering your data and reinstalling Ubuntu should be very simple. Boot from an Ubuntu 12.04 LiveCD (select "Try Ubuntu" at the first screen when booting) and you'll have a complete Ubuntu desktop running off the CD. Copy your files from the laptop HDD to a flash drive or external HDD. Make sure you get everything you want off, then install Ubuntu 12.04. Make sure you select to replace the previous Ubuntu installations so you don't wipe out Windows.
You'll be much happier with a fresh installation than an upgrade anyway.
Good luck!

---

### Post by sonicrock786 on 2012-05-22
Thank you for your reply.

I will do the steps you have suggested but I am more interested if I can repair the current OS first. If there is no option to repair it then I will have to take back up manually as you said above.

---

### Post by sonicrock786 on 2012-05-22
There isn't much data to backup but most important things are my Bookmarks/Favourites in Mozilla Firefox and Chromium.

Does anyone have any idea how can I backup that from live cd ?

---

### Post by cortman on 2012-05-22
> **sonicrock786 said:**
> There isn't much data to backup but most important things are my Bookmarks/Favourites in Mozilla Firefox and Chromium.

Does anyone have any idea how can I backup that from live cd ?

On my Ubuntu VM firefox bookmarks are two .json files stored in ~/.mozilla/firefox/bddc4pd3.default/bookmarkbackups.
Chromium files will be stored in a similar setup in your home folder; when viewing the files press left ctrl+h to view hidden files, and find a .chromium folder. Search for bookmarks in there.

---

### Post by agerbo on 2012-05-22
I don't know is this can help you.

I upgraded from 11.04 to 12.04, but the installation stoppede at a file debconfig and I had to kill ubuntu. When I startet again grub did not work og I could'nt get into ubuntu. I burned a live cd (download in windows and burn on cd with free program "iso burn"). I  started pc and got in on live cd, chose install. I did not choose alongside or erase, but the third choise and I saw the partitions. I doubleclicked the line with linux. In my case sda5. I chose root (in the dropdown /) and in use as I took journal files and under loader installation I took sda (the first), even if it told someting about Samsung, end my pc is Lenovo. When the installation was finished and I restarted, grub was ok. And all my files in Ubuntu was ok.

Next year I will first burn a live cd og check that it works. Then I will upgrade, and if it does not work, I will use the method above ( of course it depends of how you initialy installed ubuntu)

---

### Post by rybu on 2012-05-23
I tried the "install alongside" option today.  It seems to have corrupted my grub install.   I had 12.04 already installed, and asked the install CD to install another 12.04 alongside it.  IMO this "install alongside" option isn't very well set up yet.  When you're resizing the partitions (with the slider) it's not clear which partition is which. 

I suspect it was designed only with Linux being installed alongside an existing Windows installation, and other options were not given much thought? 

Who knows.  I've erased the partition and started with a clean install.

---

### Post by Alastair Rae on 2012-05-23
> **cortman said:**
> We're all volunteers here. Be patient. :)

Recovering your data and reinstalling Ubuntu should be very simple. Boot from an Ubuntu 12.04 LiveCD (select "Try Ubuntu" at the first screen when booting) and you'll have a complete Ubuntu desktop running off the CD. Copy your files from the laptop HDD to a flash drive or external HDD. Make sure you get everything you want off, then install Ubuntu 12.04. Make sure you select to replace the previous Ubuntu installations so you don't wipe out Windows.
You'll be much happier with a fresh installation than an upgrade anyway.
Good luck!
So why the heck does it offer an upgrade if it can mess up your system? Do we really have to completely reinstall the OS every 6 months and restore our data? Upgrade in place messed up my system on an earlier release so I'm not touching it.

---

### Post by cortman on 2012-05-23
> **Alastair Rae said:**
> So why the heck does it offer an upgrade if it can mess up your system? Do we really have to completely reinstall the OS every 6 months and restore our data? Upgrade in place messed up my system on an earlier release so I'm not touching it.

You may as well apply the same logic to "why does it allow us to use root privileges if it can mess up our system"? You don't have to upgrade if you don't want to; in fact the wide majority of users stick with the LTS releases which are supported for five years. You can go till 2017 without touching your OS if you desire, and it'll still be fully supported and updated. You can upgrade every six months if you wish, but be prepared for some bugs.
A clean installation of ANY OS will always be leaner and more stable than an upgrade.

---

