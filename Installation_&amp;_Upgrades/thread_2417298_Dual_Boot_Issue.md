---
title: "Dual Boot Issue"
date: 2019-04-22
forum: Installation &amp; Upgrades
---

### Post by insertvicious on 2019-04-22
[FONT=arial]Hello, hope someone will help me with this issue I had from only 2 days ago (I'm also between beginner-amateur on this topic and I want Ubuntu for how easy you can edit things for example folder images). Well I wanted to try Ubuntu as a hobby on my laptop (**Acer Aspire F15 F5-537G, pre-installed Windows 10 x64**) beacuse I had Ubuntu on my old laptop and I loved that distro. 

Things that I did to install Ubuntu. *Resize the partition* on my 1TB disk, so I have space for the distribution.
After that *I made a bootable USB* with the version 18.04 from Ubuntu (amd64). Then I came to my *UEFI BIOS updated to the newest* 
(wich is the 1.27 [https://www.acer.com/ac/en/US/content/support-product/6739?b=1](https://www.acer.com/ac/en/US/content/support-product/6739?b=1)) *disabling secure boot*, giving priority to *boot first my USB* and installing it *on UEFI not in Legacy mode*. 

Then all worked just so fine, I did the installation, checked the partitions and all looks good, however after I did a reboot *I've never had the chance to get in again* but is installed, I saw the screen of grub for less a sec and never saw again on the first reboot having Ubuntu. 
Is there a way to fix this? Any kind of guide or what more to do? I give more information if needed, thanks![/FONT]:-k[FONT=arial]
[/FONT]

---

### Post by insertvicious on 2019-04-22
I did some more research, i was giving up, and magically found [this article]("https://itsfoss.com/no-grub-windows-linux/").

Basically, with only a line code inside Windows my grub is now showing when rebooting :o

You have to first go to the *windows icon*, search *cmd and execute as administrator with a right click*, otherwise you get **access denied, **after that you just have to type the following line and press enter:

[FONT=trebuchet ms][SIZE=3]bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

[/SIZE][/FONT]After that you just have to reboot and by me it worked, [COLOR=#ff0000]if it doesn't[/COLOR] the article explains more so I suggest taking a look before doing this :-)

---

