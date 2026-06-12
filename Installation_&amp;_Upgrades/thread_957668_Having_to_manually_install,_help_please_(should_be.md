---
title: "Having to manually install, help please? (should be quick to answer)"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by go7Ul1ai on 2008-10-24
Hello,

I'm fed up of losing my data, I'm a student and can't afford an external Hard Disk so I can't back up my data. Something went wrong and I had to do a fresh install. I used a live USB of Ubuntu 8.10 Intrepid Ibex (Release Candidate) and had an idea, I would create a separate Home partition so if something goes wrong and I can't boot, I won't lose my important data.

What I did was manually install, I had my large partition as / , a smaller partition mounted as /Home and an even smaller partion as /Swap.

When I reinstall, would I have to do the manual installation again? And would I lose all the data in my Home Partition? The reason I'm asking is because when I went to test by going through Ubiquity, it detects my smaller, new Home partition as the main partition and offers to install Ubuntu on that one, any way I can get it to install on the other partition using the automated process?

Many thanks in advance,

Lee Jarratt

---

### Post by dabl on 2008-10-24
> **lee.jarratt said:**
> Hello,

When I reinstall, would I have to do the manual installation again? 


Yep.  Since there's no mounted hard drive filesystem at the time you're running the installer, it has no idea which partition(s) you mean to use, so you have to manually point it to the correct partitions.  :)

---

### Post by go7Ul1ai on 2008-10-24
> **dabl said:**
> Yep.  Since there's no mounted hard drive filesystem at the time you're running the installer, it has no idea which partition(s) you mean to use, so you have to manually point it to the correct partitions.  :)

Thanks for the quick reply, so would that mean it would have to partition /Home partition?

Lee Jarratt

---

### Post by dabl on 2008-10-24
No, you just leave the partitioning as it is, unless you have some problem with them.

When you're running installation, you first pick the partition where "/" (the main OS filesystem) will go.  It's OK to format it, or not.  Then you also need to check the box in front of the partition that you want /home on, and indicate that it is to be mounted as "/home".  Just be sure NOT to indicate that it should be formatted.

The swap partition should be detected automatically.  :)

---

### Post by go7Ul1ai on 2008-10-24
> **dabl said:**
> No, you just leave the partitioning as it is, unless you have some problem with them.

When you're running installation, you first pick the partition where "/" (the main OS filesystem) will go.  It's OK to format it, or not.  Then you also need to check the box in front of the partition that you want /home on, and indicate that it is to be mounted as "/home".  Just be sure NOT to indicate that it should be formatted.

The swap partition should be detected automatically.  :)

Thanks again, but last time I did that, I made sure I checked for my / partition to be formatted, and I made sure my /Home partition was not going to be formatted. But it formatted it anyway, I don't know what's going on there.

Thanks again and for any more help in advance,

Lee Jarratt

---

### Post by dabl on 2008-10-24
> **lee.jarratt said:**
> 

 But it formatted it anyway, I don't know what's going on there.



Me neither -- doesn't sound right.  But it definitely proves the value of backup up your data before launching an installation.

:)

---

### Post by go7Ul1ai on 2008-10-24
> **dabl said:**
> Me neither -- doesn't sound right.  But it definitely proves the value of backup up your data before launching an installation.

:)

Hehe, I have some weird OCD and have to format and reinstall, I do it around once a week and it gets worse, I just like setting things up. How lame is that :P

Anyway, many thanks for the information and for your kindness to help me, it's much appreciated!

Lee Jarratt

---

### Post by dabl on 2008-10-24
> **lee.jarratt said:**
>  I just like setting things up. How lame is that



Well, practice is a good thing, but once a week .....?

If you want to get away from the possibility of borking your data, you might want to do what I do.  Install all of *buntu on the one partition that you made for it.  Edit /etc/fstab to automatically mount the extra partition when you boot the computer.  Make some folders in the extra partition: Docs, Images, Music, Porn, whatever.

Then, open your /home folder in one window, and the data partition in a second window, drag the folders from the data partition to the /home folder, click "link here", and you're done.

VOILA!  No more nuked data when you do your weekly installation ritual.   :guitar:

---

### Post by go7Ul1ai on 2008-10-24
> **dabl said:**
> Well, practice is a good thing, but once a week .....?

If you want to get away from the possibility of borking your data, you might want to do what I do.  Install all of *buntu on the one partition that you made for it.  Edit /etc/fstab to automatically mount the extra partition when you boot the computer.  Make some folders in the extra partition: Docs, Images, Music, Porn, whatever.

Then, open your /home folder in one window, and the data partition in a second window, drag the folders from the data partition to the /home folder, click "link here", and you're done.

VOILA!  No more nuked data when you do your weekly installation ritual.   :guitar:

Hahah, I will have to try that next time! That's a great tip,

Thanks again!

---

