---
title: "[SOLVED] why doesn't chroot(ing) work as it used to?"
date: 2008-11-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mdurham on 2008-11-17
Hi, With prev distros, I used to be able to "sudo chroot /media/sda2 su" and do an "apt-get update" etc. But it doesn't work any more. Is there any other way of updating a distro on another partition without resorting to rebooting? What's changed?
Cheers, Mike

---

### Post by RAOF on 2008-11-17
I can't answer any of those questions without more information about what doesn't work.  What *happens* when you try to chroot to your other root?  Don't be afraid of posting too much information; too much is almost always better than not enough!

---

### Post by mdurham on 2008-11-17
> **RAOF said:**
> I can't answer any of those questions without more information about what doesn't work.  What *happens* when you try to chroot to your other root?  Don't be afraid of posting too much information; too much is almost always better than not enough!

Hi RAOF, here's what happens
> mike@intrepid-8:~$ sudo chroot /media/sda2 su
root@intrepid-8:/# apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_AU
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_AU
  Could not resolve 'archive.ubuntu.com'
.
.
.
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_AU.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_AU.bz2)  Could not resolve 'archive.ubuntu.com'
.
.
.etc

---

### Post by caljohnsmith on 2008-11-17
It looks like you might have a networking DNS problem, because the error is that it couldn't resolve host "archive.ubuntu.com". Can you ping archive.ubuntu.com? While you are chrooted, try:
```
ping archive.ubuntu.com
```
I'm guessing that won't work. I think it would help if you set up a better chroot environment first:
```
sudo mount --bind /dev /media/sda2/dev
sudo mount --bind /proc /media/sda2/proc
sudo mount --bind /sys /media/sda2/sys
sudo chroot /media/sda2 /bin/bash
```
Try that and see if it helps. And of course make sure your internet connection is working fine too by trying the ping command first. Let me know how it goes. :)

---

### Post by mdurham on 2008-11-17
> **caljohnsmith said:**
> It looks like you might have a networking DNS problem, because the error is that it couldn't resolve host "archive.ubuntu.com". Can you ping archive.ubuntu.com? While you are chrooted, try:
```
ping archive.ubuntu.com
```
I'm guessing that won't work. I think it would help if you set up a better chroot environment first:
```
sudo mount --bind /dev /media/sda2/dev
sudo mount --bind /proc /media/sda2/proc
sudo mount --bind /sys /media/sda2/sys
sudo chroot /media/sda2 /bin/bash
```
Try that and see if it helps. And of course make sure your internet connection is working fine too by trying the ping command first. Let me know how it goes. :)

> root@intrepid-8:/# ping archive.ubuntu.com
ping: unknown host archive.ubuntu.com
root@intrepid-8:/# 


Looks like you are right caljohnsmith. It's strange as it always worked before. I'll try the other stuff that you reccomended and see how that goes. My Internet connection is fine by the way, I'm using it to write this!
Cheers, Mike

---

### Post by mdurham on 2008-11-17
Tried you suggestion caljohnsmith, here's the result.
> mike@intrepid-8:~$ sudo mount --bind /dev /media/sda2/dev
mike@intrepid-8:~$ sudo mount --bind /proc /media/sda2/proc
mike@intrepid-8:~$ sudo mount --bind /sys /media/sda2/sys
mike@intrepid-8:~$ sudo chroot /media/sda2 /bin/bash
root@intrepid-8:/# sudo apt-get update
sudo: unable to resolve host intrepid-8
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
  Could not resolve 'archive.ubuntu.com'
E

---

### Post by caljohnsmith on 2008-11-17
Have you tried pinging archive.ubuntu.com outside of the chroot environment? Let me know if that works or not.

---

