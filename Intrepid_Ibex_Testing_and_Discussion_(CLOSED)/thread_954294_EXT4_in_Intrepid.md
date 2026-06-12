---
title: "EXT4 in Intrepid"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MALEADt on 2008-10-21
Now EXT4 has been finalized (no more ext4dev), is there a chance Ubuntu developers will include those final patches (which normally only enter the kernel in 2.6.28) and update the development version which is included in intrepid? It'd be a major feature, and ext4 provides many enhancements above ext3.

maleadt

---

### Post by FuturePilot on 2008-10-21
It's way too late to do that at this point being only a little over a week away from release.

---

### Post by Gina on 2008-10-21
May make it in the next version.

---

### Post by MacUntu on 2008-10-21
Agreed. 

Looking forward to see it in a stable state in Jaunty (I don't want a separate boot partition - GRUB can't handle ext4 yet).

---

### Post by Archmage on 2008-10-21
I would like if this happen, although I fear that it will be to late to do this.

Kindly allow me to point out that you can't boot from ext4, but in all other cases it seems to be okay.

---

### Post by gnomeuser on 2008-10-21
I was browsing the development mailing lists and one of the ext4 developers have been answering questions over the last few weeks. It seems we will get the userspace tools, the module is apparently available in the kernel, the only thing not there is the ability to format and install onto ext4 via the installer.

---

### Post by ssam on 2008-10-21
I expect it will still be a while before ext4 is considered proven stable enough to be the default (ext3 has a very stable reputation).

If you want to have a go with ext4 maybe you should try fedora 10. They are more experimental with kernel stuff (redhat has better links with kernel people than ubuntu).

---

### Post by MacUntu on 2008-10-21
> **ssam said:**
> ext3 has a very stable reputation

Unless you force a check of a mounted volume. :D

---

### Post by Vishal Agarwal on 2008-10-21
> **MacUntu said:**
> Unless you force a check of a mounted volume. :D


:)

---

### Post by Archmage on 2008-10-21
> **ssam said:**
> I expect it will still be a while before ext4 is considered proven stable enough to be the default

We are not talking about making ext4 making the default (I see no reason to do this now), but at least giving the people the possiblity to mount ext4 at all. At the moment it seems that you are unable to use ext4 at all in the 8.10. So we could only hope for 9.04.

But what can we do in the meantime if we want/need to use ext4? As you know you can't mount ext4 as ext3.

---

### Post by smartboyathome on 2008-10-21
> **Archmage said:**
> We are not talking about making ext4 making the default (I see no reason to do this now), but at least giving the people the possiblity to mount ext4 at all. At the moment it seems that you are unable to use ext4 at all in the 8.10. So we could only hope for 9.04.

But what can we do in the meantime if we want/need to use ext4? As you know you can't mount ext4 as ext3.

You can mount ext4 as ext3 (its backwards compatible), but you don't get any of the advantages of ext4 if you do.

---

### Post by aaronb on 2008-10-21
Please see this link for a little more info on the status of ext4.

[http://www.osnews.com/story/20409/Ext4_Completes_Development_Phase](http://www.osnews.com/story/20409/Ext4_Completes_Development_Phase)

To sum it up :), in Linux 2.6.28 the ext4 gets renamed from 'ext4dev' to 'ext4'. So maybe ubuntu 9.04 would be a better time as in Linux 2.6.27 its  still marked as development.

---

### Post by Archmage on 2008-10-22
> **smartboyathome said:**
> You can mount ext4 as ext3 (its backwards compatible), but you don't get any of the advantages of ext4 if you do.

After you did use the extensions (and EXT4 will do this by default) EXT4 can't be mounted as EXT3.

But EXT3 can be mounted as EXT4, but than use the extensions and you can't use it as EXT3 anymore.

---

### Post by Gina on 2008-10-22
Seems to me it's not ready yet.

---

### Post by bigbear2350 on 2008-10-24
Its in Intrepid I am using it now. It seems stable to me although i dont have my personal data on it. I do have data on it that i dont care that gets lost though.

---

### Post by GuitarRocker2562 on 2008-10-24
Well, it will be in the 2.6.28 kernel as a stable fs. Ubuntu 9.04 will probably support it.

---

### Post by zoomy942 on 2008-10-24
> **bigbear2350 said:**
> Its in Intrepid I am using it now. It seems stable to me although i dont have my personal data on it. I do have data on it that i dont care that gets lost though.

howd you do that?

---

### Post by bigbear2350 on 2008-10-25
sudo mount /dev/yourhardrivepartition ext4dev /youmountpoint


You have to add test_fs to your ext3 partition first though.

by

> sudo tune2fs -E test_fs /dev/whateverdriveparition


Beware you wont be able to remount it as ext3 once its mounted as ext4dev

---

### Post by Polygon on 2008-10-25
> **Archmage said:**
> We are not talking about making ext4 making the default (I see no reason to do this now), but at least giving the people the possiblity to mount ext4 at all. At the moment it seems that you are unable to use ext4 at all in the 8.10. So we could only hope for 9.04.

But what can we do in the meantime if we want/need to use ext4? As you know you can't mount ext4 as ext3.

yes you can

unless you enable extents, then the backwards compatibility ends

and i would NOT make ext4 default. cause it takes a long time for these things to be proven stable, and the filesystem is the last thing we want instability on.

---

