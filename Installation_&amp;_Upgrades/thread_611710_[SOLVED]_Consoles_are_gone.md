---
title: "[SOLVED] Consoles are gone"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by x1a4 on 2007-11-13
Hi,

After upgrading to Gutsy my consoles are gone, yet according to ps the gettys are running.  

When I boot with the previous kernel the consoles show up but X is blank.  It is running but I get a blank screen, and when I run startx I get a message the server is already running on display :0.  

How do I fix this?

Thank you.

---

### Post by x1a4 on 2007-11-29
Anyone?  :?

---

### Post by juve on 2007-12-28
Could you fix it yet?

I have the same problem. And i had it before in feisty, but i don't know when they vanished.

I just upped to gutsy and it didn't help

---

### Post by x1a4 on 2007-12-30
> **juve said:**
> Could you fix it yet?

I have the same problem. And i had it before in feisty, but i don't know when they vanished.

I just upped to gutsy and it didn't help

No.  Though after a recent kernel update they came back, but with a huge font.  and my X servers became blank.  I now reverted back to Feisty and things work just fine.  Try this:  

reboot, and when you get GRUB's boot menu, select the kernel you want to boot and press **e** to edit the menu entry.  add**vga=ask** to the kernel options, hit ENTER then **b** to boot.  When you get a menu of available console sizes type **scan** (and hit ENTER) then select a value from the menu.   This should bring your consoles back up.  Once you know which size you want, edit your /boot/grub/menu.lst file to set **vga=** to the value you want.

---

### Post by x1a4 on 2008-01-26
I ended up doing a fresh Gutsy install and the consoles were visible but again with a huge font.  Turns out that Gutsy has the VESA frame buffer disabled by default.  I wrote [this HOWTO]("http://hex1a4.net/xubuntu/howto.php?htid=02") explaining I enabled it

---

