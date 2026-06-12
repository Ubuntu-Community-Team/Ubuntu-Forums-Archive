---
title: "GParted I so."
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by Yezinki on 2013-02-25
I am trying o install  Ubuntu on m gfs  Dell Inspiron, using GParted iso  cd. I created  3 partitions but have issues how to log out/ exit.  cannot highlight 
gparted, edit, file, decide manager..........I have tried usin the tab
, space  bar, enter,  etc....any kind of assistance would be appreciated. thanks

---

### Post by offgridguy on 2013-02-25
> **Yezinki said:**
> I am trying o install  Ubuntu on m gfs  Dell Inspiron, using GParted iso  cd. I created  3 partitions but have issues how to log out/ exit.  cannot highlight 
gparted, edit, file, decide manager..........I have tried usin the tab
, space  bar, enter,  etc....any kind of assistance would be appreciated. thanks
I had the same issue with the gparted live CD. The only way I could logout/shutdown was to to do a hard shutdown  ie; hold down the power button,
if this is a laptop?

I now use partedmagic, contains  gparted and more, and lets me log out.

---

### Post by Sef on 2013-02-25
When logging out, with the cursor on the desktop, I had to left click and from there, I was able to log out.

---

### Post by Yezinki on 2013-02-25
Thanks , I did that but Ubuntu  C:D won't install........

---

### Post by Sef on 2013-02-25
Have you checked the disk to make sure that the burn to it went well?

---

### Post by Yezinki on 2013-02-26
thanks Sef, the CD works fine on my Sony,, have installed Ubuntu several times using this CID, now hen  Boot her dell, press F12'. To boot using optical drives it won't and see a message no active partitions........anysugeestions.  Thanks

---

### Post by gnueliafnak on 2013-02-26
Have you tried to use GParted again and delete all the partitions then exit out of the program and boot Ubuntu from a LiveCD with the install? Also after you are done with the partitions, you have to I believe right click for a minute or was it left click on the desktop area to bring up a menu to "Exit" GParted which will then go into a terminal/command line black screen and you would hear a long system beep asking you to remove the media from the CD and then hit enter etc.

Have any screenshots you can provide?

---

### Post by Yezinki on 2013-02-26
Thanks, after I have created partition , / /home, Linux swap all 3 primary, 1st 2 ext4' and I try to exit, it wouldn't give the option to take out the media.....any suggestions.

---

### Post by Bucky Ball on 2013-02-26
*Thread moved to **Installation & Upgrades**.*

Just wondering why you're bothering to do this *prior* to installing. If you click 'Something Else' when you get to the partitioning section of the install then you can delete and create whatever partitions you want, whatever size you want; /, /home and /swap are even there as default mount points.

If I'm understanding you correctly what you're doing appears to be an extra, unecessary step to me. ;)

---

### Post by offgridguy on 2013-02-26
> **Bucky Ball said:**
> *Thread moved to **Installation & Upgrades**.*

Just wondering why you're bothering to do this *prior* to installing. If you click 'Something Else' when you get to the partitioning section of the install it takes you to Gparted and you can delete and create whatever partitions you want. /, /home and /swap are even there as default mount points.

What you're doing seems like an extra, unecessary step to me. ;)
+1, plus the OP seems to be on another topic than the original post.

---

### Post by Yezinki on 2013-02-26
Thanks I agree with you but now I have deleted windows and when I try booting using Ubuntu live cd it displays no active partitions......

---

### Post by gnueliafnak on 2013-02-26
can you provide a screenshot of what you are seeing?

When you boot from LiveCD, it should boot up to the Ubuntu installation screen with the option to "Try Ubuntu" or "Install Ubuntu". 

If you go to Install Ubuntu, you get like 3 options, the last one is the one you want called "Something Else" which allows you to create and modify partitions. You can then setup root partitions, swap partitions, home partitions, boot partitions etc.

---

### Post by Bucky Ball on 2013-02-26
Are you talking about when you are booted from the LiveCD, have hit Something Else to manually partition and are in that section? If so, you can now go ahead and create /, /home and /swap, if that is what you want, then continue to install.

I'm presuming you are looking at free space?

---

