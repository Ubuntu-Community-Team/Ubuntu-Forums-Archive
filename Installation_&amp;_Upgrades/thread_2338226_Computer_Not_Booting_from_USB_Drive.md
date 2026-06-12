---
title: "Computer Not Booting from USB Drive"
date: 2016-09-26
forum: Installation &amp; Upgrades
---

### Post by ddet1207 on 2016-09-26
Hello All!

I am very new to Ubuntu, and just got a used PC for gaming. After installing Steam on the computer, I attempted to install Skyrim. The game failed to download, and after a little bit of searching I found that Steam games can only be installed on Ubuntu 12.04 and I was running 16.04. My first thought was to try to install the older version using a bootable USB and go from there. Unfortunately, I seem to have installed a very bare-bones OS, and was not able to get anything more than a command line screen. I tried using commands that I found online to try to install and load a GUI:

```
startx
sudo apt-get install ubuntu-desktop
sudo service lightdm start
```

There are probably others, but I can't remember them all. Either way, it looks like there is no GUI installed on my PC. I am trying to decide where I want to go from here, and it seems like my options are to try to install a GUI on my computer via command line, or try to reinstall 16.04 and run a Windows version of Steam using Wine. _My first question is which of the two you guys think would be the better option._

I tried to reinstall 16.04 on my computer using a bootable USB drive that I had made using UNetbootin and the amd64 iso file from the Ubuntu website (because it did seem like the easier option of the two), but when I booted the PC with the drive in, it didn't even seem to respond to the contents on the drive. I've already configured the boot priority in BIOS, and my drive is number one priority. I'm really at a loss for what to do here. I'm not able to use a disc with 16.04 on it, as my PC doesn't have an optical drive, and I don't have the money for an external drive. For some reason the flash drive worked just fine for the first installation, but I'm not having any luck now.

My apologies for the long post, but I'm really not sure what to do here. I don't know what I'm doing incorrectly, and my lack of computer knowledge means that I don't know what to look for on Google to find it out. Thank you in advance for helping, and if there's any information about my computer that I can provide, please let me know.

---

### Post by C.S.Cameron on 2016-09-26
12.04.5 is supported til April 2017.
You can download the Full 64 bit iso here:
[http://releases.ubuntu.com/12.04/ubuntu-12.04.5-alternate-amd64.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04.5-alternate-amd64.iso)
Unetbootin should be ok for making the install disk.
If the bootable USB only has one partition you can format to FAT32 using Windows.

I would think Steam might work for some games installed to USB3 flash drive if there is lots of RAM.

---

### Post by ddet1207 on 2016-09-27
Those things are good to know, but you didn't really answer my questions. At least not that I can tell. I made a bootable USB out of that ISO file, tried booting my PC from it, and got the same result. My computer can tell there's a flash drive in the USB slot, but it won't boot from the drive. I'm doing the exact same procedure I used to get 12.04 on my computer in the first place, and still I get nothing. My computer also isn't extremely powerful, so I'm still wondering whether it would be more efficient to run Steam on 12.04 or Steam through Wine on 16.04.

---

