---
title: "Updating system"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by christooss on 2005-05-08
WhenUpdate manager notifys me that there are new updates avalible. I click on the icon in tray. And then befor new updates are shown it writes soething like:"Some packages cannot be updated... you can update them with apt get dist-upgrade." Then he list two packages

libxvidcore4
mplayer-386

When I run apt-get dist upgrade there are still those two packages unchanged.

How can I update those packages. Or remove them forum list of Unchanged packages

Thanks for the anwser

---

### Post by clb137 on 2005-05-08
hi,

have you added the extra repositries in your etc/apt/sources.list?


clinton

---

### Post by christooss on 2005-05-08
Xes I did backports and marillat

---

### Post by clb137 on 2005-05-08
hi,

have you tried apt-get install the packages on there own, one at a time?

---

### Post by Gandalf on 2005-05-08
[QUOTE=christooss]Xes I did backports and marillat[/QUOTE]
 don't add marillat, it's a bad bad idea to add debian repository unless you need a specific package from there,
here's my sources.list, put it as yours and  you will be fine
```

# ubuntuforums.org backports
deb http://backports.ubuntuforums.org/backports hoary-backports-staging main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

# debian marillat, stable, testing and unstable, must not uncomment
#deb ftp://ftp.nerim.net/debian-marillat/ stable main
#deb ftp://ftp.nerim.net/debian-marillat/ unstable main
#deb ftp://ftp.nerim.net/debian-marillat/ testing main

# wine repository
#deb http://wine.sourceforge.net/apt/ binary/
#deb-src http://wine.sourceforge.net/apt/ source/

# ubuntu repository, must not be commented
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse


# rox desktop repository
#deb http://www.janw.easynet.be/rox/ i386/

```

---

### Post by christooss on 2005-05-08
Just one more question. If I install hoary server installation and then instal x org and then change repositories to debian one. is there any problems in changing. Will I breake my system. I ask this beacause debian do not have x.org supported?

---

### Post by Gandalf on 2005-05-08
[QUOTE=christooss]Just one more question. If I install hoary server installation and then instal x org and then change repositories to debian one. is there any problems in changing. Will I breake my system. I ask this beacause debian do not have x.org supported?[/QUOTE]
 why the heck you want to do such thing, debian debs are not *completely* compatible with ubuntu don't you ever update ubuntu with debian repository

---

### Post by christooss on 2005-05-08
OK I wont do it. Now tell me how to install mozilla firefox without installing package ubuntu-desktop

---

### Post by Gandalf on 2005-05-08
[QUOTE=christooss]OK I wont do it. Now tell me how to install mozilla firefox without installing package ubuntu-desktop[/QUOTE]
 sudo apt-get install mozilla-firefox

---

### Post by christooss on 2005-05-08
khm I know that but there are some packages which has to be installed and ubuntu-desktop is one of them

---

### Post by nilus on 2005-05-08
I had the same problem, but with apt-get dist-upgrade i resolved.

This is my sources.list, if can helps you:
> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

---

### Post by christooss on 2005-05-08
My problem resolved with Gandalfs sources.list

Nilus: I had sourec.list like yours only with backports insluded. Now with Gandalfs reposotories list every thing works fine.

---

### Post by Gandalf on 2005-05-08
[QUOTE=christooss]My problem resolved with Gandalfs sources.list

Nilus: I had sourec.list like yours only with backports insluded. Now with Gandalfs reposotories list every thing works fine.[/QUOTE]
 in fact those are bored2k repository :D

---

### Post by christooss on 2005-05-08
Can I copy this repositories list from internet. I would like to wget them.

---

### Post by Psquared on 2005-05-08
[QUOTE=Gandalf]in fact those are bored2k repository :D[/QUOTE]

I noticed in your sources.list that you have commented out the rox-filer repo. Do you have rox-filer installed? Are you having any problems with it?

---

