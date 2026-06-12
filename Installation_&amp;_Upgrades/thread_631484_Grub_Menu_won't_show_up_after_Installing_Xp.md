---
title: "Grub Menu won't show up after Installing Xp"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by LukeV on 2007-12-04
Ok so I used to have Wndows Xp and Ubuntu dual booting together. That was working fine but I recently needed to reinstall windows. So I deleted the partition using the ubuntu partition manager and I installed windows on the same partition I had it on before. But now whenever I start up my pc the Grub menu doesn't show up...instead it boots directly into xp.

Anyone know how I can get grub to show up again?

---

### Post by forestpixie on 2007-12-04
you need to reinstall grub - it can be done with the [livecd]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") or alternatively you could use [supergrub]("http://supergrub.forjamari.linex.org/") 

there are other threads in the forum - but I found the supergrub method really easy when I needed to do the same - download and burn it as an iso and boot with it

---

### Post by pratik.ac on 2007-12-04
[FONT="Georgia"][FONT="Courier New"]boot into the computer with the live cd.
fire up a terminal and give the following commands in order:-
sudo su
grub  (this gets the grub promt)
find /boot/grub/stage1
(this will return something like (hd0,x) x will be the partition number)
root (hd0,x)
(now either one out of the following commands)
setup (hd0)               ----if you want to rewrite the mbr with grub
setup (hd0,y)          --- where y is the partition where you want to install grub

now reboot and bingo your grub should be back on track :)[/FONT][/FONT]

---

### Post by LukeV on 2007-12-04
Oh man I got grub to work but when I select Ubuntu it gives me an Error 22: No such partition or something like that.

Please please please tell me this can be fixed...I had some important stuff on ubuntu:(

EDIT: Nevermind I did some research and I managed to fix the problem. 

For anyone who had the same problem:

> If you boot and select your ubuntu,hit the 'e' key and see were it's pointing to.
You changed your boot order so hd0 is hd1 now,and I'm pretty sure your ubuntu points to hd1,2)
Change this to (hd0,2) and hit the 'b' to boot.
If this works you'll have to change it permanently in your menu.lst.

Looking into your fstab to see if everything is listed as it should is the next step you'll have to take.


Don't take any notice to the specific hd references. Those are specifically for another user. Mine was hd(0,1)...found it through trial and error to be honest :P

---

