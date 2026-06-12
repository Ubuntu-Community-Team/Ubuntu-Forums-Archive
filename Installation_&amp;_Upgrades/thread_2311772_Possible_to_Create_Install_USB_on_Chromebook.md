---
title: "Possible to Create Install USB on Chromebook?"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by teejay17 on 2016-01-29
Hi everyone, I would like to create an install USB of Ubuntu using my chromebook. However, I wish to install on an old Windows laptop, and not the chromebook itself. And therein lies the challenge: searching Google only uncovers how to install on Chromebook... And that's what I don't want. 
Any help would be appreciated.

---

### Post by Bucky Ball on 2016-01-30
Use one of these:

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

Universal USB Installer:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Doesn't make any difference what you create the install media on and what you install on. All you need to worry about is whether the machine you're going to install on is 32bit or 64bit. Once you know that, download the correct ISO, 32 or 64bit, create install USB, install on the other machine. Done.

There are [literally hundreds]("https://duckduckgo.com/?q=install+ubuntu") of websites explaining how to install Ubuntu on a regular ol' PC. Strange you only find the ones that relate to Chromebooks. :-k

[See here. ]("http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html")

---

### Post by howefield on 2016-01-30
I'm pretty sure you could use Crosh and the dd command. 

Research it.

---

### Post by teejay17 on 2016-01-31
> **Bucky Ball said:**
> Use one of these:

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

Universal USB Installer:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Doesn't make any difference what you create the install media on and what you install on. All you need to worry about is whether the machine you're going to install on is 32bit or 64bit. Once you know that, download the correct ISO, 32 or 64bit, create install USB, install on the other machine. Done.

There are [literally hundreds]("https://duckduckgo.com/?q=install+ubuntu") of websites explaining how to install Ubuntu on a regular ol' PC. Strange you only find the ones that relate to Chromebooks. :-k

[See here. ]("http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html")
There's no option to create install media using a Chromebook on those sites you've provided. For clarification: I won't be installing Ubuntu on the Chromebook. I am seeking a way to make install USB from Chromebook. So basically I am seeking a Web-centric methodology. Does such a method exist?

---

### Post by Vladlenin5000 on 2016-01-31
There are no similar tools for ChromeOS. The suggestions were for Windows - because you said you had a Windows PC -...

---

### Post by sudodus on 2016-01-31
I'd have a second look at this alternative.

> **howefield said:**
> I'm pretty sure you could use Crosh and the dd command. 

Research it.

***dd*** is doing what you tell it to do without any questions. So if you tell it to wipe your family pictures, it will do it. dd is nicknamed 'disk destroyer', but when you harness it correctly, it is a very powerful tool. ***Please double-check and triple-check, that the target device is the correct one.***

Unmount all partitions in the target device x. Run this command line with superuser (root) privileges (I'm not sure sudo is available in crosh),

```
sudo dd if=/path/file.iso of=/dev/sdx bs=4096
```

where x is the drive letter of the target device.

***Edit:*** According to [10-commands-included-in-chrome-oss-hidden-crosh-shell](http://www.howtogeek.com/170648/10-commands-included-in-chrome-oss-hidden-crosh-shell/)

you can use ***shell*** in crosh

> shell: Opens a full bash shell where you can run other Linux commands, including ones that can launch standard Linux desktop environments after you install them.

and get a full bash ...

---

