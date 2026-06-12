---
title: "synaptic and skype?"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by furunculus on 2005-06-28
hello all, maybe i am a bit dumb but i cannot install the debian package from the skype site, but i keep getting some bizarre message about a missing .lib file, or some such nonsense.

so my question is; does this synaptic doo-dangle have a skype package lurking in some far away repositiory that it will cleverly auto-install for me?

cheers

---

### Post by mingus on 2005-06-28
Here is how to get it . . .

[http://ubuntuguide.org/#skype](http://ubuntuguide.org/#skype)

While you are there, highly advisable to check out this guide, you will undoubtedly have reason to come back to it

Also note that while Ubuntu shares an architecture and toolset with Debian, it doesn't follow that all .deb packages are interchangeable.  Packages are often compiled for a particular distribution, and will not necessarily work on another.

In the guide, look for "extra repositories".  That will get you to all the Ubuntu deb's.  In the case of skype, you are getting a an "unofficial" deb that was created by the community for Ubuntu.

---

### Post by GazaM on 2005-06-28
furunculus, the .deb package on the skype website works fine with ubuntu. The most probable cause of your problem is missing libqt3, which is the Qt package skype uses for it's interface. Check it out, the lib is in synaptic. Skype should work once you have that.

---

### Post by furunculus on 2005-07-02
cool, so how do i get this lib thingy, via synaptic, and if so how?

cheers

---

### Post by alastair on 2005-07-02
Do you see the big "search" button in Synaptic?

Try using that - type in "libqt3".

---

### Post by lotusleaf on 2005-07-06
According to this thread on the Skype forums:

["yum/apt repositories - please test"](http://forum.skype.com/viewtopic.php?t=29679) posted by 'terminus', a member of the 'Skype staff'

They now have an official Skype apt source for Skype for Linux. From the above linked post, here's the details on the apt repository:

> Using Skype's apt repository

Simply add the following line to your sources.list file (usually /etc/apt/sources.list):

```
deb http://download.skype.com/linux/repos/debian/ stable non-free
``` Now you can use apt-get update to sync to latest repository and then apt-get install skype to install Skype on your machines.

Edit: I just added it to my sources.list and it works fine.

Comments?

---

### Post by lotusleaf on 2005-07-06
[HowTo: Add Official Skype Apt Repository](http://www.ubuntuforums.org/showthread.php?t=46954)

---

