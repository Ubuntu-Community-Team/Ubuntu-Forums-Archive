---
title: "package manager"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by bondmatt on 2011-01-21
Edit: I used a usb to ethernet port converter to bypass this issue.

I have a laptop on which I have installed Xubuntu with a live cd. I am now trying to get ndiswrapper to work but apparently I need to compile it. Apparently I need build-essential to compile ndiswrapper. However, when I try to install build-essential from the cd it fails to find the other required packages. Now I have no internet connection on this laptop (it has no ethernet port) so I have been transferring packages one or two at a time on a usb stick... I have noticed after some time that either with sudo apt-get or the synaptic package manager if there is more than one dependency it will always fail to find the 2nd. Am I going crazy? I am about to abandon Ubuntu to see if I have more luck elsewhere...
 
Any advice would be appreciated,
- Matt Bondy

---

### Post by Bucky Ball on 2011-01-21
Why are you using ndiswrapper??? Really to be avoided as most cards work now without it. Do you know what card you have?

If you haven't, plug in an ethernet cable and get your updates; System>Admin>Update Manager. The card may well be picked up in the process. After updates System>Admin>Additional Drivers.

To find your card open a terminal - Applications>Accessories>Terminal - and paste this in:

```
lshw -C network

```

---

### Post by bondmatt on 2011-01-21
The laptop does not have an ethernet port. It is ancient (IBM Thinkpad 390X) and had a whole 64MB of RAM before I found someone through local classifieds with old computer parts (now it has 256 and runs XUbuntu fairly well).

I have purchased a Netgear wg511 pcmia wireless card. When I put it in and repeatedly rebooted and ran commands like the one you posted (as per Ubuntu documentation) there was no sign the card was working. However, at this point (with my very limited Linux knowledge - commands like cd and ls) I cannot separate in my mind the pre and post ndiswrapper attempts to get the card working.

Thank you for trying to help, it is appreciated.
- Matt

---

