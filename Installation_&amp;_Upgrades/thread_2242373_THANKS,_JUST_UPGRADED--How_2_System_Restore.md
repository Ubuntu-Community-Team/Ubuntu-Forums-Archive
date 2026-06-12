---
title: "THANKS, JUST UPGRADED--How 2 System Restore?"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by skyesharica on 2014-09-01
[CENTER][SIZE=4][I]Saved my life, people.  Just upgraded to 14.04 LTS ... after lots of crashes ... and it's perfect.  I am ill and needed it for food delivery even!  :-({|=  

If I get "voltages" >>> (and don't want to give up on life) >>> how do I system restore, if I start crashing (You know, like a factory restore with Windows?)

My guess is that I do the same.  I use the same USB Flash Drive, restart after backing up, go to the boot menu, and simply install it all again.

Is that right?[/I][/SIZE]

[ATTACH=CONFIG]256041[/ATTACH] 
[/CENTER]

---

### Post by Mark Phelps on 2014-09-01
Sorry, but there is no built-in system restore or factory restore.  

What I would recommend is that you install Clonezilla and make an image backup of your partition to an external drive.  If you want something with a simpler GUI interface, look into RedoBackup.

---

### Post by skyesharica on 2014-09-02
Thankyou Friend, for the prompt reply.  I see.  I can't possibly understand what you mean by a partition etc etc.  But would I be able to do a clean install of Xubuntu 14.04 LTS from Ubuntu 14.04 LTS - from a USB stick? After extreme confusion, I clicked on the link "download torrent" for Xubuntu 14.04 LTS. I got a weird "Transmission" box that's doing it!!!  See the image  below.  Well, will I just put this ISO file onto my USB stick and do a  clean install of that, if I start crashing? 

[CENTER][ATTACH=CONFIG]256072[/ATTACH]

[/CENTER]
BTW ... (by the way) is  Xubuntu easy for beginners ... i.e. it has less user interface, and  programs using up resources, but is just as easy as Ubuntu ... or do you  need programming?

Also - and alternatively - is it best to update into every new version of Ubuntu, to avoid crashes?  I.E. Adjust Settings?



[CENTER]
[/CENTER]

---

### Post by sotiris2 on 2014-09-02
No Xubuntu does not require you to have programming knowledge.
Transmission is a bittorent client and is installed by default. 
I would suggest updating (and doing so via new installs) to each lts version, which is released every 2 years.

---

### Post by skyesharica on 2014-09-02
Replying quickly - in case it is Tuesday morning for you in the States - is it? - it's 3 am (very bad, late night) in Australia.  That's super help.

I've just finished the download of the raw CD image - the Xubuntu 14.04 LTS .iso file.  Will I put this on a USB stick and try a boot up and clean install from Ubuntu 14.04 - if I start crashing.  Sorry to repeat myself?  Beginner.

> **sotiris2 said:**
> I would suggest updating (and doing so via new installs) to each lts version, which is released every 2 years.

I have to go to bed in Australia now - or I turn into a pumpkin.  :KS

Anyway, I decided to leave my settings somehow safe, and only upgrade to the next LTS version.  What might happen to the less supported versions, in between?  Who knows?

But PHLEEEEZZZZ can you read my reply above ... and tell me if I can do the change with my new .iso file on a USB stick?

---

### Post by Mark Phelps on 2014-09-02
> Will I put this on a USB stick You do NOT copy the ISO file to a USB stick -- if that is what you are intending to do.

Instead, you have to create a bootable USB stick USING the ISO file.  You can do that using Unetbootin. Google that and read the details.

Also, your thread started out asking about doing "system restore" and now, you've jumped into something completely different.  IF you intend to pursue this new line of questioning, you need to CLOSE this thread a start a new one, as it's a bad idea to jump from topic to topic in the same thread.

---

### Post by grahammechanical on 2014-09-02
Ubuntu 14.04 is called Long Term support (LTS) because it has support for 5 years starting at April 2014. Every two years a new LTS version of Ubuntu is released and we get an offer to upgrade from Update Manager.

In between the LTS releases there are Standard or Interim releases that only have 9 months support. These are stable releases like an LTS but should be seen as a way of keeping up with the development of Ubuntu. This is why we often recommend that people install the LTS version and stick with it for at least two years.

We can break Ubuntu. And as you see from this forum some of us are very good at breaking Ubuntu. And in those cases a re-install is often the simple and easy way to fix things.

But if we are content with only making minimum changes to the user interface then you will find that Ubuntu does not crash like some other operating systems. Make regular backups of data that you do not want to lose. I keep all my data on a separate partition. 

We can burn an ISO image of Ubuntu to either a DVD disk or a USB stick. It is all the same. 

Regards.

---

### Post by skyesharica on 2014-09-03
> **Mark Phelps said:**
> IF you intend to pursue this new line of questioning, you need to CLOSE this thread a start a new one, as it's a bad idea to jump from topic to topic in the same thread.

Thanks For All Of That Mark.  I will close the thread then.  ):P

