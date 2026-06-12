---
title: "'uname -r' reports different to /usr/src/linux-headers"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by kaushd on 2009-11-21
Hi All,

I'm trying to update my linux-headers to sort out a sound issue in Jaunty, but when issuing a:

```

$ uname -r
2.6.28-16-generic
$ sudo apt-get -y install linux-headers-2.6.28-16-generic libncursesw5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.28-16-generic

```

I've also tried running it with a `uname -r` instead of manually, but still the same problem. I see that /usr/src lists shows:

```

$ ls | grep linux
linux-headers-2.6.31-14
linux-headers-2.6.31-14-generic

```

Obviously these don't match with my uname output (I'm not sure if this is a problem), how can I fix this, and get them both back in snyc?

TIA

---

### Post by jim_charlton on 2009-11-21
linux-headers-2.6.31-14
linux-headers-2.6.31-14-generic
These are the header files for Ubuntu Karmic Koala 9.10.  Did you upgrade to Karmic at some point?  Do an "aptitude search linux-headers".  Are all of the packages listed?  Which ones are installed?  If you can't see the Jaunty packages, then your /etc/apt/sources.list file is not right.

---

### Post by ajgreeny on 2009-11-21
Have you installed the new kernel, but are still booting to the previous one for some reason?  As far as I'm aware the karmic kernel at release time was the 2.6.31-14 which you have as your headers, but the kernel you are actually running is the old jaunty one, so you must have done a distro upgrade online, I suspect.

Are you using legacy grub or the new grub2 to boot your system, as I think it may be legacy grub which is causing the problem. If so, I see no reason why you can not edit the /boot/grub/menu.lst file to get the new kernel version running, assuming it is actually installed, which I think it must be.

If that is the case add extra stanzas to your grub menu.lst file like this from mine.  They are just like all the others from legacy grub and in my case work faultlessly to boot karmic, even though I am still on jaunty as my main system, and karmic appears at the bottom of my menu.  You, of course, should add these stanzas to the top of your list in order to make them the default kernel.

> title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=499975f7-bef1-4de5-9b9d-da96c1bd6c9f ro   quiet splash
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

#title        Ubuntu 9.10, kernel 2.6.31-14-generic  (recovery mode)
#root        (hd1,0)
#kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=499975f7-bef1-4de5-9b9d-da96c1bd6c9f ro   single
#initrd        /boot/initrd.img-2.6.31-14-genericJust change the partition and UUID info to fit your system also, or your machine will not boot, and remove the comment marks from the recovery mode part if you still want that to show.

---

### Post by kaushd on 2009-11-21
oops...apologies, typo in my first post. I'm actually running Karmic (just upgraded - and wasn't thinking).

when I double tab when running the command I get the following options:

```

$ sudo apt-get -y install linux-headers-2.6
linux-headers-2.6                    linux-headers-2.6.31-14-generic-pae  linux-headers-2.6.31-9-rt
linux-headers-2.6.31-14/             linux-headers-2.6.31-14-server       linux-headers-2.6-486
linux-headers-2.6.31-14-386          linux-headers-2.6.31-302             linux-headers-2.6-686
linux-headers-2.6.31-14-generic/     linux-headers-2.6.31-302-ec2         linux-headers-2.6-amd64

```

none of which match the output of my 'uname -r' output:

```

2.6.28-16-generic

```

As you probably tell, I don't really know what i'm doing, but any help would be appreciated.

--edit just noticed ajgreeny's post above - i think you're on to something. I'll check that out now!

---

### Post by kaushd on 2009-11-21
excellent - thanks for posting your menu.list file. I edited, rebooted and it worked a charm.

I've now booted using the updated kernel - and can proceed trying to fix my audio!

---

