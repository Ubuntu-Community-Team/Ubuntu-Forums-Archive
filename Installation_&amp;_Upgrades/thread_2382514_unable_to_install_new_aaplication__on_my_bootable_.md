---
title: "unable to install new aaplication  on my bootable usb"
date: 2018-01-14
forum: Installation &amp; Upgrades
---

### Post by aayan18 on 2018-01-14
dear sir,
           i am not being able to install new software in my ubuntu 16.04 i have access the help section in 
                   ubuntu menu but the method given there coudldn't understand well.plz help!!

---

### Post by ian-weisser on 2018-01-14
Help with what?
What are you trying to do?
What is going wrong?

---

### Post by DuckHook on 2018-01-14
Welcome to the forums, aayan18.

A bootable USB (or LiveUSB) is not writable by default. Think of them as just a DVD, but on a USB stick. In order to make it writable, you have two options:

[LIST=1]
[*]Make it *persistent* , which is a variation of a LiveUSB with an extra partition for holding apps and data, or
[*]Use the LiveUSB to install a full operating system onto a second USB. This method treats the second USB as if it is a hard disk.
[/LIST]
Instructions for using *mkusb* to create a *persistent* LiveUSB are here: [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

