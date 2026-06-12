---
title: "installing grub again"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by mrblondeisback on 2008-03-18
I run a dual boot system, Ubuntu and XP on two separate hdds, so I can still game.  Windows, in typical fashion, has gone all haywire on me again, and I had to reinstall. But since my master boot record was on that hdd, Grub doesn't come up and I can't get to my linux drive.  Just goes straight to windows now.  Is there a way I can just install grub again so I can get to it?  The alternative cd lets you jump around in the install process is it possible to just do that?

---

### Post by dstew on 2008-03-18
To reinstall grub, from the Live CD terminal enter ```
sudo grub
```This gets you the grub command line, with the **grub>** prompt. At the grub prompt, enter ```
find /boot/grub/stage1
```This will give you the name of the Linux partiton in grub-speak. Whatever it returns, use as the argument in the grub root command:```
root (hd1,0)
```Then, install grub into the MBR of the first disk, then quit:```
setup (hd0)
quit
```Quit the live CD and reboot. You should get your grub menu back. If not, post back and we can work on it a bit more.

EDIT: If you only have an Alternate Install CD, I am not sure how to get a grub prompt. There probably is a way. But, you can always make and use a [grub boot floppy]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy") to reinstall grub.

---

### Post by mrblondeisback on 2008-03-18
Thank you for the help.  I did find the way to do it with the alternative cd as well, it's somewhat easier, under the rescue mode you can just reinstall grub.  How do I mark this thing solved?

---

### Post by Taino on 2008-03-19
> **mrblondeisback said:**
> How do I mark this thing solved?

[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") ya go. :)

---

### Post by Herman on 2008-03-19
> I did find the way to do it with the alternative cd as well, it's somewhat easier, under the rescue mode you can just reinstall grub. Cool! :cool:

In case anyone else wants to know how to re-install GRUB using the 'Alternate' CD, here is a link, [                                                                         Re-install GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub") with the Alternate CD Rescue mode.

Regards, Herman :)

---

