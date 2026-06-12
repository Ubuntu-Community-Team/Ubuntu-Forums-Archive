---
title: "Several upgrade paths blocked"
date: 2018-08-28
forum: Installation &amp; Upgrades
---

### Post by daniel-clement on 2018-08-28
Hello,

My wife's laptop is still running 14.04; it might be a good idea to upgrade. But I have 3 issues:
- the update manager, even if I run it with -d parameter, doesn't offer the next LTS (I guess this is because we somehow skipped 16.04);
- (in case of reinstall) the laptop (a Dell XPS 13) now refuses to boot from USB (though it did before). Maybe it doesn't like the bootable USB stick created with another PC, but then...
- its own USB disk creator fails to complete. After pointing it to the desired ISO, it gives an error message telling that it cannot create the USB stick.

Now, I know these are different issues, but it's almost checkmate here. What would be my best option? I know that the upgrade can be triggered from the command line, but I have never tried that.

I would rather not break anything, so any insight welcome. Regards, Daniel

---

### Post by Autodave on 2018-08-28
First off, at this point I would back up everything that you cannot afford to lose!!!

My suggestion would be a clean install especially since 14.04 is currently on there.

As far as the USB stick is concerned, you could have a bad stick: they do fail quite often.  Does that machine have a DVD drive in it? If so, you could boot from that. There is also the possibility of a bad download of the .iso.

The machine that was used to create the USB: can that machine boot from the created USB?

---

### Post by daniel-clement on 2018-08-28
Thanks for replying Autodave, here is more info:
> **Autodave said:**
> First off, at this point I would back up everything that you cannot afford to lose!!!No problem with that, the /home is separate and all the important files are backed up real-time to a NAS device.
> My suggestion would be a clean install especially since 14.04 is currently on there.Yes that's what I would prefer (I'd like to do some testing in a live session). But I've got nothing to boot from so far...
> As far as the USB stick is concerned, you could have a bad stick: they do fail quite often.  Does that machine have a DVD drive in it? If so, you could boot from that. Alas no, it's an "ultrabook" (is that correct?)
> There is also the possibility of a bad download of the .iso.Yes but I had ruled that out (as well as the bad stick) because...
> The machine that was used to create the USB: can that machine boot from the created USB?Yes, indeed! Even another machine, though none of them is running Ubuntu.

Actually, this Dell ultrabook has already booted from USB before. I'm quite sure this is precisely how I installed 14.04 (fresh install). Of course I could grab a removable DVD, but I really wish I could get back the ability to boot from USB.

---

### Post by daniel-clement on 2018-08-29
Well, problem almost solved, because I managed to get a working USB key to boot from (another key, made from a Debian PC).

So I think we'll go for a fresh install, which we'll do quietly after double-checking what must be saved. It might be even quicker than a double upgrade 14.04 -> 16.04 -> 18.04.

Thanks again - best regards, Daniel

---