### Post by Gandalf on 2005-05-08
[QUOTE=Psquared]I noticed in your sources.list that you have commented out the rox-filer repo. Do you have rox-filer installed? Are you having any problems with it?[/QUOTE]
 well i was trying to install it but this repository is not available anymore :( couldn't find one

---

### Post by Gandalf on 2005-05-08
[QUOTE=christooss]Can I copy this repositories list from internet. I would like to wget them.[/QUOTE]
 what do you mean??? you want a ready sources.list file???

---

### Post by christooss on 2005-05-09
I mean that there is a page [www.something.com/sources.list](www.something.com/sources.list) with this sourcefile.list

---

### Post by Gandalf on 2005-05-09
[QUOTE=christooss]I mean that there is a page [www.something.com/sources.list](www.something.com/sources.list) with this sourcefile.list[/QUOTE]
 i don't know what is your purpose of this but here you go
```

wget http://www.siemens-mobiles.org/ubuntu/sources.list

```

---

### Post by christooss on 2005-05-09
Thanks. This is exatclly what I need.

---

### Post by Psquared on 2005-05-09
[QUOTE=Gandalf]well i was trying to install it but this repository is not available anymore :( couldn't find one[/QUOTE]

Here's where you can get it. Note all the dependencies. I had to install the *-dev versions of most to get it to install.

I have a problem with a broken link that I can't seem to fix so if you go about installing it I'd like to know if you have the same problem.

[http://rox.sourceforge.net/phpwiki/](http://rox.sourceforge.net/phpwiki/)

Scroll down a bit and you will see that you can just install the file manager (rox-filer) or the entire package which includes a cool looking DE.

I just installed rox-filer, but when it starts I get an error which says:

> Failed to create symlink '/home/peyre/.icons/ROX':
File exists

(this may mean that the ROX theme already exists there, but the 'mime-application:postscript' icon couldn't be loaded for some reason)


Rox-filer runs, but all I get are default icons. (yield signs with questions marks) See what happens when you install it.

---

### Post by Gandalf on 2005-05-09
well i wait then for the repository to get back

---

### Post by Psquared on 2005-05-09
[QUOTE=Gandalf]well i wait then for the repository to get back[/QUOTE]

It's in the repositories - it might backported, but its there. I had the same problem with that version though ..... that is why I installed from source.

---

### Post by Gandalf on 2005-05-09
[QUOTE=Psquared]It's in the repositories - it might backported, but its there. I had the same problem with that version though ..... that is why I installed from source.[/QUOTE]
 well apparently they are back, when i tried, [http://www.janw.easynet.be/rox/](http://www.janw.easynet.be/rox/) gives 404 now it gives an explination page, i will try tonight 10x

---

### Post by Psquared on 2005-05-09
Cool - would you post your results back here so I can see what's up with my version?

thanks. :D

---

### Post by Gandalf on 2005-05-09
[QUOTE=Psquared]Cool - would you post your results back here so I can see what's up with my version?

thanks. :D[/QUOTE]
 ok no problem i will begin right away

---

### Post by Gandalf on 2005-05-09
ok i installed it, went into XFCE session, ran rox-filer but i don't find the imortance of this package :) what it is good for?

---

### Post by Psquared on 2005-05-09
[QUOTE=Gandalf]ok i installed it, went into XFCE session, ran rox-filer but i don't find the imortance of this package :) what it is good for?[/QUOTE]

I fixed the problems I was having.  :grin: 

Its just another file manager like Nautilus, Konqueror and XFFM. However, you can install the entire package called rox-sessions which is an entire DE separate and part from Xfce, Gnome and KDE.

It can be installed as a "zero install" or as a full-blown DE. The zero install version downloads the programs from the internet and puts them in your cache so they start very fast after the first time. You need a broadband connection.

It's just eye-candy really, but it is based on a different premise than the other DEs. As I understand it you can download a program called "wrapper" which will allow you to run your other apps like gimp, OpenOffice, etc. that are already installed.

I like the rox-filer manager because it fully supports drag and drop and other features.

---

