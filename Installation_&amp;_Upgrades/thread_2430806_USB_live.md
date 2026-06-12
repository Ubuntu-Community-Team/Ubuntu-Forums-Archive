---
title: "USB live"
date: 2019-11-07
forum: Installation &amp; Upgrades
---

### Post by alek5a on 2019-11-07
Hey everyone, since my Lenovo has bios block to install Linux I'm going to use USB live, and it doesn't look bad except for not saving config, always Bluetooth on when start, and needing to download app like VLC every time I want to watch a movie &#129300;.
So what are off line download option to install in cease no Internet available. 
Like could I have VLC instalation package on memory card

---

### Post by tux-peng on 2019-11-07
Maybe running a VM like virtualBox or VMWare might be better for you or a solution like [https://distrowatch.com/table.php?distribution=kodachi](https://distrowatch.com/table.php?distribution=kodachi) or [https://www.fosslinux.com/10212/how-to-install-a-complete-ubuntu-on-a-usb-flash-drive.htm](https://www.fosslinux.com/10212/how-to-install-a-complete-ubuntu-on-a-usb-flash-drive.htm)

---

### Post by CatKiller on 2019-11-07
You might find [this](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/) useful.

---

### Post by C.S.Cameron on 2019-11-07
If you have a second USB drive you can use the first USB to do a Full install to it just as you would to an internal drive.
Safest if you disable your internal drive before proceeding, then use "Something else" when installing.

---

### Post by alek5a on 2019-11-07
Interesting, how do I disable internal drive?

---

### Post by sudodus on 2019-11-08
it depends on the computer. Please tell us about it: The **model**. I have a Lenovo that works well with Ubuntu, but some models may be more reluctant.

The straight-forward way is to unplug the internal drive, which is easy with some computers but more complicated with other computers. Watch out for static electricity, when opening the computer!

There might be a 'soft' way via the UEFI/BIOS system.

---

### Post by C.S.Cameron on 2019-11-08
If you are careful and install using "Something else" and make sure you put "/" and the boot loader on the USB, not the internal drive, you do not need to unplug the internal drive.

Your manual should cover disabling your internal drive: [https://support.lenovo.com/lk/en/solutions/ht077589](https://support.lenovo.com/lk/en/solutions/ht077589)

---

### Post by alek5a on 2019-11-09
I've got it installed side by side windows 10, I think 19.10 must have advanced to bypass Lenovo exclusivity to Microsoft.

Thanks for all prompteus responses. Glad to be back in Linux environment

---

