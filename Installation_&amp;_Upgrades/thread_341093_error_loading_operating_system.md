---
title: "error loading operating system???"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by nkko on 2007-01-18
please help! :)

I pop in CD 6.06.1... ubuntu live boots... i start installation from it...

my conf is:
Promise RAID: 
2*160GB mirror (sata) with Windows XP on them (boot)
1*40GB stripe - 64kb - (ide) blank (non-boot)

than i chose 40gb disk to install Ubuntu on... disk is erased and partitioned.

i reset pc and in raid setup menu chose 40gb disk as boot drive... after that i get message:

"error loading operating system"

how can i solve this? please help?

---

### Post by nkko on 2007-01-18
anyone??? please

---

### Post by goodfella on 2007-01-18
I had the same problem; however I do not have a raid set up.  What I did to fix it was I booted from the live using the **Boot From First Hard Drive** option.  I then typed in the following command in the terminal:

```
grub-install /dev/hd0
```

/dev/hd0 is the drive where my linux installation is on.  It is also my first bootable drive as set in my bios.  It seems that the number grub assigns drives is related to the boot order.  Since my linux drive is my first bootable hard drive it has a number of 0 hence hd0.

If choosing the option **Boot From First Hard Drive** does not work then select the first option from the live cd, I don't remember the name of it, and follow this post [grub tips]("http://www.ubuntuforums.org/showthread.php?t=334149")

One thing to remember his how linux and grub differ in the way they reference drives.  Linux uses letters and numbers while grub uses just numbers.  

For example the above drive (/dev/hd0) in grub is of course /dev/hd0.  In linux it is referred to as /dev/hda.  

Also partitions in linux start at 1 but partitions in grub start at 0.  

For example the first partition in on my first drive in linux is referred to as /dev/hda1 while the first partition on my first drive according to grub is (hd0,0).

Let me know if this helps.

---

### Post by nkko on 2007-01-18
...uf.. :)

Thanks, I'll try it!

---

### Post by Straft on 2007-01-20
> **goodfella said:**
> I had the same problem; however I do not have a raid set up.  What I did to fix it was I booted from the live using the **Boot From First Hard Drive** option.  I then typed in the following command in the terminal:

```
grub-install /dev/hd0
```

/dev/hd0 is the drive where my linux installation is on.  It is also my first bootable drive as set in my bios.  It seems that the number grub assigns drives is related to the boot order.  Since my linux drive is my first bootable hard drive it has a number of 0 hence hd0.

If choosing the option **Boot From First Hard Drive** does not work then select the first option from the live cd, I don't remember the name of it, and follow this post [grub tips]("http://www.ubuntuforums.org/showthread.php?t=334149")

One thing to remember his how linux and grub differ in the way they reference drives.  Linux uses letters and numbers while grub uses just numbers.  

For example the above drive (/dev/hd0) in grub is of course /dev/hd0.  In linux it is referred to as /dev/hda.  

Also partitions in linux start at 1 but partitions in grub start at 0.  

For example the first partition in on my first drive in linux is referred to as /dev/hda1 while the first partition on my first drive according to grub is (hd0,0).

Let me know if this helps.


Hmm...I'm having the same problem. I did the "**Boot From First Hard Drive**" and it give me the same "Error loading operating systen" error,,,this is really annoying :(

---

### Post by Jori on 2007-12-27
Im having this problem as well.  Ubuntu has been nothing but a pain in the **** so far :/.  It wont let me do the manual grub install through terminal says permission denied or something to that effect.  Ive been wrestling with Ubuntu all day..  Ugh.  Why cant it just work.  Have to run it with noapic nolapic or else it wont even let me install, just goes to a black screen and hangs.

---

