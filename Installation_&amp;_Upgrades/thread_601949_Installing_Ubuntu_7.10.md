---
title: "Installing Ubuntu 7.10"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by working_night_owl on 2007-11-03
I downloaded Ubuntu 7.10 from the website and saved it to my computer. I want to be able to execute the .iso file so that I can install Ubuntu on my computer. Is there a good program or software that I can use to open this file without having to burn it to a CD?

---

### Post by Pumalite on 2007-11-03
You have to burn the iso to CD after doing md5sum, burn at 4x.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
That is, if you want to install.
Inspecting the contents might be done with UltraIso if you are in Windows
In Linux:

If you want to look at your filename.iso, just mount it and then you can access it.

Applications -> Accessories -> Terminal
Code:

sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop

Now, you can browse over to /media/iso with nautilus and see everything in there.

---

### Post by working_night_owl on 2007-11-03
There is no way to just open it and install without burning to a CD? I know that I have opened a .iso file before using a software program I downloaded without even having to burn the file but don't remember what it was called. I have InfraRecorder but am having a hard time with burning it correctly so I just wanted to execute the .iso file and just install it.

---

### Post by Pumalite on 2007-11-03
The solution to that question I ignore; if there is one.

---

### Post by logos34 on 2007-11-03
> **working_night_owl said:**
> There is no way to just open it and install without burning to a CD?.

Yes:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
(-->'CD image approach')

But you need to download the (text-based) Ubuntu Alternate desktop CD--live cd won't work. 

You don't open the .iso, just copy it to C: root directory.  

Or use thenetwork installation approach--'Windows NT/2000/XP (using Grub)'--on same howto. (Note: windows 98/loadlin section no longer appears to be operable).

---

