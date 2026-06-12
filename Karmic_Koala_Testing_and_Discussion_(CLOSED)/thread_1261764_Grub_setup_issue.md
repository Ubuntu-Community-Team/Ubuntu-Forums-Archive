---
title: "Grub setup issue"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sendervictorius on 2009-09-09
I need some help setting up grub to boot into my experimental install of Alpha 5.

I installed Alpha 5 on a spare partition. Seeing as I didn't want to change my existing grub setup, I chose not to install grub at the end of the Alpha 5 install.

I manually updated my menu.lst in Jaunty by adding

```
title		Clean Ubuntu 9.10 Alpha 5, kernel 2.6.31-9-generic 
root		(hd0,8)
kernel		/vmlinuz root=/dev/sda9 ro  single
initrd		/initrd.img
```

I have tested this by running grub command mode, and checking the root(hd0,8) and presence of vmlinuz and initrd. All ok.

When I boot, I get grub Error 15 - file not found.

Googling around, I suspect it needs grub setup in /boot/grub on my Alpha 5 partition. Right now /boot/grub is empty.

Is this the solution?

If so, how do I install grub without disturbing my existing grub setup and overwriting MBR (so I could use chainloader, for instance)

---

### Post by philinux on 2009-09-09
You need to ```
grub-install 
```to the target partition. 
You could do this by chroot to the karmic install or from the karmic live cd. It will complain about being installed to a partition, ignore this.

The grub bit in my jaunty install is this. Karmic is on disk 2 and root is partition one hence 1,0
title        SDB Karmic
root (hd1,0)      
chainloader +1


At the end of installation from live cd you could have chosen the advanced tab and done it there.

---

### Post by kansasnoob on 2009-09-09
> **Sendervictorius said:**
> I need some help setting up grub to boot into my experimental install of Alpha 5.

I installed Alpha 5 on a spare partition. Seeing as I didn't want to change my existing grub setup, I chose not to install grub at the end of the Alpha 5 install.

I manually updated my menu.lst in Jaunty by adding

```
title		Clean Ubuntu 9.10 Alpha 5, kernel 2.6.31-9-generic 
root		(hd0,8)
kernel		/vmlinuz root=/dev/sda9 ro  single
initrd		/initrd.img
```

I have tested this by running grub command mode, and checking the root(hd0,8) and presence of vmlinuz and initrd. All ok.

When I boot, I get grub Error 15 - file not found.

Googling around, I suspect it needs grub setup in /boot/grub on my Alpha 5 partition. Right now /boot/grub is empty.

Is this the solution?

If so, how do I install grub without disturbing my existing grub setup and overwriting MBR (so I could use chainloader, for instance)

I also installed alpha 5 w/o grub. Since I'm lazy I just went to Synaptic and removed 'grub-pc' and 'os-prober', then installed 'grub'.

Afterwards I just ran "sudo update-grub" which asked me if I wanted to generate a menu.lst and I said yes (y). Then "cat /boot/grub/menu.lst" gives me the lines needed to add to whatever legacy grub I'm using.

Like (mine as an example only):

> title		Ubuntu karmic (development branch), kernel 2.6.31-10-generic
uuid		58ea03f2-8f77-474e-a577-1823dee8b657
kernel		/boot/vmlinuz-2.6.31-10-generic root=UUID=58ea03f2-8f77-474e-a577-1823dee8b657 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-10-generic

title		Ubuntu karmic (development branch), kernel 2.6.31-10-generic (recovery mode)
uuid		58ea03f2-8f77-474e-a577-1823dee8b657
kernel		/boot/vmlinuz-2.6.31-10-generic root=UUID=58ea03f2-8f77-474e-a577-1823dee8b657 ro  single
initrd		/boot/initrd.img-2.6.31-10-generic

title		Ubuntu karmic (development branch), kernel 2.6.31-9-generic
uuid		58ea03f2-8f77-474e-a577-1823dee8b657
kernel		/boot/vmlinuz-2.6.31-9-generic root=UUID=58ea03f2-8f77-474e-a577-1823dee8b657 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-9-generic

