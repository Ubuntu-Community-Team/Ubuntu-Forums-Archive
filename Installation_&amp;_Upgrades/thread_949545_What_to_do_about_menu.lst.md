---
title: "What to do about menu.lst"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by GregMB on 2008-10-16
NOTE: I have never upgraded the kernel before, so I'm kinda a newbie. That in mind, let me state my problem.

So, I decided to install all the updates that Ubuntu wanted me to, via the Update Manager. 10 minutes later a message pops up asking me what to do about menu.lst, with a list of about 6 items, and I have no idea what to pick. To the best of my memory, I've never edited menu.lst, but I bought my computer from a Linux OEM (Thanks, Zareason!), so maybe they did something with it. So, my simple question is, what the heck do I do? If you need more info, please ask.

---

### Post by shawnrgr on 2008-10-16
What are your options? Are they like... Merge, Update, Replace?

---

### Post by zvacet on 2008-10-16
That probably means that you have more then one kernel.If the newest runs O.K. you can delete old vesion.But to be sure run 

```
cat /boot/grub/menu.lst
```

and post it here.

---

### Post by GregMB on 2008-10-16
Well, I ended up picking "Install Package Maintainer's Version", which worked, sort of. There was an error with the computer's BIOS, preventing me from booting into Ubuntu, as it gave me a Kernel Panic. I ended up spending half an hour on the phone with Zareason, and have to send in my computer for repairs (thank god for warranties!). So I can't say if it worked or not. But I learned an important lesson about not installing updates. (Just kidding!) Anyways, thank you to everyone who tried to help!

---

### Post by NTolerance on 2008-11-03
I'm also wondering about the proper way to deal with debconf prompts and menu.lst.  All of my Ubuntu systems have a custom menu.lst for any number of reasons (dual boot, incorrect boot drive setting such as hd2,0, vga=791 for proper TTY resolution).  What's the right choice for kernel upgrades without removing custom options that can at best break your configuration or at worst prevent booting entirely?

---

### Post by NTolerance on 2008-11-06
bump for the most important part of the update process

---

### Post by caljohnsmith on 2008-11-06
> **NTolerance said:**
> I'm also wondering about the proper way to deal with debconf prompts and menu.lst.  All of my Ubuntu systems have a custom menu.lst for any number of reasons (dual boot, incorrect boot drive setting such as hd2,0, vga=791 for proper TTY resolution).  What's the right choice for kernel upgrades without removing custom options that can at best break your configuration or at worst prevent booting entirely?
If you're really concerned about your menu.lst being messed up by the automatic menu updater that happens with a new kernel upgrade, one solution would be to copy your menu.lst to a backup file, let the automatic updater do its job, and then if anything is wrong you can fix it by comparing it with your backed up menu.lst. But a better solution would be to make sure you have the following lines correct in your menu.lst:
```

# kopt=root=UUID=[COLOR="Blue"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro
# groot=[COLOR="Blue"](hd0,1)[/COLOR]
# defoptions=[COLOR="Blue"]quiet splash[/COLOR]

```
So even though those lines are "commented", they are used by the automatic grub updater (the "update-grub" command) when updating your menu.lst with a new kernel for example. So make sure the kopt line has the correct UUID for your main Ubuntu partition, the groot line should give the partition of either your /boot partition (if you have one), or your main Ubuntu partition. Also, with intrepid, the groot line can now use the UUID of the partition rather than the (hdX,Y) notation if you want. And lastly, just add your "vga=791" option to the "defoptions" line, and that will automatically be included next time the menu.lst is updated. Is that maybe what you are looking for?

---

### Post by NTolerance on 2008-11-06
> **caljohnsmith said:**
> If you're really concerned about your menu.lst being messed up by the automatic menu updater that happens with a new kernel upgrade, one solution would be to copy your menu.lst to a backup file, let the automatic updater do its job, and then if anything is wrong you can fix it by comparing it with your backed up menu.lst. But a better solution would be to make sure you have the following lines correct in your menu.lst:
```

# kopt=root=UUID=[COLOR="Blue"]77677cb5-6e56-4936-a373-80c15de06bca[/COLOR] ro
# groot=[COLOR="Blue"](hd0,1)[/COLOR]
# defoptions=[COLOR="Blue"]quiet splash[/COLOR]

```
So even though those lines are "commented", they are used by the automatic grub updater (the "update-grub" command) when updating your menu.lst with a new kernel for example. So make sure the kopt line has the correct UUID for your main Ubuntu partition, the groot line should give the partition of either your /boot partition (if you have one), or your main Ubuntu partition. Also, with intrepid, the groot line can now use the UUID of the partition rather than the (hdX,Y) notation if you want. And lastly, just add your "vga=791" option to the "defoptions" line, and that will automatically be included next time the menu.lst is updated. Is that maybe what you are looking for?

That definitely helps.  Now all I need to know is which of the 6 or so options to choose from when debconf prompts come up during a kernel upgrade.  I don't remember what the options are though.  Something about keep current, install package maintainer's version, 3-way merge (experimental), etc...

---

### Post by NTolerance on 2008-11-19
bump

---

### Post by NTolerance on 2008-11-28
New kernel update came out today so I got a chance to try my luck.  The default option is "keep the local version currently installed".  This will leave your menu.lst untouched, and therefore you won't be running the new kernel.  Instead I chose "install the package maintainer's version".  This installed the new kernel into menu.lst, preserved my dual-boot option for Windows XP, and added the vga=791 command that I had set up in the defoptions section.  So this appears to be the way to go.

---

