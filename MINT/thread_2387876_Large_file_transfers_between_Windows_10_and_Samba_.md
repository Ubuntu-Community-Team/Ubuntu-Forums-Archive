---
title: "Large file transfers between Windows 10 and Samba server stall out"
date: 2018-03-25
forum: MINT
---

### Post by marcerickson on 2018-03-25
When transferring 13 GB + of files to my Samba server on a Linux Mint 18 computer, the transfer eventually stops.  The Windows message is "Destination Folder Access Denied You need permission to perform this action."  I can't continue the the transfer until I restart the server.  The server won't shut down or restart by the menu.  I have to hold the power button in until it shuts off and then restart it.

---

### Post by wildmanne39 on 2018-03-25
*Thread moved to **MINT, a more appropriate forum**.*

---

### Post by Morbius1 on 2018-03-25
13GB with like hundreds of individual files?

Um ... what I would try is making an archive ( like a zip file ) of the things you want to transfer so that the server sees a file and not many files and directories. 

And you might consider using http not samba. It's not as complicated as it sounds:

** Install droopy:
```
sudo apt-get install droopy
```
** Change directories to where you want the files to end up - for example:
```
cd /home/tester/Public
```
Then run droopy:
```
droopy
```
On the Win10 machine open your _Internet Browser_ and connect to the server this way using it's lan side ip address - for example:
```
http://192.168.1.214:8000
```

You will end up with a web page that has a Browse button that you can use to select the zip file for upload.

---

### Post by marcerickson on 2018-03-25
The same thing happens when transferring large amounts of files between two mapped drives on the the server.  Each mapped drive maps to a two drive RAID array on the server.  The files are large video files - 200 MB each and larger.

---

### Post by marcerickson on 2018-03-25
In the case of the transfer between the Win10 box and the server, the files are being moved to their permanent home.  In the case of the mapped drives, I'm moving files from one almost full drive (array) to one almost empty drive (array) to free up space on the almost full drive.  In both cases, these are almost certainly one-time only operations - until I need to replace the drives due to aging and the higher probability of failure.

These operations did work in the past - several different distros of Linux ago on the server.  I like to try stuff out.  I guess I also like to torture myself.  ;-)  I'd rather make something that used to work, work again - instead of going to a new solution.

---

### Post by marcerickson on 2018-03-28
Maybe it's related to this issue?  [https://ubuntuforums.org/showthread.php?t=2388098](https://ubuntuforums.org/showthread.php?t=2388098)

---

