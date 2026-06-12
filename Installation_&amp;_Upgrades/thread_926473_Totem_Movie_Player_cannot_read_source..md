---
title: "Totem Movie Player cannot read source."
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2008-09-22
I was trying to play a rented DVD film with the Totem Movie Player but, I got the message that it cannot read from source.  I tested other DVD's and got the same results but, it did play a free mp4 film downloaded from the Internet Archive.

I found postings in Forums which guided me to Medibuntu. I read the restrictions, (which don't apply), and the instructions, and downloaded and installed the recommended libraries, but the DVD still won't play.

The recommended libraries are:libdvdcss2, libdvdread3 and libdvdnav4.  I am using Ubuntu 8.0.4.  What am I missing?  Thanks in advance.

---

### Post by Partyboi2 on 2008-09-22
have you got ubuntu-restricted-extras installed?

---

### Post by ineuw on 2008-09-22
> have you got ubuntu-restricted-extras installed?

the ubuntu-restricted-extras are installed.

---

### Post by ineuw on 2008-09-22
I installed vlc and all the related extensions and now this works fine.  So, for the time being, I am going to use vlc.

Thanks for the replies.

---

### Post by Drakkor on 2008-09-22
Got this from cj100570 on another thread,and it worked for me ! :)

Do a restart after issuing the following commands.

sudo aptitude install libdvdcss2
sudo /usr/share/doc/libdvdread3/./install-css.sh

---

### Post by vladan.b on 2009-09-04
> **Drakkor said:**
> Got this from cj100570 on another thread,and it worked for me ! :)

Do a restart after issuing the following commands.

sudo aptitude install libdvdcss2
sudo /usr/share/doc/libdvdread3/./install-css.sh

This worked for me too.  Thanks!

---