title		Ubuntu karmic (development branch), kernel 2.6.31-9-generic (recovery mode)
uuid		58ea03f2-8f77-474e-a577-1823dee8b657
kernel		/boot/vmlinuz-2.6.31-9-generic root=UUID=58ea03f2-8f77-474e-a577-1823dee8b657 ro  single
initrd		/boot/initrd.img-2.6.31-9-generic

title		Ubuntu karmic (development branch), kernel 2.6.31-5-generic
uuid		58ea03f2-8f77-474e-a577-1823dee8b657
kernel		/boot/vmlinuz-2.6.31-5-generic root=UUID=58ea03f2-8f77-474e-a577-1823dee8b657 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-5-generic

title		Ubuntu karmic (development branch), kernel 2.6.31-5-generic (recovery mode)
uuid		58ea03f2-8f77-474e-a577-1823dee8b657
kernel		/boot/vmlinuz-2.6.31-5-generic root=UUID=58ea03f2-8f77-474e-a577-1823dee8b657 ro  single
initrd		/boot/initrd.img-2.6.31-5-generic

title		Ubuntu karmic (development branch), memtest86+
uuid		58ea03f2-8f77-474e-a577-1823dee8b657
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


Alternatively you can find the uuid's by running:

```
sudo blkid -c /dev/null
```

But I prefer the lazy way.

---

### Post by Sendervictorius on 2009-09-12
Thanks for you help.

I followed both your advice, and eventually got completely tied up in knots. Nothing would work, and synaptic kept dying on me. So, I took the easiest way out - which was to re-install Karmic again, and include grub on the install. Then chainload into the Karmic partition.

This worked. 

I suspect the problem was that I was moxing the two versions of grub in my attempts to fix things.

---

### Post by VMC on 2009-09-12
Your asking a couple of questions. One, /boot/grub being empty should have nothing to do with booting that partition from another mbr. I would question the use of linux and initrd.img. Are they links to the full kernel? Two I was under the impression that you wanted to keep grub legacy, which would be under jaunty's /boot/grub/menu.lst control.

---

### Post by Sendervictorius on 2009-09-14
> **VMC said:**
> Your asking a couple of questions. One, /boot/grub being empty should have nothing to do with booting that partition from another mbr. I would question the use of linux and initrd.img. Are they links to the full kernel? Two I was under the impression that you wanted to keep grub legacy, which would be under jaunty's /boot/grub/menu.lst control.

The problem was: on my initial install of Karmic I didn't install Grub, thinking I didn't need to. I created an entry in the jaunty menu.lst to boot using grub legacy into the kernel on the karmic partition. (The code in my original posting). I couldn't get it to boot (error 15). A number of postings I found suggested that you needed a grub setup on the karmic partition. (I couldn't understand that, but hey, what do I know about grub?)

I spent a lot of time messing around - trying to install grub on my karmic partition from my karmic live CD, chrooting onto the new partition root, all with little success - until I blew away the partition and reinstalled karmic complete with grub 2 in that partition. I didn't overwrite the MBR, so I can continue to boot with grub legacy into Jaunty, and now I chainload into grub 2 on my karmic partition.

It now all works, good enough for now.

I am still curious to know what was the cause of my original problem. It might help improve my grub knowledge. If anyone can shed some light, please post what you think was going on.

---

### Post by VMC on 2009-09-14
Interesting. So now it works, but you needed to install grub2 into karmic partition, correct?

You boot chainload karmic through grub-legacy from jaunty partition, correct?

Regarding your code block. Try:

```
title		Clean Ubuntu 9.10 Alpha 5, kernel 2.6.31-9-generic 
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.31-10-generic root=/dev/sda9 ro
initrd		/boot/initrd.img-2.6.31-10-generic

```Replace kernel & initrd with whatever is in karmics /boot folder

---

### Post by Sendervictorius on 2009-09-15
yes, I tried that as well. There are symbolic links in the root that link to the latest kernel version and initrd.img in /boot.

---

### Post by bwallum on 2009-09-15
I'm missing initrd.img-2.6.31-10-generic

Where can I manually download it please?

---

### Post by zika on 2009-09-15
> **bwallum said:**
> I'm missing initrd.img-2.6.31-10-generic

Where can I manually download it please?```
sudo update-initramfs -c -k 2.6.31-10-generic
```

---

