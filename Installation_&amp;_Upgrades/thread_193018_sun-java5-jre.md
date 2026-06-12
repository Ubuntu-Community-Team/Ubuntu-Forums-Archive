---
title: "sun-java5-jre"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by craftbrewer on 2006-06-09
My problem is that sun-java5-jre does't even show up in Synaptic. Add/Remove Programs tells me there's no resource. I have all the binary & source Multiverse repos enabled on a fresh install of Ubuntu 6.06.

I saw a thread that speculated it wouldn't last long in the multiverse... has it been removed?

I'm new to Ubuntu, but not Debian. I've previously installed Sun's RPM package using alien on other distros. Would this be a safe method to use on Ubuntu?

My new MediaServer's gonna be pretty lame without my MusicIP Mixer! :)

---

### Post by John.Michael.Kane on 2006-06-09
sun-java5-jre is in Libraries multiverse

---

### Post by craftbrewer on 2006-06-09
[QUOTE=SD-Plissken]sun-java5-jre is in Libraries multiverse[/QUOTE]

Note mine.  See [http://ubuntuforums.org/showthread.php?t=191852](http://ubuntuforums.org/showthread.php?t=191852) 

I don't seem to be the only one with this problem.

---

### Post by John.Michael.Kane on 2006-06-09
Use my source list.  

```
**sudo gedit /etc/apt/sources.list**

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

**Then run sudo aptitude update**
 
```


Heres a screenshot: [[IMG]http://img70.imageshack.us/img70/7863/screenshot2du.th.png[/IMG]](http://img70.imageshack.us/my.php?image=screenshot2du.png)

---

### Post by craftbrewer on 2006-06-10
Thank you!  I now have sun-java5.jre available to me.

Curiously enough I initially just tried removing "ca." from my sources as suggested in the other thread, but this did not work either.

---

### Post by John.Michael.Kane on 2006-06-10
craftbrewer your welcome. please post should you have any other problems.

---

### Post by thriftee on 2006-07-01
Thanks a milion.  Spent 5 hrs looking for and trying solutions trying to get java installed for firefox.  I'm surprised its not just a click the box type install. 

Had to do one other thing to get the plugin working after changing the sourcelist, etc as suggested above...  The link below shows how to link the plugin to firefox.

[http://www.ubuntuforums.org/showthread.php?t=199498&highlight=install+java+plugin+firefox](http://www.ubuntuforums.org/showthread.php?t=199498&highlight=install+java+plugin+firefox)

---

