---
title: "Problema booting Vista after Hardy install"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by Macdelaney on 2008-04-29
I've been using Vista for a few months now, having also XP installed in a 60Gb partition, and reserving a 300gb partition for storage. Now when Hardy come out i figured it'd give it another try, so from the Ubuntu partitioner i erased the Xp partition and installed ubuntu unto it (leaving a 4Gb partition for Swap).
Everything worked fine with ubuntu, but when i start my computer Grub doesnt let me choose between anything but different Ubuntus adnd the memtest.
So i figured id just had to add a proper entry to /boot/grub/menu.lst, wich i did and is the following (my vista partition is /dev/sda3) :

title Windows Vista
root (hd0,2)
savedefault
makeactive
chainloader +1

Obviously this didnt work, and the "NTLDR is missing" message poped up. To fix this problema i was told to run "fixmbr" from the command prompt in the Vista CD, but the commando wasnt recognize so i was left at 0 again.
I also tryed  to format the ubuntu partition and install Vista on it, hoping it would restore the boot loader but nothing happened. Then i tryed intstalling ubuntu again there, but the same problem arises.
Can anyone help me? I've tryed quiet a lot of things at this moment and nothing seems to work.

---

### Post by Reg Editor on 2008-04-29
[http://blogs.msdn.com/winre/archive/2006/10/20/where-are-recovery-console-commands.aspx](http://blogs.msdn.com/winre/archive/2006/10/20/where-are-recovery-console-commands.aspx)

good luck

---

### Post by Rallg on 2008-04-29
Whoa, it sounds like your have made your setup too complicated to diagnose.

First, Hardy installes just fine with Vista dual-boot. Second, the Vista boot fix (from its installation DVD) also does work; I have used it for another purpose.

Now, did you move your Vista partition at any time, via partitioner? If you merely shrunk it (or expanded it), that should not cause a problem. BUT if you used the partitioner to move the starting point of Vista, that could indeed be a problem. In my past experience, Vista is unhappy if its partition does not start on the hard drive where it originally started. My solution was to clean it off and re-install Vista anew, but of course that will evaporated your own files and pograms.

There might be a way to fix your problem using Midnight Commander on the System Rescue CD (downloadable online from elsewhere). But Midnight Commander is difficult to use, so it's not the best place to start.

---

### Post by Macdelaney on 2008-04-29
thanks, this looks like its going to fix my issue.
Will try this at home and post back.
By the way, should i leave the last bit i added to /boot/grub/menu.lst?
Is it correctly written taking into consideration that i'm trying to boot from /dev/sda3??
I really appreciate your feedback

Rallg:

i neither shrinked it nor expanded it, i just used the partition where XP was minus 4Gb for Swap, Vista partition wasnt touch at all, unless i messed up somewhere. How could i know if i've moved the starting point of vista?

I can still see all the files, so copying them to the Storage partition should be too much of a hazzle, but i've just gotten to the point ehere im 100% comfortable with the OS, with everything looking like i want it to and everything, so it would be a pity. 
If there's no other choice i'll just have to go for it, but i rather fix this and try to learn something in the way.

---

### Post by Rallg on 2008-04-29
One other thing: I don't think Vista uses NTLDR. So, are you sure that your reference to (hd0,2) is the correct partition? Maybe it is the old XP partition? If in doubt, it won't hurt to play with the numbers. If you choose the wrong place and Vista bootloader is not there, nohing will happen. Keep in mind that if your Grub is on other media, it may think your hard drive is hd1 or whatever.

Also, whenever a partition is re-formatted, its UUID is changed. If Grub refers to the old UUID, then it won't be able to mount the partition in question. This is probably not your problem, but if it is, you can either (a) discover the new UUID via live CD, or (b) eliminate reference to UUID in Grub menu.lst, and instead refer to device path "the old way." Note that (b) is not recommended, but I'm not sure why.

If you moved the starting point of a partition, you would know it. That doesn't happen unless you tell the partitioner to do it, and in particular the installer does not move it (it does not have that feature). It only happens if you do it by intent in Gparted or some other partitioner program.

---

### Post by Macdelaney on 2008-04-29
i dont think im pointing to the incorrect partition because where XP was got formated to ext3, leaving only two NTFS partition (the one for Storage and the  one with vista). i will try using the commandlist Reg Editor suggested first, to see if by doing "BootRec /FixMbr" from the Vista CD anything gets fixed. But in case, that doesnt work, and i know im kind of pushing the envelope here, but how do i discover the UUID from Ubuntu, and where should i modify it? in /boot/grub/menu.lst? 
Just so its clear, i dont need to use the Live CD, the Ubuntu installation works perfectly. Do you recommend doing it from the Live CD anyway for any reason or is it the same?

---

