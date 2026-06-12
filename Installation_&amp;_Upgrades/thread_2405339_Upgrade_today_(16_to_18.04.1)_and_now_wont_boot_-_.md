---
title: "Upgrade today (16 to 18.04.1) and now wont boot - Pentium i386"
date: 2018-11-04
forum: Installation &amp; Upgrades
---

### Post by ccx-junk on 2018-11-04
My install did an auto update today - it complained a little about partial packages - but the install completed.
Now my Pentium 2 machine boots and I get the Orange screen, (and initially the mouse was an X) - but now theres no mouse pointer.
I tried installing the NVidia graphics drivers via the terminal (after a suggestion from earlier this year) - no avail.

Obviously I can get to the terminal via Ctrl-Alt-F1.

How can I repair this ?
I looked for a i386 image of Ubuntu 18.04 - but aparently there isnt one...

Any all help appreciated - but at the moment the machine is pretty dead - terminal only.

---

### Post by ccx-junk on 2018-11-05
Update :
ive run apt update/upgrade a few times and rebooted many.

apt says 460 packages can be upgraded, and when I list them many appear related to the python3.. But not many that make much sense in terms of bionic beaver (e.g Unity schema/settings).

im back at the point where I see the beaver on the orange screen, and the mouse pointer as an X

any ideas what I can do next ?

---

### Post by Impavidus on 2018-11-05
A release upgrade gone wrong can be very hard to fix. You may want to consider a fresh install. I assume you've got backups of all your important files, right?

There is indeed no live disk of 32 bit Ubuntu 18.04 or newer. It's assumed that any computer that can run Ubuntu 18.04 can run 64 bit. 32 bit 18.04 is still available as one of the lighter flavours, as an upgrade from a previous release or from the minimal installer. You didn't give a complete overview of your hardware, but it may be just too old to run Ubuntu 18.04.

---

### Post by ccx-junk on 2018-11-05
thanks for the response.

The majority of the issue is when I do a apt-get-dist-upgrade  I get a host of these errors : could not resolve @gb.archive.ubuntu.comA

Im happy to do a clean install - but where do I find the i386 ISO for 18.04.1 ?  the isos seem to be AMD only.

PS my bad - but I have a Pentium 4 - and yes it can run 64 bit &#8230;.
Am I daft, and there are no 18.04 i386 ISO's ? Do I have to get a 16.04 LTE (32 bit) and re-run all the updates for days ?

---

### Post by Impavidus on 2018-11-06
There is a 32 bit installer for Ubuntu 18.04. Look for the [minimal network installer](https://www.ubuntu.com/download/alternative-downloads#network-installer). It's however not a live disk. Alternatively, you can pick one of the lighter flavours, like [Xubuntu](https://xubuntu.org/). They have a different look and are lighter. A Pentium 4 is pretty old, so that may be better anyway.

How much memory does that computer have?

---

### Post by kurt18947 on 2018-11-06
I agree with Impavidus, consider a 'lighter' version. Xubuntu is pretty well regarded though some consider the UI "old fashioned" which it sort of is. I have a small Xubuntu install to play with and it is lighter than Ubuntu. I'd think Xubuntu on a P4 machine with reasonable DRAM - a couple GB or more - should run okay.

---

### Post by mastablasta on 2018-11-07
AMD64 = 64bit iso = i686

it's named AMD because AMD was the first to use the 64bit technology. it was then in all repos and packages and it stayed. not sure who will win the 128bit naming.

if it can handle 64bit you can just install it over the current install (just don't select to erase the disk).

---