### Post by mdurham on 2008-11-17
> **caljohnsmith said:**
> Have you tried pinging archive.ubuntu.com outside of the chroot environment? Let me know if that works or not.
Yes it works fine.
> mike@intrepid-8:~$ ping archive.ubuntu.com
PING archive.ubuntu.com (91.189.88.40) 56(84) bytes of data.
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=1 ttl=42 time=344 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=2 ttl=42 time=341 ms
64 bytes from dresche
as a point of interest, can you chroot and apt-get update?

---

### Post by caljohnsmith on 2008-11-17
OK, how about when you are in the chroot environment do:
```
cat /etc/resolv.conf
```
I'm guessing that doesn't show your DNS hosts, or does it? You'll want to compare that with the same file outside of your chroot environment. If your chroot resolv.conf file is empty, maybe simply copying over the one outside of the chroot environment first before doing your chrooting will solve the problem. Let me know how it goes.

---

### Post by mdurham on 2008-11-17
caljohnsmith, as a point of interest, can you chroot and apt-get update?

---

### Post by caljohnsmith on 2008-11-17
> **mdurham said:**
> caljohnsmith, as a point of interest, can you chroot and apt-get update?
I've never actually run "apt-get update" in a chroot environment, but I've run many programs and even GUI applications successfully from a chroot environment, so I think it's possible. Did you try checking your resolv.conf file? Or are you thinking maybe it's not worth the hassle to pursue it further at this point? :)

---

### Post by autocrosser on 2008-11-17
Interesting--I just tried it & it won't work in my system either---

Both targets are Jaunty installs--The one I'm in right now is a "fresh" Intrepid with all Jaunty updates & the one I tried to chroot is my old testing install--fresh install during the Intrepid Beta phase...

Tried both the way I've always used: sudo chroot /mnt/name of the drive & then I tried pinning everything as per the prior post---still no go...a ping gives the same:

root@linux:/# ping archive.ubuntu.com
ping: unknown host archive.ubuntu.com

Both systems are current as of Sat evening & there are no internet problems whilst logged in them....

I'll boot my baseline Hardy install & try the chroot from there--will post back soon.

---

### Post by mdurham on 2008-11-17
thanks caljohnsmith, copying resolv.conf fixed it.
That's great, now I can update Jaunty in the background whilst doing other errr... important work.
Thanks again. Mike

---

### Post by caljohnsmith on 2008-11-17
> **mdurham said:**
> thanks caljohnsmith, copying resolv.conf fixed it.
That's great, now I can update Jaunty in the background whilst doing other errr... important work.
Thanks again. Mike
That's great news, glad it worked. Cheers and hope Jaunty works well enough for you. :)

---

### Post by smartboyathome on 2008-11-17
I had this problem, to fix it you need to bind your network file to the chroot. I had to do something like:
```
mount --bind /etc/resolv.conf /path/to/chroot/etc/resolv.conf
```
Try that.

---

### Post by psusi on 2008-11-17
> **smartboyathome said:**
> I had this problem, to fix it you need to bind your network file to the chroot. I had to do something like:
```
mount --bind /etc/resolv.conf /path/to/chroot/etc/resolv.conf
```
Try that.

You can't bind mount individual files -- only directories.

---

### Post by smartboyathome on 2008-11-17
I said I had to do something like that, maybe I copied that file to the chroot instead of mounted, I can't remember. Sorry. :(

---

### Post by autocrosser on 2008-11-17
Interesting--looks like network manager now custom-edits the file every time--I don't remember having this problem in Hardy (last time I needed to chroot to fix a broken install)---must have come in with the new version....

---

### Post by mdurham on 2008-11-19
> **autocrosser said:**
> Interesting--looks like network manager now custom-edits the file every time--I don't remember having this problem in Hardy (last time I needed to chroot to fix a broken install)---must have come in with the new version....
That's right, /etc/resolv.conf always gets emptied, what's that all about?

---

### Post by xebian on 2008-11-19
> **mdurham said:**
> caljohnsmith, as a point of interest, can you chroot and apt-get update?