P.S.  Oh hang on ... the next post helped so much ... maybe others have the same problem ... I'll leave it open in case there's one more useful post.  That OK with you?

> **grahammechanical said:**
> Ubuntu 14.04 is called Long Term support (LTS) because it has support for 5 years starting at April 2014. Every two years a new LTS version of Ubuntu is released and we get an offer to upgrade from Update Manager.

In between the LTS releases there are Standard or Interim releases that only have 9 months support. These are stable releases like an LTS but should be seen as a way of keeping up with the development of Ubuntu. This is why we often recommend that people install the LTS version and stick with it for at least two years.

We can break Ubuntu. And as you see from this forum some of us are very good at breaking Ubuntu. And in those cases a re-install is often the simple and easy way to fix things.

But if we are content with only making minimum changes to the user interface then you will find that Ubuntu does not crash like some other operating systems. Make regular backups of data that you do not want to lose. I keep all my data on a separate partition. 

We can burn an ISO image of Ubuntu to either a DVD disk or a USB stick. It is all the same. 

Regards.

WOW - THANX 4 ALL OF THAT MARK.  I see now that I have the same thing as a system restore.  I can reinstall Ubuntu 14.04 LTS or clean install Xubuntu 14.04 LTS from the boot menu.  Thankyou!!!  I remember the people that help me.   :KS

---

### Post by varunendra on 2014-09-03
Just to answer the original question, pretty much just a tiny addition to what Mark Phelps already said in first post -
> What I would recommend is that you install Clonezilla and make an image backup of your partition to an external drive.

The addition is - If you run clonezilla _twice_, using the _same location as destination_ to save the cloned image that you used the first time, it detects the previously saved image and gives you the extra options to create **Automated Restore image(s)** (ISO for DVD, or .zip for USB, or both).

If the Ubuntu (or any *buntu) installation is fresh and contains only the OS, programs (not huge games) and settings, its image created by clonezilla is usually small enough to fit on a DVD. In that case, you can just create an Automated Restore ISO > burn it onto a DVD. When you need to restore your system, just put in the DVD > boot from it > Answer "Y" when clonezilla asks you (it'll ask you twice! Since it is an operation that will overwrite your existing partition(s)) > Sit back and relax while it restores the image.

Restoration of a normal image, that can fit on a DVD usually takes less than 15 minutes.

If the cloned image is too large to fit on a DVD, you can choose to create only the .zip Auto Recovery image. Once created, you just have to extract the contents of this .zip file on ANY USB disk which your system can boot > run a script that clonezilla puts within these contents to make the USB disk bootable. When you need to restore the OS, you simply boot from this USB > answer "Y" > let it do its job.

One thing VERY IMPORTANT here : In the extra steps of creating the automated recovery images, clonezilla asks about how to deal with partition table while restoring the image. For best compatibility (in case the partition table changed since the image was created) - it suggests to Overwrite the existing partition table by default, and that causes _[COLOR="#FF0000"]ALL the existing data on the hard disk to be lost[/COLOR]_ (just like the original factory reset of laptops)!

In order to keep the other partitions (which are not to be restored by the image) and data on them, one has to manually select the option "-k" (stands for "keep partition table") in this step. For the rest, it is fine to go with defaults.

There are guides with screenshots to show how to use clonezilla to create the initial image. I couldn't find one with the extra steps about the "Automated Recover" images though. I may create one if this sounds interesting.

---

### Post by skyesharica on 2014-09-03
Thankyou so much for your very very extensive reply but this information is far too advanced for me.  To avoid confusion I will close the thread.  If I can work out how.

> **grahammechanical said:**
> Ubuntu 14.04 is called Long Term support (LTS) because it has support for 5 years starting at April 2014. Every two years a new LTS version of Ubuntu is released and we get an offer to upgrade from Update Manager.

In between the LTS releases there are Standard or Interim releases that only have 9 months support. These are stable releases like an LTS but should be seen as a way of keeping up with the development of Ubuntu. This is why we often recommend that people install the LTS version and stick with it for at least two years.

We can break Ubuntu. And as you see from this forum some of us are very good at breaking Ubuntu. And in those cases a re-install is often the simple and easy way to fix things.

But if we are content with only making minimum changes to the user interface then you will find that Ubuntu does not crash like some other operating systems. Make regular backups of data that you do not want to lose. I keep all my data on a separate partition. 

We can burn an ISO image of Ubuntu to either a DVD disk or a USB stick. It is all the same. 

Regards.

I have just tried.  It is impossible to do something similar to a factory restore and do a re-clean install of Ubuntu 14.04 LTS if you already have it.  It IS possible to do a clean install of Xubuntu 14.04 LTS from the bootable disc.  So that is my "system restore solution" until the next LTS version comes out.

---

