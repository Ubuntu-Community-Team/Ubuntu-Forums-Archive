---
title: "What  other linux distro can I supplement ubuntu with ?"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-11-07
I am an ubuntu fan, it is the only linux distro I know, after 2 years I will like to learn an other distro just for the sake of curiousity.
As I don't know any other linux distro I need advice/suggestion  on witch one to try.
They are so many out there it is difficult to choose.

---

### Post by dino99 on 2010-11-07
hard to answer, depend on your skills and profile:

- ubuntu is for "human" :)

if you have knowledge (and time) to fight with "techies" distro or built your own config:

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by hoboy on 2010-11-07
> **dino99 said:**
> hard to answer, depend on your skills and profile:

- ubuntu is for "human" :)

if you have knowledge (and time) to fight with "techies" distro or built your own config:

[http://distrowatch.com/](http://distrowatch.com/)

Well I am programmer, so I was thinking of a user friendly distro like ubuntu.

---

### Post by dino99 on 2010-11-07
if you look at right pane on distrowatch, you find the top distro. Maybe you can have fun with fedora, gentoo, or if you like the wild side, why not a try to bsd :)

---

### Post by cascade9 on 2010-11-07
Going from ubuntu to another debian based distro (Debian, Mint, Mepis, Aptosid, etc) is the easiest leaning curve. 

Debian is probably the most difficult of them, but its not that hard. LMDE (linux mint 'debian edition') would be the eaiest way to try a rolling release distro. 

RPM distros are pretty easy (in general) as well, and being a different package manager you'll have to learn new things.

---

### Post by hoboy on 2010-11-07
Thanks guys, my way to linux was a colleague gave me an ubuntu cd, now that I am navigating on my own it is not that easy to 
for example 
[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)

---

### Post by I'mGeorge on 2010-11-07
I guess Debian would be the most proper replacement. It also has a history, I believe it's one of the oldest distros around, and when it comes mixing functionality and the latest software with stability few distros can match it.

---

### Post by hoboy on 2010-11-07
> **I'mGeorge said:**
> I guess Debian would be the most proper replacement. It also has a history, I believe it's one of the oldest distros around, and when it comes mixing functionality and the latest software with stability few distros can match it.

