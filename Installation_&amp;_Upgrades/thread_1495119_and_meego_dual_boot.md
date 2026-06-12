---
title: "and meego dual boot?"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by steve19137 on 2010-05-27
see, ive used and done moblin/unr dual boots before, and they are pretty successful. but now that meego is out, im done with moblin. but i have a problem. when you went through the moblin installer, you were able to choose where you install the bootloader. now, in the meego installer, you cant. it automatically overwrites the current bootloader, which the ubuntu grub2 bootloader. i want to chainload the ubuntu grub2 from the moblin grub2. how can i do that? or is this kind of configuration that people havent had the chance to smooth out yet?

---

### Post by afonteijn on 2010-06-04
I second this question. I would like to run meego next to the unr and windows xp installations that I currently have. How would I go about this? Ubuntu and xp are already installed. 

Just a thought, is it possible to just install meego and later on restore the boot loader to see meego, ubuntu and xp?

---

### Post by haruspexed on 2010-06-30
... install windows / anyother first
... then install meego
... then install ubuntu.

ubuntu grub2 will show meego and others n bootlist

you also could manually patch bootloader to list the os but thats not handy...

---

### Post by The2DQuartet on 2010-07-09
> **haruspexed said:**
> ... install windows / anyother first
... then install meego
... then install ubuntu.

ubuntu grub2 will show meego and others n bootlist

you also could manually patch bootloader to list the os but thats not handy...

I was trying to sort out a similar setup but with only UNR and MeeGo (no Windows installation) and I couldn't get it to work either way. I've been running Ubuntu for a few days then today installed Meego, but its bootloader -- MeeGo uses extlinux -- wouldn't recognise or boot Ubuntu either by adding it as an option during installation or after I added it to */boot/extlinux/extlinux.conf*

To try and mend the problem I reinstalled UNR alongside MeeGo but it said it was unable to install grub2 on any partition, so I selected the option to proceed without a bootloader. I thought I could at least add it later, but when I rebooted after the installation finished it picked up what I think was the existing grub2 installation.

Long story short, using grub I can now boot into either UNR or an 'unknown Linux distribution' (grub2 doesn't seem to know what MeeGo is but at least it knows it's there!)

---

### Post by marshcast on 2011-01-23
> **haruspexed said:**
> ... install windows / anyother first
... then install meego
... then install ubuntu.

ubuntu grub2 will show meego and others n bootlist

you also could manually patch bootloader to list the os but thats not handy...

no, I think that's the point of the thread.... there is no entry for unknown linux partition. just when updating grub.

at least that's the prob i have, so that's how i read it.

am i wrong?

---

