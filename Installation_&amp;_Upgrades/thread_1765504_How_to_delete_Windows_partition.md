---
title: "How to delete Windows partition?"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by wilwil0 on 2011-05-23
I'm using 9.10. I want to delete my Windows partition.

On System--> Administration there is something called "Disk Utility".

Here is a screenshot:
[http://tinypic.com/view.php?pic=14mtc9x&s=7](http://tinypic.com/view.php?pic=14mtc9x&s=7)

Is it as simple as clicking the "delete" button? I thought I would have to do something with the Terminal, though I would prefer not to.

---

### Post by coffeecat on 2011-05-23
If you delete the partition, you will end up with 80GB unallocated space. No filesystem - no partition. So, yes. But 80GB of unallocated space is not much use. What do you want to do with the space? If you want to use it In Ubuntu, simply reformatting it with a Linux filesystem will effectively delete it, but give you an empty 80GB partition to use.

However, I seem to remember that the Disk Utility app in 9.10 was not as feature rich as later versions, so I don't know what reformatting options you have. Which leads me to:

> **wilwil0 said:**
> I'm using 9.10.

9.10 is now unsupported. You need to think about upgrading to a supported version or even re-installing with a supported version.

---

### Post by wilwil0 on 2011-05-23
I do want to use it for Ubuntu. Is it possible to resize the partition to include the unallocated space on Disk Utility? Could I delete both partitions during the installation process of installing 11.04 of a cd?

I have all the individual documents I want on backup. Would you recommend I simply install 11.04 and on the installation process delete both partitions?

---

### Post by Bucky Ball on 2011-05-23
11.04 could equal a world of pain. I would go for the current long-term release, 10.04 LTS, unless you want to spend some time nutting out bugs and fiddling in the terminal.

Back up your important data and start again I would say. Good luck. ;)

---

### Post by wilwil0 on 2011-05-23
Good thinking, I'll do 10.04 LTS :)

Can I do all those things (deleting partitions) on the installation of 10.04 LTS?

---

### Post by coffeecat on 2011-05-23
Your Ubuntu partitions are inside an extended partition. If you wanted to enlarge them, you would have to enlarge the extended partition first which is a bit fiddly but quite doable. But not with Disk Utility and not while using your permanent installation. You would have to use Gparted from the live CD.

If you are thinking of doing a fresh install of 11.04, then the easiest option would be to start the installer and choose the "use whole disk" option". I believe that in 11.04 this option is now called "Erase Disk and install Ubuntu". That would certainly overwrite all your existing partitions and use all available space.

If you are thinking of jumping directly to 11.04, a couple of suggestions/comments. Try running the 11.04 desktop live before you install - choose the "try Ubuntu" option when you boot up the CD. Some people are reporting difficulties with some hardware. Also, you won't see the Unity desktop in the live session if you have a nvidia card; this needs the proprietary driver installed.

However, don't believe all the negativity and alleged bugs you will read about 11.04. It's as stable as a rock on four different machines in this household.

---

### Post by Bucky Ball on 2011-05-23
Maybe, coffeecat, but OP would rather not use a terminal and I'm guessing you did just a bit of that while getting those four machines running faultlessly! For a lot of people 11.04 is posing problems, as evidenced by the number of threads concerning it on the forum. ;)

In answer to wilwil0, yes, you could delete the partitions and repartition during the install procedure. It is like using the Gparted from the LiveCD (as suggested my ccat). Use manual partitioning and delete the ones you don't want (this includes windows).

You could stretch partition from the LiveCD but if you were wanting to upgrade to a supported release you would be reinstalling anyway, so ...

---

### Post by wilwil0 on 2011-05-23
Thanks for all the advice people it has been very helpful :)
I can always upgrade to 11.04 from 10.04 LTS and I'll try out 11.04, I tend to find criticisms of bugs in Ubuntu are exaggerated.

---

### Post by coffeecat on 2011-05-23
> **Bucky Ball said:**
> Maybe, coffeecat, but OP would rather not use a terminal and I'm guessing you did just a bit of that while getting those four machines running faultlessly!

The trouble with guesses is that they can often be very wrong! I've had no bugs to fix, with or without the terminal.

> **wilwil0 said:**
> I tend to find criticisms of bugs in Ubuntu are exaggerated.

Someone after my own heart! :wink: Good luck with whatever you choose.

---

### Post by wilwil0 on 2011-05-23
Ok, one more question. If I delete the Windows partition what effect will this have on the grub when booting up? The box asking which partition you would like to go on, Windows or Ubuntu.

---

### Post by coffeecat on 2011-05-23
If you are not re-installing and simply delete the Windows partition, run this code:

```
sudo update-grub
```

... and the Windows entry will disappear from the grub menu.

But I thought you decided to re-install and use the whole disc. In which case the installation will create a new instance of grub and there will be no Windows menu entry.

---

### Post by wilwil0 on 2011-05-23
Yeah, I just wasn't sure what happened if there was only the Ubuntu partition. Thanks everything is fine :D

---

### Post by Bucky Ball on 2011-05-23
> **coffeecat said:**
> The trouble with guesses is that they can often be very wrong! I've had no bugs to fix, with or without the terminal.

I stand corrected. You are one of the lucky ones. Good luck and have fun all. ;)

---

### Post by coffeecat on 2011-05-24
> **Bucky Ball said:**
> I stand corrected. You are one of the lucky ones. Good luck and have fun all. ;)

And good luck with whichever version of Ubuntu you prefer. I'm sorry if you are one of the ones experiencing bugs with Natty. Hopefully, the worst will be ironed out soon. I remember a year ago there was a tide of complaints about bugs in Lucid when it was first released. People were saying it was a disgrace that an LTS should be released in such a state. The weeks passed, the complaints diminished, and now people recommend it over later versions. :) That's life!

---

