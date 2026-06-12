---
title: "New Install Help"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by W@LT on 2010-08-15
I am back after a few years and trying to install the latest version of Ubuntu 10.04

I must admit after some fairy basic bad experiences some years ago I had hoped that the new install on my Window 7 machine would have been relatively easy

Sadly not!!

All installs OK but after selecting Ubuntu at the grub start up the keyboard functionality disappears so I cannot login.

Please can someone let me know how to overcome this..

Using a Logitech - Wireless keyboard

Thanks

---

### Post by davidmohammed on 2010-08-15
a quick google has revealed that logitec wireless keyboards are a common complaint.  Any fixes suggested are specific to the actual keyboard.

Suggest the following to obtain more information.  Hopefully, armed with this info, someone can help.

Disconnect the usb device.  Plug in a regular keyboard and boot.

when you get to a desktop open a terminal session.

type 

dmesg

note where the last message is displayed.

plug in you usb device.

type

dmesg

copy and paste the new text displayed in a reply (dont forget to paste using a code tag- i.e. from when you initially typed dmesg above.

type

lsusb

copy and paste the output here in a reply.

---

### Post by W@LT on 2010-08-15
Thanks David

At least Ubuntu is consistent!!

I ditched Ubuntu before after a raft of compatibility problems.... 

It looks like nothing has progressed in my absence :D

---

### Post by davidmohammed on 2010-08-15
...

hope you are not blaming ubuntu...

shame logitech doesnt put in more effort to support linux.

---

### Post by W@LT on 2010-08-15
Ubuntu... Possibly

Some searches seem to indicate that this was not a problem with older versions of Ubuntu.

Which would seem to indicate that someone has missed out some code somewhere in the latest release... 

I have now resolved my problem thanks to Google Searches... although not an easy fix.

Thanks for the support and I apologise for venting my frustrations

---

### Post by W@LT on 2010-09-16
I don't believe it..

I made the mistake of doing the update thing and guess what?

The KeyBoard doesn't work... looks like the fix has not yet found its way into the release.

If this was Windows MS would have fixed it by now..... or not!! ;)

---

