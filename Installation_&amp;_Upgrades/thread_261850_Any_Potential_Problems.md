---
title: "Any Potential Problems?"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by seismicmike on 2006-09-20
Hello, I'm writing this to see if anyone can advise me on how best to proceed. I have a dual boot system, Windows XP (obviously) and Ubuntu Linux 5.01 (Breezy Badger). I want to upgrade my Ubuntu to Dapper Drake, but I want to be extremely cautious. I don't remember exactly what I did before but I remember that I tried to do something with the linux partition once (I think I tried to re-install Breezy) and it caused a major problem in the GRUB boot loader causing me to have to completely reinstall Windows and reset my system. I don't want to have to go through this again because, besides the normal headache of reinstalling Windows, I lost several files.

I know what you're going to say, "Why do you even still have Windows?" The fact is I'm still tied to some of the software that, sadly, isn't supported in Linux (and I'm currently having trouble getting any distro of Linux to use my sound card properly and since I'm a music fanatic, I have to have Windows to listen to music!). Plus because it's a laptop and the funkyness of ndiswrapper the boot sequence has been rather long for Linux (even though I did create a wonderful script that does it automatically).

Anyway, is there any way to prevent damaging GRUB (or recovering it if I do damage it)? I'm writing from a live session of Dapper and I want so badly to click the "Install" button, but I'm afraid of losing all my stuff.

Any suggestions? Thanks.

PS if you can fix my sound card issue I'll love you forever!

---

### Post by skymt on 2006-09-20
You should be able to do it live. Just boot into Breezy, edit */etc/apt/sources.list* changing "breezy" to "dapper", and run "sudo aptitude update && sudo aptitude dist-upgrade". I assume you're backed up!

If that doesn't work (big changes sometimes cause problems), you can still do it without wrecking Windows. Just run the installer and tell it to only format your existing Ubuntu partition. Obviously, it's even more important to back up before trying this plan.

---

### Post by seismicmike on 2006-09-20
Thanks, I shall give it a whirl.

---

### Post by seismicmike on 2006-09-20
Yeah, I guess I didn't think of it before... It would make since that you wouldn't have to re-install the OS completely b/c that would mean losing your files each time there was a new release. Thanks :)

---

### Post by al_sharpe on 2006-09-21
Hello Seismicmike:

You will lose your home directory if you reinstall ubuntu

It is always a good idea to install your home directory on
a separate partition from /

then you can do as skymt suggests.

I second his idea to back up your home directory files to a
cd rom to reinstall later.

good luck, should be no problems.

Al

---

### Post by seismicmike on 2006-09-21
so far so good... I just need to check windows now to see if I broke anything

---

