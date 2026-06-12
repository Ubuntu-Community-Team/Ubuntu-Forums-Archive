---
title: "Dapper install on PC with SATA controller"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Roscoe62 on 2006-06-04
I downloaded the Dapper ISO, MD5'd it, burnt it to CD and have just had a go at installing it. 

The live CD came up OK so I decided to install it. The only relevant point of interest I noticed during the install to Hard Drive was that it gave me the choice of where I wanted the installation to go - On my 120Gb Samsung SATA drive connected directly to the MBoard, or the 500Gb Seagate drive connected via a Promise TX4 300 SATA controller card. I don't know whether it's relevant, but the 500Gb drive appears first on the list of drives and is selected by default.

I wanted to install Dapper onto my 120Gb drive (as this is to be my boot drive) so I selected that and off it went. Finally it gave me the instruction to remove the CD and reboot so I did that. However, now when it goes to reboot, soon after I just get an error message "Error 22 - No such partition. Press any key to continue". After pressing any key I get 3 choices - boot normally, boot in safe mode or some kind of memtest. None of these options work. 

I wonder whether Dapper is trying to find the files it needs on my 500Gb drive? Or maybe I'm just speculating?

Anyway, if anyone can provide any instructions on where to go from here, I'd appreciate it! :) 

Thanks.

---

### Post by Peepsalot on 2006-06-04
I have a strange problem with my SATA hdd where linux cannot detect it from a restart(warm boot).  If I turn off the computer for 10 secs and then back on, linux boots fine.  I still haven't figured out why, but maybe your problem is similar?  Have you tried from a cold boot?

---

### Post by John.Michael.Kane on 2006-06-05
Roscoe62 switch the postion of the drive put the 120gig where the 500gig, and try to reinstall the OS. it should now see your 120Gb as the frist drive.

---

### Post by Roscoe62 on 2006-06-05
Hi SD Plissken, 

Thanks for responding. :) 

No disrespect intended, but why would Dapper give a HDD on a SATA controller a higher priority than one attached directly to the Motherboard? That makes no sense at all.

My intention for this box is to set it up as a file server. The TX-4 controller card has 4 SATA ports and, as I can afford it, I will populate all 4 ports with SATA HDD's - all dedicated to movie & music files. This is the reason why I'm reluctant to move the 120Gb HDD to the SATA controller.

As an alternative, I could just remove the controller card (or the 500Gb drive) while installing Dapper. I'm just a bit concerned that as soon as I do that and then add the controller/drive back in I'll be in exactly the same position. 

Any thoughts? :-k

---

### Post by John.Michael.Kane on 2006-06-05
There is a known issue with sata drive not being seen in proper order. this why i asked  you to trade the drives places. to see if the 120gb is seen frist. however if you   reluctant to do so i don't know what else to tell you. you can read this **Temporary workaround for SATA drive misassignment **[http://www.ubuntuforums.org/showthread.php?t=185697]("http://www.ubuntuforums.org/showthread.php?t=185697")

---

### Post by Scunizi on 2006-06-05
I had similar problems with my SATA drives.  I have 2 connected to the motherboard and an additional IDE drive.  I had to disconnect the IDE then after reading the release notes for 6.06 I had to disable Raid before installing.... even though I don't have a raid setup.  Type "sudo mdadm --stop --scan" then "sudo /etc/init.d/mdadm stop"  then "sudo vgchange -a n".  That did it for me.  I picked the drive and created the appropriate directories and file sys type and off it went.

---

### Post by Roscoe62 on 2006-06-05
Guys,

Thanks very much for the heads-up. 

Well, that's certainly an issue I didn't know about! Hopefully it's one the devs are willing to fix. In the meantime I guess I'm going to have to think about the best way to approach this. :???: 

At the very least it's nice to see the TX-4 was recognised and set up immediately. That certainly didn't happen in Breezy.

Thanks again for responding.

---

