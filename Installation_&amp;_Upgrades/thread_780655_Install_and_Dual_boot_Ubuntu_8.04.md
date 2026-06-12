---
title: "Install and Dual boot Ubuntu 8.04"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by RandomInfinity on 2008-05-03
I recently installed on a Dell 560 with XP SE 2.  Everything seemed to do fine.  I was able to use open office, play some games, mount and unmout drives.
When I booted in Windows, I got a message that my drive was below the minimum space available.  For some reason, my second 80GB internal NTFS drive had been filled up or changed to the point that all the unused space was now filled.

I can not get to this area with either operatiing system.  The existing files are accessable on both OS.  Ubuntu made the 20GB of files into a mountable drive.  The C drive which holds both OS seem to be fine.  All space is visible and accessable by either OS.

How do I get to the 60GB on the second drive to free it up so I can use it.  I have copied the avaible files on the D drive to a backup drive.

During install, Ubuntu stated that it was backing up files before it parsed the drive.  At the time I thought it was dealing with the C drive only.  I could believe that the now occupied space is the backup files but there was no indication that the space was being used on the D drive for this backup.  

I was surprised that Ubuntu could access the NTFS drive though I am somewhat pleased that I could get to the drives and files located there.  Maybe that is the problem with the trapped space.

Please give me some ideas to free up the 60 GB space on the D hard drive.  If I need to reformat the drive, which OS shoud I use?

---

### Post by Pumalite on 2008-05-03
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Post screenshot of Gparted with the offending drive in sight.

---

### Post by RandomInfinity on 2008-05-13
> **Pumalite said:**
> Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Post screenshot of Gparted with the offending drive in sight.

I was able to get Gparted to a CD and run it on my computer.  I got the screen shot of the drive information.  Gparted saved it to root as gparted.jpg.  I could not change the file name so I could only get one image.  When I went to root,  in Ubuntu, to get the file, it was not there.
 I did not change any of the settings in Gparted when I used it and maybe I limited my options with the program.  Are there more detailed instructions which will help me with gparted?

---

### Post by iaculallad on 2008-05-13
Try visiting this site for the detailed documentation:

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by housam on 2008-05-13
Boot from ubuntu live cd >> sys. >> admin.>> partition editor ( Gparted ). then take a screen shot and save it to the desktop. connect to the internet and then insert the attachment to your post while you are still on the live cd .

---

### Post by RandomInfinity on 2008-05-17
I finally got gparted to work.  Here is the information Associated with the drive which I have loss access to part.  The attached jpeg files show screenshots of the information of the drive with the area I can not access.  I have not figured out how to get these to a web as yet so hopefully you can see the attached images clearly.



> **Pumalite said:**
> Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Post screenshot of Gparted with the offending drive in sight.

---

### Post by Pumalite on 2008-05-18
You have sdb2 unformatted. Right now it's 'unallocated' space. Use Gparted to format it.

---

