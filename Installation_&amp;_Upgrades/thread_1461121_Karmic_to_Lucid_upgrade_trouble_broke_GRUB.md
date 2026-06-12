---
title: "Karmic to Lucid upgrade trouble broke GRUB"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by mjpatey on 2010-04-23
Hi, all-

I've been running Karmic 64-bit, and last night decided to try an upgrade to the Lucid release candidate.  I fell asleep during the process, and in the morning, my wife "clicked away" a window that was asking something about keeping or deleting something.

Long story short, I attempted to reboot, and was greeted with a wonderful GRUB error:

> GRUB loading.
error: the symbol 'grub_puts_' not found
grub rescue>_


I searched high and low, and tried various commands that grub rescue is supposed to recognize, but all I could get it to do was to list the available hard drives.

Eventually, I discovered the Super GRUB2 CD, a GRUB rescue disk, which I've now booted into, and allows me to select a GRUB config file to boot from, and takes me into my beloved Ubuntu installation from there.  It actually works!  But I have to boot into the CD to get to my Ubuntu install, and obviously, that's not what I want.

I tried the simplest possible solution, and did a sudo apt-get install GRUB2, then rebooted, hoping that may have installed the missing components.  But it didn't.

So I need to know what file or files to repair, and how, in order for GRUB to work as it's supposed to without the GRUB rescue CD.  Any idea?

Thanks in advance for any light you can shed!

-Mark

---

### Post by bcbc on 2010-04-24
> **mjpatey said:**
> and in the morning, my wife "clicked away" a window
Blame it on the wife. That's a good one. :)

Use your cd to boot ubuntu and reinstall grub2 to the MBR.
```
sudo grub-install /dev/sda
```

Edit: for good measure you should also run (and make sure everything looks good)```
sudo update-grub
```

---

### Post by mjpatey on 2010-04-24
bcbc-

Thanks, but my problem is that booting with a live CD doesn't work... I can only boot with the SuperGRUB2 disk.  It brings up a menu that allows me to select a broken GRUB to boot from, and then boots from it.  But all the while, the SuperGRUB2 CD must remain in the drive, even now as I type this in an otherwise normal GNOME desktop session... so I have no way to boot to a live CD.

And only a very few commands are available to me at the GRUB rescue prompt that I'm left with... for some reason, all the GRUB-fixing suggestions I've read online are not recognized by this "grub rescue>" prompt.

Is there a config file I can edit while booted into the OS like I am now?

---

### Post by mjpatey on 2010-04-24
Well, don't I feel silly?  :-D

After posting that, I had a flash of near-normal intelligence, and decided to try ```
sudo update-grub /dev/sda
``` from my current GNOME session, and voila!  A reboot worked flawlessly!

And mind-blowingly fast, now that I'm booting to Lucid.

bcbc, thank you so much for the insight!

-Mark

---

### Post by bcbc on 2010-04-24
> **mjpatey said:**
> Well, don't I feel silly?  :-D

After posting that, I had a flash of near-normal intelligence, and decided to try ```
sudo update-grub /dev/sda
``` from my current GNOME session, and voila!  A reboot worked flawlessly!

And mind-blowingly fast, now that I'm booting to Lucid.

bcbc, thank you so much for the insight!

-Mark

I don't think update-grub takes that sort of argument ("/dev/sda"). If you did type that, then you probably didn't have a valid grub menu, as update-grub appears to ignore the extraneous input and re-generates the grub menu anyway.

Either way, it's great that everything is running fine.

---

