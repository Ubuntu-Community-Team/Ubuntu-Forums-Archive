---
title: "Vista won't load after Dual Boot 9.04"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by idontknowlinux on 2009-04-04
[CENTER]Problem: Vista won't load after I tried to dual boot 9.04[/CENTER]I just tried to boot the new 9.04 beta with both Vista and 8.04 already on my computer. I made it to where i needed to partition my hard drive (It was going to shrink Vista and add 10g's for 9.04). Then I got an error that it couldn't read the CD and that I should try burning it at a slower speed. I was going to try to burn it again so I went to Vista. When I tried using Vista it would go to the Vista boot screen, but after it was done I would see a black screen with my mouse. It wouldn't even go to the Welcome Screen. I have already tried the windows recovery program to start from a recovery point but it said that there was an error with the C drive. I know my C drive is still in tact with all my Vista files because I saw if I could backup my files, which I could. I'm taking ANY ideas that would get Vista up and running.[CENTER]FYI: Hardy Heron was dual booted onto Vista. It is a 32 bit.**[/CENTER]

---

### Post by Connoro on 2009-04-04
Try using your Ubuntu disc again, but run it as a live CD. Check if you can see the files on your hard drive. It's possible the installation ruined your hard disk.

---

### Post by idontknowlinux on 2009-04-04
Ok, right now I am running the 9.04 Live CD and I found all of my files on my C Drive. I even just tried to open up one of my .odt files from my C Drive and it opened up perfectly.

---

### Post by SteveNorman on 2009-04-04
you probably need to run a disk check. I dont know how to do that if you cant log into windows though. I dont know if fsck will work for this either. I would do some googling about doing a disk check on a windows partition with a dual boot.

What I am worried about is that during your re-partitioning you may have killed a boot file.

I would do another post in the "other OS" catagory of the forums

---

### Post by idontknowlinux on 2009-04-04
Hey SteveNorman,

Thanks for the advice. I was wondering though if I have to make a completely different post or if I could move this one.

---

### Post by SteveNorman on 2009-04-04
Not sure, the mods can move it, but I dont know how to get thier attention in a positive way.

---

### Post by idontknowlinux on 2009-04-04
I used chkdsk C: /R to fix my problem. I used the command prompt in Windows Recovery. :D

---

### Post by kansasnoob on 2009-04-04
> **idontknowlinux said:**
> I used chkdsk C: /R to fix my problem. I used the command prompt in Windows Recovery. :D

Glad you got that straightened out.

That's why Vista should always be resized using only Vista's own partitioning tools!

---

