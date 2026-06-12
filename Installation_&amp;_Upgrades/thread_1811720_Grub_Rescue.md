---
title: "Grub Rescue"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by ninjaschwa on 2011-07-25
Hello,

I will start by saying I have searched and searched for solutions to my problem but I cannot find much that is close enough to my particular conundrum (nothing that works at least).

The laptop I'm trying to sort (for a friend) is an Acer Aspire 5100 which I did have dual booting Windows XP and Ubuntu 11.04, however, they did not play nice together so I got rid of the Ubuntu partition.

Rather foolishly I simply wiped the Ubuntu partition in Windows and reset, so now Grub won't work and I am simply dumped to:

```
grub rescue>
```

Now, I know there is a working version of XP on there in its' own partition but I cannot boot it to fix the MBR, I also cannot use a LiveCD because everyone I try I get a kernel panic:

```
cannot open root device "(null)" or unknown-block(8,1)
```

and

```
unable to mount root fs on unknown-block(8,1)
```

I have tried appending a correct "root=" tag in the boot line, but I get the same message for each except "(null)" is replaced with the relevant tag.

Any clues?

Thanks in advance!

Josh

EDIT: I also forgot to mention that I cannot access the recovery partition with alt+F8 as I should be able to, otherwise I would have tried to recover from there, since I do have a recovery partition I do not have a Recovery CD, figures eh? :)

---

### Post by YannBuntu on 2011-07-25
Hi
Did you try booting on a Ubuntu live-USB ?

---

### Post by ninjaschwa on 2011-07-25
I have done so as-per-your suggestion, but to no avail. I have tried several different usb drives and both 11.04 and 10.04LTS and each time I get "failed to install bootloader". I think Linux problems just gravitate towards me :P

---

### Post by tlcstat on 2011-07-25
Greetings,
If you have a second computer I suggest you download Super Grub and create the Super Grub boot disk. After you boot the disk you can patch your boot sector to point Grub to the Windows system. After you have your XP booting you can reinstall your dual boot or what ever you want to do.
tlcstat

---

### Post by ninjaschwa on 2011-07-25
Thanks for the tip, I used a similar method in the end and burned a Trinity Rescue Kit CD to rewrite the MBR; now it boots Windows fine... my new problem is keeping the blasted thing stable long enough to find a way of gaining access to the "e-recovery" partition!

Thanks for the help anyway :)

---

