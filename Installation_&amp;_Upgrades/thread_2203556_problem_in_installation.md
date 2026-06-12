---
title: "problem in installation"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by Jayam on 2014-02-04
I have Ubuntu 12.04 L.T.S one when i started my computer it showed the pink screen at startup and nothing else. so i uninstalled it and tried to intallit again it shows following error message: an error occurred :
                                               Error Executing command
                                               >>command=C:\Users\Asim\AppData\Local\Temp\pyIDF67.tmp\bin\r
                                               esize2fs.exe-f C:\ubuntu\disks\root.disk17744M
                                               >>retval=1
                                               >>stderr=
                                               >>stdout=resize2fs 1.40.6(09-Feb-2008)
                                               open:No such file or directory while opening C:\ubuntu\disks\root.disk


                                               For more information please see the log file:
                                               C:\users\asim\appdata\local\temp\wubi-12.0.1-rev273.log

---

### Post by sudodus on 2014-02-04
Welcome to the Ubuntu Forums :-)

I see 'wubi' in your last line. This is a method to test Ubuntu with an installation 'inside' Windows. The method was nice but not as stable as a regular installation alongside Windows, 'dual boot', but due to the new systems to lock the computer to Windows, UEFI, wubi does not work with new computers, and it is abandoned in new versions of Ubuntu.

1. I suggest that you try Ubuntu in another way: Boot from the Ubuntu CD/DVD/USB drive. Do not install it while Windows is running.

2. Please tell us about your computer and version of Windows. It makes it easier to give good advice.

- Brand name and model of the computer (or motherboard if you built the computer yourself).
- CPU
- RAM (size)
- graphics chip/card

- Version of Windows

---

### Post by Jayam on 2014-02-05
I am running Windows 7 Ultimate
My Cpu is of Odessey 
and graphic card of NVIDIA
You told me to boot from a u.s.b just how to do that
AND why did ubuntu run well before I unintalled it

---

### Post by sudodus on 2014-02-05
I meant that you boot from either CD, DVD or USB. You can make a USB boot drive according to this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You may have problems with the graphics. In that case, try the boot option ***nomodeset*** according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I don't know what made the difference compared to the previous time.

---

