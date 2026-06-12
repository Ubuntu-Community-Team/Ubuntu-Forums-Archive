---
title: "Booting OSes"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by Shadius on 2012-03-06
My issue is this:

I have a Windows XP desktop computer and my friend gave me a 40 GB HD which I installed Ubuntu on. However, the way I installed Ubuntu 11.10 was that I disconnected my HD that had XP on it and hooked up the free 40 GB HD and used the LiveCD to install Ubuntu 11.10. So Ubuntu has it's own HD and XP has it's own HD. I thought I would be able to select which OS I would like to boot into when I hooked back up my XP HD, but that option wasn't there. How do I go about doing this? 

Any help is greatly appreciated! Also, I'm a newbie to Linux, so please be patient with me! Thanks in advance!

---

### Post by mastablasta on 2012-03-07
you now need to uupragde grub so it can see the windows disk.
 
i think there is some graphic tool ah here it is (i think this works in liveCD): [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
more info here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldfred on 2012-03-07
If you set BIOS to boot the Ubuntu drive and run this it should find & add the Windows to the boot menu.
```

sudo update-grub
```

If an old IDE system you may not be able to set BIOS to boot another drive as it is controlled by jumpers on drives. Then the only choice is to install grub2's boot loader to the MBR of the Windows drive. Then see links by mastablasta above.

---

### Post by Shadius on 2012-03-08
Thank you both for trying to help me. Yes, the drive that has Ubuntu on it isn't being seen in the BIOS so I will try the method mastablasta described. Thanks again. Will update if I need any more help. :)

---

### Post by Shadius on 2012-03-12
Hey guys, I'm confused. :( Do I have to have both HDs hooked up and start up my computer with the Boot-Repair CD in the CD Drive, or do I disconnect my Windows XP HD and boot up into Ubuntu then use Boot-Repair? My Windows XP HD is my primary drive, and my Ubuntu 11.10 HD is my secondary drive. The Ubuntu 11.10 drive isn't being seen in the BIOS, so I can't tell the BIOS to just boot into that drive, that's why I have to disconnect the Windows XP drive in order to boot into Ubuntu. Hope this isn't too confusing.

---

### Post by Shadius on 2012-03-12
I figured it out! Thanks for the help!

---

### Post by Shadius on 2012-03-12
If I were to reinstall Ubuntu would I need to use the Boot-Repair CD to reinstall the MBR to my Windows HD or would the Windows HD automatically revert back to it's MBR? The reason I'm asking is because after I did a partial update on Ubuntu, I can no longer login to my user account.

---

### Post by oldfred on 2012-03-12
Because you have two drives and you have each system separately installed on each drive, neither should update the MBR of the other unless you tell it to. 

Of course I always have a liveCD or repairCD for each versions of operating system installed in case I do have to repair something.

If you reinstall you do have to use manual install (Something Else) to have the combo box to choose which drive to install the grub2 boot loader into. Otherwise it defaults to sda which then will overwrite your Windows MBR. See last link which is just a screenshot showing the grub2 install combo box.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Shadius on 2012-03-12
> **oldfred said:**
> Because you have two drives and you have each system separately installed on each drive, neither should update the MBR of the other unless you tell it to. 

Of course I always have a liveCD or repairCD for each versions of operating system installed in case I do have to repair something.

If you reinstall you do have to use manual install (Something Else) to have the combo box to choose which drive to install the grub2 boot loader into. Otherwise it defaults to sda which then will overwrite your Windows MBR. See last link which is just a screenshot showing the grub2 install combo box.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Thank you.

---

