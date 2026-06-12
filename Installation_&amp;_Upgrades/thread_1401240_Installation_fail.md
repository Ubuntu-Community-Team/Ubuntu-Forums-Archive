---
title: "Installation fail"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by 9a8sy on 2010-02-07
I just downloaded the latest version of Ubuntu and went to install it on a Pentium 4 desktop that previously had XP on it. I get the main setup screen where it allows you several options including installation. Once I select installation, it appears to be installing but then comes up with a message that includes the following: "removing gdm-guest-session" It will not do anything else and the machine appears to go into sleep mode. When I try to shut it down, it appears that the kernel had loaded. Any ideas why the normal installation isn't continuing?

---

### Post by 9a8sy on 2010-02-08
Unbelievable, a forum for ubuntu geeks and nobody has any installation suggestions for me...... Nice

---

### Post by imanewbie on 2010-02-09
we have the same problem man... what's you video card??? im gonna try swapping my video card with another one here... il keep you posted on what happens next...

---

### Post by Claus7 on 2010-02-09
Hello,

I suppose that this is a specific bug hunting karmic. I would suggest you to try another distro and see if you get the same error...

Now reading this:
[https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/449712](https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/449712)

I would try to find the guest-session-cleanup.sh and try to run it myself with root privileges and see if I would get rid of the error. In order to do so I would put in the installation cd and try to search where this file is located. 

Another thing would be to upgrade my system. Maybe there I would have some new versions of the problematic files and solve my issue (via sudo apt-get upgrade).

Regards!

---

### Post by ABW1 on 2010-02-09
Interesting! Try downloading another distro maybe and try that

---

### Post by 9a8sy on 2010-02-09
Video card is nVidia. I believe it is a 7 series. I did download and install open Suse without any issues. However it seems to be quite a bit different than Ubuntu. I'm still a novice at operation Linux on the command line.

---

### Post by 9a8sy on 2010-02-13
Does anyone know where I could find an answer to this question?? I'd really like to put Ubuntu on my PC but it isn't looking too good right now.

---

### Post by 9a8sy on 2010-02-13
Well, I figured it out so I hope everyone puts this on in their memory banks in case someone else experiences the issue. I change my video card and the problem when away.....

---

### Post by jken146 on 2010-02-13
You could try a different method of installing Ubuntu, perhaps a net-install.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

