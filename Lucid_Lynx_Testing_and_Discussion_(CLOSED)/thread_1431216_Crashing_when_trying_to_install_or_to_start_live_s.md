---
title: "Crashing when trying to install or to start live session"
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by leorolla on 2010-03-16
Hi all,

I have a LiveUSB for Lucid Alpha 3 Desktop i386

It boots fine, I see the language dialogue, I see next screen.

But when I choose Try without installing or Install ubuntu the system freezes after a few seconds and the screen goes black.

How do I keep the text messages so that I know where it crashed?

What packages should I file this bug against?

---

### Post by VMC on 2010-03-16
> **leorolla said:**
> Hi all,

I have a LiveUSB for Lucid Alpha 3 Desktop i386

It boots fine, I see the language dialogue, I see next screen.

But when I choose Try without installing or Install ubuntu the system freezes after a few seconds and the screen goes black.

How do I keep the text messages so that I know where it crashed?

What packages should I file this bug against?

At the bottom you will see Options. Push F6 then remove "quiet" from the boot string. Note you can even add "--verbose" to add more to the boot messages. "/var/log/syslog" then should contain some information.

---

### Post by leorolla on 2010-03-16
> **VMC said:**
> At the bottom you will see Options. Push F6 then remove "quiet" from the boot string. Note you can even add "--verbose" to add more to the boot messages. "/var/log/syslog" then should contain some information.

Thanks.

It showed me a buch of stuff, got black and froze again.

I can see it got black when it started the graphical mode.

Then it shows a bunch of quick error messages (too fast to read) and that's it.

How do I access the /var/log/syslog ?

Note: Karmic LiveUSB works perfectly.

---

### Post by leorolla on 2010-03-16
I also removed slpash and chose noacpi

It seems fine for a moment, then starts giving an error to handle USB devices, complained about a live file system not accepting address 10, error -110, unable to enumerate USB device on port 5.... etc...

Finally it shows ```
(initramfs)
``` It is locked here. When I press enter it just repeats the same line.

---

### Post by VMC on 2010-03-16
> **leorolla said:**
> I also removed slpash and chose noacpi

It seems fine for a moment, then starts giving an error to handle USB devices, complained about a live file system not accepting address 10, error -110, unable to enumerate USB device on port 5.... etc...

Finally it shows ```
(initramfs)
``` It is locked here. When I press enter it just repeats the same line.

Those handle errors are because your using a LiveUSB flash drive. Its a problem area. Sometimes a cold boot will stop them. Also F6 and change to "cdrom-detect/try-usb=true" will help.

What video card do you have. that's very important.

---

### Post by leorolla on 2010-03-16
> **VMC said:**
> Those handle errors are because your using a LiveUSB flash drive. Its a problem area. Sometimes a cold boot will stop them. Also F6 and change to "cdrom-detect/try-usb=true" will help.

What video card do you have. that's very important.

I will try that.

My video:
```
$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:0364] (rev 80)
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:1364]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:2364]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:3364]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:4364]
00:00.5 PIC [0800]: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller [1106:5364]
00:00.6 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device [1106:6364]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge [1106:7364]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:02.0 PCI bridge [0604]: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller [1106:a364]
00:03.0 PCI bridge [0604]: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller [1106:c364] (rev 80)
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VT8237A SATA 2-Port Controller [1106:0591] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 07)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237A PCI to ISA Bridge [1106:3337]
00:11.7 Host bridge [0600]: VIA Technologies, Inc. VT8251 Ultra VLINK Controller [1106:287e]
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
00:13.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237A Host Bridge [1106:337b]
00:13.1 PCI bridge [0604]: VIA Technologies, Inc. VT8237A PCI to PCI Bridge [1106:337a]
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] [1106:3371] (rev 01)
06:01.0 Audio device [0403]: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) [1106:3288] (rev 10)
$ 

```

Edit: it was already running "cdrom-detect/try-usb=true" by default.

---

### Post by ikt on 2010-03-16
> **VMC said:**
> Those handle errors are because your using a LiveUSB flash drive. Its a problem area. Sometimes a cold boot will stop them. Also F6 and change to "cdrom-detect/try-usb=true" will help.

What video card do you have. that's very important.

I have the same issue, have a nvidia 8800gts

---

### Post by leorolla on 2010-03-16
> **ikt said:**
> I have the same issue, have a nvidia 8800gts

Maybe you can help providing information here:
[https://bugs.launchpad.net/ubuntu/+bug/539020](https://bugs.launchpad.net/ubuntu/+bug/539020)
And also marking that this bug affects you too.

---

### Post by ikt on 2010-03-19
> **leorolla said:**
> Maybe you can help providing information here:
[https://bugs.launchpad.net/ubuntu/+bug/539020](https://bugs.launchpad.net/ubuntu/+bug/539020)
And also marking that this bug affects you too.

heya,

I don't have the download capacity at the moment but will check with the beta.

---

### Post by cariboo on 2010-03-19
You may want to try the nomodeset option, by pressing F6, I have two different systems with Nvidia graphics chipsets, that need that option to boot the Live CD, USB shouldn't be any different.

---

### Post by leorolla on 2010-03-20
> **cariboo907 said:**
> You may want to try the nomodeset option, by pressing F6, I have two different systems with Nvidia graphics chipsets, that need that option to boot the Live CD, USB shouldn't be any different.

How do you know it is nvidia from the lspci?

---

### Post by leorolla on 2010-03-22
Nomodeset didn't help.
I'm trying Beta1 now.

Any other idea?

---

