---
title: "Can not boot from live cd"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by dolphinsonar on 2008-03-26
EDIT:  I figured out I just had a bad live CD.  Once I got an official live CD it worked.  False alarm!

I have Gutsy installed, and I restarted this morning only to be dropped into a 

The ubuntu logo splash screen shows up, then I get dropped into the BusyBox shell.  I can't access bash.  I have the boot order setup in my BIOS to check the CD drive before the hard drive, but it won't boot the LiveCD that I have in the cd drive...

I can hear the cd spin and load, then it goes right past grub to try to load the hard drive, which I am guessing isn't found.  Then back to BusyBox.

---

### Post by dolphinsonar on 2008-03-26
Is there a way to add the CD Drive to grub?  Right now I have:

```
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+
```

I would hazard a guess that there is a way to add the CD drive onto this menu, but I am not finding the code to type in here to be able to do that.  My sig tells what type of computer I am on.

---

### Post by dolphinsonar on 2008-03-26
Update: I can not even get the liveCD boot screen.  I think this is a hard drive issue.

---

### Post by DJ_Peng on 2008-03-26
It sounds like perhaps it may be a BIOS issue. You may need to get into your BIOS settings and set it to boot from the CD before your primary hard drive.

---

### Post by dolphinsonar on 2008-03-26
I went ahead and checked the bios, and I am positive that the boot order is correct.  The bios checks the CD drive before anything else, I can see the green light and hear the whirring noise in the drive.  Then it seems to just "move on".  I am not sure how else to explain it.  I guess next I should check to confirm the the boot CD's are correct.  I will post an update after I do that.  

Thanks for the response, it is much appreciated.

---

### Post by stefangr1 on 2008-03-26
I had something similar with a bad cd, if you have the possibility to redownload and reburn it on another computer you could give that a try.

---

### Post by dolphinsonar on 2008-03-26
Thanks!  This was a clear case of "I didn't burn the ISO right" on the live CD.  It would have done the same thing if I put in the latest GWAR album.  It ignored the CD because it wasn't recognized as a boot disk.

Thanks everyone!

---

