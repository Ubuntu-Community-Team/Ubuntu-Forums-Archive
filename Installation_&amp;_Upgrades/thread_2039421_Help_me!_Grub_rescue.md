---
title: "Help me! Grub rescue"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by Gootch on 2012-08-08
Alright. I have an HP desktop and I have ubuntu dualbooted on it. I today wanted to reformat my computer to factory settings so I proceededto deleteting my ubuntu partition. I went to restart my PC and I get this

Error: no such partition.
grub rescue>

I don't know what to do. This is my only computer and it was having problems so that's why I wanted to reformat it. I don't have the CD for windows either.

Please help me

---

### Post by drs305 on 2012-08-08
Gootch,

Sorry your first post to the Ubuntu Forums isn't under happier circumstances. Nevertheless, welcome!

If your Windows boot files are still intact, we may be able to restore Windows using an Ubuntu LiveCD.

Boot the the LiveCD, open a terminal (CTRL-ALT-t), then run the following commands to point the MBR to your Windows bootloader. The commands assume your drive is sda. Run only the commands below and disregard any messages about lilo not being fully configured.
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Reboot. If the boot flag is still on your Windows partition you should be greeted by the Windows menu.

---

### Post by Gootch on 2012-08-08
> **drs305 said:**
> Gootch,

Sorry your first post to the Ubuntu Forums isn't under happier circumstances. Nevertheless, welcome!

If your Windows boot files are still intact, we may be able to restore Windows using an Ubuntu LiveCD.

Boot the the LiveCD, open a terminal (CTRL-ALT-t), then run the following commands to point the MBR to your Windows bootloader. The commands assume your drive is sda. Run only the commands below and disregard any messages about lilo not being fully configured.
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Reboot. If the boot flag is still on your Windows partition you should be greeted by the Windows menu.
 The thing is I don't have a UbuntuCD what do I do. I do have a windows xp Cd but that doesn't matter.

---

### Post by drs305 on 2012-08-08
You may be able to use the XP disk to run 'fixboot' - which Windows OS are you running? 

I'm not a Windows person. If you are trying to restore your Windows OS you'll either have to wait for someone else to reply or try to get help in a more appropriate support forum (i.e. a Windows forum).

---

### Post by Gootch on 2012-08-08
I am running windows 7. I cant use the xp disk because I need the system restore one. What should I do?

---

### Post by drs305 on 2012-08-08
If you can use a flash device you can install Boot Repair or another rescue app such as Grub Super Disk onto it and set the BIOS to boot that device first. Boot Repair can do what I proposed to do with lilo earlier in the thread.

Here is a link:
[http://ubuntuforums.org/showthread.php?t=1831869]("http://ubuntuforums.org/showthread.php?t=1831869")

---

### Post by Gootch on 2012-08-08
What do you mean a flash device? Like a USB? I maybe able to use my dads PC and install Ubuntu on the USB a run it and do the command like you said in the first reply. Would the first reply require the ubuntu OS? It would be easier if I could just install a bootfixing program on my usb. How should I do it? Thanks

---

### Post by drs305 on 2012-08-08
> **Gootch said:**
> What do you mean a flash device? Like a USB? I maybe able to use my dads PC and install Ubuntu on the USB a run it and do the command like you said in the first reply. Would the first reply require the ubuntu OS? It would be easier if I could just install a bootfixing program on my usb. How should I do it? Thanks

Yes, a USB thumb drive. You could make a bootable USB drive on any device and then plug it into your problem computer to boot it. You would just have to make sure the BIOS was set up to boot the thumb drive first. Accessing BIOS varies by computer manufacturer but usually involves pressing the DEL, ESC or one of the function (F1-F12) keys.

You can make a bootable Ubuntu drive or one using one of the rescue apps I mentioned earlier. I'm logging off for the evening so I hope you get this resolved.

---

