---
title: "Using Boot Repair to find SSD with Kubuntu install amoung other HDs/OSs"
date: 2017-03-19
forum: Installation &amp; Upgrades
---

### Post by horseatingweeds2 on 2017-03-19
I have an SSD with Kubuntu installed on it in a computer with two other HDs, each with their own operating systems installed, like so: 

SSD  Kubuntu
HD1  Windows XP, Kubuntu
HD2  Windows 7

The system automatically boots into Windows 7. The ASUS BIOS menu let's we either auto boot into this drive or the DVD drive. I can also select the other drives to boot from. When I choose the SSD, I get a regular Grub menu, listing Windows XP, 7, and Ubuntu. When I choose Ubuntu though, the Kubuntu install on HD1 boots, not the install on the SSD. Also, Windows XP doesn't boot at all -- it tries but crashed. I don't so much care about this. I'd just like to figure our how to boot the SSD Kubuntu. 

I ran Boot Repair, and it said to send an email to boot.repair at G Mail. Here is a paste bin of the output: [http://paste2.org/GK9wV4N5](http://paste2.org/GK9wV4N5)

The output says this for the SSD/Kubuntu partition: "Syslinux looks at sector 32792 of /dev/sdd1 for its second stage. The integrity check of Syslinux failed.  	                       No errors found in the Boot Parameter Block." Is this the issue? 

Any advice would be appreciated.

---

### Post by horseatingweeds2 on 2017-03-21
Is grub able to recognize multiple Ubuntu installations?

---

### Post by oldfred on 2017-03-21
Ignore error message as that is on your flash drive sdd.

You show a new UEFI system, but all drives are configured for the 35 year old BIOS/MBR.

And your SSD is using LVM, is that also encrypted?

You need to boot the Ubuntu live installer in BIOS mode. And then make sure your LVM is mounted & if encrypted, make sure you have unencrypted it. Then Boot-Repair should work. Boot-Repair often has issues knowing if you have FakeRaid or LVM as both use /mapper and grub repairs then are not the same.

---

