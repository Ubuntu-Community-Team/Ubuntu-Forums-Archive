---
title: "Hardy x86 alternate CD doesn't recognize keyboard"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by armitage1337 on 2008-05-03
Hi,

I'm trying to upgrade one of my computers to Ubuntu Hardy x86, using the alternate install CD. However, when I boot up the CD, the keyboard is not recognized. I've never had this problem with an Ubuntu CD/install before, and I've been using Ubuntu on this computer since Dapper. It's a ~6 year old HP Pavilion desktop, using a PS/2 keyboard. Any ideas?

Thanks in advance for the help!!!

---

### Post by armitage1337 on 2008-05-04
Any ideas? I still can't figure out what's going on. When I boot into Gutsy on the computer, everything's fine. But the Hardy alternate CD won't work.

---

### Post by rosciol on 2008-05-04
I've got the same problem with the alternate install CD for Hardy; my keyboard works fine in Gutsy and *after* the Live CD for Hardy initializes (but not in the first screen for selecting language).  I can't use the alternate install CD because of this problem, which is making it very difficult to set up any of the more advanced options I'm hoping for.

Any ideas what might be wrong?  I poked around in my Bios for any relevant USB settings, having seen that someone solved it by disabling legacy USB support, but no BIOS changes helped me out so far.

Thanks.

---

### Post by armitage1337 on 2008-05-05
Well, since this computer is old and I can't use the Ubuntu Live CD, I instead used the Xubuntu Live CD, which had a timeout, and that allowed for X to load, in which the keyboard worked. I was able to install it that way, and it's working fine now. I just left it with XFCE for now, but you could definitely just remove xubuntu-desktop and replace it with ubuntu-desktop, if you wanted to.

---

### Post by daemmon on 2008-05-05
after upgrading to gutsy my keyboard stopped working - i downloaded the live-cd and got the same problem. my solution was to change the keyboard layout to another language, by modifying xorg.conf from under windows

---

### Post by armitage1337 on 2008-05-06
Could you change it back after that and still have it work?

---

