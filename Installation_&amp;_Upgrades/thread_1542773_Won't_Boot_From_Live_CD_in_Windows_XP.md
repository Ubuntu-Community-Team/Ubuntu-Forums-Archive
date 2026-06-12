---
title: "Won't Boot From Live CD in Windows XP"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by Meganehmbee on 2010-07-31
I'm trying to boot with my Lucid live CD on my Windows XP Pro so I can dual boot my system. I get to a black screen with a little rectangle at the bottom next to a a little guy in a circle and then suddenly my monitor goes to sleep and nothing I do can wake it back up.

I know the CD works because I used it to dual boot my Windows Vista computer.

Any ideas on how to make the boot work so I can install Ubuntu?

---

### Post by ronnielsen1 on 2010-07-31
I'm not sure if this will work from a lucid cd or not but try pressing F6 and using one of the options below

> **What parameters to use?**

 Unfortunately,  there is no sure fire approach when you have never done this before or  are new to Linux in general. There are some very commonly used  parameters, however, that can be tried, and will likely work. 
Some  boot problems can be fixed by simply removing the quiet splash-- at the  end of the boot options line. If that fails, you may try some of the  commonly used options listed below: 

[LIST]
[*]**noapic nolapic** 
[*]**acpi=off** 
[*]**irqpoll** 
[*]**lapic pci=routeirq** 
[/LIST]
One  of the above combinations will very likely work on a machine that will  not boot the live cd to a desktop for installation purposes. 
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

