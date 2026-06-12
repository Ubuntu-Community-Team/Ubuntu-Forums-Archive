---
title: "Ubuntu and Solaris 10 dual boot on x86"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by yogesh.sajanikar on 2007-04-21
I have ubuntu and would like to install Solaris 10 to coexist with ubuntu. Has anybody done this?

Any help / documentation on this is welcome!

Thanks,
~Yogesh

---

### Post by robstr12 on 2007-08-19
Hello, yogesh.sajanikar

I am trying to do this now, so that I can do folding@home (distributed computations) on Solaris 10.  In order to accomplish that, you need the GNU/Linux available to the [lxrun]("http://developers.sun.com/solaris/articles/lxrun/") utility.

I am installing Ubuntu first.  The Solaris 10 installation will overwrite the mbr (at least, as I understand it it will), but I suppose one could use the alternative Ubuntu install disk and have grub written to the / partition, and then use the gag boot loader to boot into either OS, or, just edit the menu.1st file in Solaris to get grub working for Ubuntu again.

I myself am not concerned with booting into the Ubuntu, but rather, into Solaris only, and having the Ubuntu available to me on its partition.



Kind Regards,

Robert

---

