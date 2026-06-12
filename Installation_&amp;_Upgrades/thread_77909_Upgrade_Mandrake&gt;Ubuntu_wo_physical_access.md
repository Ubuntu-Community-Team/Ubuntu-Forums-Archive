---
title: "Upgrade Mandrake&gt;Ubuntu w/o physical access?"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by n6mod on 2005-10-17
I have a "Dedicated Linux Server" at my local ISP. These are el-cheapo boxes hosted in their datacenter, with pre-installed Mandrake 10.0. It's a great deal, and I've had great experiences with this ISP. But...Mandrake? eeeewwwwww. ;)

So, does anyone have any bright ideas about a way to, without physical access, get this box upgraded to Breezy?

There's nothing on the box yet, so preserving data is no factor, but they're likely to charge me for their time if I blow it and they have to re-image the machine for me. (and that drops me back to Mandrake)

I'm thinking of some kind of repartition>install (what?) on new partition>boot from new partition>wipe old partition dance.

Any suggestions/wisdom/harebrained ideas are welcome, and I have a similar machine here that I could test on.

Thanks! -Zandr

---

### Post by Curufir on 2005-10-17
Hmm. Probably resize the partition it's currently running on, make a new partition in the empty space then use debootstrap to start installing ubuntu.

Sounds like fun. Good luck.

---

### Post by bluck on 2005-10-17
sounds like quite an adventure!

let us all know how it goes :)

---

### Post by T.M on 2005-10-18
If you have an empty partition then you can try this:
[http://www.underhanded.org/papers/debian-conversion/remotedeb.html](http://www.underhanded.org/papers/debian-conversion/remotedeb.html)

I upgraded my home server from work. Mandrake --> debian couple of years ago from. My server is also NAT/Firewall and  somehow debian kernel changed eth0<-->eth1 interfaces and i could not connect the machine after reboot (firewall-rules). But the machine was in working condition and after i changed the  networking setup everything was OK.

---

### Post by n6mod on 2005-10-18
Thanks for the pointer to the article at Underhanded. I think that's what I'm going to try.

I'll take copious notes, and report back if/when I make it work.

Thanks,
Zandr

---

### Post by n6mod on 2005-10-20
OK, it worked. I did a dry run on a machine that I could reach, and I'm glad I did, because I got caught out by a couple of things.

Basically, I followed the HOWTO from Erik Jacobson that's [here.]("http://www.underhanded.org/papers/debian-conversion/remotedeb.html")

There were some differences along the way, however. I'll write something proper for the Wiki this weekend, but for now I'm going to pour myself a celebratory Scotch. :cool:

A quick rundown of the diffs from the above doc:

debootstrap: You want an Ubuntu-flavored debootstrap, of course. Rather than take the time to roll an rpm, I just installed Erik's debootstrap rpm, then grabbed a current Ubuntu version from pool and manually copied the scripts over the ones from the rpm.

base-config: Ubuntu's base-config tries to run itself inside script. This didn't seem to work, but is easily bypassed by 'export BASE_CONFIG_IN_SCRIPT=0'.

LILO: Once you get apt running and are installing things, be sure to install lilo, since Ubuntu won't on its own. I suppose you could convert bootloaders while you're at it, but I had a nice howto that left me with a working LILO config. Since this is a leased server at a colo, I don't care deeply about bootloaders.

Enable root: Before you log out of the chroot the first time, set a password for root. I know it's not the Ubuntu way, but if you don't get all the bits of hostname and hosts right, you can end up with sudo broken and no way to su. 

This is one of a couple of traps that make me doubt the wisdom of disabling root, but that's a different topic. :)

Hope this helps someone...

-Zandr

---

