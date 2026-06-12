---
title: "Dual boot with Windows 7"
date: 2013-09-03
forum: Installation &amp; Upgrades
---

### Post by mike73 on 2013-09-03
Ok so I decided to give Ubuntu a try today after reading more into it since I had some free time on my hands. I ran into a problem and was wondering if someone wouldn't mind helping me out. So I downloaded Ubuntu 13.04 extracted all the files then copied and pasted them into my flash drive. When I restarted I changed my BIOS to load the USB first then I proceeded to install it along side my Windows 7. It said it was successfully installed and then when it restarted I didn't get an option to choose which OS to load it just loaded up Windows 7. Could someone tell me why it didn't let me choose which OS I wanted to load?

Also after I installed it and couldn't get Ubuntu to load off my HD I decided to just load it off my USB since I was pretty eager to try it out. When it loaded it said I wasn't connected to the internet. When I clicked on network settings it said that I had a wired connection. I was kinda confused cause I don't have my Ethernet cord plugged in. When I was under network settings how come it's not showing any wireless connections? How can I get it to log under my wireless network?

Thanks in advance,
Mike

---

### Post by oldfred on 2013-09-04
Best to see details on boot issues. May be better to start separate thread on wireless issues or search forum based on your Wireless chip as there have been many threads. My old laptop just works so I am not familiar with all the issues, but there are some with certain chips.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

