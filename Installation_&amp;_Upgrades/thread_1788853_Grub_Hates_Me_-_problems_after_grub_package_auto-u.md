---
title: "Grub Hates Me - problems after grub package auto-update"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by TheFr00n on 2011-06-23
So, I have this lovely Ubuntu 10.10 install. It's fantastic, does everything I want it to, and just works.

But last night, the Update Manager ran, and installed a grub update, and now, when I reboot, I no longer have a grub menu. I get unceremoniously dumped to the Grub command prompt, which I don't know what to do with.

I have attempted booting off a LiveCD and reinstalling Grub, using instructions I found online (mount your partition in /mnt, etc etc) and have regenerated the grub.cfg file. Grub doesn't care. When I boot, it still drops to the prompt, without showing me a menu.

I don't know what to do, and I am kinda freaking out because this is my main work machine - been trying to fix it since 6AM.

Any ideas? Am I the only one who has this problem?

---

### Post by mue.de on 2011-06-23
what's about > find /boot/grub/stage1 after that grub-Prompt ?

---

### Post by TheFr00n on 2011-06-23
Thanks for the suggestion. It returns with:

> error: unknown command "find"

---

### Post by zepherashe on 2011-06-23
I'm still new to grub but have a look at Super Grub Disk
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by TheFr00n on 2011-06-23
Thank you for the suggestion. From the look of it, the variant called Rescatux might help me. Downloading now ... 375mb arrrrrrgh. I'll report back when it arrives.

---

### Post by westie457 on 2011-06-23
> **TheFr00n said:**
> So, I have this lovely Ubuntu 10.10 install. It's fantastic, does everything I want it to, and just works.

But last night, the Update Manager ran, and installed a grub update, and now, when I reboot, I no longer have a grub menu. I get unceremoniously dumped to the Grub command prompt, which I don't know what to do with.

I have attempted booting off a LiveCD and reinstalling Grub, using instructions I found online (mount your partition in /mnt, etc etc) and have regenerated the grub.cfg file. Grub doesn't care. When I boot, it still drops to the prompt, without showing me a menu.

I don't know what to do, and I am kinda freaking out because this is my main work machine - been trying to fix it since 6AM.

Any ideas? Am I the only one who has this problem?


If I remember correctly 10.10 uses Grub2.

Probably your best option at [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")
is to use 'Rescatux'.

If all else fails and what I am about to say is very nearly the final option, reinstall from the LiveCD.
When the 'Where do you install' dialogue comes choose 'Manual/Advanced/Something else'.
In the next screen you will see a list of all your drives and partitions. Pick the one that already has a Linux partition (Ext3/Ext 4). A window opens then in the box that says 'Do not use Partition' pick the file system that already matches your Linux partition. Leave the 'Format' box **_unchecked_**. Next in the 'Use as' box select use as root (it will have a / ).
Click on 'finished with partitioning' ignore the warning about 'No partitions have been selected for formatting'. Go ahead and reinstall. 

This will leave all your personal files and any added applications where they are and reset Grub.

As I said earlier this is more or less a last resort if no one else comes up with a simpler solution.

---

### Post by TheFr00n on 2011-06-23
OK, so, I still have no idea what caused this problem, and frankly I am quite worried that it might happen again in future. Having one's system arbitrarily borked by an update is less amusing than you might think.

I did try Rescatux, but in the end, all it seems to do is just slap a GUI on the standard commands I had already been trying - which is a bit cheeky for a 375mb download. It was also thoroughly confused by the fact that I had a separate /boot/ partition.

I did attempt reinstalling without formatting my partitions, but the installer crashed for some reason.

In the end, I fixed this by doing a clean reinstall, formatting my / and /boot partitions. Thankfully, my /home/ folder lives on a separate partition (a habit I picked up back during Suse 8) so all my data is fine. 

It is, however, a bit annoying not to understand the cause of a problem. Hopefully it just doesn't happen again.

Thanks for all the suggestions.

---

