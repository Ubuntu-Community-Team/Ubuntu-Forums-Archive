---
title: "Jaunty repo's"
date: 2008-10-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ibizatunes on 2008-10-31
I know this is early but does anyone know when will the repo's will be opened?

---

### Post by plun on 2008-10-31
Well, I can see a few packages now.....:)

[https://lists.ubuntu.com/archives/jaunty-changes/](https://lists.ubuntu.com/archives/jaunty-changes/)

I havent checked if those are build or not at Launchpad/Ubuntu.

---

### Post by plun on 2008-10-31
Test string....:)

```
 sudo sed -e 's/\sintrepid/ jaunty/g' -i /etc/apt/sources.list 


```


```
sudo apt-get update && sudo apt-get dist-upgrade

```

404....:^o:

```
sudo sed -e 's/\sjaunty/ intrepid/g' -i /etc/apt/sources.list 
```

---

### Post by int on 2008-10-31
opennnn

```
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted multiverse universe
```

---

### Post by plun on 2008-10-31
Well, rather funny...  :tongue:

"Most stupid install"  :confused:

[[img]http://ubuntu-pics.de/thumb/5053/stupid_GRSYZ3.jpg[/img]](http://ubuntu-pics.de/bild/5053/stupid_GRSYZ3.jpg)

[-X

---

### Post by plun on 2008-10-31
Well, I have home on a separate partion and also backups....

Here we go...

> plun@plun:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu jaunty (development branch)"


[IMG]http://ubuntu-pics.de/bild/5055/nuts_hu8Rwi.jpg[/IMG]

---

### Post by smartboyathome on 2008-10-31
Not gonna be much difference between Jaunty's and Intrepid's repos at this point, so no use upgrading imo.

---

### Post by plun on 2008-10-31
> **smartboyathome said:**
> Not gonna be much difference between Jaunty's and Intrepid's repos at this point, so no use upgrading imo.

Well.. FREE software should be tested ....:lolflag:

I dont know if I survive a reboot... tomorrow adventure.:-D

"The concrete" is nevertheless removed in Windows 7....:twisted:

So the challenge is clear for Jaunty...

---

### Post by Eclipse. on 2008-10-31
Your kidding.:s

Jauntys repo is open already.

The intrepid repo didnt open for weeks after hardy was released.

---

### Post by UbuWu on 2008-10-31
The new toolchain and stuff is just getting uploaded. It will take a little longer for real updates to begin, some preparation is needed. It looks like it is going a lot faster than for intrepid though.

---

### Post by autocrosser on 2008-10-31
Done & Ready for new toys!!!!

---

### Post by BCurtisWX on 2008-10-31
VM's work wonders

---

### Post by Mazza558 on 2008-11-01
Right - that's it! I'm going in for Jaunty! Bleeding edge, here I come!

---

### Post by amano on 2008-11-01
They should integrate Luke Yelavich's pulseaudio branch as soon as possible to get lots of testing from the beginning of the cycle on.

And they should add the cruft-remover to ubuntu-standard again for the same reasons (and btw p7zip-full should be added to ubuntu-standard as well since many fileroller features depend on that since GNOME 2.24 - I will file a bug on that).

That would be some cool ideas to start the jaunty cycle.

---

### Post by autocrosser on 2008-11-01
Do you know if the new GDM will "finally" be up during this cycle? I've seen enough to really want to try it ;)

---

### Post by amano on 2008-11-01
I think that the new GDM will be the default one for the new gnome. Fedora is shipping it for some time already.

So it would be a good idea to upgrade to it NOW to  get it strong testing for the whole cycle as well.

---

### Post by autocrosser on 2008-11-01
+3 on the new GDM for testing!!!!

---

### Post by Gina on 2008-11-01
OK so where can I find the Jaunty ISOs, please?  They don't seem to be on the chromium server I've been using with an rsync script to update my Intrepid ISOs for testing.

---

### Post by plun on 2008-11-01
> **autocrosser said:**
> +3 on the new GDM for testing!!!!

And a +  from me....  MacSlow was working on this.

Maybe to visit GDMs trunk...:)

[http://live.gnome.org/GDM](http://live.gnome.org/GDM)

---

### Post by jpeddicord on 2008-11-01
> **Gina said:**
> OK so where can I find the Jaunty ISOs, please?  They don't seem to be on the chromium server I've been using with an rsync script to update my Intrepid ISOs for testing.

You can't and wont be able to get them for some time. The jaunty repository was just activated, and packages take a while to be uploaded. The first alpha ISO will probably be in a month or two.

---

### Post by ronacc on 2008-11-01
> **Gina said:**
> OK so where can I find the Jaunty ISOs, please?  They don't seem to be on the chromium server I've been using with an rsync script to update my Intrepid ISOs for testing.

the toolchain isn't even up yet and the 1st alpha isn't due for 3 weeks .
[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

---

### Post by Gina on 2008-11-01
Thank you - I think I got the wrong impression.  I didn't really expect to have anything in Jaunty to test just yet :lolflag:

---

### Post by plun on 2008-11-01
> **Gina said:**
> Thank you - I think I got the wrong impression.  I didn't really expect to have anything in Jaunty to test just yet :lolflag:

Well you have...   lsb-release output...:popcorn:

Also a new C library...useful:lolflag:

---

### Post by jnw222 on 2008-11-02
repos are up?

toolchain isn't due for 4 days and intrepid was released only 4 days ago or so?


goes to consider upgrading or wait till alpha1

---

