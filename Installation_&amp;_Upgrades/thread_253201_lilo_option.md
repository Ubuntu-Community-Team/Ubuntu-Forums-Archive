---
title: "lilo option"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by pmshah on 2006-09-08
First of all I did a lot of search but did not find the answer or a decvent thread to my question hence this new thread. If I missed on the answer please guide me to it. 

I have had bad luck with GRUB on a number of occassions & now refuse to use it at all.

I was wondering if there is a method or available choice for installing lilo to the ubuntu partiton and NOT TO THE MBR?

I use another boot managet called BootITNg which serves me extremely well.

Thnaks.

---

### Post by zxee on 2006-09-08
Probably in your situation it would be good to use the alternate cd.
The desktop cd now just installs grub to the mbr.
So you could install from the alternate cd, chose not to install grub, open a console (Alt+Ctrl+F1) hopefully you have a network/internet connection and then you can get lilo and install it-lilo might even be in the repos-I don't know that for a fact though-if not you can use wget to get it.

---

### Post by pmshah on 2006-09-08
Incidentally I got the Ubuntu 6.06 DVD with a magazine. I don't particularly care to download an iso just for the sake of trial. What I am surprised at is the fact that they have totally ignored the posibility of end user needing to use lilo or grub installed to the  installation partition.

Another culprit I came across was Suse Linux which dows not show the lilo option until much later in the installation process.

I also have Puppy linux installed on my machine amongst other Linux distros. It very clearly gives a choice grub destination.

Mandrake is the only one which very clearly shows me all available option at the very first stage.

---

### Post by zxee on 2006-09-08
> **pmshah said:**
> Incidentally I got the Ubuntu 6.06 DVD with a magazine. I don't particularly care to download an iso just for the sake of trial. What I am surprised at is the fact that they have totally ignored the posibility of end user needing to use lilo or grub installed to the  installation partition.

Another culprit I came across was Suse Linux which dows not show the lilo option until much later in the installation process.

I also have Puppy linux installed on my machine amongst other Linux distros. It very clearly gives a choice grub destination.

Mandrake is the only one which very clearly shows me all available option at the very first stage.

Actually ubuntu and a lot of distros use to give the option of where or even not to install grub/lilo. As I understand it specifically to ubuntu anyway the message that something was going to overwrite your mbr and or the need to make a decision about that was scaring potential users from trying to install it.
Not sure I agrre with that decision but ubuntu has a lot of things going for it-and I've tried the top 20+ distros on distrowatch. 
Someone here would probably mail you the recent 6.06.1 alternate (which is updated-those magazine cds are old) if you provide a SASE.

---

### Post by K.Mandla on 2006-09-08
LILO is an option on the alterate install CD. If you escape out of the installation process at any point, you should be presented with a menu of installation steps, and one of those is to install LILO.

By the way, if you pick a filesystem to boot to (such as XFS), which GRUB doesn't like, LILO becomes the default bootloader. ...

---

### Post by pmshah on 2006-09-09
I have successfully booted live CD in VMplayer. I liked what I saw & decided to try it. 

Can I try installation in Virtual Machine? Will it work? I would not like to chance another disaster. 

I live in Mumbai (Bombay) India. Where can I send a SASE (self addressed stamped envelope) in India?

BTW the DVD i got was with current issue (Sept)"Linux for You" so its not all that old.

I will try the escape route on a new machine I am currently building. At most a couple of hors worth of effort.

---

