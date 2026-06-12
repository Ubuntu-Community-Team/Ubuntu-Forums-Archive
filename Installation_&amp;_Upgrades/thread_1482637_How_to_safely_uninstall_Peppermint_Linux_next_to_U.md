---
title: "How to safely uninstall Peppermint Linux next to Ubuntu"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by oserdavid on 2010-05-13
I guess you should never do what you don't know how to undo.
 
In my case, getting fed up with Lucid's flaky behaviour with my particular display, having tried various solutions that were really only half-baked workarounds (the best being to install a mainline kernel) - I decided to install Peppermint Linux next to Ubuntu, thus creating a dual boot system. But I've decided I don't really like Peppermint Linux. Further, in the meantime, I've found a workaround for Lucid which (so far) seems like a longer term solution (I installed Kernel xxxx?-22, while increasing my display's refresh rate - and now all is hunky-dory - it starts perfectly, with a 'normal' visual effects desktop, and even Cheese no longer crashes the system with my old webcam). 

Now here's the rub.... 

How to (a) uninstall Peppermint Linux (with its Grub - which was obviously set over Lucid's) (b) reclaiming the whole hard drive (it's only 40gb total - as it's an oldish machine) for Lucid - without having to reinstall Lucid, which I now have very nicely set up indeed, albeit currently squeezed for space?

Ho hum...

Is there some nice patient geek out there who can put me out of my misery with a step by step guide? I've tried Google - but everyone with a similar problem seems to want to reclaim the space for Windows!

Best
David

---

### Post by uRock on 2010-05-13
This;
> **presence1960 said:**
> You can repair the MBR to a windows MBR from  ubuntu or the ubuntu live CD. Install lilo by running in terminal  ```
sudo apt-get install lilo
```Ignore the warning and next run in  terminal ```
sudo lilo -M /dev/sdX mbr
```where is sdX is your  disk/device, i.e. sda, sdb,sdc, etc

---

### Post by uRock on 2010-05-13
I have run that before and Windows booted seamlessly as if Linux was never there.

---

### Post by oserdavid on 2010-05-13
> **uRock said:**
> I have run that before and Windows booted seamlessly as if Linux was never there.
Thanks for the try uRock - And with such speed! But I thought I'd made it clear I'm running Ubuntu Lucid not Windows. I guess my post was too long to parse accurately. I must try harder for brevity!
Best
David

---

### Post by uRock on 2010-05-13
Oops, shame on me, I'll stand in the corner.

Looks like you should be able to delete the other flavor and install grub from a LiveCD.

This link will tell you how to install grub2 from a LiveCD. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Sorry I misread your original post.:oops:

uRock

---

### Post by oserdavid on 2010-05-14
> **uRock said:**
> Oops, shame on me, I'll stand in the corner.
Looks like you should be able to delete the other flavor and install grub from a LiveCD.  This link will tell you how to install grub2 from a LiveCD. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) Sorry I misread your original post.:oops:uRock
No problems uRock - thanks for trying to be helpful.

OK - let's start again. I have a dual boot system with Lucid (Ubuntu 10.04) installed first, and subsequently, Linux Peppermint installed. 

Via Lucid, I have now reinstalled Lucid's Grub, run update-grub and checked that Lucid's Grub now loads on reboot, rather than Peppermint's. Though, of course, it still shows Peppermint, but lower down the chain of boot options.

The next thing I want to do is to completely get rid of Linux Peppermint from (it sez here) sda6 and to reclaim its partition(s?) for the Lucid OS. I haven't a clue how to do that. Presumably just uninstalling its files and kernel from within Peppermint will not recover the partition (apart from being a highly tedious process, anyway). So, what's the smart way of doing it?

Best
David

---

### Post by Plumtreed on 2010-05-19
I came across your post while searching for comments on Peppermint.

To remove Peppermint I would load a live Ubuntu CD and remove Peppermint, and it's swap, using GParted. You could then re-unite the partition.

You could then utilise your entire Hardisk. 

You would not really need to do anything about Grub except ignore the reference to Peppermint when you boot.

Why don't you just keep Peppermint; it seems excellent? Your Hardisk would be adequate for both.

---

### Post by oserdavid on 2010-05-20
> **Plumtreed said:**
> I came across your post while searching for comments on Peppermint.

To remove Peppermint I would load a live Ubuntu CD and remove Peppermint, and it's swap, using GParted. You could then re-unite the partition.

You could then utilise your entire Hardisk. 

You would not really need to do anything about Grub except ignore the reference to Peppermint when you boot.

Why don't you just keep Peppermint; it seems excellent? Your Hardisk would be adequate for both.

Thanks Pumtreed. I tried that, although using a live CD of GParted - but for some reason found it impossible to expand Ubuntu's partition into the free space left after deleting Peppermint's. Dunno why.

In the end I reinstalled Ubuntu from scratch using an unofficial release designed to overcome the i8xx display chip bug. See here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511?comments=all) 

(see #162 on...)

All is now well, for the time being...

Best
David

---

