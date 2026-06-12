---
title: "Painfully slow internet under 10.04"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by charco83 on 2010-04-04
Running 10.04 on my Samsung NC10 and the net is painfully slow for browsing.  Presuming this to be related to IPV6 I looked into disabling but this appears to be different to previous version (no aliases file).

Can someone advise on a solution?  Don't particularly wish to return to Windows but can't take slow internet browsing!

---

### Post by LADmaticCA on 2010-04-05
I too would love to see this solved. I've been searching hard this weekend for a solution.

---

### Post by sixthwheel on 2010-04-05
I have not noticed any decrees in speed, with my internet.
Firefox is about the same as in Karmic, and Chromium seems a little snappier.

---

### Post by PhilGil on 2010-04-05
I had this problem when testing the 10.04 Beta.  The OpenDNS fix worked for me.  Instructions are in [this thread]("http://ubuntuforums.org/showthread.php?t=1317164"); works the same in Lucid as it did in Karmic.  [DodgeV83]("http://ubuntuforums.org/member.php?u=547250")'s post describes the command line method, [sgosnell]("http://ubuntuforums.org/member.php?u=774876")'s and my post link to OpenDNS's instructions for using the Network Manager.  You'll probably need to reboot for the change to take effect.

---

### Post by delmore on 2010-04-07
I would like to confirm that this method:

[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

Worked to boost my internet speeds running Ubuntu 10.04 Lucid Lynx Beta 1

I went from just under a Mb/s to 16 Mb/s!

---

### Post by pieface on 2010-04-08
> delmore              **Re: Painfully slow internet under 10.04**
         I would like to confirm that this method:

[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

Worked to boost my internet speeds running Ubuntu 10.04 Lucid Lynx Beta 1

I went from just under a Mb/s to 16 Mb/s!     


Worked for me thanks mate.

---

### Post by e1ektrob0y on 2010-04-08
> **charco83 said:**
> Presuming this to be related to IPV6 I looked into disabling but this appears to be different to previous version (no aliases file).


I disabled ipv6 by editing grub in 10.04. i was having DNS issues...

---

