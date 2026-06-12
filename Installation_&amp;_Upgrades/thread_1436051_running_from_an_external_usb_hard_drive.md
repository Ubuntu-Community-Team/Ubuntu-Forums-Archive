---
title: "running from an external usb hard drive"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by marie-p on 2010-03-22
Hi,

I have a netbook that is already running ubuntu netbook remix. However, my storage space on that computer is limited so I bought an external usb hard drive. 

The software I use stores its data on the same drive as where it is running, so rather than have to move my data back and forth, I would like to install ubuntu on the usb hard drive. How would I do that? Would the usb connection be fast enough for me to work on video files? 

Also, I would need to transfer files from a desktop computer (running Windows) to my usb hard drive. Would I still be able to do that?

---

### Post by phillw on 2010-03-22
Hi,

This community document should answer your questions --> [https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

USB2 should be quite fast enough for video streaming.

Regards,

Phill.

---

### Post by viralmeme on 2010-03-22
> **marie-p said:**
> .. The software I use stores its data on the same drive as where it is running, so rather than have to move my data back and forth ..

What's the name of the software? I don't see a problem with saving to an external HD, just link a local directory to the external one.

[http://en.wikipedia.org/wiki/Ln_%28Unix%29](http://en.wikipedia.org/wiki/Ln_%28Unix%29)[URL="http://en.wikipedia.org/wiki/Ln_%28Unix%29"]
[/URL]

---

### Post by marie-p on 2010-03-22
> **ymitchell said:**
> What's the name of the software? I don't see a problem with saving to an external HD, just link a local directory to the external one.

[http://en.wikipedia.org/wiki/Ln_%28Unix%29](http://en.wikipedia.org/wiki/Ln_%28Unix%29)[URL="http://en.wikipedia.org/wiki/Ln_%28Unix%29"]
[/URL]

It's a software made specifically for oral history called StoriesMatter. The media files are supposed to go in the folder marie/.appdata/com.storiesmatter/Local Store/medias

I tried to create a link by going to my usb hard drive, right clicking on the file, and choosing 'Make Link' but it gives me an error message. (it says 'Operation not permitted')

---

### Post by viralmeme on 2010-03-26
> **marie-p said:**
> It's a software made specifically for oral history called StoriesMatter. The media files are supposed to go in the folder marie/.appdata/com.storiesmatter/Local Store/medias

I tried to create a link by going to my usb hard drive, right clicking on the file, and choosing 'Make Link' but it gives me an error message. (it says 'Operation not permitted')

You probably need to be 'root' to do that.

[http://www.cyberciti.biz/faq/unix-creating-symbolic-link-ln-command/](http://www.cyberciti.biz/faq/unix-creating-symbolic-link-ln-command/)

---

