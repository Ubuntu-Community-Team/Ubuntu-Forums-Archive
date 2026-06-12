---
title: "VLC 1.0.0 on Hardy 8.04?"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by Neo_The_User on 2008-09-09
I have vlc 0.9.0 videolan multimedia player on Hardy but is there a way I can get 1.0 because I really don't want to get used to Intrepid Ibex. Took me long enough cracking Ubuntu 8.04 to avoid all the security paranoia around every corner.

---

### Post by tuxxy on 2008-09-09
Where did you get 0.9.0 im still on 0.8.6 here :lolflag:

---

### Post by oldos2er on 2008-09-09
> **Neo_The_User said:**
> I have vlc 0.9.0 videolan multimedia player on Hardy but is there a way I can get 1.0 because I really don't want to get used to Intrepid Ibex. Took me long enough cracking Ubuntu 8.04 to avoid all the security paranoia around every corner.

 Yes, where are you finding vlc 1.0?

---

### Post by Neo_The_User on 2008-09-12
I'm sorry for not sharing that info.

Go to System > Administration > Software Sources > Third Party Software

Add these 2 in there.

deb [http://ppa.launchpad.net/mapopa/ubuntu](http://ppa.launchpad.net/mapopa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/mapopa/ubuntu](http://ppa.launchpad.net/mapopa/ubuntu) hardy main

That is vlc 0.9 (way better than 0.8)

Latest nightly build (git)

git clone git://git.videolan.org/vlc.git

What I want:

[http://nightlies.videolan.org/build/intrepid-i386/latest/](http://nightlies.videolan.org/build/intrepid-i386/latest/)

or

[http://nightlies.videolan.org/build/sid-i386/latest/](http://nightlies.videolan.org/build/sid-i386/latest/)

but installing it through gdebi never works so I did

sudo dpkg -i (dragged in the files 1 by 1) and then messed up my entire computer and I had to re-install it because it erased libc6 and all this other stuff so it really messed it up trying to unpack it as if it was a kernel.

The order you have to install it is in this order:

libvlccore1
libvlc2
vlc_nox
vlc

---

### Post by oldos2er on 2008-09-12
"For developers who want the latest bleeding version and want to deal with tool chain problems:

[http://downloads.videolan.org/pub/videolan/vlc/0.1.99/](http://downloads.videolan.org/pub/videolan/vlc/0.1.99/)"

 The latest bleeding edge? These files are four years old.

---

### Post by Neo_The_User on 2008-09-12
oh sorry wrong link.

VLC source via Git:

git clone git://git.videolan.org/vlc.git

(use git pull to stay up to date)

---

### Post by michael37 on 2009-07-02
Resurrecting old topic.

Now that VLC 1.0.0 is nearing completion (rc4 released recently), has anyone managed to get it working on hardy?

I noticed that latest rc is available at [https://launchpad.net/~kow/+archive/ppa](https://launchpad.net/~kow/+archive/ppa) for intrepid and jaunty only.  Kow says he doesn't think it will work on hardy.

---

