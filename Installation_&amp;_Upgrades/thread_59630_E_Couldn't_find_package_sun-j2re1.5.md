---
title: "E: Couldn't find package sun-j2re1.5"
date: 2005-08-24
forum: Installation &amp; Upgrades
---

### Post by simple on 2005-08-24
for some reason sun-j2re1.5 isn't found in the repository.. here's my sources.list
> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Multiverse repositories
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary multiverse

## Hoary Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security multiverse


---

### Post by Koba on 2005-08-24
[QUOTE=simple]for some reason sun-j2re1.5 isn't found in the repository.. here's my sources.list[/QUOTE]
 [www.ubuntuguide.org](www.ubuntuguide.org) the Guide is your friend :) use the repositories.

---

### Post by jasmuz on 2005-08-24
I recommend you change the mirrormax backports servers to these:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

save and close, sudo apt-get update

(ive heard there is an issue about that package, but im sure it must be resolved alredy)

---

### Post by simple on 2005-08-24
[QUOTE=Koba][www.ubuntuguide.org](www.ubuntuguide.org) the Guide is your friend :) use the repositories.[/QUOTE]
um, okay thanks? now mind helping me with my problem.

---

### Post by simple on 2005-08-24
[QUOTE=jasmuz]I recommend you change the mirrormax backports servers to these:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

save and close, sudo apt-get update

(ive heard there is an issue about that package, but im sure it must be resolved alredy)[/QUOTE]
tried those backports before.. and why not, tried again.. same thing

---

### Post by simple on 2005-08-24
you can delete this thread if you want? i tried searching google and found nothing so automatically assumed it wasn't addressed.. used the forum search function and used bored2k's little howto for simply building your own package.. i'll post the link and what he said to do.. 
[http://ubuntuforums.org/showthread.php?t=59229&page=2&pp=10&highlight=jre-1_5_0_04-linux-i586.bin](http://ubuntuforums.org/showthread.php?t=59229&page=2&pp=10&highlight=jre-1_5_0_04-linux-i586.bin)
> Originally Posted by bored2k
Okay just forget about the Backported Java and build yer own ! It's just as easy.

1. [https://sdlcweb2d.sun.com/ECom/ECom...6B](https://sdlcweb2d.sun.com/ECom/ECom...6B) F462B33D27F
2.
Download Linux self-extracting file jre-1_5_0_04-linux-i586.bin 15.83 MB
3.
sudo apt-get install fakeroot java-package
4.
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
5.
sudo dpkg -i *.deb (whatever the newly Sun- DEBian package is named)

---

### Post by mellem on 2005-08-25
I've got the same problem with sun-j2re1.5. The "problem" isn't solved, because if you browse the servers ([ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) and  [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/)) one can clearly see that the  package isn't there. Must have been removed for some strange reason. The updates are there though, for what that is worth........

---

### Post by sbassett on 2005-08-25
Untrue. At least for the mirrormax.net source. It is under hoary-extras restricted. I have been having the same problems, also with acroread 7. I have downloaded a few of the debs myself to install. But that is what apt-get is for. It seems to ignoring the backports and hoary-extras, at least portions, for some reason. This is very odd behavior. If anyone has an answer for this one, please share.

Please see:
[Link to sun j2re](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update04_i386.deb)

---

### Post by mellem on 2005-08-25
You're so right. My mistake.   :---)
But now I have absolutely no idea what's wrong.

---

### Post by theGerbil on 2005-08-28
Folks,

Don't know why it isn't working but Just browse on over to:

[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/)

download

sun-j2re1.5_1.5.0+update04_i386.deb

and install it with dpkg -i 

Found it today and it works a dream with both Mozilla and Firefox browsers.

Good luck!

theGerbil

---

### Post by PokerFacePenguin on 2005-08-28
[QUOTE=simple]you can delete this thread if you want? i tried searching google and found nothing so automatically assumed it wasn't addressed.. used the forum search function and used bored2k's little howto for simply building your own package.. i'll post the link and what he said to do.. 
[http://ubuntuforums.org/showthread.php?t=59229&page=2&pp=10&highlight=jre-1_5_0_04-linux-i586.bin](http://ubuntuforums.org/showthread.php?t=59229&page=2&pp=10&highlight=jre-1_5_0_04-linux-i586.bin)[/QUOTE]


bored2k's solution worked like a charm for me as well.......except i had to go to the sun website and accept their agreement before i could download their software.  

have another cup on me bored2k  :)

---

### Post by plumcreek on 2005-09-19
[QUOTE=sbassett]Untrue. At least for the mirrormax.net source. It is under hoary-extras restricted. I have been having the same problems, also with acroread 7. I have downloaded a few of the debs myself to install. But that is what apt-get is for. It seems to ignoring the backports and hoary-extras, at least portions, for some reason. This is very odd behavior. If anyone has an answer for this one, please share.

Please see:
[Link to sun j2re](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/sun-j2re1.5_1.5.0+update04_i386.deb)[/QUOTE]

It may have been there when you posted, but it's gone now.

---

