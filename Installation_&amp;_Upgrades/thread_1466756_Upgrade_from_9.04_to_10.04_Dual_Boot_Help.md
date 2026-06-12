---
title: "Upgrade from 9.04 to 10.04 Dual Boot Help"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by omegayen on 2010-04-30
Hi,

I am running dual boot with windows7 and ubuntu 9.04... am looking to update to ubuntu 10.04, was thinking a clean install is the best.

Can anyone provide any documentation for this or link me somewhere so I don't mess anything up. Thanks.

---

### Post by oldfred on 2010-04-30
Welcome to the forums. Are you thinking of keeping the 9.04 for a time and have extra space for a new install. Do you have a separate /home which is much better for either another install or replacing your existing install. If you have a separate /home how much space is your current root. My root is only about  5GB with lots of software installed as my home and data are in different partitions.

Whichever you do you will have to use manual install and specify which partition is / (root) and its format, /home (if you have one) and DO NOT format. It seems to find you current swap on its own.

I have not seen any Lucid instructions but Karmic was similar and even older instructions are not a lot different other than any reference to grub should be grub2 and be sure to use use different instructions for grub2.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by Threlkeld on 2010-04-30
Upgrading from 9.10 to 10.04 using update manager has lost me my dual boot to XP Professional, though it shows in the Grub menu. It just hangs with a blank screen.
(Toshiba Portege 200R)
Even the Ub8untu boot is odd. Nothing at all happens for about 35 seconds, then some text flashes up too fast to read, and in about another 10 seconds I get to the logon prompt. It takes about another 10 seconds to get to the desktop, so I suppose that's not too bad. But that first apparently dead pause is a bit unnerving.

And the large pointer that I had set up for my eyesight problem has reverted to tiny and won't reset at all. Makes things very difficult for me.

I guess that it's my own fault for upgrading so soon. In another 6 months I expect it will be OK. Good thing this is only a test machine. Test not too successful.

---

### Post by Threlkeld on 2010-05-03
I found that my problem could be corrected using testdisk. I followed the procedure given in
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

My pointer problem goes away if I select System/Preferences/Appearance/Visual Effects/None

---

### Post by tgpfx on 2010-05-03
> **omegayen said:**
> Hi,

I am running dual boot with windows7 and ubuntu 9.04... am looking to update to ubuntu 10.04, was thinking a clean install is the best.

Can anyone provide any documentation for this or link me somewhere so I don't mess anything up. Thanks.

try [http://www.ubuntu.com/news/ubuntu-10.04-desktop-edition](http://www.ubuntu.com/news/ubuntu-10.04-desktop-edition) and follow the upgrade notes - I first upgraded my 9.04 to 9.10, then updated 9.10 with update manager and then upgraded to 10.04 and it all went like a dream.

---

### Post by Stern Effect on 2010-05-03
Thank you [Threlkeld]("http://ubuntuforums.org/member.php?u=423597").  That fixed my dual-boot XP problem.

---

