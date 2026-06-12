---
title: "Ubuntu does sometimes boot sometimes not"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by guybru$h on 2010-12-23
OK - so I am new to this whole Linux thing.
I installed Ubuntu 10.10 and it worked fine - i run it together with Windows XP on a HP pavilion Laptop.
Sometimes ubuntu does not boot though - I dont get any error messages. the screen is just black - when I reboot it usualy works after switching the laptop off.

When I try to run in the recovery mode (faile safe graphic mode) it sometimes works, sometimes not... when it does not boot the last message I see on the screen is: "no floppy controllers found"

I installed all recommended updates but it still happens.

I find it a bit disturbing that the system apppears to randomly decide when it want to boot and when not ???

any suggestions anyone --- please?

Dave

---

### Post by theasprint on 2010-12-23
Hi,

I suspect that the problem comes from your graphics card.

First can i know what graphics card you have?
Try booting Ubuntu from a LiveCD (that means Try Ubuntu without any Changes) and type the output of this command: 
```
lspci | grep VGA
```

About the "no floppy controllers found" thing, that may be also a hint. But you would need to wait for someone expert in this to tell you more.

One way to check that your PC is compatible with Ubuntu is to boot from LiveCD.
That's why I told you to execute the command above in LiveCD to ensure that your PC is compatible. Also while in LiveCD mode, check if you can use other features of your PC for compatibility check.

---

### Post by guybru$h on 2010-12-23
hey thank you.
I executed the command:

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)

I did not execute it from live cd though - live cd works - i have tried it before - at the moment I am in ubuntu and it works fine - just sometimes I need several attempts for it to boot properly

---

### Post by theasprint on 2010-12-23
Hi,

While booting your installed ubuntu 10.10, did you use any Nvidia drivers from Ubuntu?
That means did you use the drivers under System> Administration> Hardware Drivers?

I assume yes. Many people do that.
* If your Nvidia card is an Optimus one, means hybrid graphics, then do not follow my instructions.

I would like you to use the official Nvidia drivers and see if your problem is solved. 

1. Turn off/Disable the Nvidia drivers Ubuntu provided you.(Under System> Administration> Hardware Drivers)

2.Go to Nvidia.com and download the latest Nvidia driver for your card. Remember to get the Linux version.

3. Turn off your gdm(graphics mode)
```
sudo service gdm stop
```

4. Install your downloaded Nvidia driver
```
sudo bash <your Nvidia driver's directory>
```

5. Turn on your gdm
```
sudo service gdm start
```

Here are threads which users also solved their Nvidia problems:
[http://ubuntuforums.org/showthread.php?t=1648734]("http://ubuntuforums.org/showthread.php?t=1648734")
[http://ubuntuforums.org/showthread.php?t=1651377]("http://ubuntuforums.org/showthread.php?t=1651377")

* If you still face problems, go to the thread below at my signature and follow the instructions of TheRawGod and see if that helps.

* However if the problem is still not solved I may suspect that your install of Ubuntu is a bad install. (Like installed with a bad .iso file, just like bad egg=bad chicken)

Good Luck :D

---

