---
title: "Apt-Get asking me to insert Ubuntu install disk?"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by s0c0 on 2005-06-07
Sometimes when I install an application over apt or aptitude (haven't tried w/ synaptic) I will be prompted to insert my Ubuntu disk?  This is no problem really.  I'd just like to understand this a bit better.  Thanks.

---

### Post by kb00heda on 2005-06-07
Just a wild guess on my behalf, but maybe you haven't commented out the CD source from your apt source list, i.e., /etc/apt/source.list? I did that after my Ubuntu install, if I remember it correctly.

However, you say "sometimes", and I think this would apply always, so I'm not sure this is it.  :-?

---

### Post by Seti on 2005-06-07
Have a look at your /etc/apt/sources.list. At the top of the file you will see the following:
"deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted"

So to change this do:```
sudo gedit /etc/apt/sources.list
``` 

and comment this like out with a hash mark (#).

Now apt will ignore the cdrom as a source.

---

### Post by Seti on 2005-06-07
ah you beat me to it! :smile:

---

### Post by kb00heda on 2005-06-07
I just about did...! But you put it down better and more precise than me.  :)

---

### Post by az on 2005-06-07
The confusion comes from the fact that the installer caches a lot of packages from the cd onto your harddrive (/var/cache/apt/archives)

When you need a package, it will install it from there instead of from the internet or your cd.  If you clean your cache, then you will start to be prompted for the cd again.

There is nothing wrong with freeing up the space.  the tradoff is that you have to either get the stuff from the net (by deleting the repository in the list, as mentioned) or find your cd whenever you want to install one of those particular packages.

---

### Post by andlinux21 on 2005-06-09
[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]Thanks for the info I was wondering why I had to always grab the CD.[/COLOR][/SIZE][/FONT] ](*,)

---

### Post by s0c0 on 2005-06-13
This fixed it, thank you guys!

---

### Post by Russellkhan on 2005-06-27
Hi there,

I thought I'd resurrect this thread since my problem is very closely related to the subject matter covered. 

I also got the pop in the cd request (in my case, from aptitude)  and I couldn't find my cd so I tried commenting out the line about the cd from /etc/apt/sources.list . But then when I tried again to install, the package I wanted (epiphany-browser) couldn't be found. It doesn't even make sense that there would be any packages on the cd that aren't in one of the repositories - how would such a package get updated?

So, I searched around, found my cd, popped it in the drive, uncommented the line in sources.list and ran aptitude update. It asked me to run apt-cdrom to get the cd recognized again, so i did, but it was looking for it at /cdrom/ and my cdrom drives are mounted at /media/cdrom0/ and /media/cdrom1/ . I found how to tell apt-cdrom where my cd was, and now it's recognized, but I can't seem to get aptitude (or apt-get, I tried that too - and checked the man pages for both) to look anywhere besides /cdrom/ for a cd. 

My preference would be to use the online repositories only, but if that's impossible, I would like to be able to install from the cd. Can anyone clue me in to what to do for either of these problems?


Just in case it's relevant, here's the non-commented lines from my sources. list:
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

```

Thanks for any help!

---

