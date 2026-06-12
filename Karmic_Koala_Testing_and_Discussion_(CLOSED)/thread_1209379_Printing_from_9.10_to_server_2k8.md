---
title: "Printing from 9.10 to server 2k8"
date: 2009-07-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2009-07-10
I have widows sever 2k8 with a HP OfficeJet Pro L7590 printer attached to it, I can browse shared files on ws 2k8 but I can not add the printer to 9.10, any ideas?

The same printer, if attached to wxp, I can find and print to it.

---

### Post by tad1073 on 2009-07-10
Ubuntu 9.10 is unable to find network printers. I have a thread here [http://ubuntuforums.org/showthread.php?t=1209379](http://ubuntuforums.org/showthread.php?t=1209379) about windows server 2008 network printer. Thinking that was the problem,  I installed Ubuntu 9.04 server but the problem persists.

---

### Post by tad1073 on 2009-07-10
Please close this thread as it is no longer valid.

---

### Post by cariboo on 2009-07-11
It would be nice if you told us what you did to solve the problem.

---

### Post by cariboo on 2009-07-11
I have an Epson R340 connected to a computer running XP and a HP 5P connected to my Jaunty server. I just setup both this afternoon with zero problems. The HP was auto detected, all I had to do was fill in the printer information, name, printer type and location. The Epson was a little harder, I had to select the make, model, then fill in the printer inforamtion. It may be a problem on the Windows end, if you don't see it from Karmic.

BTW I merged you two threads.

---

### Post by tad1073 on 2009-07-11
> **cariboo907 said:**
> I have an Epson R340 connected to a computer running XP and a HP 5P connected to my Jaunty server. I just setup both this afternoon with zero problems. The HP was auto detected, all I had to do was fill in the printer information, name, printer type and location. The Epson was a little harder, I had to select the make, model, then fill in the printer inforamtion. It may be a problem on the Windows end, if you don't see it from Karmic.

BTW I merged you two threads.

I did a quick fix of the problem.

I disconnected the printer from ubuntu server and connected it to the xp machine and I am able to find and print to the printer.

I think it may be a problem with 9.10 because I had the same effects on both ubnutu server and windows server. I was trying to connect to the printer via samba share, I was able to connect to via IPP though.

---

### Post by inportb on 2009-07-11
Network printers work just fine with Karmic, for me. Perhaps it's only an issue with SMB printers?

---

