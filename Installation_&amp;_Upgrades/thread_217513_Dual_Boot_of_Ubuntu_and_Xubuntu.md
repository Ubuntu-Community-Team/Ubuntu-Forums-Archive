---
title: "Dual Boot of Ubuntu and Xubuntu?"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by jsradley on 2006-07-17
Hi all,
I have a brand new installation of Ubuntu 6.06 on drive /dev/hda, and it is working fine.

I'd like to now install a fresh copy of Xubuntu on /dev/hdb and be able to dual boot. (So I can make direct comparisons!!)

Do I need to download the "alternative" CD of Xubuntu to do this, or will the normal one update Grub on /dev/hda automatically.

Thanks
John

---

### Post by Choad on 2006-07-17
> **jsradley said:**
> Hi all,
I have a brand new installation of Ubuntu 6.06 on drive /dev/hda, and it is working fine.

I'd like to now install a fresh copy of Xubuntu on /dev/hdb and be able to dual boot. (So I can make direct comparisons!!)

Do I need to download the "alternative" CD of Xubuntu to do this, or will the normal one update Grub on /dev/hda automatically.

Thanks
John
normal one will be fine!

---

### Post by Choad on 2006-07-17
> **Choad said:**
> normal one will be fine!
oh but its not neccessary

you can simply apt-get install xubuntu-desktop and you will have an option at the login screen as to whether to use gnome or xfce :)

that way the 2 systems can share programs!

---

### Post by monergist on 2006-07-17
Yeah, no need to dual boot just use:

```

sudo aptitude update
sudo aptitude install xubuntu-desktop

```

Apparently using aptitude instead of apt-get will give you a cleaner install [i saw a thread on this the other day but can't seem to find it]

Now, just log out and at the log in screen click options and then sessions (I believe, from memory). You'll have options such as 'default', 'gnome', etc and you should have a xfce option. click on that. Log in as usual.

---

### Post by jsradley on 2006-07-18
Many thanks for those suggestions. Never occurred to be that a window manager change was all that was required.
It is Pentium III 600Mhz with 192M, so just want to see if it speeds up a bit, although Ubuntu is quite usable.
Thanks again
John
:)

---

### Post by monergist on 2006-07-18
Hope everything worked out for you :)

---

