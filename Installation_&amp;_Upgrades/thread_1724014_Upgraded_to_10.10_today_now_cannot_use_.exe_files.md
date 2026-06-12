---
title: "Upgraded to 10.10 today: now cannot use .exe files"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by kmarzi on 2011-04-07
Hello,

I upgraded today from 10.04 to 10.10. Now, when I try to click on an .exe, the program simply won't work. I get this message: "There is no application installed for executable files". 

So, I go to properties>permissions and check the box "Allow executing file as program". However, the box immediately (and consistently) unchecks itself. 

I found a "Solved" thread on one of the Ubuntu formus where  a similar problem was reported. The solution, however, was to move the folder which hosts the file   and then click on the .exe. Not only does it  seem strange for this thread to  be classed as "Solved" (does that mean we have to move ALL our folders to be able to change permissions?) but it simply didn't work for me. Indeed, I have moved the folder and still I cannot change permissions in any way.

Moreover, when I click on permissions, I cannot change any of the settings e.g. File Access, Folder Access, etc. When I change one of these settings, they automatically revert to their previous state. As such, I am unable to change a thing.

Can any one please help?

Kind regards,
Kmarzi

---

### Post by pricetech on 2011-04-07
Your "exe" files are all windows executables.  They don't work under Linux.

---

### Post by kmarzi on 2011-04-07
Well, for Urban Terror (online game), for example, I have simply double-clicked the icon (which I assume is an .exe, but may not be) for about 1 year. It has consistently worked. I upgrade to 10.10 - now it doesn't. Plus, I am unable to change the permissions for anything with regards to this file.

The error message reads: The file '/media/Expansion Drive/UrbanTerror/ioUrbanTerror.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

The point is, I simply can't mark it as executable in permissions. And, as mentioned, it has worked for me for some time now. 

Any ideas?

---

### Post by kmarzi on 2011-04-07
Indeed, Urban Terror download instructions:


**Linux**
Linux 32bits executable: ioUrbanTerror.i386
Linux 64bits executable: ioUrbanTerror.x86_64
*You need to make it executable first: right click it, properties and tick the 'allow execution' box.*

---

### Post by Dutch70 on 2011-04-07
If a .exe has ever worked for you on Linux, you're using Wine and/or Play on Linux to run it. Otherwise, an .exe will not run on Linux.

---

### Post by kmarzi on 2011-04-07
Nope, I wasn't using  Wine in this instance. Like I say, it may not be an .exe. 

In fact, I tried opening it in Wine and even then it didn't work, given that I simply cannot change any of the permissions.

But I can assure you, I have never used Wine to play Urban Terror.

---

### Post by el_koraco on 2011-04-07
click alt-f2, put the command gksu nautilus in the box, and then try to go to the file and change the properties.

---

### Post by kmarzi on 2011-04-07
Thanks for the help... But, alas, that didn't work either. 

Error message: "Could not display "/media/Expansion Drive/UrbanTerror/ioUrbanTerror.i386". The location in not a folder."

I just downloaded Urban Terror again. As per the Linux download instructions, I tried to click on the "Allow executing file as program" box in properties and, as before, it simply unchecks itself. Very strange...

---

### Post by ottosykora on 2011-04-08
make sure wherethe file is really located, then make sure the drive is mounted and then tray something like

sudo chmod755 /media/Expansion Drive/UrbanTerror/ioUrbanTerror.i386

---

### Post by djpemberton on 2011-05-20
I have the exact same problem when trying to run linux portable apps from an external drive with 11.04. Any solution yet? I haven't had this problem (unable to mark executable) in previous versions.

---

### Post by kmarzi on 2011-05-20
Hey. Unfortunately, no solutions as yet...

---

