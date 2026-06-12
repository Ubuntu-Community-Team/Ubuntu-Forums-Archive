---
title: "Problem w/ Dapper Beta 2 ?"
date: 2006-05-29
forum: Installation &amp; Upgrades
---

### Post by dr_d on 2006-05-29
Hey lads...

I just installed a fresh copy of dapper beta 2... I must say I'm pretty impressed with the graphical install.

The thing is, I've edited my sources.list to include backports, multiverse, etc... but I seem to be having some strange problems installing packages.

I was able to install unrar (the non free version) no problems, but I can't seem to install any media player :( 

My media player of choice is VLC, here's the error I got when I tried to apt-get it:

```

Reading package lists...
Building dependency tree...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  vlc: Depends: libdc1394-13 but it is not installable
       Depends: libdvdnav4 (>= 0.1.9) but it is not installable
       Depends: libdvdread3 but it is not installable
       Depends: libgsm1 (>= 1.0.10) but it is not installable
       Depends: libid3tag0 (>= 0.15.1b) but it is not installable
       Depends: libmad0 (>= 0.15.1b) but it is not installable
       Depends: libmodplug0c2 (>= 1:0.7-4.1) but it is not installable
       Depends: libmpcdec3 but it is not installable
       Depends: libxml2 (>= 2.6.24) but 2.6.23-1ubuntu5 is to be installed

```

The only players I've ever used are: VLC, windows media player and itunes. (and winamp that time there was a memory corruption vulnerability in it :))

So as you can see I really dont want to move to some other player... In any event, I'd heard that MPLAYER is decent, so I tried to apt-get it and got almost identical errors.

Is this a problem with dapper beta 2? beta 1 was working fine...

Please help me lads - I have a dual boot config and I've been spending so much time in windows it's sending me insane.

Cheers!

---

### Post by dr_d on 2006-05-29
I just realised this is in the breezy upgrade section..

Can an admin please move my post to the dapper section?

Thanks

---

### Post by Metro on 2006-05-29
I'm using this sources.list:

> ## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free

## Skype
# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

Try it:)

---

### Post by dr_d on 2006-05-29
heyy it worked! now i can listen to my music again.

i have no idea what was wrong with my previous sources.list, but come to think about it, i don't really care.

thanks buddy.

---

