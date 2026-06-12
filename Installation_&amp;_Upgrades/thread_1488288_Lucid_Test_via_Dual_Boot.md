---
title: "Lucid Test via Dual Boot?"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by leehach on 2010-05-19
I'm planning to upgrade from Hardy to Lucid. A previous attempt to upgrade to Intrepid failed miserably, so I reinstalled Hardy and have stuck with it until the next LTS. I'd like to avoid another disaster, so I'm thinking about trying out Lucid as a dual boot first.

My system is currently dual boot Vista / Hardy. I*have separate partitions for / /home /data, so what I'd like to do install Lucid on / and have it use the preexisting /home and /data. 

I have not dual booted two different Ubuntus, so my general question is, how should I*plan for it and what should I keep in mind? Already have seen the problems with grub2 all over the forums, so I think I'll be able to avoid that, but what else should I know?

Thanks,
--Lee

---

### Post by lemming465 on 2010-05-21
The first thing I'd do in your situation is stuff in a live desktop CD of lucid and see how that went.  If it likes your hardware, an upgrade will probably succeed. 

On systems where I'm planning to test upgrades, I like to have at least one spare partition of 10-20 MB for parallel installs.  If you haven't got one, and can't easily create one by shrinking an existing partition, you might want to consider an external disk or flash drive as an install target.  Just don't let the installer put a new grub on the MBR in this case, you would want to pick the "advanced" option and direct it elsewhere, usually to the new root partition instead.

Doing a fresh install of Lucid onto / while keeping a /data partition would be OK, but you might run into issues on /home with unconverted incompatible "dot" files full of application configuration data.  In your case I'd actually recommend either backing up /home and restoring just the visible files afterwards, or doing an in-place upgrade from hardy to lucid.

I haven't personally had any issues with grub2, other than it being a little different from grub1, and by now the grub2 help and directions are pretty good, so have no fear of it.  You don't have to replace an existing grub1 with grub2 unless you want to, but on new installs it's OK.

---

### Post by kansasnoob on 2010-05-21
> **leehach said:**
> I'm planning to upgrade from Hardy to Lucid. A previous attempt to upgrade to Intrepid failed miserably, so I reinstalled Hardy and have stuck with it until the next LTS. I'd like to avoid another disaster, so I'm thinking about trying out Lucid as a dual boot first.

My system is currently dual boot Vista / Hardy. I*have separate partitions for / /home /data, so what I'd like to do install Lucid on / and have it use the preexisting /home and /data. 

I have not dual booted two different Ubuntus, so my general question is, how should I*plan for it and what should I keep in mind? Already have seen the problems with grub2 all over the forums, so I think I'll be able to avoid that, but what else should I know?

Thanks,
--Lee

You'll have major problems trying to share /home between Hardy and Lucid! There are too many changes in .gconf, .gconfd, and .gnome2 just to mention a few.

I suppose it can be done if you use different usernames for each but that rather defeats the purpose :) That is you'll face permission problems, etc.

Would you mind posting a Gparted screenshot of your drive layout?

I'm thinking a new / and a new /home would be great if you have the space and it's truly viable. Then you could transfer the data from your old /home after you know Lucid runs well for you.

And, of course, your /data partition would have to mounted after installation anyway.

Or, if you can spare a 6GB partition for testing, you could just install Lucid into a testing partition and if all works out well then you could reinstall over the Hardy partitions being certain NOT to format it's /home.

---

