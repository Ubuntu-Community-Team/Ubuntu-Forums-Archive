---
title: "Synaptic: lost the original sources.list...."
date: 2004-11-10
forum: Installation &amp; Upgrades
---

### Post by troutrou on 2004-11-10
I was trying to install mplayer, searched the forum and following this thread : ttp://www.ubuntuforums.org/showthread.php?t=3691&highlight=mplayer

I modified my sources.list file.

Bad idea, when I started Synaptic, I got hundreds of errors.

Could someone please reproduce here, the original content of this file (Warty stable of course), so that I recover a clean Synaptic ?

I promise next I fiddle with a config file, I will make a copy first.... :-/

Vince.

---

### Post by ubuntu-geek on 2004-11-10
Original sources.list

> deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted


---

### Post by troutrou on 2004-11-10
Thanks Ubuntu-Geek :-)

Vince

---

### Post by anklator on 2004-11-10
u should have the old version of sources.list.old(or something similar) in /etc/apt, althought its solved check it  ;)

---

### Post by troutrou on 2004-11-10
[QUOTE=anklator]u should have the old version of sources.list.old(or something similar) in /etc/apt, althought its solved check it  ;)[/QUOTE]

Hello Anklator, well, I have no back-up file at all... I made sure that hidden files wer displayed, but still, I really only have the source.list file and that's it !  I hope my Ubuntu is not misbehaving then, should I really have that .old file ?!  :shock: 

BTW I noticed in the file, that the name of my CD is "Ubuntu 4.10 _Warty Warthog_ - **_Preview_** i386 Binary-1 (20041020)"

"Preview", I hope this doesn't mean it's an unstable version ?! I downloaded the ISO file from the Ubuntu site as I couldn't wait for my CD's to arrive in the post, so I hope I didn't download the wrong ISO !! :shock:  :-(

I think I better re-install all my Ubuntu once I get the official CD's, maybe it will cure some problems I am having....

Vince

---

### Post by wallijonn on 2004-11-10
Which only goes to prove - always do a backup / 'copy-save as' before editing a config file. You'll only be able to save it to //home/<username>

---

### Post by HiddenWolf on 2004-11-11
Hm.

Here is my sources.list.
I have added all hoary entries, so I can switch the moment I feel like it. :-)

```
#current distribution: warty
deb http://archive.ubuntu.com/ubuntu/ warty main restricted 
deb http://archive.ubuntu.com/ubuntu/ warty universe 
deb http://archive.ubuntu.com/ubuntu/ warty multiverse 
deb http://security.ubuntu.com/ubuntu/ warty-security main restricted 

#development distribution: hoary
# deb http://archive.ubuntu.com/ubuntu/ hoary main restricted  
# deb http://archive.ubuntu.com/ubuntu/ hoary universe
# deb http://archive.ubuntu.com/ubuntu/ hoary multiverse   
# deb http://archive.ubuntu.com/ubuntu/ hoary-security main restricted
```

---

