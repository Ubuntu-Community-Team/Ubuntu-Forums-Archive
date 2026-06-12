---
title: "Grub dual boot question"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by pcmikeb on 2009-12-02
When I first installed Ubuntu, it was the only OS on the computer. I recently installed Windows XP in a second partition. 

After installing XP, the computer would only boot to XP. I just now booted Ubuntu from the CD, went into Terminal and reset Grub to be the boot manager using instructions from the Ubuntu web site on how to reset Grub to be recognized on boot-up.

Now my computer boots only to Ubuntu.  There is now selection screen to make a choice as to OS to boot to.

I would like to make Grub give me a choice on booting.

Thanks for any help.

---

### Post by darkod on 2009-12-02
Which instructions did you follow exactly? Which commands did you use? Also do you know if you are using grub1 or grub2?

---

### Post by pcmikeb on 2009-12-02
My Grub version is 2.26.0. 

I started Terminal -- sudo grub -- root (hd0,0) -- root (hd0,
0)  -- setup (hd0)  -- quit

I then restarted my computer. Grub does not give OS options -- it just boots to Ubuntu.

Thanks

---

### Post by darkod on 2009-12-02
I haven't heard of 2.26.

Grub legacy (called grub1) is 0.97 and the new 1.97 is called grub2.

But anyway, you could look into /boot/grub/menu.lst file (if it exists) and add manually an entry for XP.

Otherwise, while you are booted with the Ubuntu 9.10 liveCD you can install grub2 with:
sudo mount /dev/sda1 /mnt   (replace /dev/sda1 with your / partition)
sudo grub-install --root-directory=/mnt/ dev/sda   (if you have more than one drive replace /dev/sda accordingly)

That should install grub2 which can automatically detect windows and adds it to the grub menu. If you installed ubuntu 9.10 you should have grub2 in fact. Maybe you did before those commands you tried.

---

### Post by pcmikeb on 2009-12-02
Ubuntu is running now -- on hard drive.  The version I quoted was the Gnome Terminal version ( doh!!).  I have tried Grub from the hard drive -- Also I am running Ubuntu 9.04.

Thanks

---

### Post by darkod on 2009-12-02
No problem, glad you got it working. Cheers.

---

### Post by pcmikeb on 2009-12-02
Ubuntu is running -- problem is -- I can't run Win XP ( Win XP is on dev/sda2 ) -- Grub boots directly to Ubuntu without a menu to choose OS

Thanks

---

### Post by darkod on 2009-12-02
In terminal do:
sudo gedit /boot/grub/menu.lst

If you are sure XP is on /dev/sda2 after th entry for ubuntu in menu.lst add:

title Windows XP
rootnoverify(hd0,1)
makeactive
chainloader +1

Reboot and see if it works. If when you try to open menu.lst it opens an empty (new) file that means it doesn;t exist and you are using grub2. There are different commands for that.

---

### Post by Megafag on 2009-12-02
> **darkod said:**
>  There are different commands for that, that suck.

Fixed

TS if you have grub2, which i doubt you do being as you are running 9.04, i would suggest re-doing your system starting with XP

---

### Post by pcmikeb on 2009-12-02
I must have Grub 2 -- there ware no entries in the 'menu.1st' file.

Thanks again

---

### Post by darkod on 2009-12-02
Then it's even easier. In terminal just run
sudo update-grub

It will write few entries, hopefully something like
Windows XP loader on /dev/sda2

If you see something like that, reboot and test the new entry that should be in the grub menu.

PS. It's very late here so I'm already slow. :) You can actually check your grub version by executing
grub-install -v

---

### Post by CaminoSS on 2009-12-02
I had the same type problem.
Ubuntu / Vista listed in grub menu
Installed grub2 and grub was chained to grub2
After running upgrade-from-grub-legacy
I lost my Windoze selection in grub2 menu
I used Vista to execute bootrec /fixboot then bootrec /fixmbr
which disables grub completely
I then re-installed grub from Ubuntu CD
then lose the Vista choice in grub menu
When I run update-grub2 I get:
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /windows/Boot
boot: No such file or directory
done.
The entry "ls: cannot access /windows/Boot
boot: No such file or directory"

How or where is the entry above stored? I believe
the correct entry should be /windows not /windows/Boot

any ideas?

---

### Post by darkod on 2009-12-02
The cannot access error sounds bad. It's like grub2 is not allowed to look for it.
You could always try adding manual entry for grub2. That's done in /etc/grub.d/40_custom file. Basics guide here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Scroll few pagedowns and there is sample Windows entry.

---

### Post by Megafag on 2009-12-02
> **pcmikeb said:**
> I must have Grub 2 -- there ware no entries in the 'menu.1st' file.

Thanks again

Its a .Lst not 1st

and grub2 still has one you just cant edit it.

EDIT: sorry forgot to F5

---

### Post by darkod on 2009-12-02
> **Megafag said:**
> 
and grub2 still has one you just cant edit it.



You actually can but they recommend not to edit grub.cfg directly. Although in some cases the update-grub was not able to solve the problem and directly editing grub.cfg helped. :) Of course, if you don't locate your problem on next update-grub it will change the grub.cfg back (undo your manual changes).

---

### Post by pcmikeb on 2009-12-02
I finally got gedit to edit the file correctly -- I can now boot to either OS.

Thanks for the help

---

