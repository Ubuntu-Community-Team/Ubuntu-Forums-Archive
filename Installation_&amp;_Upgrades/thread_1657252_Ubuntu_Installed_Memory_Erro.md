---
title: "Ubuntu Installed Memory Erro"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by edisonl on 2011-01-01
Hi everyone,

I had download the relevant files (Ubuntu Netbook, USB creator) to my external Hardisk. So I tried to proceed to intallation by clicking **wubi** icon was prompted with Demo and Full Installation or Learn more> Click **Demo & Full Installation**> **Help me to Boot From CD** radio button

It will run, but after a while it prompt me with insufficient memory to the c:\Document and Settings\User\Temp which is why I dont understand why it chooses C:\ drive instead of my external hardisk. I checked my C:\ drive and it still does have the balance of 30++ GB

What I basically like to achieve is to make the external hardisk to run Ubuntu on the laptop start (Which I understand that I need to boot into Nios and reconfigure the system startup from CD/ Hardisk etc)thats all. I even prepared a cd of 700mb. My external hardisk does have addition of more than 450GB too.

I am not sure why is this happen, Can someone enlighten me please?

Regards, Edison

---

### Post by Idefix82 on 2011-01-01
You don't want to do a Wubi install. Rather, follow the steps on the download website to create a bootable usb stick or a LiveCD, then make sure that in the boot order in the BIOS, USB/CD ROM is at the top, boot from the USB stick/the CD and proceed to install from there.

The Wubi icon tries to install Ubuntu within windows, rather than on its own partition.

---

### Post by edisonl on 2011-01-15
> **Idefix82 said:**
> You don't want to do a Wubi install. Rather, follow the steps on the download website to create a bootable usb stick or a LiveCD, then make sure that in the boot order in the BIOS, USB/CD ROM is at the top, boot from the USB stick/the CD and proceed to install from there.
 
The Wubi icon tries to install Ubuntu within windows, rather than on its own partition.
 
Thanks a lot for the reply. Will try it out definately :)
 
Regards, Edison

---

