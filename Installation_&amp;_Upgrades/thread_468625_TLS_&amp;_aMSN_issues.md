---
title: "TLS &amp; aMSN issues"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by The Pinny Parlour on 2007-06-09
Hi,

Fresh install of Ubuntu on Acer laptop.  Install aMSN but won't log onto aMSN.  something about a TLS is missing, install it blah blah blah.  Go to install it but it fails:  Error installing TLS module::  Couldn't get [http://switch.dl.soundforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz](http://switch.dl.soundforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz)


Any help to get this sucker working would be great.

Cheers,

---

### Post by benevolent on 2007-06-09
hi, 

first of all install tcl/tls

```
sudo apt-get install tcltls
```


then```
sudo gedit /usr/lib/tls1.50/pkgIndex.tcl
```

and there you'll find that: 
[i]
# pkgIndex.tcl - 
#
#    A new manually generated "pkgIndex.tcl" file for tls to
#    replace the original which didn't include the commands from "tls.tcl".
#

package ifneeded tls **1.5** "[list load [file join $dir .. libtls1.50.so] ] ; [list source [file join $dir tls.tcl] ]"
[/i]

and you have to change 1.5 to 1.50:
[i]

# pkgIndex.tcl - 
#
#    A new manually generated "pkgIndex.tcl" file for tls to
#    replace the original which didn't include the commands from "tls.tcl".
#

package ifneeded tls **1.50** "[list load [file join $dir .. libtls1.50.so] ] ; [list source [file join $dir tls.tcl] ]"
[/i]

if still it doesn't connect, set manually the tcl directory(preferences -> advanced): /usr/lib/tls-1.50/pkgIndex.tcl


it works fine with me :)

---

### Post by The Pinny Parlour on 2007-06-09
Cool.  thanks that seems to get me further than before.   How does one delete the profiles as mine is all *** about face, and needs resting or deleting.  

Cheers,

---

### Post by The Pinny Parlour on 2007-06-09
I found it.

---

### Post by legrandyon on 2007-06-14
Hello,
I have feisty and I had a similar experience with amsn when I installed amsn from automatix2. The same exact failure when trying to log in. I followed the instructions posted by benevolent and it didn't solve the problem. I solved it by removing amsn with automatix2 and installing amsn with the add/remove... of ubuntu. 
Then, no problem to log in.
legrandyon

---

### Post by Koutroumpesis on 2007-06-16
> **legrandyon said:**
> Hello,
I have feisty and I had a similar experience with amsn when I installed amsn from automatix2. The same exact failure when trying to log in. I followed the instructions posted by benevolent and it didn't solve the problem. I solved it by removing amsn with automatix2 and installing amsn with the add/remove... of ubuntu. 
Then, no problem to log in.
legrandyon

1000thnx :D:D:D

---

