---
title: "Upgraded to 11.04, tried to run the Live CD but stucked in 'Try Ubuntu'"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by reivann on 2011-05-01
I updated my 10.10 to 11.04 last night and when it restarted it gave me the error message: 

error:  symbol not found: 'grub_env_export'
grub rescue>

I tried to locate the grub folder and found it at (hd0,msdos6)
**set prefix=(hd0,msdos6)/boot/grub** 
 **set root=(hd0,msdos6)**

and then I both tried:

**insmod linux** 
**insmod /boot/grub/linux.mod**

However, it gave me the message:

error: symbol not found: 'grub_mm_base'


I decided to fix the grub problem using the LiveCD but I'm stucked in loading 'Try Ubuntu'. I am loading it for two hours now, and it's still not working. I used to load it for around 5-10 minutes with the same 10.10 CD. My other computer doesn't have the grub problem, but, it's also stucked in the 'Try Ubuntu' page when I tried other 10.10 Live CD. 

I have to access my files ASAP, but it seems I'm loading eternity. 

:((

Please help. A newbie here. :(

---

### Post by Mwanyoko on 2011-05-13
Having same error quad booting win xp, win 7, ubuntu 11.04 & backtrack 5.

Just after some updates and rebooting from ubuntu 11.4, i got an error: unknown filesystem 
and a command line open grubrescue>

i tried some info provided on: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

but nothing seem to solve my problem.
Now am stuck with this : 'grub_mm_base' not found

any help pls???

---

### Post by Sox_Rule on 2011-05-15
Same problem here. Installed 11.04 on sda1 with seperate home partition on sda6. Installed 10.10 on sda7. Deleted sda7 to remove 10.10 and now get the grub rescue prompt at boot. Guess installing 10.10 overwrote the mbr which I then deleted :confused:

Get the same missing symbol error as described above.

The PC is one I use for experimentation but would be nice to solve this without having to reinstall...

Or at least understand what I can do to avoid this in the future - use seperate /boot partition?

Any help would be much appreciated.

Cheers

---

### Post by Bucky Ball on 2011-05-15
> **Sox_Rule said:**
> Same problem here. Installed 11.04 on sda1 with seperate home partition on sda6. Installed 10.10 on sda7. Deleted sda7 to remove 10.10 and now get the grub rescue prompt at boot. Guess installing 10.10 overwrote the mbr which I then deleted :confused:

Deleting 10.10 from sda7 removed the grub boot from wherever it was installed, MBR or otherwise.

---

### Post by Bucky Ball on 2011-05-15
> reivan = error: symbol not found: 'grub_mm_base'
Mwanyoko = 'grub_mm_base' not found... are not the same problem. Mwanyoko, you should probably create a separate thread giving as much detail as possible and a descriptive thread title. ;)

---

### Post by Sox_Rule on 2011-05-15
So need to reinstall grub? When I 'ls' the content of sd1 I can still see a /boot/grub directory with all it's contents.

Appreciate your assist.

---

### Post by Bucky Ball on 2011-05-15
reivan, are you saying the CD does the same thing in two separate machines? If so, that would probably be the CD. I didn't quite get you. ;)

---

### Post by MAFoElffen on 2011-05-15
> **Sox_Rule said:**
> So need to reinstall grub? When I 'ls' the content of sd1 I can still see a /boot/grub directory with all it's contents.

Appreciate your assist.
Sorry for jumping in on this...

I'm confused also.  Your title says you had problems when update went to 11.04.  You later in same post said your using 10.10 LiveCD...

I would boot from a 11.04 LiveCD > mount your drive and sys > Reinstalll grub.
See post 3 of this sticky for the mount instructions:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

There are syntax and functional changes in grub 1.99~rc1 which comes with natty 11.04 that are different from grub 1.98 that came with Maverick 10.10, especially where "root" and "boot" is concerned...

Reinstalling to sda (or the base of whatever drive) is going to correct what grub problems you having without having to debug them and correct them manually.  It did work for you in 10.10 before the upgrade right?

---

### Post by Sox_Rule on 2011-05-15
Thanks for that. Worked perfectly!
Relative noob to Linux but learning all the time.
Cheers

---

### Post by MAFoElffen on 2011-05-15
> **Sox_Rule said:**
> Thanks for that. Worked perfectly!
Relative noob to Linux but learning all the time.
Cheers
UR Welcome..

Since you are the originator of this thread... If "Solved," please remember to use the forum thread tools to mark this thread as "solved."

---

### Post by reivann on 2011-05-28
Thanks everyone!! :D This is a very friendly community. :'(

It seemed like that the problem is just on my CD. I tried and tried the installation from the Live CD ... and then it worked. X__X. Now I learned that same procedures don't necessarily produce same results. Lol. 

Thanks again. :)

---

