---
title: "Installing ubuntu over debian etch (no cdrom drive)"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by H4z3 on 2007-09-17
Ok guys, My cdrom is broken and i want to install Ubuntu, I am running Debian Etch, i don't care about any of my files and things, I basically want a clean install as if i had done it from disk, Is there a simple way? Sorry if this isn't in the right place, I have searched the forum and not found any suitable answer.

Thanks

---

### Post by slira on 2007-09-17
Hi
could you get/borrow an external cd/dvd (via usb) just for the install? someone you know has one? my LG uses one of those, and it works fine...
hope you find one!
Best
slira

---

### Post by H4z3 on 2007-09-17
No i don't think i can, It would involve having to purchase one (which i can't do)

Is this the only option?

---

### Post by kellemes on 2007-09-17
Look here for options..
[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

---

### Post by Pumalite on 2007-09-17
Netbooting?

---

### Post by kerry_s on 2007-09-17
why? you would get locked into a release cycle, your applictions would get old very fast. with debian you just add the extra repos and your good to go, no need to worry about the next relese or getting the latest.

i use etch/lenny, my sources.list->

```
deb http://ftp.debian.org/debian/ etch main contrib non-free 
deb http://ftp.debian.org/debian/ lenny main contrib non-free 
deb http://www.debian-multimedia.org/ lenny main 

# su
# gpg --keyserver subkeys.pgp.net --recv-key 6A423791
# gpg --armor --export  6A423791| apt-key add -
deb http://deb.opera.com/opera/ lenny non-free 
deb http://deb.opera.com/opera-beta/ testing non-free  

deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 

# deb-src http://ftp.debian.org/debian/ etch main contrib non-free 
# deb-src http://security.debian.org/ etch/updates main contrib non-free 
# deb-src http://ftp.debian.org/debian/ lenny main contrib non-free 
# deb-src http://security.debian.org/ lenny/updates main contrib non-free 
```

---

### Post by kellemes on 2007-09-17
> **kerry_s said:**
> why? you would get locked into a release cycle, your applictions would get old very fast. with debian you just add the extra repos and your good to go, no need to worry about the next relese or getting the latest.

Rolling release is addictive isn't it?:popcorn:

---

### Post by kerry_s on 2007-09-17
> **kellemes said:**
> Rolling release is addictive isn't it?:popcorn:

if you like that sort of thing, me i prefer to install once and be done with it. using etch/lenny i'm already more up-to-date than fiesty, by the time gutsy comes out i will already be more up-to-date than that, because they just use a snap shot, it's a frozen moment in time, at the speed linux moves at, it makes no sense to live in the past. :lolflag:

---

### Post by dougfractal on 2007-09-17
I've just been reading 
Changing distribution remotely -- HOWTO
[http://www.goudkov.com/public/articles/changing_distro.jsp](http://www.goudkov.com/public/articles/changing_distro.jsp)

Although you have to create a basic textinstall.tarball. say with virtualbox for simplicity sake.

The other method I've been experimenting with is

[http://en.opensuse.org/Installation_without_CD#Installing_from_data_saved_on_your_local_machine](http://en.opensuse.org/Installation_without_CD#Installing_from_data_saved_on_your_local_machine)
1)mkdir /iso (a grub guide)
2)download iso
3)open with archive manager copy vmlinuz and initrd.gz to /iso
4)add entries to grub
5) it all gets a bit experimental from here. If you've only have one ext3 partition it might hard. I suppose you could swapoff and put the iso in a reformatted swap.

Have you thought of using a live USBdisk.
[http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/](http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/)

---

### Post by H4z3 on 2007-09-17
Yeah im in the process of trying different things, Thank you all for your input
I'm interested in kerry_s's sources list, I might try that also..

---

