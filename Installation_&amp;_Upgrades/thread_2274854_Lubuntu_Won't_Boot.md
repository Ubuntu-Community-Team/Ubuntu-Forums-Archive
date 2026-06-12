---
title: "Lubuntu Won't Boot"
date: 2015-04-22
forum: Installation &amp; Upgrades
---

### Post by jonathan81 on 2015-04-22
I have a new HP Envy Laptop with Windows 8.1. It has EUFI, thought I have turned it off, as well as turning off Secure Boot.

I installed Lubuntu from a flash drive in 3 new partitions as recommended.

When I boot, it automatically boots to Windows.

I tried using EasyBCD to fix this, but when I try to boot to Lubuntu using that I receive an error message saying that

\NST\autoneogrub0.mbr is missing.

How can I boot to Lubuntu? It is installed, but I can't make my laptop boot to it.

---

### Post by mattharris4 on 2015-04-23
There is an issue with HP computers with UEFI and Win 8/8.1 where it was programmed to only boot Windows.  To fix this you have to change code to fool the computer into thinking it is booting Windows but actually boot GRUB or Linux.  Here is one discussion on this issue:  [http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714) .  Here is another although a Toshiba computer is being discussed:  [http://ubuntuforums.org/showthread.php?t=2274092&p=13268309#post13268309](http://ubuntuforums.org/showthread.php?t=2274092&p=13268309#post13268309) .  Here is one more:  [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) .

Good luck with this one.  With the problems coming up regarding HP UEFI equipped computers (essentially HP computers with Win 8 or 8.1 from the factory) I would highly recommend purchasing another brand of computer if you intend to install Linux on it.  Sony is also notorious for this although they no longer make computers.  Some newer Toshibas are also having this issue (although my year old Toshiba laptop took Lubuntu dual-boot with Win 8.1 without this issue).  Dell and Lenovo computers haven't had this issue as of yet (and I don't expect Dells to have it any time soon as they sell computers with Ubuntu pre-installed, why would they use one UEFI for Linux and another for Windows computers when one for both will work, the upside for us is Dell computers can take a Linux install easily).

---

### Post by jonathan81 on 2015-04-24
Hi Matt,

Thanks for the advice.

After speaking to a colleague, I tried burning the Lubuntu ISO to a DVD drive. To do that, I had to open the ISO using Explorer, rather than installing 3rd party software. I did not know that Windows could burn DVDs by default, but that the option had been turned off.

Next, I just over-wrote the current installation using the DVD. It booted without problems even when I turned legacy mode off.

Regards,

Jon.

---

### Post by Bucky Ball on 2015-04-24
Good news. Please mark thread as solved to help future travelers (see the second link in my signature). Good luck with Ubuntu. ;)

---

