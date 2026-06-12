---
title: "Cannot install Ubuntu 10.10 32-bit desktop"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by _mOrgoth_ on 2011-01-14
Hi all!!
Well.. I am using Ubuntu for couple of years and this is the first time I see something like this.. I downloaded ISO image from Ubuntu download site and burned it to cd.. PC normally boots from CD, loads Isolinux and than come purple screen and thats it... After that display shuts down, I hear that PC load still something from CD so I leave him for 30min-s but nothing..
I downloaded ISO two times, I burned CD for two times.. I have tried boot from USB two times but same thing..
I am totally confused..

---

### Post by dino99 on 2011-01-14
always burn with the slowest speed

then boot by adding (F6) either: acpi=off, nomodeset, and remove quiet splash to see whats bad

---

### Post by yeats on 2011-01-14
Have you tried using the [alternate installer CD]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download")?

---

### Post by _mOrgoth_ on 2011-01-14
Thx for tips and advice.. SOLVED!!!!
I had to do the following:
During boot of CD, press F6 and than I get installation menu. Press F6 again and select NOMODESET. After that, installation is going normally. After Ubuntu is installed again same thing during boot..
So.. hold shift during boot. Press e to edit grub, add again nomodset after "quiet splash" and hit ctrl-x. PC boot to Ubuntu.
To make changes in grub permanent:
In console tipe: sudo gedit /etc/default/grub
edit line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
add nomodset to it:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset", save and exit..
Run command: sudo update-grub   and that is it!!
I know that bugs like this can be very irritating, specially for someone who is experiencing linux for the first time, so hope this tips might help.. Big thx again!!

---

### Post by _mOrgoth_ on 2011-01-14
Thx for tips and advice.. SOLVED!!!!
I had to do the following:
During boot of CD, press F6 and than I get installation menu. Press F6 again and select NOMODESET. After that, installation is going normally. After Ubuntu is installed again same thing during boot..
So.. hold shift during boot. Press e to edit grub, add again nomodset after "quiet splash" and hit ctrl-x. PC boot to Ubuntu.
To make changes in grub permanent:
In console tipe: sudo gedit /etc/default/grub
edit line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
add nomodset to it:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset", save and exit..
Run command: sudo update-grub   and that is it!!
I know that bugs like this can be very irritating, specially for someone who is experiencing linux for the first time, so hope this tips might help.. Big thx again!!

---

### Post by _mOrgoth_ on 2011-01-14
> **dino99 said:**
> always burn with the slowest speed

then boot by adding (F6) either: acpi=off, nomodeset, and remove quiet splash to see whats bad
Thx for tips and advice.. SOLVED!!!!
I had to do the following:
During boot of CD, press F6 and than I get installation menu. Press F6 again and select NOMODESET. After that, installation is going normally. After Ubuntu is installed again same thing during boot..
So.. hold shift during boot. Press e to edit grub, add again nomodset after "quiet splash" and hit ctrl-x. PC boot to Ubuntu.
To make changes in grub permanent:
In console tipe: sudo gedit /etc/default/grub
edit line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
add nomodset to it:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset", save and exit..
Run command: sudo update-grub   and that is it!!
I know that bugs like this can be very irritating, specially for someone who is experiencing linux for the first time, so hope this tips might help.. Big thx again!!

---

### Post by _mOrgoth_ on 2011-01-14
Sorry for triple post.. I my internet connection is breaking..

---

