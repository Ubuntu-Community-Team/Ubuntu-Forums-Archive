---
title: "Help Installing New Hard Drive"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by MSchenker on 2007-11-06
Hi All,
I have Kubuntu installed on my computer and have been using it happily for a little while.  Now I need to install a new hard drive.

Is there a way to easily transfer my Kubuntu installation to the new hard drive?  Are there open-source tools to do this?  Or do I have to reinstall Kubuntu?

Thanks,
Matt

---

### Post by bulldog on 2007-11-06
by installing a new hdd you will encounter more problems.
In my opinion is the fastest solution:
Backup your personal data from /home
Reinstall kubuntu and copy the data back.

Ofcourse you won't learn anything by doing it this way.

---

### Post by MSchenker on 2007-11-06
bulldog,
I'm still new at Linux, so I sometimes still ask simple questions!

I just want to make sure I understand...is there a way to simply copy the whole Kubuntu partition over to a new hard drive?

Matthew

---

### Post by Technophobia on 2007-11-06
if you wanted to learn something else backup you home and then make an image of your drive.

You could try [http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l) which lets you make an image of your drive and then apply it to another drive at a later time. Then use something like gparted to resize partitions. I have never used Ghost before so try doing some research on how dependable it is and other alternatives.

---

### Post by MSchenker on 2007-11-06
Technophobia,
Thanks for the link.  It sounds like the easiest thing to do is just to re-install Kubuntu.  Even though I would have to re-do all my settings and preferences, it sounds like that's less time than playing around with images and all that.
Thanks,
Matt

---

### Post by bulldog on 2007-11-06
> **MSchenker said:**
> Technophobia,
Thanks for the link.  It sounds like the easiest thing to do is just to re-install Kubuntu.  Even though I would have to re-do all my settings and preferences, it sounds like that's less time than playing around with images and all that.
Thanks,
Matt
Glad you understand,good luck

---

### Post by MSchenker on 2007-11-07
I got the new drive installed (a Seagate 320GB model) and it is running very nicely.  The whole process of getting the new drive in, reinstalling Kubuntu from scratch (including all my personal settings and applications from the repository), and putting all my data back in, took about two hours.  A lot of that was because I messed up the jumper switches and had to do trial-and-error to get them right, which is not Kubuntu's fault!  Something always has to go wrong.

Definitely, for me, it's easier to just reinstall Linux than try to transfer images.

Matt

---

### Post by bulldog on 2007-11-07
Nice hdd,I have two of them Sata and a 500Gb Sata works very good.

I hope you made a separate /home partition,so if you have to do a new install for some reason,all your preferences should be preserved.

But anyway,in most cases a reinstall is the fastest way to be up and running again.

---

### Post by MSchenker on 2007-11-09
bulldog,
Thanks for the help.  Yes, I've got it all set up now and running very well.  I'm actually thinking of adding a second drive as a backup.  Doing backups to a second internal drive is a lot faster than doing it to an external drive!
Matt

---

