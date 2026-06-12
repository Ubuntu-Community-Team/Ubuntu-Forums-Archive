---
title: "Unable to boot or format after swapping HDD"
date: 2018-08-19
forum: Installation &amp; Upgrades
---

### Post by ak4zh on 2018-08-19
Device: Lenovo G580

I am new to ubuntu and installed Ubuntu on my daily drive laptop 2 months ago, since then I had lost access to BIOS settings, as soon as I turn it on it boots to ubuntu and pressing all recommended keys only take me to grub2

Now today I messed up it more. I had another laptop laying around which had low config but 1 TB HDD, I decided to swap my 500 Gb Lenovo HDD with 1 TB

I simply swapped the HDD and formatted both HDD thinking I will be able to boot with the Bootable pendrive.

But now my Lenovo does not boots only shows a blackscreen.

The other HP laptop is working fine so I formatted 500 GB HDD with Windows 10 and 1 tb with Ubuntu, but Lenovo laptop still doesn’t work even if I put the newly formatted 1 TB hdd while that boots correctly on the HP laptop.

What can I do to recover my Laptop to install any OS.

---

### Post by oldfred on 2018-08-19
Were both installs UEFI  as your Lenovo is a newer UEFI system?

UEFI has fast boot which is different than Windows fast start up/hibernation.
Fast boot assumes no system change, so UEFI/BIOS does no checking of what hardware you have and just immediately jumps to default boot in UEFI boot menu.
Normally cold boot, not warm reboot will have UEFI check hardware and that gives time to get into UEFI. May have to remove laptop battery and drain power to force the  full cold boot with laptops.

You have to get into UEFI's boot menu and select USB flash drive or UEFI:flash drive type entry to boot flash drive.

You should also update UEFI from Lenovo. 

Often issues similar by brand. Bigger differences if Intel or AMD.
       Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212](http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

---

### Post by ak4zh on 2018-08-19
Yes bot installs are UEFI

I swapped HDD multiple times as to test and install Ubuntu fromthe other laptop so yes I did also removed battery everytime. But nothing seems to work. I just get a black screen.

My laptop shows this info:

F2 to Enter setup, F12 to enter Multiboot menu...

Both option takes me to same black screen of death, pressing nothing takes me to same black screen.

When I press ESC it shows me some info about BIOS

System BIOS shadowed
Video BIOS shadowed
BIOS Version: 62CN40WW

And some other info.

---

### Post by oldfred on 2018-08-19
There was one post where a user had to use an F-key to turn brightness up to see screen.

But issues getting into UEFI/BIOS f2  or boot menu f12 are not Ubuntu related but related to your hardware. You should always be able to get into those. But fast boot can prevent that, and then if no bootable system found due to UEFI settings, even if there is a valid boot if settings in UEFI were different.

---

### Post by ak4zh on 2018-08-20
Function keys are working I am able to increase / decrease brightness, turn on / off display etc.

But nothing else...

---

### Post by westie457 on 2018-08-20
Have you tried to start your system using the 'Novo' button?
If that does not show a menu to enable you to get to system setup pages or to boot from a different HDD then the problem is very serious.

---

### Post by ak4zh on 2018-08-20
That also does a normal power on just like power button.

---

