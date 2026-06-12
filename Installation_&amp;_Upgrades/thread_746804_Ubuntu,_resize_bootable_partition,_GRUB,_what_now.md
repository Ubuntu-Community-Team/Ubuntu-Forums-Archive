---
title: "Ubuntu, resize bootable partition, GRUB, what now?"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by oduartix on 2008-04-05
Cheers everyone,

I've got two issues that are raising a lot of questions for me and I would appreciate all the help you can give:

This is my partition map:
[IMG]http://farm3.static.flickr.com/2078/2390672315_44b1c3ab84_o_d.jpg[/IMG]
(sorry for making this a JPEG, I'm not sure if PNG would preview on this page)

Issue 1
About Disk2
I've got excited with Ubuntu 7.10 a few days ago and downloaded a whole load of stuff. The thing was I filled the 4GB system partition so much I couldn't login.
After solving that issue I decide it was time to give it some more space (another 4GB). 
I got Acronis Disk Director 10 (on Windows) to work and took those 4GB from /home (part #7), moved the swap (part #6) forward and as I was getting ready to resize **root** (part #5), I got the message you see on the picture, saying I will have to perform some additional operations to boot from Ubuntu, after the resize process.
Q1) Will Ubuntu boot after the resize?
Q2) Is the boot diskette mentioned the Installation CD or is it something I'll have to create?
Q3) I'm using Grub. Will it still be there even if Ubuntu doesn't boot? How do I make a Linux partition bootable in Grub?

Issue 2
When I installed Ubuntu I had some repeated labels for drives/partitions between Disk1 and Disk2.
I think I had two named **Windows** and 2 named **Storage.**
Ubuntu didn't automatically make mount points for some of them.
Q4) Is it because their partition numbers (1 and 5) are repeated between disks 1 and 2?
Q5) Can  Acronis Disk Director 10 (or any other tool) help solve that, and won't it break anything on Ubuntu?

Thank you for any help.

---

