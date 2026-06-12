---
title: "How to install ATI Catalyst Driver?"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by emptycoder on 2011-11-17
I'm still new to Linux, so would anyone please help how to install ATI Catalyst Driver?
I have downloaded the latest Driver from thier website (ATI Catalyst 11.11)
ati-driver-installer-11-11-x86.x86_64.run
But I don't know what to do next.
I have Ubuntu 11.10 (Oneiric Ocelot) 64bit with GNOME shell. 
Thanks.

---

### Post by Mark Phelps on 2011-11-17
There are various ways to do this. To find out the details, go to the link below, enter the information for your card:

[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")

When you get a drivers download page, you will see a line Release Notes.  Click on that and download the PDF file to your PC.  That contains instructions for installing the driver.

---

### Post by MAFoElffen on 2011-11-17
> **emptycoder said:**
> I'm still new to Linux, so would anyone please help how to install ATI Catalyst Driver?
I have downloaded the latest Driver from thier website (ATI Catalyst 11.11)
ati-driver-installer-11-11-x86.x86_64.run
But I don't know what to do next.
I have Ubuntu 11.10 (Oneiric Ocelot) 64bit with GNOME shell. 
Thanks.
These are for the binaries:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing ATI Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")**[/SIZE][/COLOR][/SIZE][/COLOR]

This is to install debian packaged drivers of the same:
Edit the sources list to include the the Conical Partner Repo's:
```

sudo nano /etc/apt/sources.list

```Then 
```

sudo apt-get update
 sudo sh /usr/share/ati/fglrx-uninstall.sh
 sudo rm /usr/share/ati/fglrx-uninstall.sh
 sudo apt-get remove --purge fglrx*
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install fglrx
sudo apt-get upgrade
sudo reboot

```
The second through fourth commands may get a file nor found... Thats okay.  Ensuring fragments are not there.

---

### Post by emptycoder on 2011-11-17
I did but the link doesn't exist.
File not found.

And FAQ doesn't exist either, please help.

---

### Post by emptycoder on 2011-11-17
Thanks, but is that going to install the latest edition? 11.11?
Because I have read some articles that said the last edition has fixes for GNOME 3 shell. so it's really important to me to install it because I'm using that shell.

---

### Post by Mark Phelps on 2011-11-17
> **emptycoder said:**
> I did but the link doesn't exist.
File not found.

And FAQ doesn't exist either, please help.

If your referring to my post ... I just tried it (again -- I always try the links after posting to ensure they work) and it works just fine.

As to FAQ -- I mentioned Release Notes, not FAQ.

---

### Post by emptycoder on 2011-11-17
i clicked on it and it leads me to this page
[http://www2.ati.com/relnotes/Catalyst_11.11_Linux_Installer.pdf](http://www2.ati.com/relnotes/Catalyst_11.11_Linux_Installer.pdf)
file not found!
if somehow works fine with you, could you please upload it to mediafire or any file-sharing sit so i can have it?
sorry if i asked too much/

---

### Post by ratcheer on 2011-11-17
Post #4 instructions in this thread worked perfectly for me:

[http://ubuntuforums.org/showthread.php?t=1873072](http://ubuntuforums.org/showthread.php?t=1873072)

Tim

---

