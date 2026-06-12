---
title: "Some things to think about for the hardy to lucid upgrade"
date: 2009-10-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by whoop on 2009-10-29
Whenever I install ubuntu on somebodies machine, I tend to give them the LTS hardy (just too keep them of my back for a wile ;-) ). All these people will be upgrading when Lucid becomes available.

This made me think about grub and ext:

Do you think the lucid upgrade process should/will assist in the optional/required upgrade from grub1 to grub2?

Do you think the lucid upgrade process should/will assist in the optional/required upgrade from ext3 to ext4?

For grub I think yes (optional upgrade).
For ext I don't know (yes, optional <-- why not)(no, I tend to see ext4 as an intermediate fs between ext3 and btrfs, but I could be wrong).

---

### Post by Twintop on 2009-10-29
> **whoop said:**
> Do you think the lucid upgrade process should/will  assist in the optional/required upgrade from grub1 to grub2?

This is tricky...does anyone know how well Ubuntu currently does grub1->grub2 transitions? This is probably a much bigger concern for systems that have custom grub setups (more than just Ubuntu or Ubuntu/Windows). Probably make this optional...

> **whoop said:**
> Do you think the lucid upgrade process should/will  assist in the optional/required upgrade from ext3 to ext4?

Can't ext3 be mounted as ext4, sans some ext4-specific features? Again, I'd say make this optional, but default to mount as ext4.

---

### Post by zekopeko on 2009-10-29
> **Twintop said:**
> Can't ext3 be mounted as ext4, sans some ext4-specific features? Again, I'd say make this optional, but default to mount as ext4.

Yes, ext3 can be mounted as ext4 but I don't see the point. AFAIK the best parts of ext4 are only enabled if you formated the partition to ext4 from the start. Not to mention that once you mount it to ext4 there is no turning back. I think that this should be left up to the user.

---

### Post by qamelian on 2009-10-29
> **zekopeko said:**
> Yes, ext3 can be mounted as ext4 but I don't see the point. AFAIK the best parts of ext4 are only enabled if you formated the partition to ext4 from the start. Not to mention that once you mount it to ext4 there is no turning back. I think that this should be left up to the user.
You're right. The only files that benefit from mounting ext3 as ext4 are any that are newly created (or maybe those modified as well, but I don't think so) after doing so. You really only get minimal, essentially almost unnoticable benefit without starting of fresh with a partition that begins it's 'life' as ext4.

---

### Post by whoop on 2009-10-29
> **qamelian said:**
> You're right. The only files that benefit from mounting ext3 as ext4 are any that are newly created (or maybe those modified as well, but I don't think so) after doing so. You really only get minimal, essentially almost unnoticable benefit without starting of fresh with a partition that begins it's 'life' as ext4.

Isn't modifying a file (excluding stuff like touch) essentially the same thing as rewriting the file; which is somewhat the same as a newly creating a file?

---

### Post by slakkie on 2009-10-30
> **whoop said:**
> Isn't modifying a file (excluding stuff like touch) essentially the same thing as rewriting the file; which is somewhat the same as a newly creating a file?

No. [http://ubuntuforums.org/showthread.php?t=1293615](http://ubuntuforums.org/showthread.php?t=1293615)

The inode isn't touched, so you still have an ext3 file when you write to an existing file.

---

### Post by flipper9 on 2009-10-30
> **slakkie said:**
> No. [http://ubuntuforums.org/showthread.php?t=1293615](http://ubuntuforums.org/showthread.php?t=1293615)

The inode isn't touched, so you still have an ext3 file when you write to an existing file.
Is there a way, or maybe it needs to be added, where you could have a temporary mode during upgrade of the OS or maybe running a tool to have each file recreated instead of just written?

---

### Post by ronacc on 2009-10-30
I updated my multi boot multi distro (no windows ) test box as soon as grub2 hit the repos ( I had started at toolchain upload ) and it went off with only 1 minor hitch , probably caused by my strange custom set up . Ranch hand has a good introduction to grub2 posted in the karmic forum ( you can access the forum you just can't add to it ).

---

