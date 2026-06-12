---
title: "upgrading headache"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by thedevilisbad on 2011-04-29
Hey guys,

Just got through my upgrade today. It took over 12 hours to download, the servers must have been packed.

It downloaded, then installed the packages. I got a ton of error messages during this part. Lots of issues with packages not upgrading.

When I booted up it wouldn't let me use unity, all of my indicators didn't work (using gnome), and my wifi quit. (I'm connect via ethernet to my router as I type.) I decided to open synaptic which then told me I had 74 broken packages. I've tried reinstalling and upgrading, nada :-/

Any ideas?

---

### Post by K_45 on 2011-04-29
Have you tried a clean Natty install?

---

### Post by lisati on 2011-04-29
Mental note for self: wait a few days before downloading, so the servers aren't so busy, and the process of dealing with any remaining kinks that come to light has begun.....

---

### Post by thedevilisbad on 2011-04-29
> **lisati said:**
> Mental note for self: wait a few days before downloading, so the servers aren't so busy, and the process of dealing with any remaining kinks that come to light has begun.....

I tell myself that every time I upgrade and this type of thing happens.




and no, I didn't do a clean install because I didn't want to deal with having to spend several hours backing up all my media files.

---

### Post by K_45 on 2011-04-29
> **thedevilisbad said:**
> I tell myself that every time I upgrade and this type of thing happens.




and no, I didn't do a clean install because I didn't want to deal with having to spend several hours backing up all my media files.

But the media files should already have been backed up safe just in case something like this happened . . . with broken updates.

---

### Post by thedevilisbad on 2011-04-29
> **K_45 said:**
> But the media files should already have been backed up safe just in case something like this happened . . . with broken updates.

yeah, yeah, yeah... I get the point


Is there a way to fix broken packages?

Luckily, my files are safe, it just seems to be a functionality issue.

---

### Post by K_45 on 2011-04-29
Try:

```
sudo apt-get install -f
```

---

### Post by thedevilisbad on 2011-04-29
> **K_45 said:**
> Try:

```
sudo apt-get install -f
```

Already doing it, thanks.

It's good these things happen to me. Now I'll be able to help other dumb people like myself in the future.

---

### Post by thedevilisbad on 2011-04-29
Alright, just tried it and now when I boot up nothing happens. I can't even choose recovery mode.

---

### Post by K_45 on 2011-04-29
No boot prompt? No drop down to command line? Can you hold down shift - does the GRUB menu - appear?

---

### Post by pinballwizard on 2011-04-29
> **thedevilisbad said:**
> Hey guys,

Just got through my upgrade today. It took over 12 hours to download, the servers must have been packed.



Any ideas?

Do you have an idea of how big the upgrade was? My mom asked last night cause she wants to upgrade, and I don't have time to go to her house.

---

### Post by thedevilisbad on 2011-04-29
I was able to boot into the recovery console using grub. From there I fixed the broken packages. I then rebooted and manually installed some of the missing packages. Voila!

Everything works now, thanks for the help everyone.

---

