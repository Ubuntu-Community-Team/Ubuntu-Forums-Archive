---
title: "Can't boot UBUNTU on dual boot system"
date: 2005-09-17
forum: Installation &amp; Upgrades
---

### Post by dai on 2005-09-17
Hi people - hope you can help.

After aeons of swithering I decided to go for it and install ubuntu on my PC. To start with I thought I would use a dual boot in case stuff went wrong.

I picked up an extra harddrive and added it as a slave so I could have a drive just for ubuntu. So the machine is:

PIII 500mhz (overclocked to 616)
256MB 

first hard drive - 20GB IBM - split into C: (5MB - boots Win ME), D: (10MB), E (5MB)
second hard drive - F: 8GB Seagate -  this is the one I installed ubuntu onto.

The CD rom portion of the installer ran fine, but when it rebooted to get onto the second stage of the installer my PC just booted windows and I can't find any way to boot the other drive into ubuntu and the final install pages.

Could anyone help me with:

- what I did wrong?

and

- how I can fix it?

Thanks in advance

Dai

---

### Post by docmanny on 2005-09-17
Try going into BIOS and changing the boot sequence. Have the new drive boot first.

If that works, do a search and modify the /boot/grub/menu.lst file to boot Windows too. I'm in the process of setting up my computer now, so I don't recall the exact specifics, but I've done it before! ;-)

---

### Post by dai on 2005-09-17
Thanks for your answer.

Tried that and still windows booted with no option to load ubuntu!

---

### Post by docmanny on 2005-09-17
When you installed ubuntu, where did you install grub. You may need to install it in the non-default location.

---

### Post by dai on 2005-09-17
[QUOTE=docmanny]When you installed ubuntu, where did you install grub. You may need to install it in the non-default location.[/QUOTE]
 update.

Sorry, am not ignoring your question, but have tried a few other things over the afternoon which may throw more light on to the problem.

Plugging the slave drive onto a different IDE from the main boot drive meant that I could fully install ubuntu and grub. However, grub didn't seem to want to load windows so I am reduced to swapping connections between boots. Ergh.

It seems that my slave drive is consistently numbered lower than my main drive. Main drive is usually shown as hd6 in partition manager section of install, whereas slave shows either as hd5 (PC just loads win directly) or hd2 (grub-ubuntu !windows).

So what I think has happened -coming back to your question! is that grub has installed itself on the lowest number drive (which is always the slave drive for some reason) and then can't find windows from there (don't know why).

*exasperation with self stupidity*

How can I install grub in a non-default place, as you suggest? The installer doesn't appear to offer any options.

---

