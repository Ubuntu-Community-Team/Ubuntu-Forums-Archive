---
title: "Moving Installation"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by OutlandishKnight on 2012-03-22
I was a bit torn which section to put this in. It was a toss-up between here and hardware, and since I can see the case for either I'm hoping this forum is fine.

I'm getting a new laptop for various reasons, and it would be nice and, due to busy-ness, very useful to recreate my current setup as quickly and easily as possible. I've heard from some places that with Ubuntu, unlike Windows, you can just move the hard drive across. This would obviously be great but, having Googled to double check that it actually works, I've come across conflicting reports. Some say absolutely not. Others say yes, all the drivers etc will be sorted automatically, and it will work just fine. Others still say it won't be automatic, but it's an easy process and then it works fine. 

None of those results I found came from this forum, which for obvious reasons I trust in matters Ubuntu, so I thought I'd ask. Can anyone give me a definitive answer?

---

### Post by ajgreeny on 2012-03-22
> **OutlandishKnight said:**
> I was a bit torn which section to put this in. It was a toss-up between here and hardware, and since I can see the case for either I'm hoping this forum is fine.

I'm getting a new laptop for various reasons, and it would be nice and, due to busy-ness, very useful to recreate my current setup as quickly and easily as possible. I've heard from some places that with Ubuntu, unlike Windows, you can just move the hard drive across. This would obviously be great but, having Googled to double check that it actually works, I've come across conflicting reports. Some say absolutely not. Others say yes, all the drivers etc will be sorted automatically, and it will work just fine. Others still say it won't be automatic, but it's an easy process and then it works fine. 

None of those results I found came from this forum, which for obvious reasons I trust in matters Ubuntu, so I thought I'd ask. Can anyone give me a definitive answer?
I don't think anyone will be foolish enough to give you a straight yes or no answer, as the real answer is "it will depend on the old and new hardware".

However, it is something that is definitely worth trying and you may be very surprised that you can get the system to boot to a desktop, even if it is not quite the correct resolution, or something else not quite right.  Perhaps it will need nothing more than a new graphics driver installed; that is the most likely problem, but again, it will depend on the old and new graphic card used.

Go for it;  there's nothing to lose except a few minutes of your time changing the disk, and there is little risk.  If it a hopeless failure you still have the old machine with the old disk/setup to use as a template for the new machine.

---

### Post by OutlandishKnight on 2012-03-23
Thanks very much. I knew it wasn't likely to be a straight "yes," but I'm glad it's far from a straight "no."

---

### Post by sudodus on 2012-03-23
If you want to move your HDD, good, but there is also another option: to clone it to a drive of at least the same size. And then put the cloned drive into the new computer.

As pointed out by *ajgreeny*, you might get problems with a proprietary driver for graphics. One obvious solution might be to disable it in the old computer and enable the built-in standard graphics driver before moving or cloning the drive.

What graphics chips or cards are there in the old and new computers?

---

### Post by QIII on 2012-03-23
Just to add to ajgreeny -- to make explicit a couple of things that are implicit.

Do backups!

Remove all additional drivers first.

I've had switches like this work sometimes and fail sometimes.  In one case, I couldn't get back up even by putting the disk back in the original machine.

---

### Post by OutlandishKnight on 2012-03-23
Thank you for your additions. I will of course back up stuff first, in case, and following your advice I will remove drivers before putting it in the new machine.

Regarding graphics, that is one thing that will definitely need at least a change of driver. I'm moving from a machine with NVIDIA GeForce 8400M G to an ATI chipset (don't have the actual machine in my possession yet and am not sure which exact model, but I believe it should have either Mobility Radeon HD2600 or Radeon X1200).

---

