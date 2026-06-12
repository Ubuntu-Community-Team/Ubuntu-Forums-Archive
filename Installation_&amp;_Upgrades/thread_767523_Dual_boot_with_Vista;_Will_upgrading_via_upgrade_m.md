---
title: "Dual boot with Vista; Will upgrading via upgrade manager delete anything in Windows?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Redrazor39 on 2008-04-25
I will upgrade to the hardy release soon. I am currently running Ubuntu 7.10 in a dual boot with Windows Vista (I'm sorry, but my comp came with it and I need it for a few apps, so you know...). What I want to know is if I use the update manager to upgrade to Hardy, then will my Windows Partition be deleted? Will anything in my windows partition be deleted? Will the GRUB entry be changed or deleted? Is there anything I should know about before upgrading to Hardy such as major problems?

Thank you for any help.

---

### Post by deltadave on 2008-04-25
I installed 8.04 today on my laptop but formatted my ubuntu root partition instead of just upgrading 7.10.  I let it redo the grub loader and it boots into vista just fine.  (I boot into vista occasionally to remind me how much i hate it.)  Hope that helps.

---

### Post by Redrazor39 on 2008-04-25
I see. Thanks for the info, but I would like to just click on "Upgrade" and have everything work perfectly.

Wouldn't we all...


I just don't want to mess up my computer.

---

### Post by blegs38552 on 2008-04-25
I don't see any need to apologize for using Windows. Until someone comes up with a program that I can use my Microsoft Money files with, for example, or do my taxes as easily as I can with Tax Cut or Turbo Tax, just to name a few, or even connect to my computer wirelessly (I was never able to get that working in 7.10), I will be using Vista without apologees.

Tried downloading and burning an ISO image to a CD and installing from there, but it hungs at step 4 (partitioning). Am currently trying the upgrade route - the download is slow, but I have all weekend. Who knows, maybe 8.04 will give me my wireless connection.

---

### Post by Redrazor39 on 2008-04-25
I apologize for using Windows because I don't want to be flamed or given incorrect information by trolls and ubuntu extremists.

Then again, I could just use the report feature...

---

### Post by twright on 2008-04-25
all of the extremists use Gentoo/Slackware/Archlinux/BSD these days :)

no one will flame you for dual booting, it makes sense to dual boot just in case you need anything as long as you have the space (and you have a live cd handy incase vista nukes your MBR).> **Redrazor39 said:**
> I apologize for using Windows because I don't want to be flamed or given incorrect information by trolls and ubuntu extremists.

Then again, I could just use the report feature...

upgrading will work fine

---

### Post by Shinobi326 on 2008-04-25
This is a similar question I asked yesterday.  Here is my thread and responses:

[http://ubuntuforums.org/showthread.php?t=765128](http://ubuntuforums.org/showthread.php?t=765128)

---

### Post by Redrazor39 on 2008-04-27
I'm scared to upgrade because of all the bad rap Hardy's getting. I'm thinking of testing it out w/a live CD first.

---

### Post by twright on 2008-04-27
hardy seems amazingly stable to me, the new kernel does break some things but you can always choose the old one when you boot up.  basically it seems that most of the things which were broken in gutsy work in hardy  if you download the .iso and burn it to disk when you have tried it out you can upgrade from it by inserting it when gutsy is running and using the autorun prompt, saves having to download it twice :)

---

### Post by Redrazor39 on 2008-04-27
What kinds of things does the new kernel break?

Would you recommend testing with a Live CD and performing via update manager upgrade if all works well in the Live CD?

---

### Post by twright on 2008-04-27
ndiswrapper and some other small things may be broken just because it is different  also driver installation tutorials for the previous one might not work.  when you upgrade the old kernel is still available from you grub menu so you should be ok  windows installs and the like should not be damaged

---

### Post by lemming465 on 2008-04-27
> ... Would you recommend testing with a Live CD and performing via update manager upgrade if all works well in the Live CD?

Yes.  This worked out well for me.  If you happen to have alternate CD's around too, copy the .deb files into /var/cache/apt/packages and you can cut the download time.  (I wasn't able to get apt-cdrom to do anything useful with ISO images.)

---

