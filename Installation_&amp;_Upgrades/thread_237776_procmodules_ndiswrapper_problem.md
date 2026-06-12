---
title: "/proc/modules ndiswrapper problem"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by Kyle12 on 2006-08-16
I'm trying to troubleshoot my wireless card and I keep getting an error when attempting to run this line in Terminal: "sudo rmmod ndiswrapper" and Terminal outputs: "ERROR: Module ndiswrapper does not exist in /proc/modules." After checking the modules file I found that the entire file is completely blank. I just installed from a Live CD and attempted to connect to my router and it didn't work, sometimes using an Ethernet cable will work. My Wireless connection isn't available through System --> Administration --> Networking. I'm using this tutorial: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-2d0c63404ca00426255ef1158a8afffc67925ef6](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-2d0c63404ca00426255ef1158a8afffc67925ef6)

I've tried most of the tutorials on this forum that have to do with setting up my Broadcom wireless card, and I'm wondering if Ubuntu is worth all this configuration if my card will work at all. Somehow I got my wireless card working once but then I reformatted my harddrive because I couldn't get the card to work again (and because I modified some system files). My laptop is a Dell Inspiron B130. 

Thanks to anyone who can help me out!

---

### Post by zxee on 2006-08-16
I don't know if there's a signicant difference between the howto you posted to this one; [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
but maybe it's worth a shot? 
There are a lot of posts in the networking forum on problems with broadcom. 
I know it doesn't help you any but broadcom apparently isn't interested in providing info to the open source community.

---

### Post by Kyle12 on 2006-08-16
Thanks for the link, I'll definitely try this tomorrow! 

Thanks again, zxee. 

> I know it doesn't help you any but broadcom apparently isn't interested in providing info to the open source community.

I was going to say the same in my first post... ;)

---

