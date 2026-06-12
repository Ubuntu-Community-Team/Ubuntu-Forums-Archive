---
title: "Need to recover multiple boot options menu - how?"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by grahamst on 2010-06-21
I'll start by admitting I did a stupid thing yesterday.

Previously I'd installed Ubuntu Netbook Remix (Lucid) on my Acer Aspire One 751h netbook. the machine came with XP installed, so I installed Ubuntu as a dual-boot setup. I had various problems with the configuration of Ubuntu (nothing to do with the boot process, and now solved) so I reinstalled it.

What I'd actually done with the second installation was to install it again alongside both XP and the original Ubuntu installation (maybe that was also a stupid thing, but I didn't know it would work like that). When I realised what I'd done, I did the stupid thing, which was to delete the partitions with the older installation and swap file (using the Disk Utility).

After that, the next time I rebooted I went straight into grub-rescue. I don't know much about this, but I found a forum entry explaining the basics, so I can now issue grub-rescue commands that let me boot into Ubuntu. I've run update-grub and my /boot/grub/grub.cfg file looks fine.

However, I think this only kicks in once I've got past the initial boot menu and have chosen Ubuntu (now on sda5 - hd0,5). My problem is that the files/processes that load the boot menu on startup still have the old configuration, so when I reboot I still go into grub-rescue and I get 'partition not found' (or, since I recreated the partitions, 'file not found') and root is at (hd0,7).

Is there a way, once I've got into Ubuntu, of changing the information in the startup boot menu?

Alternatively, if I copy my entire file system from sda5 into sda7, would that do the trick?

Graham

---

### Post by wilee-nilee on 2010-06-21
Post the boot script in my signature in code tags.

---

### Post by grahamst on 2010-06-21
Thanks - I'll do that once I get home: mid-evening UK time.
 
Graham

---

### Post by darkod on 2010-06-21
The easiest fix for this, since you know how to boot your ubuntu install from the rescue prompt:

Boot again manually from the rescue prompt and in terminal just run:

sudo grub-install /dev/sda

Because you are actually booted into your ubuntu, no other parameters are needed. Note that you can't use the same command if booted in ubuntu live mode, only from your hdd ubuntu.

You still have the grub2 from the deleted installation on the MBR, hence the error. The above command will install grub2 connected with your current installation to the MBR and there should be no more errors.

---

### Post by grahamst on 2010-06-21
Thank you very much, darkrod - that did the trick. I can now see the boot menu from the MBR and can boot into Ubuntu from there.

Thanks also to wilee-nilee. I don't need to use your boot script program, but I'm grateful for the offer.

Now I'd like to see if I can resize my active partitions - but I think I should do some research (gparted?) before asking for help.

Graham

---

