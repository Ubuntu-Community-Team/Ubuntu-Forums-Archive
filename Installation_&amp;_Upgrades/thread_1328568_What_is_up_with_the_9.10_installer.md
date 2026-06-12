---
title: "What is up with the 9.10 installer?"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by futz on 2009-11-16
I've been running Ubuntu since somewhere around 2004ish. I've installed Ubuntu probably hundreds of times on lots of various machines, both multi-boot and standard boot. I just tried to install 9.10 on two different machines and had total failure on both.

I'll just stick to the simple one for this post. The machine is a Gigabyte [GA-8IG1000MK]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1655") mainboard with 1GB RAM and just a single small SATA drive. Not too modern, but not a total antique either.

I boot off the 9.10 CD and when I hit step 4, the partitioner, it pops up with a blank screen, like it can't find any partitions at all. Huh??? I tried various changes in the BIOS. Nothing helps.

When I tell the installer to cancel the install at step 4, it boots to a live disk session. I can run the gparted there and see the drive partions (from an old 8.10 install) and can even mount the drive and look at the files on it. Here's a screenshot with the installer upper left - showing the blank partitioner, gparted bottom right and Nautilus upper right showing the root partition:
[ATTACH]136486[/ATTACH]

---

### Post by htfntuna on 2009-11-16
The installer is a little buggy.
 
See my post just after yours - not the same problem, but still a problem.
 
Another thing I have noticed is that the installer gets the system time wrong. Minor, yes, but annoying, since you cannot correct it at that time.
 
Minor issues often bespeak larger ones. I'm not sure this release was entirely ready for the general public.

---

### Post by futz on 2009-11-16
> **htfntuna said:**
> The installer is a little buggy.
Hehehe :D A little? I call that totally broken.

I had massive problems with the install on the other machine too, but the partitioner worked fine there. That one is not nearly so simple as this one - there are drive partitions there that MUST be saved, so I have to be careful how I do it. Right now it won't boot at all, even though it successfully booted a couple times after installation. It broke on its own, too. I changed nothing to cause it. Weird.

Anyway, my main machine (running 8.10) is NOT getting "upgraded" to 9.10 until this gets cured. Think it might stay at 8.10 till 10.04 comes out.

---

### Post by dhavalbbhatt on 2009-11-16
Try using the Alternate installation CD - that fixed the issue for me. Basically, all I can tell is, partition manager in Desktop installation seems to be buggy. Alternate installation CD uses a different partition manager (?), which seems to fix the issue.

---

### Post by futz on 2009-11-16
> **dhavalbbhatt said:**
> Try using the Alternate installation CD - that fixed the issue for me. Basically, all I can tell is, partition manager in Desktop installation seems to be buggy. Alternate installation CD uses a different partition manager (?), which seems to fix the issue.
They still have an alternate CD? I used to use that all the time. Thought they got rid of it. Thanks. :)

---

### Post by htfntuna on 2009-11-16
[quote="futz"]Anyway, my main machine (running 8.10) is NOT getting "upgraded" to 9.10 until this gets cured. Think it might stay at 8.10 till 10.04 comes out.[/quote]
I do want to say that 9.04 has been the most satisfying Linux of any flavor I have tried. Ubuntu definitely gets it right most of the time. I'm not sure embracing Grub 2 at this stage is the best strategy, though.

---

### Post by futz on 2009-11-16
Hahahahahaaha. :D What a busted piece of crap! Burned an alternate CD and installed. It gets to the cleanup stage and at 17% it locks up and that's all she wrote.

Sigh... Guess I go back to 9.04 for this little box. 9.10 isn't worth the fight.

---

### Post by futz on 2009-11-16
OK, I take back that last post. The reason it puked is that while waiting for the install to complete, I flipped to the other machine on this KVM. The installer can't cope with KVMs I guess. So I installed the alternate CD again and just waited it out and it finished fine.

---

