---
title: "How do I install Ubuntu without a CD/DVD or USB drive?"
date: 2019-03-21
forum: Installation &amp; Upgrades
---

### Post by YMS_1975 on 2019-03-21
I have an ACER Aspire 5 A515-51-88NY. This model does not have a CD/DVD drive, and unfortunately for me, I don't have a USB drive large enough to store an OS. I did some Googling and came across this post : [https://askubuntu.com/questions/484434/install-ubuntu-without-cd-and-usb-how](https://askubuntu.com/questions/484434/install-ubuntu-without-cd-and-usb-how)

I followed the directions as best as I could, but I must've done something wrong because now when it boots up I get two options : 1) Windows 10 & 2) Unetbootin. If I select Unetbootin it gives me an error message, saying it can't find the files. If I select Windows 10, that will boot up just fine.

Can anybody help? I really want to install Ubuntu alongside my Windows 10, however I don't have the necessary drives which I always had in the past, to install this OS.

---

### Post by TheFu on 2019-03-21
To install any Ubuntu Desktop without expert-level skills, you'll need about 15G (or more) of available storage and 1-5 partitions available. If the machine came with Win10, you can shrink the existing partitions to make room on the internal HDD.

If you are an expert, you can manually install it, but doing that is ugly. I've never attempted it.  3 minutes of searching for a how-to failed me. Sorry.

But if your machine has an i5/i7 CPU and 8G of RAM, why not just install it into a virtual machine?  As long as you aren't doing high-end graphics stuff, this is the easiest, least risky, method.  VirtualBox is very popular, so that would be the hypervisor to use to get the most help from people here.  For $120-ish, you can VMware Workstation which is a little better with some nice aspects to be about 5% easier to use than virtualbox.  Both are slower than native KVM/QEMU running on Linux, which is the fastest, most flexible, hypervisor available today, but most people are quite happy with virtualbox.

---

### Post by rsteinmetz70112 on 2019-03-21
It is possible to install over a network if you have Internet access will need a disk drive with an empty partition. 
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
I've never done this so good luck.

It might be easier to get a USB stick and install the DVD ISO on it. A 8 - 10 GB USB stick is cheap, you should be able to get a big enough one for under $10. I have had some given to me by various vendors.

---

### Post by yancek on 2019-03-21
The link you posted explains how to do a "frugal" install of Ubuntu using the Unetbootin sfotware.  Basically what this does is put the Ubuntu on your computer as a 'Live' usb which you should be able to select on reboot and see the same screen you would see if you were booting from a usb or DVD.  Since that didn't happen, something obviously went wrong.  Since you are using windows 10 and it is most likely UEFI, did you use the method toward the bottom of the page which requires you to first install rEFind?  Haven't used that method so don't know how well it works?

---

### Post by aromo2 on 2019-03-21
I think TheFu is spot on. The easiest way to not screw up your Windows installation is installing VirtualBox and then create a Ubuntu virtual machine within it.

Second to that, and way more advanced is rsteinmetz's idea to get a USB drive and install it alongside Windows.

---

### Post by C.S.Cameron on 2019-03-21
The method by **xtrchessreal** on the page you mention worked for me.
I don't recall trying it with 18.04 though and UNetbootin can be a little funny with 18.04.
If 18.04 does not work try 16.04 and then upgrade.

---

