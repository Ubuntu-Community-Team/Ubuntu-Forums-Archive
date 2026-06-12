---
title: "help install the &quot;sk98lin driver&quot; for my network"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by ddavis1086 on 2011-07-31
*       Hello and thank you in advance for any help you might send my way. 
 I have been trying for a couple of weeks now to follow a Server setup tutorial.  
 I am a "newb" and cannot for the life of me install the "sk98lin driver" for my network card. I have followed the instructions that was in the Readme file many times and installed all flavors of linux (Ubuntu server and Debian server) and am now using "debian-503-i386-CD-1.iso" which is what the tutorial is based on. I know that 503 is old but the newest versions I tried all had this same issue.
 This an older system using a Asus PC4-800 Deluxe MB and I really don't want to spend any more money on it to get a new Eithnert card. I was doing this to help myself learn more about Linux and servers being used as a Internet path from my home network to the outside world. (Which is working fine with a D-Link router and Gigabit switch).
 I have installed everything that needs to be (I think, but maybe not) and run the ./install script. 

It gets to the end and says: Your kernel version is not the same as your header version.

Here is what I have:

uname -r
2.6.26-2-686
 


 uname -a
 Linux deephaven 2.6.26-2-686 #1 SMP Wed Aug 19 06:06:52 UTC 2009 i686 GNU/Linux

In the /usr/src I have these files:

linux -> linux-2.6.26.2/
linux-2.6.26.2
linux-headers-2.6.26-2-686
linux-headers-2.6.26-2-common
linux-kbuild-2.6.26

I don't really understand what is wrong and how to fix it.

I have another question please. There is also an option to generate a patch for the "sk98lin driver". This does generate a patch but when I try to run "make menuconfig" I get this error:

scripts/kconfig/mconf arch/x86/Kconfig
file drivers/net/arcnet/Kconfig already scanned?
make[1]: *** [menuconfig] error 1
make: *** [menuconfig] Error 2

I haven't a clue what that is trying to tell me.

This is VERY frustrating and I am just about to give up on trying to do this.

Any help on this or the above post would be greatly appreciated.

Thanks,
dennis

---

