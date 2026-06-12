---
title: "[SOLVED] install ubuntu without deleting xp"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by takayuki on 2008-07-25
Hi,

i've been using linux for about two years now and have always simply installed onto blank hard drives or full-on erased the (usually virus-infected) windows install.

but recently i was given a laptop with a fresh install of xp (but no disks).  so i'd like to install ubuntu *and* keep the xp install.

how can i install linux onto the laptop without hosing the xp install?

---

### Post by Partyboi2 on 2008-07-25
You could either [[COLOR=Blue]dual boot[/COLOR]]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") xp/ubuntu on there seperate partitions or install using [[COLOR=Blue]wubi[/COLOR]]("https://wiki.ubuntu.com/WubiGuide") which installs inside of windows.

---

### Post by Pumalite on 2008-07-25
Get Gparted Live CD and 'shrink' XP
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Right click on XP, choose 'resize' from the menu. Backup everything before you start. It takes a while.
In the 'free space', create 3 ¡New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
the rest for /home.
Install Ubuntu, go Manual and choose the already prepared partitions.

---

### Post by Potatoj316 on 2008-07-25
you could make only 2 new partitions if you want.  Your root and your swap.  Make swap about twice the size of your ram (especially if you dont have much ram) then allocate some space for your ubuntu install.  My entire ubuntu partition is 30GB but Im only using 10GB of that.  If you plan to put a lot of music/video/images then you might want more space.

---

### Post by Pumalite on 2008-07-25
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by manishtech on 2008-07-25
Just boot through Live CD and goto GNOME partition editor. There create two more partitions preferably inside extended partition. Please dont make these as primary as total no is restricted to 4.

One partition you need for installing Linux which is called root or / and other is called swap which is equivalent of pagefile of windows.
Keep the swap some 700-800MB in size and rest to / . let this partiton be sdax and swap be sday

Now while installing linux, mount sdax as / and swap will automatically detected and taken care...

---

### Post by Pumalite on 2008-07-25
Better Gparted Live CD because it works with unmounted drives/partitions

---

### Post by takayuki on 2008-07-25
Thanks to everyone for the advice.  I think I'm going to start with Partiboi2's link: [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Which is basically what manishtech said to do.

Pumalite, your advice is noted as well if the above doesn't work out.  Thanks also to Potatoj316 for the tips.

I'm going to intall ubuntu on the new laptop tomorrow. whoo hoo.

takayuki

---

### Post by manishtech on 2008-07-25
> **takayuki said:**
> Thanks to everyone for the advice.  I think I'm going to start with Partiboi2's link: [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

Which is basically what manishtech said to do.

Pumalite, your advice is noted as well if the above doesn't work out.  Thanks also to Potatoj316 for the tips.

I'm going to intall ubuntu on the new laptop tomorrow. whoo hoo.

takayuki
Please revert back even if you are successful. Your comment counts too.....

---

### Post by takayuki on 2008-12-04
...a few months later.

I'm happily dual-booting.  The instructions on the apc site were great.  They cover all the scenarios:

install linux/ubuntu with xp already installed
install xp with ubuntu already installed, etc.

Here's the link again: [how  to install ubuntu with xp already installed]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")

I hope someone else finds this link useful.

*(side note: I only use xp once a week to watch football.  i won't mention the luddite website that forces its users to use a wintel or mac box just to view its content.)*

takayuki

---

