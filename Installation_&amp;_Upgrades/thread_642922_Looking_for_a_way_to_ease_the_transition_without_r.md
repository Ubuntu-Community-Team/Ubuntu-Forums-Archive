---
title: "Looking for a way to ease the transition without running a virtual  MS Win"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by Recovering from MS. on 2007-12-17
This may sound backwards... but as close as everything looks the same, I find I cant do much of anything  As all my software other that the os is for Microsoft.

My biggest  problem I found so far is i can't install anything... this is the most common error;

 "Cannot open /media/cdrom0/setup.exe: No application suitable for automatic installation is available for handling this kind of file."

I think my comp might be a little week to to run a virtual windows. and it kind of defeats the purpose of trying to get away form MS...

Thanks for your time and assistance

---

### Post by Nano Geek on 2007-12-17
Have you looked at **Add/Remove**? It has many free applications for Linux.
It's under [B]Applications=>Add/Remove...

[/B]P.S. Those CDs that you are trying will only work in Windows, not Linux.

---

### Post by Recovering from MS. on 2007-12-17
Thanks for the quick response. I looked in there but I could not find a program that matched what I was looking for... Ie. the media players eather didn't support the codecs or had errors when playing dvds.

So if I cant open any setup.exe 's. ... how do I play my games?...?

---

### Post by jken146 on 2007-12-17
For codecs, it's often the case that you must install them (the proprietary ones) as well as installing a media player.  VLC seems to play everything though.

If you install the package **ubuntu-restricted-extras** you will get a lot of useful media stuff like codecs.

**libdvdcss2** may be needed to play some DVDs.

---

### Post by mangurt on 2007-12-17
VLC rocks for playing movies and music.

Another great player (for music) is Amarok.  You can find it under add/remove programs.

---

### Post by Recovering from MS. on 2007-12-17
Is there anything like media player classic... or a way to use mpC ?

also could you provide a link to a trusted site... for the extras & libdvdcss2

Thanks again...

---

### Post by Nano Geek on 2007-12-17
> **Recovering from MS. said:**
> Thanks for the quick response. I looked in there but I could not find a program that matched what I was looking for... Ie. the media players eather didn't support the codecs or had errors when playing dvds.

So if I cant open any setup.exe 's. ... how do I play my games?...?[Look here for instructions on making DVD's work.]("http://www.pcworld.com/article/id,138903-page,1-c,linux/article.html")

As for the games, I'm sorry to say it but they probably will never work in Linux since they were made for Windows.

What games are they BTW?

---

### Post by mangurt on 2007-12-17
VLC is just like MPC, I think you can even get a skin set for VLC to make it look like media player.  As for the extras and libdvdcss2, you can get those through synapic (systems, admin, synapic) and search for it there.  As for games, that will get somewhat tricky, most likely you will have to run them through wine or search around for a fix to play those games in linux (google is your friend)

---

### Post by jken146 on 2007-12-17
> **Recovering from MS. said:**
> Is there anything like media player classic... or a way to use mpC ?
VLC is the closest thing (and better IMO).  Find it in Add/Remove.

> also could you provide a link to a trusted site... for the extras & libdvdcss2
The package ubuntu-restricted-extras is in the repositories.  Use Applications > Add/Remove or System > Administration Synaptic to install it.

libdvdcss2 is in medibuntu.  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) is for adding the Medibuntu repository.  After that, install the package via Synaptic.

See [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) if you ever have difficulty installing something.

---