OK. let said that one goes for [http://www.debian.org/](http://www.debian.org/)
can I install it wiht other os like ubuntu/windows/ ?
like triple booting.
I have an esternal harddisk of 1 Tera byte, I already use dual booting ubuntu windows 7.

---

### Post by I'mGeorge on 2010-11-07
> **hoboy said:**
> OK. let said that one goes for [http://www.debian.org/](http://www.debian.org/)
can I install it wiht other os like ubuntu/windows/ ?
like triple booting.
I have an esternal harddisk of 1 Tera byte, I already use dual booting ubuntu windows 7.

Yeah sure, it's all about configuring Grub

---

### Post by hoboy on 2010-11-07
> **I'mGeorge said:**
> Yeah sure, it's all about configuring Grub
nmmmmmmmm 
>Yeah sure, it's all about configuring Grub
How do I do that, any link, example for that ?

---

### Post by cascade9 on 2010-11-07
> **I'mGeorge said:**
> I guess Debian would be the most proper replacement. It also has a history, I believe it's one of the oldest distros around, and when it comes mixing functionality and the latest software with stability few distros can match it.

Functionality and stability, I'll agree with. But newest software? *blinks* 'Stable', currently version 5.0 'lenny'  is normally a bit behind the other distros on release, and after a 1-2 years its got far older versions of software than almost anything else. 

Even 'testing' and 'sid' (akas unstable.....not that its unstable) can have software thats quite a bit older than other distros. Eg- Aptosid (using the debian 'sid' repos) is using firefox (OK, iceweasel) 3.5.15.   

@ hoboy- I'd be far more temped to go with LMDE instead of debian stable. Debian stable is just that, stable, but its almost at the end of its life now, the newer version is just finishing the freeze before it gets released as debian stable 6.0 'squeeze'. 

[http://www.linuxmint.com/download_lmde.php](http://www.linuxmint.com/download_lmde.php)

---

### Post by hoboy on 2010-11-07
> **cascade9 said:**
> Functionality and stability, I'll agree with. But newest software? *blinks* 'Stable', currently version 5.0 'lenny'  is normally a bit behind the other distros on release, and after a 1-2 years its got far older versions of software than almost anything else. 

Even 'testing' and 'sid' (akas unstable.....not that its unstable) can have software thats quite a bit older than other distros. Eg- Aptosid (using the debian 'sid' repos) is using firefox (OK, iceweasel) 3.5.15.   

@ hoboy- I'd be far more temped to go with LMDE instead of debian stable. Debian stable is just that, stable, but its almost at the end of its life now, the newer version is just finishing the freeze before it gets released as debian stable 6.0 'squeeze'. 

[http://www.linuxmint.com/download_lmde.php](http://www.linuxmint.com/download_lmde.php)

Thank as I am looking for to try a new distro I am glad for any suggestion.

---

### Post by I'mGeorge on 2010-11-07
> **hoboy said:**
> nmmmmmmmm 
>Yeah sure, it's all about configuring Grub
How do I do that, any link, example for that ?

GRUB or grand unified bootloader it's the software that let's you select from several OS's if you have more than one. When you're installing Debian, in the process you would be asked to configure grub also, choose a default OS and so on, and if everything goes smooth without any problems, like a bad copy of a Debian release, it should automatically recognize if you have other OS installed on your PC. But even if they doesn't go as they should after installing Debian just go to /boot/grub/grub.cfg open it and there you would see examples of how an windows os can be loaded with grub or a linux os for that matter, you just have to know in what partitions are they installed.

---

### Post by I'mGeorge on 2010-11-07
> **cascade9 said:**
> Functionality and stability, I'll agree with. But newest software? *blinks* 'Stable', currently version 5.0 'lenny'  is normally a bit behind the other distros on release, and after a 1-2 years its got far older versions of software than almost anything else. 

Even 'testing' and 'sid' (akas unstable.....not that its unstable) can have software thats quite a bit older than other distros. Eg- Aptosid (using the debian 'sid' repos) is using firefox (OK, iceweasel) 3.5.15.   

@ hoboy- I'd be far more temped to go with LMDE instead of debian stable. Debian stable is just that, stable, but its almost at the end of its life now, the newer version is just finishing the freeze before it gets released as debian stable 6.0 'squeeze'. 

[http://www.linuxmint.com/download_lmde.php](http://www.linuxmint.com/download_lmde.php)

Well I'm actually using Aptosid and I'm more than happy with the software updates, almost everyday there's something new around, and it works like clockwork. But yeah I would recommend Debian testing for the new comers 'cause lenny it's oldish when it comes to updates.

---

### Post by cracker89 on 2010-11-07
> **hoboy said:**
> nmmmmmmmm 
>Yeah sure, it's all about configuring Grub
How do I do that, any link, example for that ?

[http://ubuntuforums.org/archive/index.php/t-482561.html](http://ubuntuforums.org/archive/index.php/t-482561.html)

[http://www.novell.com/coolsolutions/feature/11213.html](http://www.novell.com/coolsolutions/feature/11213.html)

It shouldnt be a problem. Different partitions for different OS's, and select the right disks while formatting. The GRUB usually can handle the rest.

---

### Post by hoboy on 2010-11-07
After the responses I will like to try Linux Mint [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)
So I am looking for something like wubi for ubuntu, then I case I mess thinks op I can easily delete it.
But after googled for while now I saw that there is something called mint4win.exe but I can not find any link to download it.

---

### Post by cascade9 on 2010-11-08
> **I'mGeorge said:**
> Well I'm actually using Aptosid and I'm more than happy with the software updates, almost everyday there's something new around, and it works like clockwork. But yeah I would recommend Debian testing for the new comers 'cause lenny it's oldish when it comes to updates.

I'm actually using aptosid as well. Great distro :) 

> **hoboy said:**
> After the responses I will like to try Linux Mint [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)
So I am looking for something like wubi for ubuntu, then I case I mess thinks op I can easily delete it.
But after googled for while now I saw that there is something called mint4win.exe but I can not find any link to download it.

If your already using ubuntu with no problems, dont bother with 'normal' mint. Its just ubuntu with some tweaks, and uses the ubuntu repos. 

Linux Mint Debian Edition is quite different. Its not based on or using the ubuntu repos (based on debian and uses ther debian repos), and it is a 'rolling release' distro. Meaning that you never have to reinstall/update to a new version, you get packages when they released for debian 'testing'.

---

### Post by cracker89 on 2010-11-08
[http://www.sabayon.org/](http://www.sabayon.org/)

dont reAlly know, cant vouch but it seems beginner friendly..

---

### Post by TBABill on 2010-11-08
PCLinuxOS is a great distro for someone just wanting to venture out into "different" without requiring much Linux knowledge in general. It's fast and easy to configure and you will likely never need a command line. It's similar to Mint in terms of wanting to make it easy right out of the box. 
 
I think a person could also enjoy the learning curve adapting to many other distros. openSUSE is fairly easy, Fedora if your hardware detects and installs automatically (to keep your OS easy for you), any Mint edition, Mepis (Debian based, not Ubuntu based). Some great Linux distros to try out and it's really just a matter of figuring out which ones intrigue you and which you are willing to invest the time and energy to learn. I ran all of them and still came back to Ubuntu.

---

### Post by hoboy on 2010-11-09
> **TBABill said:**
> PCLinuxOS is a great distro for someone just wanting to venture out into "different" without requiring much Linux knowledge in general. It's fast and easy to configure and you will likely never need a command line. It's similar to Mint in terms of wanting to make it easy right out of the box. 
 
I think a person could also enjoy the learning curve adapting to many other distros. openSUSE is fairly easy, Fedora if your hardware detects and installs automatically (to keep your OS easy for you), any Mint edition, Mepis (Debian based, not Ubuntu based). Some great Linux distros to try out and it's really just a matter of figuring out which ones intrigue you and which you are willing to invest the time and energy to learn. I ran all of them and still came back to Ubuntu.

Thanks guys.. now i am in dough witch one to use.

---

