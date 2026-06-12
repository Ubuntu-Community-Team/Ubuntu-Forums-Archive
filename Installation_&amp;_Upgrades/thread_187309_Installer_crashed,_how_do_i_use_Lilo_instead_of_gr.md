---
title: "Installer crashed, how do i use Lilo instead of grub?"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by sk545 on 2006-06-02
The following is the bug that i am experiencing:

[https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/48105](https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/48105)

I am pretty sure its the xfs+grub bug, therefore i would like to install lilo if possible (i don't want to change filesystem types).  How do i go about this?  I am assuming that since the installer crashed at the end the rest of the system is ready to go?  Or do i have to start over?

Thanks.

---

### Post by sk545 on 2006-06-02
oops, double post

---

### Post by Herman on 2006-06-02
You will likely find it easiest to delete the install and try again.
Grub, (and probably Lilo also, I'm not sure) will need to be installed on a seperate /boot partition if you insist on using xfs filesystem. You could make the filesystem for your seperate /boot partition ext2 to be safe, but ext3 should work okay too.

if you don't want to re-install, you might be able to make a seperate /boot partition with a partitioner (GParted LiveCD), and then, install GRUB or Lilo to that.
To install Lilo or re-install Lilo, you can use similar methods as for re-installing GRUB. Since your Ubuntu system doesn't boot, you can use an old 'Breezy' install CD for that, by following the how to at the bottom of this web-page. [http://users.bigpond.net.au/hermanzone/p12.htm]("http://users.bigpond.net.au/hermanzone/p12.htm")__Be sure to scroll right to the bottom of that page, and look under the heading '[B]Install Lilo from Breezy Install CD'
[/B]You should be able to figure out how to install Lilo where you want using that how-to and adapting it a little to suit your needs. I am not sure yet if the same will work from a Dapper alternate CD, but it would be worth a try.
Regards, Herman

---

