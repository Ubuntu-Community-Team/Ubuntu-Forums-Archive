---
title: "newbie in need of help- I think I have kernel problems"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by phoenixrosebud on 2008-07-23
I don't know if my computer is salvagable. :(

I upgraded all the way to Hardy Heron but I was having problems with Firefox randomly crashing and my computer crashing (to the point of having to hard-boot it) when I attempted to copy materials from a DVD to my computer.

After looking through many threads on the Absolute Beginners board, it seemed that many people with a similar problem to mine solved it by using a real time kernel. So I switched my system to kernel-rt and it seemed to work okay (though it didn't fix my crashing problems). The next day, I started my computer and I had a **lot** of updates to install, so I clicked to automatically install them-but I was still doing work on my computer in Firefox and other programs-(and I think that's how I caused some problems for myself).

When I restarted my computer to finish the upgrades, my computer wouldn't fully start. It would get frozen with a plain tan background with the unmoving mouse cursor of doom. If I remember correctly, it usually happened before I logged in, but occasionally I would log in and *then* it would give me that screen of doom after cruelly getting my hopes up. 

I tried the elephant acronym trick to try to get out of the freeze, but nothing seemed to work besides hard-booting my computer. 

So, I went back to square one. I reinstalled Feisty Fawn (the install/boot disc that I have), and then tried upgrading back up to Hardy Heron, but the install froze partway through and now I can't log in normally. I can log into the failsafe or Gnome modes, but then I don't have access to the internet, and without Ubuntu Forums, I'm pitiful with Ubuntu. Another odd thing is that the error "Failed to Initialize Hal!" comes up when I am able to start the system, but as far as I can tell, that just has to do with energy saving modes. 

What should I do? Should I try reinstalling from Feisty Fawn back up to Hardy Heron again? 

Help! Please! :confused: 

I don't know all of my computer's specs, but it is about 5 years old, an Athlon 2400+, >100 GB hard drive, and 32 Bit.

---

### Post by ilrudie on 2008-07-23
Can you run memtest?  Usually when the computer boots it will say something like press escape for a boot menu.  One of the options should be something like Ubuntu-<something>memtest86+.  You should also be able to run it from the install cd if you can't run the installed one.  Run that and make sure your memory is not failing.

Next, instead of reinstalling from Feisty and upgrading have a friend get the latest Hardy image off the website and burn it for you.  You should always verify the disk before installing.  As a side note it is good idea to have the latest verified install media around.  You never know when you are going to need it.

Also HAL is the hardware abstraction layer.  You are going to want that to work.

Regarding the real-time kernel:  I think this mostly benefits music/video recording software.  I can't think of why you would need it for general use.  I would recommend sticking with the generic kernel once you get Hardy going again.

Good luck.

---

### Post by Rayaz on 2008-07-23
Hi there, if you have a CD writer why not download Hardy .iso and start from there?

---

### Post by phoenixrosebud on 2008-07-24
Thank you illrudie! I will definitely try to see if I can do that, and I'll report back.

Rayaz-I will try that. I need to look up how to use .iso files though, because I had trouble figuring out how to run the disc that I had made of Hardy previously. I didn't check the disc though, so maybe it didn't copy correctly.

Thanks!

---

