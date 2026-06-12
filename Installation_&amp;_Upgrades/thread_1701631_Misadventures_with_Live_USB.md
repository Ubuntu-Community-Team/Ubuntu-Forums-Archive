---
title: "Misadventures with Live USB"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by jcoonan on 2011-03-06
So I have a brand new computer, stats below, and I am trying to put Ubuntu on it. I have tried Live USB for 10.* and Natty both alternate and desktop and its been a nightmare. First the install would hang at Preparing to Install Ubuntu. Then I couldn't get the command-lin install past the disk partitioner. So, after reading many posts about the same thing I decided to switch usb sticks. Got a little better. During the install I needed to pull the usb stick out for it to get past certain points, this undoubtably is the root of my current problem which is just as strange and the other stuff. So it seems that the last install, the one with the new usb stick installing natty alternate from the command-line option resulted in a weird install where it will only boot to the sata if the USB is in and it seems that the File System is on the USB stick and has replaced the natty boot disk that was there before install. Whats going on?

CPU: AMD Phenom II X6 3.0GHz
RAM: Ripjaws 4GB 1333MHz
MOBO: M4A88T-V EVO USB3
HDD: Western Digital 500GB SATA
PSU: 650Watts

---

### Post by oldfred on 2011-03-06
The biggest issue lately is video cards. You did not specify what you have.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by Hedgehog1 on 2011-03-06
> **jcoonan said:**
> So I have a brand new computer, stats below, and I am trying to put Ubuntu on it. I have tried Live USB for 10.* and Natty both alternate and desktop and its been a nightmare...

jcoonan,

I think we need to see your partition layout (after all these install attempts):

Boot Ubuntu is whatever way you can, then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal),  please run this command:
```
mount
```
and then please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

