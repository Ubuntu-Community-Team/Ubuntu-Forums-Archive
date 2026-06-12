---
title: "Ubuntu 10.10 / Windows 7 dual boot"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by Replay345 on 2011-04-13
Hi,

I installed Ubuntu 10.10 on my system first, partitioned the drive & installed Windows 7. As usual the Windows 7 boot loader over-writes Grub2.

I have re-installed Grub2 so when I now reboot I boot into Ubuntu - can someone tell me how to update Grub2(?) so I have the option to boot into Windows 7? 

I have done some Googling but not entirely sure what steps I should take exactly!!

Many thanks,

Nick

---

### Post by Dutch70 on 2011-04-13
I'm not sure if it will fix it or not, but to upgrade grub, open a terminal & run the following command.
```
sudo update-grub
```

You may find some useful info here...
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I did a quick google search for "fix windows after installing grub" and got some good links.

---

### Post by Replay345 on 2011-04-13
I don't need to update Grub, just need to know what file I need to add lines to so Windows 7 is bootable?

---

### Post by Replay345 on 2011-04-13
ok I have:


gedit /boot/grub/menu.lst

& added

title Windows 7 (Loader)
root (hd0,3) 
savedefault
makeactive
chainloader +1

This hasn't worked (I still boot straight into Ubuntu)

My partitions look like this:

/dev/sda1 - ext4 (Ubuntu)
/dev/sda2 - nfts (boot)
/dev/sda3 - ntfs (Windows 7)

etc etc

This is why I chose root (hd0,3)?

Any help appreciated...

---

### Post by jwcalla on 2011-04-13
There is no menu.lst file for GRUB2... that's for the previous version of GRUB.

It should be that when you run sudo update-grub it runs an os-prober script (located in /etc/grub.d) that finds other OSes and adds them to the GRUB2 configuration file in /boot/grub/grub.cfg.

---

### Post by Replay345 on 2011-04-13
Thanks, I did the update & it detected Windows7 like you said. Now I have a lovely menu on startup with options for Ubuntu/Win7

You don't know how long I've been trying to do this for.... :P

---

### Post by jwcalla on 2011-04-13
Cool.  Now you can get to work on customizing your GRUB2 boot screen with colors and a wallpaper background.  ;)

---

### Post by Replay345 on 2011-04-13
> **jwcalla said:**
> Cool.  Now you can get to work on customizing your GRUB2 boot screen with colors and a wallpaper background.  ;)

Thanks for the suggestion, I might just do that!

New to Ubuntu (obviously) & am really looking forward to learning a new OS - could you give any advice of how to increase my knowledge, where to start first etc? 

Cheers,

Nick

---

### Post by jwcalla on 2011-04-13
Nick,

You can do a Google search for "things to do after installing ubuntu" and there are a variety of articles people post for commonly installed applications.  Some you might find useful and interesting, and others not so much.  Some articles are outdated.

Another thing is to search for ubuntu or gnome (if you're using gnome) customizations to see what you can do if you'd like to branch out beyond the vanilla look.

webupd8.org is a good place for the latest ubuntu news, to keep oneself up to speed.

And this forum is great for finding out answers and solutions to problems.

Hope that helps some... hopefully others will chime in!

John

---

