---
title: "Upgrading from Ubuntu 9.04 to 10.04.3 LTS"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by qwxy on 2011-09-14
Hello.
I want to upgrade from Ubuntu 9.04 to 10.04.3 LTS, so I want to ask you something about it.
How long would it take with a connection speed of about 105 KB/s?
What are the **MINIMUM** system requirements?
Do I meet **MINIMUM **system requirements with the computers listed below?
You see, i have a laptop and a computer:

Laptop info:

Pentium 4 - 1.86GHz
512 MB RAM
Available free disk space (Linux is installed under Windows) : 1, 3 GB

Computer Info:

Pentium III (Coppermine) - approx. 890 MHz
384 MB RAM
Available free disk space (Linux is installed as standalone system) : more than 10 GB

Also, what can you tell me about Puppy Linux?
[http://www.puppylinux.org]("http://www.puppylinux.org/")

Please answer as soon as possible, because Ubuntu 9.04 is not longer supported.

---

### Post by snowpine on 2011-09-14
Welcome to the forums!

The best way to tell whether Ubuntu 10.04 is compatible with your hardware is to burn a Live CD and take it for a test drive. :) The download is about 700mb (plus you should budget a couple hundred mb more for updates after you've installed).

Personally I would not use Ubuntu on a Pentium 3 with 384mb RAM... I would use a lightweight distro such as Lubuntu, CrunchBang, Puppy, etc.

---

### Post by mörgæs on 2011-09-14
Before deciding what to do, I would recommend that you try a live boot of Lubuntu on the smaller computer and Xubuntu on the larger.

---

### Post by qwxy on 2011-09-14
> **snowpine said:**
> Welcome to the forums!


Thank you.

---

### Post by qwxy on 2011-09-14
Thank you for such fast replies.
I would download a LiveCD, but maximum speed of my connection is only about 105KB per second.
How long would it take to donwload about 700MB with maximum speed of connection of about 105KB per second?
Also, is there the XPde edition of Ubuntu Linux?

---

### Post by snowpine on 2011-09-14
> **qwxy said:**
> Thank you for such fast replies.
I would download a LiveCD, but maximum speed of my connection is only about 105KB per second.
How long would it take to donwload about 700MB with maximum speed of connection of about 105KB per second?

Approximately 2 hours.

> **qwxy said:**
> Also, is there the XPde edition of Ubuntu Linux?

I don't know what this is, sorry.

(edit) [http://www.psychocats.net/ubuntu/xpde](http://www.psychocats.net/ubuntu/xpde)

---

### Post by qwxy on 2011-09-14
> **snowpine said:**
> Welcome to the forums!

Personally I would not use Ubuntu on a Pentium 3 with 384mb RAM... I would use a lightweight distro such as Lubuntu, CrunchBang, Puppy, etc.

Well, I already have downloaded the latest version of Puppy Linux, but I am not really sure how to set it up with Windows since GRUB from Ubuntu 9.04 is my default bootloader. If I delete Ubuntu 9.04, it will also delete GRUB. If GRUB is removed, I am not sure will Windows bootloader replace it or my computer will say that there is no OS installed. Also, I already have donwloaded GRUB for Windows. It is in attachments. 
Windows XP SP3 is the Windows which I am using.
Do not launch the program in xp-boot.zip.
If you launch it, it will replace your boot manager with GRUB boot loader for Windows.
To be of any use, you must make a folder on Windows XP partition and name it "boot".

---

### Post by snowpine on 2011-09-14
> **qwxy said:**
> Well, I already have downloaded the latest version of Puppy Linux, but I am not really sure how to set it up with Windows since GRUB from Ubuntu 9.04 is my default bootloader. If I delete Ubuntu 9.04, it will also delete GRUB. If GRUB is removed, I am not sure will Windows bootloader replace it or my computer will say that there is no OS installed. Also, I already have donwloaded GRUB for Windows. It is in attachments. 
Windows XP SP3 is the Windows which I am using.

Have you checked the Puppy forums and manual?

[http://murga-linux.com/puppy](http://murga-linux.com/puppy)
[http://puppylinux.org/main/Manual-English.htm#Manual06](http://puppylinux.org/main/Manual-English.htm#Manual06)

---

### Post by qwxy on 2011-09-14
> **snowpine said:**
> 

I don't know what this is, sorry.



It is a free duplicate of Windows desktop for Linux and maybe some other operating systems.
I am not sure is this a legal desktop envoirment to use, since it is a duplicate of Windows desktop interface, but some Linuxes use it.

---

### Post by snowpine on 2011-09-14
> **qwxy said:**
> It is a free duplicate of Windows desktop for Linux and maybe some other operating systems.
I am not sure is this a legal desktop envoirment to use, since it is a duplicate of Windows desktop interface, but some Linuxes use it.

There's a little bit of info here:

[http://www.psychocats.net/ubuntu/xpde](http://www.psychocats.net/ubuntu/xpde)

Sounds like it is not officially supported or endorsed by Ubuntu; use at your own risk. :)

---

### Post by qwxy on 2011-09-14
> **snowpine said:**
> Approximately 2 hours.



Well, you see, I tend to get extremely impatient when downloading large files.
How long would it take if I update it via Update button in Update Manager?

---

### Post by snowpine on 2011-09-14
> **qwxy said:**
> Well, you see, I tend to get extremely impatient when downloading large files.
How long would it take if I update it via Update button in Update Manager?

You have two basic options:

1. Download Ubuntu 10.04 (~700mb) and test-drive it on your computer. If you're satisfied it works well, then back up all your files/documents/data to an external drive and install 10.04, replacing 9.04. (Alternately, if you have enough hard drive room, you can keep 9.04 running side-by-side with 10.04).  

2. Perform an [End-of-Life Upgrade]("https://help.ubuntu.com/community/EOLUpgrades") from 9.04 to 9.10 (~700mb) then from 9.10 to 10.04 (~700mb). 

Personally I recommend option #1. It is the least amount of downloading and the best chance of success, in my opinion/experience.

Sorry your connection is so slow, but why not start the download/torrent when you go to bed at night; it will be complete when you wake up the next morning. :) Alternately you can look for Linux magazines at your local news stand; they frequently include a live CD/DVD with various distros.

---

### Post by mörgæs on 2011-09-14
> **qwxy said:**
> Well, you see, I tend to get extremely impatient when downloading large files.
How long would it take if I update it via Update button in Update Manager?

Don't. Refer to post 3 - you don't know how the other releases behave on this computer until you test.

By the way, for Lubuntu and Xubuntu I would recommend 11.04 and not 10.04. If downloading is a problem, you could also feed both of them Lubuntu.

---

### Post by qwxy on 2011-09-14
> **snowpine said:**
> 

1. (Alternately, if you have enough hard drive room, you can keep 9.04 running side-by-side with 10.04).  



Why to keep it installed when Ubuntu 9.04 is no longer supported?

---

### Post by qwxy on 2011-09-14
Thank you for your advices and support.

---

### Post by snowpine on 2011-09-14
> **qwxy said:**
> Why to keep it installed when Ubuntu 9.04 is no longer supported?

I would not keep 9.04 personally, but I want to be sure you understand all your options: If you wish, you can keep your old familiar 9.04 as a safety net/fallback, in case 10.04 doesn't live up to your expectations. 

If you need the hard drive space more than you need the security blanket, then by all means completely replace 9.04.

Obviously the best way to avoid disappointment is to take the Live CD for a thorough test-drive before installing/upgrading.

---

### Post by qwxy on 2011-09-14
Thank you for advices and support, snowpine.:)

---