Definitely.  But be aware you get some warnings/error because the hooks sometime stop and then re-start some processes/daemons.  dpkg would abort because of the errors so configurations would be half done, but will be completed once you boot it and do an update/upgrade again.

---

### Post by mdurham on 2008-11-19
> **xebian said:**
> Definitely.  But be aware you get some warnings/error because the hooks sometime stop and then re-start some processes/daemons.  dpkg would abort because of the errors so configurations would be half done, but will be completed once you boot it and do an update/upgrade again.
How does it work for you and not for me? As I said in a previous post my /etc/resolv.conf gets emptied somehow. Doesn't yours?
Cheers, Mike

---

### Post by xebian on 2008-11-19
> **mdurham said:**
> How does it work for you and not for me? As I said in a previous post my /etc/resolv.conf gets emptied somehow. Doesn't yours?
Cheers, Mike

I wish I know. :)

But these are what I know for my system.  This file resolv.conf is always updated everytime I boot, and stays that way until the next boot.  I confirmed this when I chrooted to it.  My system is behind a router, and my ISP DNS server ip addresses are hardcoded in my router which are then what my resolv.conf has.  Also, not sure if this matters, I don't have firewall.  My router takes care of that.  Hope this might help.

---

### Post by plun on 2008-11-19
Yes, I can also confirm it... I am there... :)

Pricechilds old manual works

[http://ubuntuforums.org/showthread.php?t=306424](http://ubuntuforums.org/showthread.php?t=306424)

About resolv.conf in the end...

BUT..... PackageKit brakes apt when chrooting (if installed).

Use a hammer to repair my GRUB....:evil:

---

### Post by mdurham on 2008-11-19
> **xebian said:**
> I wish I know. :)

But these are what I know for my system.  This file resolv.conf is always updated everytime I boot, and stays that way until the next boot.  I confirmed this when I chrooted to it.  My system is behind a router, and my ISP DNS server ip addresses are hardcoded in my router which are then what my resolv.conf has.  Also, not sure if this matters, I don't have firewall.  My router takes care of that.  Hope this might help.
Thanks for that xebian, I was just curios. It's not worth worrying about I guess.
Cheers, Mike

---

### Post by super.rad on 2008-11-19
I've made a bash script for chrooting into ubuntu as it's something I do a few times a day for updates
```
#!/bin/bash
mount --bind /dev /media/Ubuntu/dev
mount --bind /proc /media/Ubuntu/proc
mount --bind /sys /media/Ubuntu/sys
cp /etc/resolv.conf /media/Ubuntu/etc/resolv.conf
chroot /media/Ubuntu
```
Never had any problems using that

---

### Post by mdurham on 2008-11-19
> **super.rad said:**
> I've made a bash script for chrooting into ubuntu as it's something I do a few times a day for updates
```
#!/bin/bash
mount --bind /dev /media/Ubuntu/dev
mount --bind /proc /media/Ubuntu/proc
mount --bind /sys /media/Ubuntu/sys
cp /etc/resolv.conf /media/Ubuntu/etc/resolv.conf
chroot /media/Ubuntu
```
Never had any problems using that
That's what I do too but without the 'mount --bind' stuff, why is that necessary? It works fine without it.

---

### Post by smartboyathome on 2008-11-19
> **mdurham said:**
> That's what I do too but without the 'mount --bind' stuff, why is that necessary? It works fine without it.

It is necessary because without it, the chrooted system doesn't have access to the kernel, dev, and system files, which can lead to many programs breaking.

---

### Post by psusi on 2008-11-19
> **mdurham said:**
> That's what I do too but without the 'mount --bind' stuff, why is that necessary? It works fine without it.

You can do without the --bind on the proc and sys, but not on dev.  proc and sys don't take a device to mount so you can mount a new instance as many times as you want, wherever you want, and the contents will always be the same.  /dev on the other hand, is a tmpfs, so if you mount another instance, you get an empty separate filesystem, rather than connecting the /dev in the chroot to the real one.

---

