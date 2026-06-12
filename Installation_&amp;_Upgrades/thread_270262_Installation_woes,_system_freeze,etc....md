---
title: "Installation woes, system freeze,etc..."
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by normalspore on 2006-10-02
I have been trying to install Ubuntu 6.06 for an entire day! I've tried to install 6.06, but it hangs up no matter what the installer help says I try(noaipic nolapic, gdth=disable:y, then both together[that's all I could see that would apply to me, but I don't know much]).It says it's decompressing and a cursor blinks forever with no progress. I've tried a shipit 32bit, one shipit and one osdisc 64-bit, and even 32 and 64bit Kubuntu, and everyone of them freezes in the same place! I don't have a CD burner in my old pc so I can't get any different distributions without having to order them and wait some more. I have a brand new computer that's as useful as a rock! I'll appreciate so much any help. I don't like begging, but I'm at my wit's end...so, Please?
](*,) ](*,) ](*,) 

Here's my specs:

MSI K9N SLI Platinum NForce570
AMD X2 4200 AM2
2G DDR2 PC6400 RAM
2 250GB SATA II 7200RPM 8Mb
Creative Labs Audigy 4SE
Sony 16x DVD+-rw Q120A
Nvidia GeForce 7600GT 512Mb PCIe

---

### Post by _teo_ on 2006-10-03
> **normalspore said:**
> I've tried to install 6.06, but it hangs up no matter what the installer help says I try(noaipic nolapic, gdth=disable:y, then both together[that's all I could see that would apply to me, but I don't know much]).

I had a different kind of problems, but in general, you may try
```
noacpi
acpi=off

```
as well. My 2c.

---

### Post by normalspore on 2006-10-03
I think I'm suffering from a bug that many other people are having pain with, so I'll be patient and hope that Edgy will fix it...

---

### Post by wpshooter on 2006-10-03
Are you saying that you have another old machine (other than the one you describe) that is connected to internet but that does not have a CD burner ?

Also, are the Ubuntu versions you are trying to install the DESKTOP (sometimes referred to as the live CD) or the ALTERNATE CD version ?

---

### Post by crokett on 2006-10-03
I am having the same problem.  I tried the desktop CD and the alternate CD in text mode. After 8 failed installs, 2 memory tests, a HDD scan over the last 3 nights  My solution was to get the Debian net-install CD and will try that tonight.

---

### Post by normalspore on 2006-10-05
The only solution I can think of for now is to try other distros till I find one that works, then I'll just wait for Edgy and hope that it works.....

---

### Post by Denoon on 2006-10-05
I have the same problem that Teo has (decompressing and a cursor blinks forever with no progress)and have seen this noacpi acpi=off proposed solution when I tried Googling my problem.  However, being blond I dont have a clue where to insert this code.  I am trying to install it with windows still on my system.  I am using original 6.06 LTS sent to me by shipit and they work on my newer viao.  I have rudimentary dos knowledge from the happy days before windows was invented.  I can press F2 during boot up but don't know what to change if anything.  

Here are my specs:
Ubuntu live cd 6.06LTS for desktop PC (Original)
Intel Pentium III 700mhz processor (with parafin backup)
Old Sony Viao 128 MB ram 20 GB hard drive 
External CD non writable drive PCIA card

---

### Post by YumaJim on 2006-10-05
On one of my systems, I tryed to install from the live CD, Kubuntu 6.06, and the install hungup with a message 'Scan files'.
I had the system plugged into an router and I guess the installation program was trying to connect to the Internet
( I did not had an Internet connection! ) so, it just hung looking for the Internet. I unplugged the eithernet
cable and started the install again and this time the install completed. So if you don't have an Internet
connection remove the cable to the router.

Hope this may help someone.
YumaJim

---

### Post by _teo_ on 2006-10-06
> **Denoon said:**
> I have the same problem that Teo has (decompressing and a cursor blinks forever with no progress)and have seen this noacpi acpi=off proposed solution when I tried Googling my problem.  However, being blond I dont have a clue where to insert this code.

...

You can insert the Ubuntu CD in the drive and boot/reboot your computer. When it comes to the installation menu with options like instrall ubuntu, memory test, etc., you will select the very first item (selected by default) and press F6. Read instructions on screen. You can edit the boot options for kernel. And you should put there (in kernel boot options) desired additional flags, like acpi=off, etc.

Let me know whether you need further assistance.

---

