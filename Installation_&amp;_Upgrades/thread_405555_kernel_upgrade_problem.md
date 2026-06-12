---
title: "kernel upgrade problem"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by eyekode on 2007-04-09
My system is currently running 2.6.15-27-386.

I am trying to get it to run the latest 2.6.17.11_i386 (should be installed via: apt-get install linux-generic?).

But when I run this command... nothing is installed. /boot is unchanged. No errors are generated.

Running:
% dpkg -L linux-image-generic
Just returns the copyright and changelist files.

/etc/kernel-img.conf looks sane:

do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no
postinst_hook = /sbin/update-grub
postrm_hook   = /sbin/update-grub

Also note that the upgrade manager does not tell me that my current kernel is out of date.

This system used to run 5.10.

Note the end goal is to get an SMP kernel (just upgraded to an AMD X2 and am stuck on a single proc kernel :()

Any clues?
Thanks!

---

### Post by panty31772 on 2007-04-16
Have you tried just doing a full distribution upgrade ?
 I do believe that will install the latest kernel and updated software for you . 

As far as the 686 kernel  ,From what i have been reading is that there isnt much difference in performance vs/ 386 as the specific kernels have in later releases been obsoleted by the linux-generic. 

Though as far as having multiple cores active and working i have read ways to hack that  , not 100% sure since i dont have one myself! hope this helps a bit .

You could always try to install the specific kernel via synaptic see if that works for you , just a suggestion have not done so yet myself.

---

### Post by eyekode on 2007-04-16
Well, I figured it out...
When upgrading from 5.10 to 6.x it got confused and did not mount my /boot partition.
So it installed the new kernels in the root partition (under directory /boot). I later fixed this lack-of-mounting /boot problem.

At this point the system _thought_ the modules were installed, but the files were not there. I had to purge every module individually. After that I re-installed linux-generic and it worked like a charm.

Thanks!

---

### Post by sebz2005 on 2007-04-16
Well, How do update to the latest Linux kernel 2.6.20.7?
I'm a complete newbie and that version has a specific driver that I need to run my USB DVB... uh.. thing.

---

### Post by panty31772 on 2007-04-21
Upgrade from 6.06
Method A ( official ):
Just do

```
[COLOR="Blue"]sudo aptitude update && sudo aptitude upgrade[/COLOR]
```

now that your update manager is up to date do :
```

[COLOR="Blue"]gksudo "update-manager -c -d"[/COLOR]
```

For method B (alternative ):

```
[COLOR="Blue"]sudo gedit /etc/apt/sources.list[/COLOR]
```

and replace all the dapper/edgy...etc to feisty.
You might also want to uncomment all sources ( for in case you'll need universe later )

Now this is very important
```

[COLOR="Red"]sudo aptitude update 
sudo aptitude dist-upgrade[/COLOR]
```

---

