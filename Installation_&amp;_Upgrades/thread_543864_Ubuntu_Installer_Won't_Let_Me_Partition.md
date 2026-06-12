---
title: "Ubuntu Installer Won't Let Me Partition"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by condawg on 2007-09-05
Hiya.
I'm trying to install ubuntu, and I'm trying to edit an existing partition that I have Windows installed on.
When I right click and hit "Edit Partition" a window pops up saying 
"Use As: NFTS
Mount Point: /media/hda1"

So I can't edit the partition from there.
So I just select the partition and hit "Next" figuring that it would bring me to the partition table and allow me to edit it.
Instead, I get 
"No Root File System Is Defined.

Please Correct This From The Partitioning Menu"


So I figure that I just have to choose the root of the HD, not the partition itself.
But when I do that, it wants to format the drive.
I DO NOT WANT THAT!!
I just want to install this... I don't want to lose ANY of my Windows XP.
Thanks for any help

---

### Post by merlinus on 2007-09-05
You need to select re-size existing partition.  That will free up space for ubuntu.

Do not format it.

-merlin

---

### Post by Pumalite on 2007-09-05
Defrag several times, erase all temp files. In partitioner, right click XP partition and choose 'shrink partition'

---

### Post by condawg on 2007-09-05
> **merlinus said:**
> You need to select re-size existing partition.  That will free up space for ubuntu.

Do not format it.

-merlin
Well, I'm on windows right now, because I got paranoid and wanted to make sure it was still here, but I didn't see that option when I was installing :S

---

### Post by merlinus on 2007-09-05
There should be an option along the lines of Guided, resize sda (or hda) and use free space.  Then it should come up to a window with a slider so you can do this.

-merlin

---

### Post by condawg on 2007-09-05
> **merlinus said:**
> There should be an option along the lines of Guided, resize sda (or hda) and use free space.  Then it should come up to a window with a slider so you can do this.

-merlin
:'(
That wasn't there, either.
There was just "Guided: Use Whole Disk"

and

"Manual"

---

### Post by merlinus on 2007-09-05
Then choose Manual, and there will be an option to resize your windows partition.

You can experiment as much as you like, because nothing will happen until you choose Apply Changes (or something similar).  You can use the Back option to go back to previous steps.

Make sure you back up important data first!

-merlin

---

### Post by condawg on 2007-09-05
Mmkay... I'm going to attach a few screenshots to help you understand the situation I'm in.

[img]http://img260.imageshack.us/img260/894/screenshotinstalluc0.png[/img]

{then I click "Forward"}

[img]http://img260.imageshack.us/img260/1734/screenshotinstall1oh0.png[/img]

{the hard drive selected is the one I want to partition}
{right-click}

[img]http://img54.imageshack.us/img54/9018/screenshotinstall2ci5.png[/img]

{click "Edit Partition"}

[img]http://img210.imageshack.us/img210/5618/screenshoteditpartitionme2.png[/img]

{go back and click "forward" from the drive selection}


[img]http://img54.imageshack.us/img54/2060/screenshotnorootfilesysut5.png[/img]

Any help appreciated :)

---

### Post by merlinus on 2007-09-05
What is in /dev/hda2 (the fat partition)?

If you need it, choose Edit /dev/hda1.   Then you should see the slider that will allow you to resize it.

-merlin

---

### Post by condawg on 2007-09-05
> **merlinus said:**
> What is in /dev/hda2 (the fat partition)?

If you need it, choose Edit /dev/hda1.   Then you should see the slider that will allow you to resize it.

-merlin
Well that's something that came when I installed XP... I guess it has stuff that XP automatically backs up, because when on XP that's called the "backup drive".
And as I mentioned and showed a screenie of, I did hit the edit button for hda1.

---

### Post by merlinus on 2007-09-05
What happens if you choose Guided - Use Entire Disk?

And I frankly am very surprised that Manual did not give you the option of resizing your existing xp partition.

-merlin

---

### Post by mocoloco on 2007-09-05
> **merlinus said:**
> What happens if you choose Guided - Use Entire Disk?

And I frankly am very surprised that Manual did not give you the option of resizing your existing xp partition.

-merlin

That would wipe everything out, he doesn't want to do that.
Edit: I'm also surprised that there was no option that said "Guided: resize partition {whatever}".  This seems like a bug to me.

I personally don't like the new partiioner, I preferred when the liveCD used GParted.  You can still install gparted through synaptic.  I would say do that, and use it to resize, the create your new ext3 partition for Ubuntu, and a swap about 2x your RAM size.
Then when you use the installer and select manual, you just tell it to use your new partitions.

---

### Post by merlinus on 2007-09-05
Even better is to use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by condawg on 2007-09-05
I'll try that. Thanks :)
Also, another thing...
I was playing a game on Ubuntu Live CD, and after a while, this happened...

[img]http://img366.imageshack.us/img366/7333/img3210ey4.jpg[/img]

Does that happen to anyone else?

---

