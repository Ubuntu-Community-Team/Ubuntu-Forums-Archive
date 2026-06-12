---
title: "Can only install Ubuntu 8.10"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by malel on 2013-02-09
I have an Acer Travelmate 240 Laptop 2.6Ghz, 1Ghz Ram 40Gb HDD. Originally it had Win XP on it but I have put Linux on it many times. What has happened is that out of OS"S I have I am only able to load Ubuntu 8.10 32 bit.
I would like to upgrade but find I cannot as none of my disks will start up . I tried to put back windows today but it seems like there is a fault on the 2nd disk. I thought if I could load one OS on I would be able to load one of the others but maybe the disks have a problem . Any help would be appreciated.

---

### Post by MAFoElffen on 2013-02-10
First thing that comes to mind is if you can verify if your Acer's BIOS version is v1.15 or is it older?

If older than v1.15, go to Acer support and download it:
[http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=765](http://support.acer.com/us/en/product/default.aspx?tab=1&modelId=765)

Then try it... But you would need Windows running to use their flash utility. (Or a windows bootable disk)

---

### Post by snowpine on 2013-02-10
Ubuntu 8.10 is "end of life" and it sounds like your computer may be on its last legs. Here is a list of Ubuntu-certified replacement hardware: [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

---

### Post by oldfred on 2013-02-10
Several possible issues.

Lens on CD needs cleaning:
       How to clean CD lens:
[http://members.iinet.net.au/~herman546/p27.html](http://members.iinet.net.au/~herman546/p27.html)

    
CD's not burned or downloaded correctly.
       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

    Verify download:
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
    
System is so old it does not support PAE or Pentium M?
       [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)

    
So you may need Lubuntu or Xubuntu.
       [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

---

### Post by malel on 2013-02-10
Thank you Oldfred . I am trying all things . I have downloaded Ubuntu 12.04 but am unable to burn it to disk. I also downloaded Lubuntu 12.04 and tried to put it on a  USB stick although it said it had done it I cannot startup off it and it will not open for me . This 8.4 is very shaky but it is the only OS I have at this time .

---

### Post by oldfred on 2013-02-10
If computer is that old, even though you have a USB port, it may not have a BIOS that support USB booting. Only in about the last 6 years have BIOS been updated to boot from flash.

If Lubuntu CD does not work this may, I think you still partially boot with CD.
       Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

