---
title: "Medibuntu does not download Acroread properly"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dunbrokin on 2009-03-30
Following the approach on this site:

[http://ubuntu-tutorials.com/2007/10/28/how-to-install-adobe-acrobat-reader-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/10/28/how-to-install-adobe-acrobat-reader-on-ubuntu-710/)

and substituting jaunty (or even intrepid) does not lead to the proper download of Acroread.

---

### Post by cariboo on 2009-03-30
I would suggest you go [here]("http://help.ubuntu.com/community/Medibuntu"), and follow the instructions on how to set up the Medibuntu repositories. Remember to scroll down and set up the gpg key. The instructions you followed on the page you link to have nothing to do with Medibuntu.

I just downloaded Acrobat and libdvdcss2 from Medibuntu this morning with no problems.

Jim

---

### Post by dunbrokin on 2009-03-30
Thanks, that worked after a fashion.....I got much further....but now when I try to download a pdf from the web, FF just hangs half way through downloading.

---

### Post by happy_pig on 2009-04-15
Did an update yesterday and after all the other packages went through I got the following message

E: /var/cache/apt/archives/acroread_9.1.0-7jaunty1_i386.deb: trying to overwrite `/usr/share/man/man1/acroread.1.gz', which is also in package acroread-debian-files

Is this a partial upgrade and I should wait or is there something else I should do to either remove and start again or fix this?

Thanks in advance

---

### Post by dunbrokin on 2009-04-15
This is a new bug and is documented - see Launchpad for a work around.

---

### Post by FuturePilot on 2009-04-15
> **happy_pig said:**
> Did an update yesterday and after all the other packages went through I got the following message

E: /var/cache/apt/archives/acroread_9.1.0-7jaunty1_i386.deb: trying to overwrite `/usr/share/man/man1/acroread.1.gz', which is also in package acroread-debian-files

Is this a partial upgrade and I should wait or is there something else I should do to either remove and start again or fix this?

Thanks in advance

I ran into that too. I had to remove all acroread and related packages and then install the acroread_9.1.0 package again after completely removing the others.

---

### Post by rburkartjo on 2009-04-15
i did it like this in terminal first

ray@ray-desktop:~$ apt-get autoremove acroread

then ran in terminal

ray@ray-desktop:~$ sudo aptitude full-upgrade

this installed the newest version of acroread

---

