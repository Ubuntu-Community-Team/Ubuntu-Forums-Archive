---
title: "How long can I stay with 10.10 after the recent release of 11.04??"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by zhaotianwu on 2011-05-14
Hi there,
I'm not a technology savvy guy, I just need a quick answer here. With the newly released 11.04, am I forced to move forward or can I just stay with 10.10? For how long?
I am a bit busy these days with my job so I really don't want to put in too much hours learning the new interface provided in 11.04. I may try it out at a later time though.

Many thanks.

---

### Post by OllieGab on 2011-05-14
After "struggling" a bit with the new dashboard and launcher I realised that I could start 11.04 up in classical mode, thus keeping most of interface as I am used to.
I always tell myself not to run off and do a new upgrade straight away, but instead wait, perhaps until the NEXT upgrade and then update to the previous.
But I fail each time! A month or so after a new release I tend to upgrade. However, I think it's "safe" to wait as long as you like, really. A year or so, anyway!

---

### Post by Rubi1200 on 2011-05-14
There's really no need to hurry into this since 10.10 is supported until April 2012. It might also be a good idea to wait with 11.04 for a couple of months until some of the initial kinks are ironed out.

In any event, testing first with a LiveCD is usually a good idea.

See here for Unity hardware requirements as well as the release notes:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)
[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes)

---

### Post by slooksterpsv on 2011-05-14
EDIT: Removed top portion, someone answered =D

Now with Natty and Unity, I actually got it working where it's usable and not royally messed up. I disabled the global menu (where file edit etc. would go to the top) and disabled the overlay scroll bars (I have regular scrollbars).
Pretty much just had to remove a few packages.

Actually I'm starting to like Unity and there's a few widgets I've installed on the top panel. Dash is nice, just press SUPER type in what I need, press enter, makes the mouse almost obsolete for me.

That's my 2 cents.

---

### Post by dabl on 2011-05-14
> **zhaotianwu said:**
> Hi there,
I'm not a technology savvy guy, I just need a quick answer here. 

Answer: Forever.

:)

---

### Post by mcduck on 2011-05-14
> **zhaotianwu said:**
> Hi there,
I'm not a technology savvy guy, I just need a quick answer here. With the newly released 11.04, am I forced to move forward or can I just stay with 10.10? For how long?
I am a bit busy these days with my job so I really don't want to put in too much hours learning the new interface provided in 11.04. I may try it out at a later time though.

Many thanks.

You are free to keep on using 10.10 as long as you wish, although it's support will end in April 2012 after which there will be no more security (or any other) updates and it's repositories will be closed.

So you still have a year of support left. Although keep in mind that when upgrading, you can't jump over versions (apart from upgrading from a LTS release to next LTS release) so if you choose to skip 11.04, you'll have to do a fresh install when upgrading to 11.10 or 12.04.

[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

---

### Post by Lateralis on 2011-05-14
Well, Gnome2 is no longer in development by the Gnome people - they are working on Gnome3.  So from 11.10, Gnome2 will not be supported by Ubunutu and will not be available in the repos.  In fact, from 11.10, no version of Gnome will also not be installed by default, just Unity.  Gnome3 will be available to download and install from the repos, however. 

As for waiting, I personally would upgrade now.  As OllieGab has said, in 11.04 you do have the choice of using "Classic Gnome" or Unity.  You can switch between the two at the login screen (so long as you have to enter your password and do not get logged in automagically) so you can try out Unity for a bit when you have some free time and then switch back to something you're happy and comfortable with when you need to.  

As for Unity itself, the changes themselves are not that bad.  I was hugely resistant at first, and there is one thing which drives me potty and that's the main menu (which no longer exists in the form we were used to).  But, after maybe half an hour you should feel pretty comfortable with Unity.  At least I did!  

As an alternative, you may want to check out some of the other desktop managers if you really don't like Unity.  Other desktops include: Xfce, LxDE and KDE.  They can be installed from the command line 

```

sudo apt-get install xubuntu-desktop
sudo apt-get install lubuntu-desktop
sudo apt-get install kubuntu-desktop

```

for Xfce, LxDE and KDE respectively.  LxDE is the least well developed out of all of the DEs so might not be your thing.  KDE is very swish and shiny and certainly heavy weight.  Xfce is pretty well developed these days and has a Gnome classic feel to it.  So if you want to retain the feel of Gnome 2, Xfce may be the desktop to use.

---

### Post by zhaotianwu on 2011-05-14
> **mcduck said:**
> You are free to keep on using 10.10 as long as you wish, although it's support will end in April 2012 after which there will be no more security (or any other) updates and it's repositories will be closed.

So you still have a year of support left. Although keep in mind that when upgrading, you can't jump over versions (apart from upgrading from a LTS release to next LTS release) so if you choose to skip 11.04, you'll have to do a fresh install when upgrading to 11.10 or 12.04.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)


Thank you mcduck. My situation is a little bit more complicated than that. I had my hard drive full-disk encrypted using LUKS when I install 10.10, which also co-exists with my Windows 7 system. I'm wondering if I do an automatic upgrade, my current hard drive pattern will be preserved? Or will the automatic upgrading mess with the existing full disk encryption and I will have to do it all from the beginning again manually?

I'm not against Unity at all, I just don't know if this is going to be very risky with my current hard drive pattern.
Thanks a lot.

---

### Post by zhaotianwu on 2011-05-16
Hi come on my friends, could anybody help answer my question above please? Many thanks.

---

### Post by Lateralis on 2011-05-16
The upgrade certainly won't mess with your hard drive partitions.  I have no personal experience with encrypted drives, but the upgrade can't lift the encryption.  

As always though, before you embark on a major system change, i.e. a distro upgrade, ensure everything you need is properly backed up.

---

### Post by zhaotianwu on 2011-05-17
Thanks for this information. Can anybody who has similar situation (full disk encrypted with LUKS) kindly share some experience? Thanks.

---

### Post by 86themachine on 2012-01-09
I just found this post as I am asking the a similar question. I do have experience with this but my last attempt was 6-8 months ago. Using 10.10 full disk encryption has served me well and I'm still using it. I had a failed attempt to upgrade to 11.04 of which I tried 3 or 4 times and each time resulted in the same problem. Password was no longer recognised and I could not get around it. The upgrade appeared to go fine otherwise. I did a small amount of googling and found nothing.  After reviewing a non encrypted version of 11.04 I decided it was to soon to jump ship so I stuck with 10.10

Make sure you clone your drive with dd prior to doing any upgrade. I run off a 64gb usb stick with 2 cloned backups. Saved my butt a few times. As we near the end of support I will look at this subject again and report back.

sudo dd if=/dev/sd? of=/dev/sd? bs=64k
(if) is the drive you want to clone. Let me say that one more time. if=/dev/sd? is the drive you want cloned. of=/dev/sd? is the target drive (the drive which will become your backup) Read up on the dd command it rocks for back up. 
Make sure the (if) and (of) drives are of equal size. The target drive can be larger but not smaller.  READ UP ON IT. GREAT COMMAND BUT CAN WIPE YOUR SYSTEM IF NOT USED PROPERLY.

---

