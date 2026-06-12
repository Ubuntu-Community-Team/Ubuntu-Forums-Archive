---
title: "Toshiba Portege P2000 Network Install"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by jam'ez on 2006-10-02
Good evening fellow linux lovers ;)
I have just got my hands on a Toshiba Portege P2000 for free :D 
And i want to put lovely Dapper Drake on it :D, how would i go about making a network install as i do not have a CD drive in the toshiba as its so small and thin :)
I can boot with my boot options in windows via network, thats what i know. Any help? thank you :D

---

### Post by jam'ez on 2006-10-03
:mrgreen:

---

### Post by Kateikyoushi on 2006-10-03
If it can boot from net you are lucky. My noti didn't come with built in cd either, but has an external firewire.

[Installation netboot.]("https://help.ubuntu.com/community/Installation/Netboot")

---

### Post by beercz on 2006-10-05
Does this help?

[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

Good luck, let us know how you get on should you decide to give it a go.

We are all willing to help, just ask!

---

### Post by jam'ez on 2006-11-09
An update:
I managed to get hold of a PCMCIA CD-ROM Drive :)
The sad thing about this is, it only seems to like booting of certain disks such like their laptop restore disks. 
I have put Windows xp pro onto the laptop, but dapper drake or edgy disk will not boot properly. :(

I was thinking, is there anyway of installing ubuntu when in the windows desktop environment? 

Thank you in advance,

James

---

### Post by emdeem on 2006-11-09
IMO, it's easier to do a USB boot than a network boot.  If your machine can boot from a USB flash drive, you may want to try this.

---

### Post by jam'ez on 2006-11-09
Sadly the laptop does not boot from a USB :(, if i was to make a CD to point to the USB to boot, the PCMCIA CD-ROM drive would not like the CD i doubt :( :-k

---

### Post by jam'ez on 2006-11-09
I ended up giving a network install a shot.
It installed fine :) ME HAPPY :D

---

### Post by Casethejoint on 2006-11-29
Hi there - This is an interesting thread. 

I have the same situation (Portege P2000 without removeable drives) and would like to install Ubuntu. Now, I saw this how-to on [Windows Server Netboot]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot") but it is not clear to me what exactly to do with it? 

I have a Win2k box on a network behind a router, which provides DHCP. How can I use this to do the netboot? What additional files do I need, and how will the P2000 find them?

Any help in getting me out of this state of newbness is much appreciated.

-- Case.

---

### Post by Casethejoint on 2006-11-30
I managed to fix this ...

For any users coming to this, fear not the jargon (TFTP, PXE, DHCP etc). The PC you are trying to install Ubuntu simply looks across your local network to see if any PCs on it are broadcasting the availability of a bootfile. It then installs the Ubuntu Installer, connects over the net to the ubuntu archive and gets busy with installing. Easy as that really. Worked a treat.

---

### Post by phuturism on 2007-01-22
This worked for me too on my 3480ct - [http://www.ubuntuforums.org/showthread.php?t=327597&highlight=windows+install+netboot](http://www.ubuntuforums.org/showthread.php?t=327597&highlight=windows+install+netboot)

Good luck!

---

