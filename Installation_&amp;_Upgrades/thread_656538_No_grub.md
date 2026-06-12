---
title: "No grub"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by beero1000 on 2008-01-02
When my computer boots, it doesn't show the grub screen. from the bios screen it goes black for a few seconds and then it goes to the ubuntu loading screen. I can't see grub. I think it is there, but just not displayed, because when i press ctrl-alt-f1, it stops the loading and waits, but I can't see any command line.

I've searched the forums and tried every fix, but its still not working.

I'm starting from a fresh install of ubuntu 7.10.

Please help.

Thanks,
Michael

---

### Post by zvacet on 2008-01-02
Press ESC and you will see grub.

---

### Post by tgilber1 on 2008-01-02
Previous post has a point.  If you see ESC, then press the ESC key, which will get you to the GRUB menu.  The line below assumes that you do not see anything.

You could try checking out a couple things in your menu.lst, splash & timeout.  

1.  Try booting up with Ubuntu cd into rescue mode to get to root prompt.  
2.  Mount the appropriate partitions (e.g., /boot, /, etc.)
3.  Make a copy of the menu.lst for a backup before editing (e.g., cp /boot/grub/menu.lst /boot/grub/menu.lst.yourbak
4.  Verify the timeout is set to 3 for three seconds using pico/nano/vi
5.  Remove the splash portion from the kernel line closest to the top.
6.  Save changes
7.  Reboot
8.  Hopefully, you should see the grub menu.  The very least, you should no longer have the splash, which will allow you to view bootup process.
9.  Post error messages during bootup if further assistance is required.

---

### Post by beero1000 on 2008-01-02
when i push escape, the bootup stops and stays there with a black screen.

I tried editing my menu.lst, and still no grub, and no bootup process either, just a blank screen for a few seconds followed by the ubuntu loading bar and then it loads fine into ubuntu.

still working on it. I think it probably has something to do with my video card (ati x700).

any other advice?

Thanks

---

### Post by tgilber1 on 2008-01-02
After you press ESC, try pressing <ENTER> key to see if computer continues booting.

---

### Post by beero1000 on 2008-01-03
> **tgilber1 said:**
> After you press ESC, try pressing <ENTER> key to see if computer continues booting.

yes, after pressing escape the computer waits, and then after pressing enter it continues booting, all with a black screen.

---

### Post by tgilber1 on 2008-01-03
Try taking a look at the info from a previous forum contribution:

[http://ubuntuforums.org/showthread.php?p=1541970](http://ubuntuforums.org/showthread.php?p=1541970)

It sounds like you may need to change your console resolution - card may not be able to handle default resolution.  Nice little tutorial explaining how resolution setup works during bootup.

---

