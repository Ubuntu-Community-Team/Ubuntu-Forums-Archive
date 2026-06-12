---
title: "/boot/grub directory"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rumpty on 2009-10-03
Is there supposed to be a large number, maybe 100 or so, .mod files in this directory? Along with grub.cfg and other legitimate looking files, that is.

---

### Post by Elfy on 2009-10-03
Yes that is right.

---

### Post by thecow on 2009-10-03
Ah no wonder my karmic upgrade isn't working then

---

### Post by Elfy on 2009-10-03
An upgrade (I think) does not replace grub-legaacy with grub2. An upgrade might not have them in /boot/grub.

---

### Post by ranch hand on 2009-10-03
If you are upgrading from 9.04 you will get the new "common" files for both versions of grub.  To get grub2 you need to download the grub2 package (meta package) and pc-grub.  This will install grub2.

Be prepared to learn a completely new way to manage grub.  There are still some rough spots.  It is going to be better than grub-legacy although that is definitely arguable now.  It is neat and works now, you just need a lot of patients and do a lot of reading.

---

### Post by Rumpty on 2009-10-03
At the moment, on my fresh install, in a multi-boot environment, I'm a bit disheartened with Grub2. It found all my operating systems, so I allowed it to install the bootloader in the first hard drive. But when I rebooted, only Karmic (plus memtest) was available to select. 

It had "lost" Jaunty, and the two Windows installations. 

I noticed that immediately after it had installed in the MBR, it did an "update grub". Seems to me to be a strange time to do that? I have a feeling that is when it lost the other entries. Maybe.

So I have re-installed Jaunty's Grub in the MBR, and added an entry in the menu.lst for Karmic. All is now working! Hooray!

---

### Post by Elfy on 2009-10-03
> **Rumpty said:**
> So I have re-installed Jaunty's Grub in the MBR, and added an entry in the menu.lst for Karmic. All is now working! Hooray!
I was thinking of doing that - I sit and look at GRUB loading for 20 secs before I get the menu :)

---

### Post by tommcd on 2009-10-03
> **Rumpty said:**
> At the moment, on my fresh install, in a multi-boot environment, I'm a bit disheartened with Grub2. It found all my operating systems, so I allowed it to install the bootloader in the first hard drive. But when I rebooted, only Karmic (plus memtest) was available to select. 

I had the same problem. After getting the 150+ updates and rebooting grub2 detected my other operating systems. Since there were so many updates I didn't notice if there was an update to grub2 or not in the update list. Anyway, it works now.
Here is a good tutorial on grub2:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
I'm still trying to get up to speed on grub2 myself.

---

### Post by ranch hand on 2009-10-03
When grub2 is installed with the OS there are a number of times that the /boot/grub/grub.cfg is not fully generated.  When you reboot from install you need to go to terminal and run;
```

sudo update-grub

```
98 or 99% of the time this will pick up your other OS' and should be pretty accurate when it comes to Debian based OS' and WinWatever.

---

### Post by DougieFresh4U on 2009-10-03
> **ranch hand said:**
> When grub2 is installed with the OS there are a number of times that the /boot/grub/grub.cfg is not fully generated.  When you reboot from install you need to go to terminal and run;
```

sudo update-grub

```
98 or 99% of the time this will pick up your other OS' and should be pretty accurate when it comes to Debian based OS' and WinWatever.

I will agree on this. 
Also, any time I see a grub update or kernel updates, I will always do ```
sudo update-grub2
``` before rebooting.

I am running a multi boot system here and I let Windows 'have it's way' some time last year and then installed Jaunty and Karmic 32 & 64 bit on separate partitions. I have had no problems with grub2. Some times I have to update both Karmic's to get any new updates installed correctly in grub

---

