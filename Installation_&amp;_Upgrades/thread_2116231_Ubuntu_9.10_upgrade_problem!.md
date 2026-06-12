---
title: "Ubuntu 9.10 upgrade problem!"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by tamrat on 2013-02-15
Hello to the good people of Ubuntu Forums!

My name is Tamrat and I am from Ethiopia. I am totaly new to linux on a personal computer. 

I was cleaning my room when I found a Ubuntu CD my friend gave me about a year ago under my bed. I really wanted to try it out and I installed it on my PC. I choose 'Install in Windows' and I gave it a reasonanble 10GB space. After the install completed, I really started to enjoy Ubuntu. It was version 9.10 (Karmic Koala).

 I was having fun. Then I went to System > Adminstration > Update Manager and an error poped up saying "Your Ubuntu version is not supported anymore". I thought this was because KK was a bit old. Then at the top of the window I read "New Ubuntu release '10.04.3 LTS' is avialable". I clicked 'Upgrade' and infos poped up telling me what its gonna do, what is gonna be downloaded, how much time it would take and stuff.

After that a window appeared ('Distribution Upgrade') and it started performing a series of tasks and downloading stuff. But at the section of 'Getting new packages', while fetching for the last file in the list another error poped up reading "Failed to fetch http(colon)//archive.ubuntu(dot)com/ubuntu/pool/main/libp/libproxy/libproxy0_0.3.1-1ubuntu1.1_i386.deb Connection failed [IP: 91.189.92.200 80]". I thought it was a connection problem so I switched to another network but the same error appered. So I took the liberty of typing the address right in the address bar of Mozilla and again an error poped saying "Not Found The requested .....". Does any one have any idea why this is happening? Is there another way around this? 

Thank you very much for your time.

P.S: As I am in a third world country, that download took me about 5hrs, so please help me.

---

### Post by ibjsb4 on 2013-02-15
You have installed a version of ubuntu that has reached end of life and no longer supported.  You need to install ubuntu 12.04  ..

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

What are your computer spec's?  How much ram, what kind of cpu?

---

### Post by schragge on 2013-02-15
Your country blocks downloads of anything that contains *proxy* in its name. See [thread=2114860]this thread[/thread]. Looks like you were using the US Ubuntu repository. I'm not sure if this block also applies to sites inside Ethiopia. Can you download the file by clicking on the link below?
[http://et.archive.ubuntu.com/ubuntu/pool/main/libp/libproxy/libproxy0_0.3.1-1ubuntu1.1_i386.deb](http://et.archive.ubuntu.com/ubuntu/pool/main/libp/libproxy/libproxy0_0.3.1-1ubuntu1.1_i386.deb)

[highlight]Update.[/highlight]
Have sent you PM with the download link.

---

### Post by sudodus on 2013-02-15
Welcome to the Ubuntu Forums :-)

Ubuntu 9.10 is way beyond end of life, and 10.04 LTS desktop (as opposed to the server version) has only a couple of months before its end of life.

I would suggest that you get the current long time support version 12.04 LTS. There are several flavours, that you can select instead of or along with the standard Ubuntu:

- Ubuntu with the fancy but demanding desktop environment Unity
- Kubuntu with the fancy but demanding desktop environment KDE
- Lubuntu with the ultra light-weight desktop environment LXDE
- Xubuntu with the fancy but demanding desktop environment XFCE

It is also possible to start with one of these flavours and add or switch to any of the other desktop environments.

Before deciding what to do, I suggest that you let us know the specifications of your computer, particularly the cpu, ram, graphics chip/card and internet connection (wired or wireless, if wireless: the chip or card). Then we can suggest which flavour of Ubuntu to select, and how to get it.
--
If you have problems downloading because of a slow internet connection, there are a few options:

0. Don't try to upgrade from the old Ubuntu 9.10

1. Try to borrow a faster internet connection to download one or more of the [KLX]Ubuntu iso files of the version 12.04. This is free software (no cost, open software), but I don't know if you would have to pay for the download (approximately 700 MB). Check that the download was good with md5sum, and burn a CD (or make a boot USB drive if you have one).

2. Buy a CD from Canonical, the company supporting Ubuntu. See this link

[[COLOR="Red"]https://shop.canonical.com/product_info.php?products_id=976[/COLOR]]("https://shop.canonical.com/product_info.php?products_id=976")

---

### Post by tamrat on 2013-02-15
> **schragge said:**
> You country blocks downloads of anything that contains *proxy* in its name. See [thread=2114860]this thread[/thread]. I'm not sure if this block also applies to sites inside Ethiopia. Can you download the file by clicking on the link below?
[http://et.archive.ubuntu.com/ubuntu/pool/main/libp/libproxy/libproxy0_0.3.1-1ubuntu1.1_i386.deb](http://et.archive.ubuntu.com/ubuntu/pool/main/libp/libproxy/libproxy0_0.3.1-1ubuntu1.1_i386.deb)

Hello, your theory seems plausible since my country uses satelite jammers and has a sophisticated data control and filtering developed by the Chinese. As for the link you provided, my browser wont even load the page, let alone download the file.

Can I ask for a favour and can you rename and compress that file and upload it to a file sharing site? But first is it even possible to download this file from another source and add it to the upgrade process?


As for the other replies, I know it would be better just to download the latest version but I simply can't at the moment. Internet is not that bad but the pricing is really bad. Fast internet can only be found in internet cafes. Most home internets are dial up or cdma 1x. I cant even buy the CD because there are no int banks and there is no possible online payment method (like visa or mastercard).

Thank you all for your replies!

---

### Post by snowpine on 2013-02-15
It will be less download in total to start fresh with 12.04 than to attempt an "end of life" upgrade.

If you are totally new to Linux, have very limited bandwidth, and aren't particularly attached to Ubuntu in specific, then consider using Puppy Linux (150mb), SliTaz (35mb), or TinyCore (10mb). Ubuntu is one of the larger distros and you must budget not just for the original download but also for the hundreds of mb's of software updates you will receive through the life cycle of the product.

---

### Post by sudodus on 2013-02-15
> **snowpine said:**
> It will be less download in total to start fresh with 12.04 than to attempt an "end of life" upgrade.

If you are totally new to Linux, have very limited bandwidth, and aren't particularly attached to Ubuntu in specific, then consider using Puppy Linux (150mb), SliTaz (35mb), or TinyCore (10mb). Ubuntu is one of the larger distros and you must budget not just for the original download but also for the hundreds of mb's of software updates you will receive through the life cycle of the product.

Yes, it is a good idea to download a small linux 'distro'. I have best experience of ***Puppy Linux*** among these suggested distros. (The size is less than 25% of Ubuntu's size).

---

### Post by ibjsb4 on 2013-02-15
Puppy linux can also use the Ubuntu repositories.

---

### Post by tamrat on 2013-02-15
Thank you everyone for your replies. I know there are other, lighter, linux distros but I went for Ubuntu because I found the installation disc, to bad it was outdated. But @schragge's PM fixed my problem and I am now upgraded, though this one expires on April 2013 like you said. 

Thank you all for the warm welcome and quick replies! I am already loving linux!!

---

