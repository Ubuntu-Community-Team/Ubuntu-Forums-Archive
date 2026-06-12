---
title: "Which partitions will I need to reformat when reinstalling?"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by eentonig on 2007-09-13
Hi,

**[COLOR="Red"]STARTING POINT[/COLOR]**
When I did my partitioning. I was wise enough to create some extra partitions.

[B][COLOR="Black"]/dev/sda1             9.7G  288M  8.9G   4% /[/COLOR]
[COLOR="Black"]/dev/sda2             241G  140G   89G  62% /home[/COLOR][/B]
[COLOR="Green"]/dev/sda3             9.7G  151M  9.0G   2% /media/sda3
/dev/sda5             9.7G  151M  9.0G   2% /media/sda5[/COLOR]
[COLOR="Black"][B]/dev/sda6              49G  3.3G   43G   8% /usr
/dev/sda7              47G   15G   29G  35% /var[/B][/COLOR]

The partitions in black, are currently in use.
The partitions in green are reserved for installing seperate OS to boot from.

**[COLOR="Red"]Question:[/COLOR]**

Say I want to try out Gutsy. I know if I reinstall, I can reuse the** /home**/ partition without formatting. And as such, retain all my user settings and documents.

- Does the same goes for these two partitions?
[COLOR="Black"]**/dev/sda6              49G  3.3G   43G   8% /[B]usr**
/dev/sda7              47G   15G   29G  35% /**var**[/B][/COLOR]

- Is there a risk in alternating between a Gutsy and Feisty install that use the same /home partition?


Please let me know if I'm not clear on something.

---

### Post by dabl on 2007-09-13
No, you don't want to try to share /usr or /var.  Actually, it's not totally clean to share /home the way you are proposing, because not only does /home contain your user data, but it also has configuration settings, such as things that automatically start upon bootup. If you don't have all the same packages and all the same destop settings in both OS's that are trying to share /home, you're going to have trouble.  :(

I just let each OS have its own /home directory, but I do have the luxury of disk space.  If you can't do that, you might want to consider a special partition for /MYDATA and then you'll have to mount that for each OS ( a fairly simple /etc/fstab edit).  But at least your configuration settings won't get borked up.  :)

---

### Post by eentonig on 2007-09-13
Ah, I already thought so. Just wanted to make sure.

diskspace is not a problem. I've got plenty. Most of my ~/ is filled with pictures, movies and music. And those are all backed up to the last day on an external HD. 

But I'll just use one of the free partitions to tryout Gutsy for now.

Thanks for the answer.

---

### Post by dabl on 2007-09-13
Sure. By the way, you only need one swap partition -- it is fully shareable by whichever OS you boot.

:)

---

