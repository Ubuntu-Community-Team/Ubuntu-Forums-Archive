---
title: "Unable to boot from USB drive after strictly following all instructions"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by mjadams101 on 2013-12-12
Hi,

After reading and following all instructions I have attempted to run Ubuntu desktop edition 12.x from a 16GB USB drive. I downloaded the iso and the universal pen drive utility. I allocated the max 4GB storage on the drive with an apparent successful install. My system is both 32bit and 64bit compatible. When restarting the system, I used the F8 option to choose the USB drive as the start up device. The first few times I only got what appeared to be an icon of a hard drive and a person at the bottom of the screen. Eventually I was able to get to a progress bar which seemed to be loading. Just when I thought all was going to work, the screen turned into a massive black and white screen of non stop scrolling zeros and ones. Please note that I have also tried changing the USB drive to the start up drive in the bios with the same results. Any help and/or advice would be greatly appreciated.

Thank You,
Mark

Q? - If I were to install Ubuntu as a dual operating system on the same Hard hard drive with Windows 7, is there a risk of any existing malware on the windows 7 drive contaminating the Ubuntu installation?

---

### Post by sudodus on 2013-12-12
Welcome to the Ubuntu Forums :-)

Several things might be causing your problems. It will be easier to give good advice, if you specify your computer

- Brand name and model
- CPU
- RAM (size)
- Graphics and wifi chips/cards

1. Have you checked with ***md5sum***, that the download was good?

2. Have you tried another tool to make the USB install drive? Maybe you should start without persistence because it is easier. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)[URL="http://ubuntuforums.org/showthread.php?t=1958073"]
[/URL]
3. It might be the graphics card. Try with the boot option ***nomodeset*** and some other boot options too. See this link

 [URL="https://help.ubuntu.com/community/BootOptions"]https://help.ubuntu.com/community/BootOptions
[/URL]

---

### Post by C.S.Cameron on 2013-12-13
A lot of people report problems when using Universal, try UNetbootin or Startup Disk Creator.
Sudodus, (the previous poster), also makes a foolproof installer called OBI for doing Full installs.

I have not heard of Ubuntu catching malware from Windows or anywhere else.

---

