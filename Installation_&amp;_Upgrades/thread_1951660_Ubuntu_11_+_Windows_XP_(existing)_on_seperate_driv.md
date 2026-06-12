---
title: "Ubuntu 11 + Windows XP (existing) on seperate drives"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by skanger on 2012-04-02
Hi

I have a windows xp installation on the main drive in my laptop. There is a second data drive that I haven't been using and have cleaned all old files off it.

What I want to do is install Ubuntu 11 on the second drive, but not use any kind of special boot loaders. I would like to use the laptop BIOS to select the drive I want to boot from (and thus the OS).

How would I do this without causing any changes to the XP installation and also keep the Ubuntu installation totally independent of the XP drive?

One person suggested taking out the XP drive and and then install the secondary drive in its place after which Ubuntu would be installed on that drive. The drives would finally be put into their original positions and selected in BIOS. Would that work with no problems?

Thank you,
S

---

### Post by nd456 on 2012-04-02
From what I can tell, this is along the lines you are looking for...
[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

---

### Post by bfmetcalf on 2012-04-02
I do this exact thing with ArchLinux.  The way I did it that worked incredibly well and easy was to unhook the windows HDD and install on the second drive as normal.  Then I hooked the windows disk back up and told bios to boot off of the windows drive first which basically ignores the second drive until I tell it to.

---

### Post by oldfred on 2012-04-02
Ubuntu will not care that drive order has changed, but be sure to plug Windows back in to first drive.

This works if you have a newer computer that lets you choose drive to boot from BIOS. All system with SATA will work. Some older IDE/PATA systems only boot from primary master either by jumper on drive or location on cable. Those older systems it will not work.

You can run this with both drives plugged in and it will add Windows to the grub menu so you can boot it.
```

sudo update-grub
```

If you do not want to disconnect drive you have to pay close attention to where you install the grub2 boot loader. And you only get that choice if you use manual install or Something Else. With 2 drives you should use the manual install anyway.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by skanger on 2012-04-03
Thanks to each of you for your reply, especially old Fred. Nothing is ever as simple as I would like to be.  :)

Fred, if my 2006 laptop does not allow for selecting which HD will boot then I suppose I have to use GRUB. 



> **oldfred said:**
> Ubuntu will not care that drive order has changed, but be sure to plug Windows back in to first drive.

This works if you have a newer computer that lets you choose drive to boot from BIOS. All system with SATA will work. Some older IDE/PATA systems only boot from primary master either by jumper on drive or location on cable. Those older systems it will not work.

You can run this with both drives plugged in and it will add Windows to the grub menu so you can boot it.
```

sudo update-grub
```If you do not want to disconnect drive you have to pay close attention to where you install the grub2 boot loader. And you only get that choice if you use manual install or Something Else. With 2 drives you should use the manual install anyway.


I don't quite understand what you mean by adding windows to the grub menu so it can be booted. Do  you mean that once the procedure of installing ubuntu to the second drive (to be selected in BIOS as the boot drive when needed) is complete, any time that ubuntu is the booted drive/OS grub will offer a menu of the two operating systems to choose from?

Thanks for the good links. The maverick page confirmed a number of settings that I was wondering about and now don't have to repeat in these forums. Unfortunately there are a lot of linux pages that show up in searches with limited or incomplete information.

S.

---

### Post by Mark Phelps on 2012-04-03
To add MS Windows to the GRUB menu, do the following:
1) Boot from the Ubuntu drive
2) Once into a desktop, open a terminal and enter "sudo update-grub"  This will regenerate the default GRUB config file.

When you reboot, you should see a GRUB menu with options to choose Ubuntu or Windows.

---

### Post by oldfred on 2012-04-03
My 2006 Toshiba lets me boot USB, so it has the BIOS that allows multiple boot choices, not sure if it is IDE or SATA inside.

I like grub and its menu lets you boot just about any other operating system you install automatically. It has an os-prober that runs as part of the update-grub that finds other systems and adds them to the menu. You then do not have to use BIOS, but I like to keep each system on a drive and have its boot loader in the MBR ot the same drive. So if you ever have a drive issue you can use BIOS to choose the other drive.

---

### Post by skanger on 2012-04-04
> **oldfred said:**
> My 2006 Toshiba lets me boot USB, so it has the BIOS that allows multiple boot choices, not sure if it is IDE or SATA inside.

I like grub and its menu lets you boot just about any other operating system you install automatically. It has an os-prober that runs as part of the update-grub that finds other systems and adds them to the menu. You then do not have to use BIOS, but I like to keep each system on a drive and have its boot loader in the MBR ot the same drive. So if you ever have a drive issue you can use BIOS to choose the other drive.

Thanks Fred. It worked out as you described.

Though this could be a new thread, I found that after suspending my laptop, trying to re-awaken it gives just a black screen with what appears to be a re-awakened system (based on cooling fans and indicator lights). I'm using a HP DV8100. Are there specific profiles or settings for various laptop power settings that have something to do with this? Thanks again.

S.

---

### Post by oldfred on 2012-04-04
Glad you got it installed.

Suspend just works for me. You may be best to start a new thread with suspend and your model HP to see if others have had same issue.

---

