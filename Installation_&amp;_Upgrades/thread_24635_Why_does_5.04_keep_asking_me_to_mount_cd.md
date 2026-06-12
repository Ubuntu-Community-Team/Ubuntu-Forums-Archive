---
title: "Why does 5.04 keep asking me to mount cd"
date: 2005-04-07
forum: Installation &amp; Upgrades
---

### Post by btdown on 2005-04-07
I've installed Ubuntu 5.04 rc using the "lo resource" instructions at:
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html) and everything works pretty well. I did however, try to install biittorrent and screen and some other packages and sometimes it asks me to put in the cdrom to install instead of going to the online apt repositories. It doesnt do it all the time, only sometimes. Installing stuff from the online repositories works without any problems, so why would I sometimes need to insert the cdrom, and sometimes not?

Thanks,
BT

---

### Post by Nis on 2005-04-07
[QUOTE=btdown]I've installed Ubuntu 5.04 rc using the "lo resource" instructions at:
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html) and everything works pretty well. I did however, try to install biittorrent and screen and some other packages and sometimes it asks me to put in the cdrom to install instead of going to the online apt repositories. It doesnt do it all the time, only sometimes. Installing stuff from the online repositories works without any problems, so why would I sometimes need to insert the cdrom, and sometimes not?

Thanks,
BT[/QUOTE]
 If the package is listed as being available on the CD then Synaptic (and maybe apt, I'm not sure) will try to get that package because downloading is sometimes slow for some people.  If you comment out the CD line in your /etc/apt/sources.list and reload your sources then you should always download a package instead of trying to get it off the CD.

---

### Post by btdown on 2005-04-08
I dont use synaptic, and an entry isnt present in sources.list for the cdrom. Could you please take a look at my sources.list and give me your opinion if its optimal, and would it support the upgrade to 5.04 final? I've searched on here and found many different sources.list and I'm not quite sure where I stand:

```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

```

Thank you,
BT

---

### Post by Nis on 2005-04-08
No problems that I can see.  If you want to disable CD-ROM installation of new packages comment out
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted

```

Also, you might want to add multiverse if you want things like Flash.

---

### Post by btdown on 2005-04-08
Ah thanks for the tip, I thought the "deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386...." was a comment or a title or something.....I didnt know it was actually pointing to the cdrom as an installation source.

Thanks for the multiverse tip. I was wondering why I couldnt find some apps. I wonder why they dont put it in the sources.list and comment it out so you at least know it exists.

thanks again!
BT

---

### Post by kahping on 2005-04-08
[QUOTE=btdown]Ah thanks for the tip, I thought the "deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386...." was a comment or a title or something.....I didnt know it was actually pointing to the cdrom as an installation source.

Thanks for the multiverse tip. I was wondering why I couldnt find some apps. I wonder why they dont put it in the sources.list and comment it out so you at least know it exists.

thanks again!
BT[/QUOTE]

it was there for warty, so i guess the devs thought the community should already be in the know. newbies can get the info from forum regulars :-P

kahping

---

