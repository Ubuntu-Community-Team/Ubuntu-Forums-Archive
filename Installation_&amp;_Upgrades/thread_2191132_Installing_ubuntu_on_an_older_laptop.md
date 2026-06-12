---
title: "Installing ubuntu on an older laptop"
date: 2013-12-01
forum: Installation &amp; Upgrades
---

### Post by andjelavuchkovich on 2013-12-01
Hello everyone :)
I've been using Linux, mostly ubuntu based, for couple of years now on my computer. I would now like to install it on an older laptop, but I'm not quite sure which one would be good for it, since I don't have experience with linux on laptops. Please give me some advice, because after one day with windows again, I'm going crazy :)
Laptop is Sony Vaio, model PCG-GRT815E, and it runs on:
Intel (R)
Pentium 4 CPU 2,80 GhZ
512 mb of RAM
Graphic card Nvidia GEForce FX Go5600
It's currently on Windows XP. 
Thanks in advance :)

---

### Post by fantab on 2013-12-01
Try Lubuntu. With only 512Mb RAM, [**Lubuntu**]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") is your best bet. If you have problem installing with the regular Lubuntu DVD/USB, then try [Lubuntu/Alternate_ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") or [Lubuntu/Minimal Install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")

If a RAM upgrade is possible then you can add some more memory to the machine.

---

### Post by ibjsb4 on 2013-12-01
With that amount of ram, I would try Lubuntu.

[http://www.lubuntu.net/](http://www.lubuntu.net/)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Sony+Vaio&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Sony+Vaio&sa=Search&cof=FORID:9)

---

### Post by Topsiho on 2013-12-01
Might be you are thinking of extending Ram (to at least 1 GB), and installing Ubuntu with Unity.
However, the latest Unity is very heavy on older graphics cards, and probably won't work with the Geforce FX 5600.
It doesn't work well with my FX 5500 AGP-card, in one of my desktops.

But installing more Ram and trying Xubuntu or Lubuntu, might be the solution.
On my 8 years old Toshiba laptop, 1GB Ram, I run Xubuntu very succesfully, extending it's usability for probably a few more years :)

Topsiho

---

### Post by sudodus on 2013-12-02
Have a look at the beginning and end of the following thread

[URL="http://ubuntuforums.org/showthread.php?t=2130640"]Old hardware brought back to life
[/URL]
If you have problems with graphics, use the [boot option]("https://help.ubuntu.com/community/BootOptions") nomodeset and install a proprietary driver for the nvidia chip/card.

---

### Post by andjelavuchkovich on 2013-12-14
Thanks for your answers :) I made Live CDs of Lubuntu & LXLE, but now I have another problem to solve-my laptop won't boot from CD, and there's no option for USB boot. I'm not giving up on trying to install Linux, so I'll post here my experience when I get it to boot from CD :) (PS. I set it up in BIOS, but it doesn't work, if anyone wanted to suggest that :) )

---

### Post by mörgæs on 2013-12-14
Does the CD you created work in another computer?

---

### Post by andjelavuchkovich on 2013-12-14
Yes, I have PC that runs on Elementary OS, and it works :)

---

### Post by andjelavuchkovich on 2013-12-14
UPDATE:
After a lot of trouble, I figured out the problem with booting from optical drive. Even though it's a pioneeer dvd reader&writer, computer would only register regular CDs for booting from optical drive. SO, LXLE was unfortunately out of the game. I booted from a CD with Lubuntu 12.10 on it, and, after choosing Try live, I couldnt get pass the blank black screen after I choose it. Than I chose again, nomodoset checked this time, and I could run it, but it froze, and I couldn't install it.
When trying to go right to the install, it either freezes on a black screen or a screen with Lubuntu and load dots. When hitting ESC, i get something like line 7 can't open dev/sdb no medium found.
I tried numerous time, but I just can't get it to start with the install.
Any ideas on how to fix this? :)

---

### Post by mörgæs on 2013-12-14
Yes, in post #2 you were given a couple of good ideas.

Do you have anything in the USB ports when installing?

Have you disabled everything USB-related in BIOS?

---

### Post by sudodus on 2013-12-15
> **mörgæs said:**
> Yes, in post #2 you were given a couple of good ideas.

Do you have anything in the USB ports when installing?

Have you disabled everything USB-related in BIOS?

+1

The ***alternate*** or ***mini iso*** contain installers, that work will low RAM. Another alternative for low RAM is the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"). It can boot from ***Plop*** on CD or floppy which transfers the boot to a USB device, even where you cannot boot directly from a USB drive.

---

