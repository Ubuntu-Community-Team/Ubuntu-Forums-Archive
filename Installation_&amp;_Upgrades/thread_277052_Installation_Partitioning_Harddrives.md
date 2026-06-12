---
title: "Installation: Partitioning Harddrives"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by twx on 2006-10-13
I am about to install ubuntu on my main pc. I have 40gb on c drive and 40 gb on d drive on my computer. I want to keep the d drive the same as it is in windows (it has files saved in it etc) and install  ubuntu on c drive just like installing windows where only c drive is affected. but it seems the only option that came up was to partition the whole drive of 80gb? can someone explain this to me and tell me how can I just format the c drive and leave d drive the same as before and install linux only on c drive.

thanks in advance

---

### Post by John.Michael.Kane on 2006-10-13
During the install you should have been given the option to resize your hd free space.

If your doing the install from a live/cd then use the gparted program to setup the partions,and install.

Click on System->Administration->Gparted

---

### Post by gvgerman on 2006-10-13
I don't know if this is related, but it might well be. 

I tried to install Ubuntu DD on a 80G USB FAT32 drive that contained approx. 6G of data.  No mater what I tried, the LiveCD would not alter the 80G. It would not resize using gparted and when trying the install from the LiveCD, even when I selected resizing the 80G FAT32 to a 30G and leaving (essentially) 50G for Ubuntu to install, the install would quit w/ some message like "not enough free space found".  The only way I could get Ubuntu to install was to reformat the 80G to 30G using MSWindows, thus leaving 50G "empty".  With this situation, the LiveCD installed Unbuntu in the 50G empty space.

---

### Post by twx on 2006-11-12
Ok what I am trying to do is, I have some files from windows xp I would like to preserve. so I want to keep the old files and still install ubuntu

---

### Post by rajeev1204 on 2006-11-12
hi
i seem to have the same problem it seems.i have 80 gb sata harddrive.with 50 percent primary partition and 50 logical on extended partition.but gparted shows no free or used space.and like u mentioned it gives same message on installation - failed to create free space for installation

---

### Post by rajeev1204 on 2006-11-13
ok i formatted my whole d partition and finally managed to install ubuntu.nothing further !

---

