---
title: "Uninstalled Ubuntu Incorrectly"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by linuxgirl28 on 2011-01-04
So let me just throw this out here that I'm not the best with computers and this was my first experience with Ubuntu.

I really like Ubuntu but something wasn't working right so I tried to uninstall it with the intentions of reinstalling it and I screwed it up. I deleted a wrong file and with it went the ability to uninstall Ubuntu properly. Now when I turn on my computer, its a Windows Vista that I was dual booting, I still have the option to choose Ubuntu but it doesn't lead anywhere because the files are not on my computer.

Basically, I just want to know how/if I can get the scraps of my original Ubuntu off of my computer so I can redo the installation?

Advanced thanks to those that can help me and sorry to those that I annoy with my ignorance. Just trying to figure things out.

---

### Post by wilee-nilee on 2011-01-04
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by linuxgirl28 on 2011-01-05
I'm having trouble booting into Linux though, so I can't run the boot info script that you suggested. I deleted the wrong folder with all of the Ubuntu files so I can't do the LiveCD either. Thanks for trying to help, I do appreciate it. I'll just keep doing trial and error until I either give up or figure it out.

---

### Post by presence1960 on 2011-01-05
> **linuxgirl28 said:**
> I'm having trouble booting into Linux though, so I can't run the boot info script that you suggested. I deleted the wrong folder with all of the Ubuntu files so I can't do the LiveCD either. Thanks for trying to help, I do appreciate it. I'll just keep doing trial and error until I either give up or figure it out.

The ubuntu Live CD/USB should boot regardless of what is on your computer. You need to press a key (my BIOS uses F9) to choose what device to boot from. With the Ubuntu Live CD/USB in your machine (either optical drive or USB port) boot and press the key that controls which device to boot. Choose the device that you want to boot that corresponds to your ubuntu Live CD/USB.

If you can't figure this out you need to go into BIOS and set the device boot priority to have your device boot before hard disk. Save changes to CMOS and continue booting. Then run the boot info script willee-nilee asked.

---

