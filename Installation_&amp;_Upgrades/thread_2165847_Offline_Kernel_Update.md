---
title: "Offline Kernel Update"
date: 2013-08-06
forum: Installation &amp; Upgrades
---

### Post by HappyFishFace on 2013-08-06
I need to update to the new kernel, (3.10.5, right?) 
but i cannot use wget, because the current kernel on Ubuntu 13.04 does not support my Ethernet chipset. (Killer E2200)
I was lead to believe that kernel 3.10 does have support for it, though.
Being a little new to Ubuntu, I need a step by step process to update the kernel while totally offline.
Any explanation of the steps also helps me to understand my OS more.
I need to know exactly what to download and from where.
I need to know what commands to run.
I have not been able to download any programs/applications other than the ones included with the default 13.04.
I am dual booting windows 7, using grub to switch between OS's. (idk if that matters)
Both OS's are 64-bit.
I am using two drives, one for OS and other for data.(also, maybe unnecessary)

Thanks in advance for anything and everything.


Also, is it kernel or kernal?

---

### Post by sanderj on 2013-08-06
A few remarks as you say "anything and everything":

- has your computer Wifi? If so, can you connect to your LAN/Internet using Wifi? That would make things much easier.
- if not, have burnt and live-booted Ubuntu 13.10? It has a very recent Linux kernel built in. See [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
- what is your source that tells linux kernel 3.10.5 supports your Killer E2200?

---

### Post by HappyFishFace on 2013-08-06
-I do not have any form of internet connectivity besides the ethernet port on my motherboard.

-I was not aware that 13.10 was out. 
  -Would it be easier to re install the new version, upgrade to it while offline, or update the kernel offline?

-An Ubuntu Forums post [http://ubuntuforums.org/showthread.php?t=2008332&page=12](http://ubuntuforums.org/showthread.php?t=2008332&page=12) told me.

---

### Post by sanderj on 2013-08-06
> **HappyFishFace said:**
> -I do not have any form of internet connectivity besides the ethernet port on my motherboard.

-I was not aware that 13.10 was out. 
  -Would it be easier to re install the new version, upgrade to it while offline, or update the kernel offline?

-An Ubuntu Forums post [http://ubuntuforums.org/showthread.php?t=2008332&page=12](http://ubuntuforums.org/showthread.php?t=2008332&page=12) told me.

No Wifi? Can you plugin a Wifi-USB-stick?
13.10 is not out; it's a pre-release. I do not necessarily advice to install it, but to live-boot to see that your hardware works with that kernel. 
Offline installing software (with dependencies) is quite hard. Therefor I advice these alternatives

---

### Post by sanderj on 2013-08-06
PS: worth a try: [http://linuxg.net/how-to-install-kernel-3-10-on-ubuntu-linux-mint-debian-and-derivates/](http://linuxg.net/how-to-install-kernel-3-10-on-ubuntu-linux-mint-debian-and-derivates/)

Do three wget-commands on Windows, and install the files under Linux.

---

### Post by jeremyandroid on 2013-08-06
You can go here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) . Find the kernel you are looking for. Click on the link then download the headers,all and the image. When they are downloaded open a terminal cd into the downloads folder or where ever you put them. Then simply run      sudo dpkg -i* . deb    Then the install will begin. When its done run   sudo update grub. Then reboot and all should be updated. Also if you dont want to install them like that you can double click on each download and use the market to install them. But you still have to update grub. You can then run   uname -ar   to see your kernel version before and after install. After the download you can then work offline to do all of the rest. You will have to be online to use the market for the install but being you dont want to be online use the terminal and you will be fine. Hope I helped buddy.

---

