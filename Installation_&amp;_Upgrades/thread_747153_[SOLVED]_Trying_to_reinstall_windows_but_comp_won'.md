---
title: "[SOLVED] Trying to reinstall windows but comp won't boot disc!"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by Fzang on 2008-04-06
I want to format/kill/wipe/remove whatever, EVERYTHING from my harddisc, then install a fresh windows vista back on it (I'll get to learn linux when I have the time)

But linux won't let me boot from vista CD! It just turns on normally

What do I do??

---

### Post by Pumalite on 2008-04-06
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Delete everything in your HDD. Then make one large partition of your whole HDD, formatted ntfs. Then install Vista.

---

### Post by wjp.reg on 2008-04-06
go into the CMOS and change the setting to CD boot; make sure you have a bootable CD/DVD

---

### Post by Fzang on 2008-04-06
EDIT: wjp, I could run the ubuntu install CD, so I should be able to boot this as well? Or not? Tell me how I do it otherwise if this is different from ubuntu CD

EDITEDIT: never mind, found out how to change mirror

---

### Post by Pumalite on 2008-04-06
That too.

---

### Post by Fzang on 2008-04-06
Okay, the CD is ready and it's working

What do I press in the menu? There's a whole lot of stuff to choose

---

### Post by Pumalite on 2008-04-06
Try 'autodetect' first, and then follow the list until you are able to boot.

---

### Post by Fzang on 2008-04-06
Gotcha :)

CD is booted up and I'm inside this menu that shows

ext3
linux-swap
ext3
extended
linux-swap

What do I do to delete all of it and install windows?

---

### Post by Pumalite on 2008-04-06
Click on each one and press 'Delete. One you have deleted everything, the whole HDD will appear gray as 'free space'. Then click on it again and go to Partitions and make 'New of your whole HDD, formatted ntfs.

---

### Post by Fzang on 2008-04-06
It asks me on the left side:

Free space preceeding (MiB)
New size (MiB)
Free space following (MiB)

[v] round to cylinders

My disc has a total size of 149,06 GiB (gigabit? Don't know how many bytes that is, but I asume it's 120 or so)

Now what do I put in the three options?

---

### Post by Pumalite on 2008-04-06
When you click on 'free space' and go to 'Patitions'>'New', you will have an amount established with the maximum of your drive. All you have to do is choose the format; ntfs in this case.

---

### Post by Fzang on 2008-04-06
Done! :KS

How do I exit the program? Some kind of special procedure?

EDIT: Clicked on APPLY and chose it to shut down, now it's stuck at some wall-of-tekst blackscreen, what do I do? Wait?

---

### Post by Pumalite on 2008-04-06
There is an icon on the bottom to exit.

---

### Post by Fzang on 2008-04-06
I restarted

When I try run vista CD it says



GRUB loading stage 1.5.

GRUB loading, please wait...
Error 22



What do I do??

---

### Post by Pumalite on 2008-04-06
You didn't delete your entire HDD. Check the documentation of Gparted Live CD. Or use DBan and then Gparted: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by Fzang on 2008-04-06
So, after I ran that autonuke thing, do I run Gparter once again? Or can I go directly to vista?

---

### Post by Pumalite on 2008-04-06
You have to format the HDD ntfs.

---

### Post by Fzang on 2008-04-06
Thanks for your awesome help! I hope I can take it from here

If not, this post will rise to the top of the page again

---

### Post by SunnyRabbiera on 2008-04-06
well what is so hard about linux though?
what is making you want to go back to that virus ridden OS for?
if you needed to help you should have asked, you cant just use something and expect it to work miracles in a week.

---

### Post by Fzang on 2008-04-06
I will buy some RAM for my stationary computer and learn how to use linux there

I don't have time to use it on my laptop because I need it for school, tomorrow and I need some specific windows programs. But once I learn how to use it properly (sorry, but it seemed a bit complicated when you first switch from windows) I'll try put it on my laptop again

Hope I didn't hurt your feelings:KS

---

### Post by Pumalite on 2008-04-06
Good luck.

---

### Post by Fzang on 2008-04-06
The autonuke says 4 hours remaining:-&

Why is it being this slow? I already wiped 99% of the files from the disc?

---

### Post by Pumalite on 2008-04-06
That's 'nuke' for you.

---

### Post by Fzang on 2008-04-07
Yet again, I need help...

I ran nuke thingie, then Gparted and formated as MSDOS then ntfs

Now computer won't boot vista CD, it just hangs on a black screen with a flashing underscore in the corner

What do I do? Is the CD defect or is there another option?

EDIT: I've checked the vista CD and it works on this computer, but on the other computer (the cleaned one) it doesn't work, however, ubuntu live CD seems to be working

---

### Post by Fzang on 2008-04-07
Bump

Any solutions?

---

### Post by andahunter on 2008-04-07
cant u just format the disk get in linux Gnome partition editor in applications>add or remove> all avalable softwares and search for gnome partition editor :D

---

### Post by andahunter on 2008-04-07
oh and u need a Bootable cd, that was the problem with my xp cd when i tried 2 have dual booting, set in bios 2 boot from cd, bios>advanced>first boot device :D

---

### Post by Fzang on 2008-04-07
Are you saying the vista CD will only boot **inside** an OS? Like, different from the ubuntu CD, which will boot whenever you put it in?

---

### Post by Fzang on 2008-04-07
I'm getting ubuntu then and see how it works out

Thanks for your support anyways :)

---

