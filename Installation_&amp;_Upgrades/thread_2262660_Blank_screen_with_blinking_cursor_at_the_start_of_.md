---
title: "Blank screen with blinking cursor at the start of a new installation"
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by Xylon- on 2015-01-26
First of all apologies for yet another topic about this issue. I've read through a bunch of other threads however I still haven't got it to work.

I'm trying to install Ubuntu 14.04.1 64-bit on a somewhat old laptop (first time for me).

Each time I start from the USB and either select the live option or the install option I end up with a white screen with a blinking cursor.

Ubuntu was downloaded [here]("http://www.ubuntu.com/download/desktop/") and [these]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") steps were taken to create the usb. 

The laptop has:
Intel Mobile Core 2 Duo T6500
ATI Mobile Radeon HD 4500
4gb memory
300gb hard disk

The hard disk has two partitions of about the same size. One of the partitions runs Windows 7 and the other one should run Ubuntu.

This seems to be a somewhat common problem for older laptops. From what I've been reading it seems to be an issue with older graphic cards which has to do with 'nomodeset' ([source]("http://ubuntuforums.org/showthread.php?t=1613132")).

Many of the options I see talk about issues after updates or changing settings further in the installation process. Or show screens that don't look like what I have. For example [this]("https://www.youtube.com/watch?v=jd9WIcPKc-o") video. It shows an installation screen which doesn't even come close to what I'm seeing.

[This]("http://i.imgur.com/YCxJMSf.jpg") is the menu I'm seeing and [this]("http://i.imgur.com/Cs1739F.jpg") is what I see when I select the first or second option.

As you can see there's also the option to press TAB and edit a menu entry. I did that on the install entry and I got a long statement ending with "ignore_uuid initrd=/casper/initrd.lz quiet splash --". So I thought how about I add 'nomodeset' here like in some examples. "ignore_uuid initrd=/casper/initrd.lz quiet splash nomodeset --" was what I had then. However after pressing enter I'm still greeted by the exact same white screen.

I also tried waiting. However after about 12 minutes I didn't expect anything to happen anymore.

There's also a long [sticky]("http://ubuntuforums.org/showthread.php?t=1743535") in this subforum which is also about a blank screen, however that seems to deal with this issue after upgrading and suggesting steps that I can't take because I haven't even installed it yet.

I'd really appreciate it if someone could help me figure this out.

---

