---
title: "Amarok does not play any media!"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by raks1991 on 2010-05-10
I've been a Ubuntu user for the last 7 days and just switched from Vista.I've been loving it so far except for this tiny problem.
Amarok does not play media files at all.The pre-installed Rhythmbox with 10.04 works great.In Amarok,it isn't that I don't get sound. It just won't *play*. If I click  a file, then click *play* it quickly goes through an amount of  songs and then it tries to play all the songs in the playlist unsuccessfully.
I'm using Ubuntu 10.04 Lucid Lynx and Amarok 2.3.0(KDE 4.4.2) in a 32 bit system.

---

### Post by damien_d on 2010-05-11
> **raks1991 said:**
> I've been a Ubuntu user for the last 7 days and just switched from Vista.I've been loving it so far except for this tiny problem.
Amarok does not play media files at all.The pre-installed Rhythmbox with 10.04 works great.In Amarok,it isn't that I don't get sound. It just won't *play*. If I click  a file, then click *play* it quickly goes through an amount of  songs and then it tries to play all the songs in the playlist unsuccessfully.
I'm using Ubuntu 10.04 Lucid Lynx and Amarok 2.3.0(KDE 4.4.2) in a 32 bit system.

Ditto, though with 64-bit lucid.

---

### Post by damien_d on 2010-05-11
Found a solution that works for me:
```

damien@damien-desktop:~$ sudo apt-get install libxine1-ffmpeg libxine1-all-plugins

```

 -- Damien

---

### Post by raks1991 on 2010-05-12
Hi Damien,
I tried what worked for you,but I get

E : Couldn't find package libxinel-ffmpeg.

---

### Post by raks1991 on 2010-05-12
I figured it out.I hadn't installed Ubuntu restricted extras.That's why Amarok wasn't playing any files.The restricted extras can be found here.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Just run the installation file,it downloads all the files in the package(17) and after you're done,restart Amarok and it should work just fine.Thanks for the reply Damien.:)

---

### Post by damien_d on 2010-05-12
> **raks1991 said:**
> I figured it out.I hadn't installed Ubuntu restricted extras.That's why Amarok wasn't playing any files.The restricted extras can be found here.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Just run the installation file,it downloads all the files in the package(17) and after you're done,restart Amarok and it should work just fine.Thanks for the reply Damien.:)

Awesome :)

Can you mark the thread as solved? It might help someone else that comes across the same problem.

There are several bugs filed against amarok for this behaviour.  All are marked as "invalid", but I'm going to ask for some sort of pop-up that says why the media isn't being played.

 -- Damien

---

### Post by jetta on 2010-05-16
> **damien_d said:**
> Found a solution that works for me:
```

damien@damien-desktop:~$ sudo apt-get install libxine1-ffmpeg libxine1-all-plugins

```

 -- Damien

thanks, its work for me too
(just fresh isntall to 10.04)

---

### Post by maestrobwh1 on 2010-05-16
Also:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

If you want everything about multimedia working.

---

