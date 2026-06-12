---
title: "&quot;Writing GRUB to Boot Device Failed&quot; When updating to GRUB 1.99-21"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by Spice002 on 2012-09-29
I just got back to my house and found that there was an update for GRUB (to 1.99-21). Since it's a GRUB update I thought "why not" and went ahead and installed it. As it was nearing the end of the installation, it brought up Debconf where it asked me which devices I wanted to install GRUB on (see Image 1). I selected The drive and partition Ubuntu is on, but when I hit next, I got what the title says (Image 2). I don't want to simply continue, because of the warning it gives. At this point, I have absolutely no idea what to do. Any amount of help would be appreciated.

[IMG]http://i50.tinypic.com/14uuuf8.png[/IMG]
*[SIZE="2"]Image 1. Please note that the first drive on the list is a drive with a broken Windows installation that I now use as storage, and the bottom one is a drive also for storage. the Samsung drive is where Ubuntu resides (and below it is the partition for Ubuntu)[/SIZE]*
[IMG]https://lh6.googleusercontent.com/-XUc0aDYp2ys/UGdsEaB5WvI/AAAAAAAAS_A/DBxn9CMp3VI/s0/Screenshot%2Bfrom%2B2012-09-29%2B17%253A43%253A37.png[/IMG]
*[SIZE="2"]Image 2. This is the results from pressing forward from Image 1.[/SIZE]*

---

### Post by darkod on 2012-09-29
Grub2 goes to a MBR of a disk which doesn't contain numbers (number means a partition).

So, just select /dev/sdb, without the /dev/sdb1. Actually the error is only about sdb1 so I guess it already might have installed successfully on sdb.

If you are booting your computer from sdb then you will see this grub menu.

---

### Post by Spice002 on 2012-09-29
When I select just sdb, it brings a checkbox with "Continue without installing GRUB?". 
After posting, friend of mine told me to install grub from terminal (sudo grub-install /dev/sdb) and that worked without errors. But I'm not sure what do do about the Debconf window now.

---

### Post by darkod on 2012-09-29
If you installed grub2 on sda, just close the Denconf window. You can open it anytime anyway, with:
sudo dpkg --reconfigure grub-pc

You only need grub2 on one disk, and it doesn't have to be the one where ubuntu is. You have three disks, only remember where you installed it and use that disk as first boot option. That's it.

---

### Post by Spice002 on 2012-09-29
Sorry, I mistyped. It was sdb (it's been a long day). 
I just went ahead and continued. Not sure why it would do that when I could install it perfectly fine from the terminal.

---

