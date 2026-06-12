---
title: "GNU GRUB Loader menu"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Tejus on 2009-12-06
Hey! I just made my system dual boot by installing WinXP followed by Ubuntu koala. They are both installed on the same hard drive.

Right after installing Ubuntu completely, the GRUB loader gave me these options at startup:

```
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows XP Media Center Edition (on /dev/sda1)

```I wanted to find out how to move the windows option to the first slot so my dad can access it more easily.

After starting Ubuntu the first time, it updated a few things. After downloading the updates, a window came up asking something along the lines of what to do with the grub loader as it had updated, and the entries right now are not default. There were a few options like use the default one in the repository maintainer, or keep the current settings, or see the difference side by side, and some other similar stuff.

I selected keep current settings.

Now, the GRUB screen on startup reads:

```
GNU GRUB 1.97~Beta4

Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows XP Media Center Edition (on /dev/sda1)

```I hope nothing has gone wrong. If everything is fine:
1.How can I remove those Ubuntu options that have -14
2.How can I move Windows up to the first slot?
3.What are those Memory test options?

---

### Post by phillw on 2009-12-06
> **Tejus said:**
> Hey! I just made my system dual boot by installing WinXP followed by Ubuntu koala. They are both installed on the same hard drive.

Right after installing Ubuntu completely, the GRUB loader gave me these options at startup:

```
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows XP Media Center Edition (on /dev/sda1)

```I wanted to find out how to move the windows option to the first slot so my dad can access it more easily.

After starting Ubuntu the first time, it updated a few things. After downloading the updates, a window came up asking something along the lines of what to do with the grub loader as it had updated, and the entries right now are not default. There were a few options like use the default one in the repository maintainer, or keep the current settings, or see the difference side by side, and some other similar stuff.

I selected keep current settings.

Now, the GRUB screen on startup reads:

```
GNU GRUB~Beta4

Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows XP Media Center Edition (on /dev/sda1)

```I hope nothing has gone wrong. If everything is fine:
1.How can I remove those Ubuntu options that have -14
2.How can I move Windows up to the first slot?
3.What are those Memory test options?

Hi, A good introduction to Grub2 which covers the things you want is over here --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It is always advisable to keep the LAST known working Kernel (14, in this case) in case you find that the new kernel doesn't like a part of your computer suddenly !!

MemTest is for checking the RAM on your computer - you can remove it from the list if you want.

Regards,

Phill.

---

### Post by Tejus on 2009-12-06
Sorry, forgot to write the version of grub in the first post. It says GRUB 1.97 Beta 4. So does that link you sent apply to me?

---

### Post by darkod on 2009-12-06
Yes, grub 1.97 is in fact grub2. 0.97 is grub1.

Easy way to move windows to first spot is to go to /etc/grub.d folder and make a copy of the file 30_os-prober. Then rename the copy to 06_os-prober. Then in terminal execute:
sudo chmod +x /etc/grub.d/06_os-prober
sudo update-grub

Reboot and check the menu. There should also be windows entry on the top. Check whether it's working fine. If it is, let us know and I'll tell you how to remove the unneeded entry at the bottom and the memtest entries.

Note: If this works at first the windows on top will become default if nothing is pressed. But that can be changed too if you want.

---

### Post by Tejus on 2009-12-06
I have to rename the file so it begins with 06, and then delete the old file that began with 30?

I got the rest in the guide whose link phillw sent, thanks! 

But just to make sure, this is what I'll do to remove the -14 entry. I don't know for sure what a kernel is, so I'll go ahead and remove that entry:

[LIST=1]
[*]Go to synaptic package manager
[*] Mark for removal and remove these entries:
[/LIST]

[LIST]
[*]linux-headers-2.6.31-14
[*]linux-headers-2.6.31-14-generic
[*]linux-image-2.6.31-14-generic
[/LIST]
 Is that right?

And to remove the memtest entries, I did what the guide said, ie; uncomment the appropriate line in /etc/default/grub. That worked for me.

---

### Post by darkod on 2009-12-06
> **Tejus said:**
> I have to rename the file so it begins with 06, and then delete the old file that began with 30?

First check if the new entry is working fine. After that, personally I wouldn't delete the 30 file instead just make it unexecutable with:
sudo chmod -x /etc/grub.d/30_os-prober

You probably guessed, +x makes executable, -x unexecutable. Then when you do:
sudo update-grub

(needed after any change to config files) it will just ignore 30 file, but you still have it there in case of need.

For kernels I also recommend keeping it. If you get your windows corrupt, that's it. In linux if the new updated kernel makes issues for you, or it goes corrupt, you simply start a previous one. Can't exactly explain it, it's sort of the core files of the OS. You can corrupt your 31-16 but still be able to use your ubuntu with 31-14. Keeping at least one older kernel is nice.

---

### Post by Tejus on 2009-12-06
lol...I got a little impatient waiting for a reply, so I just did what I thought was safest, exactly what you said: make it unexecutable. 

Oh...okay, I'll keep it then! So is it possible to rename the old kernel to something more recognizable, like "Ubuntu backup copy (Kernel 2.6.31-14)". I read something in that guide which seemed to tell how to do this, but I couldn't quite follow it.

 I'm doing all this so that my dad will have an easier time shifting to Ubuntu slowly.

---

### Post by darkod on 2009-12-06
Well the 14 is telling you it's older, not sure if you can easily rename it. Grub2 is new, just came out with 9.10 and I don't know it myself either. And I don't mind it being 14.

---

### Post by Tejus on 2009-12-06
Hmm...okay, not a prob! Thanks a lot!

---

