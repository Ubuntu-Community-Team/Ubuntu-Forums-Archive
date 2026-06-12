---
title: "VirtualBox folder Access question."
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by Kaizoku001 on 2011-09-11
I just installed Ubuntu 11.04 on a 2 tera HDD
partitioned it so /root, /, and /Home are on diff partitions (home having the bulk of it all.
Question:
I would like to install Win 7 using virtual Box. I'm wondering, will Win have access to the files in my home folder? or do I need a special NTFS partition that the 2 OS can share?

---

### Post by haqking on 2011-09-11
> **Kaizoku001 said:**
> I just installed Ubuntu 11.04 on a 2 tera HDD
partitioned it so /root, /, and /Home are on diff partitions (home having the bulk of it all.
Question:
I would like to install Win 7 using virtual Box. I'm wondering, will Win have access to the files in my home folder? or do I need a special NTFS partition that the 2 OS can share?


Visit [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

and download latest version for your system (it is in the software centre but a bit out of date)

Also download the extension pack on the same download page

To make USB work (common question here) you need to add yourself to the Vboxusers group by doing the following:

sudo usermod -a -G vboxusers username 

Then  you are set to go.

After installing your chosen OS in a VM you will need to install the VboxAdditions (not the extension pack, you should of installed this already as they are different)

The additions install inside the VM to add graphics functions and the like.

see here [http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html) for installing additions

As for accessing files you can setup shared folders so that your VM has access to whatever you like on your Host system. Setting up shared folders is in the same chapter i linked to above

I personally give it access to a USB flash drive which i rsync daily my documents etc to and then use that under my VM but its personal choice.

Have fun

Regards

haqking

---

### Post by Kaizoku001 on 2011-09-12
Thanks is for the reply,

Will give ita try tonight or tomorrow anklet you know how it goes.

---

### Post by rodlph on 2011-09-12
Provided you have completed all necessary installation procedures as stated by haqking; You can also define folder access once your Guest OS is running. Here's how I do it with win xp. Should basically be similar to what you do with Win 7.

Right-click on the folder icon of your VBox instance(lower-right side of your Vbox window). (You can also click on the Devices menu of your VM window.)
Click Shared Folder, then click on the folder+ icon. Browse to the desired folder to share with the Guest OS.
Once the folders are available for the guest - browse the network on your guest os for  "VirtualBox Shared Folders" or something similar.
Click Vboxsvr
From there you should see a list of Folders you shared with the previous steps.

Hope this helps. :)

---

### Post by Kaizoku001 on 2011-09-13
Little problem here!
I DLed the latest version of VB ose Amd 64
virtualbox-4.1_4.1.2-73507~Ubuntu~natty_amd64
I then UN-installed the previous version,
Yet when I Doubl click the VB file, software center comes up and says:
**Conflicts with the installed package 'virtualbox-ose'**

Any Ideas?

---

### Post by haqking on 2011-09-13
> **Kaizoku001 said:**
> Little problem here!
I DLed the latest version of VB ose Amd 64
virtualbox-4.1_4.1.2-73507~Ubuntu~natty_amd64
I then UN-installed the previous version,
Yet when I Doubl click the VB file, software center comes up and says:
**Conflicts with the installed package 'virtualbox-ose'**

Any Ideas?


how did you remove the previous version ?

use synaptic package manager:

then

sudo apt-get autoclean

then double click the .deb

---

### Post by Kaizoku001 on 2011-09-14
Ok this is weard.

UN-installed the old version.
Installed the new one. the installed the extension packs (when I 2x click them VB opens and let me install them). 
Now this was all done 2 days ago.
This morning I decide to create a win VM and type virtual box in my app and no icon come up. VB is not in my app group. I tried Oracle and VM but nothing.
yet if I 2x click the extension pack VB opens.
???
Where do i find the icon for VB?

---

### Post by haqking on 2011-09-14
> **Kaizoku001 said:**
> Ok this is weard.

UN-installed the old version.
Installed the new one. the installed the extension packs (when I 2x click them VB opens and let me install them). 
Now this was all done 2 days ago.
This morning I decide to create a win VM and type virtual box in my app and no icon come up. VB is not in my app group. I tried Oracle and VM but nothing.
yet if I 2x click the extension pack VB opens.
???
Where do i find the icon for VB?


you can launch it from terminal:

```
virtualbox
```

also you can 

```
whereis virtualbox
```

to show all instances, the executable is in /usr/bin or should be.

If it is installed then you can create a launcher for it, if it didnt put on on your menu, mine by default comes up in the system tools menu i think, which im not bothered about as i have a link on my desktop

---

### Post by Kaizoku001 on 2011-09-15
> **haqking said:**
> 
If it is installed then you can create a launcher for it, if it didnt put on on your menu, mine by default comes up in the system tools menu i think, which im not bothered about as i have a link on my desktop
Thanks...

Well the code works, but I still can't see it in my system Tools, although it shows as being a tool recently used???

How can I put an icon on my Desktop?

---

### Post by haqking on 2011-09-15
> **Kaizoku001 said:**
> Thanks...

Well the code works, but I still can't see it in my system Tools, although it shows as being a tool recently used???

How can I put an icon on my Desktop?

right click on desktop, choose create new launcher and browse to location which should be /usr/bin

---

### Post by Kaizoku001 on 2011-09-18
Ok so I have VirtualB running.
I installed Win 7 (64), but...
can't access the INTERNET? Do I need to do something special to give VB INTERNET access?

---

### Post by haqking on 2011-09-18
> **Kaizoku001 said:**
> Ok so I have VirtualB running.
I installed Win 7 (64), but...
can't access the INTERNET? Do I need to do something special to give VB INTERNET access?


Depends how you have your networking setup, NAT is the easiest way from the VM Netowkr settings, which should be default.  Or if bridged then the VM needs its own valid IP for the LAN.

What are your VM network settings ?

---

### Post by Kaizoku001 on 2011-09-18
Thanks
I had my VB set to NAT,
Once I changed it to Briged, my net connection went live

DOMO Arigato

---

### Post by haqking on 2011-09-18
> **Kaizoku001 said:**
> Thanks
I had my VB set to NAT,
Once I changed it to Briged, my net connection went live

DOMO Arigato

Do  itashimashite ;-)

Glad i could help.

make sure you use thread tools to mark the thread as solved.

Peace

---

### Post by Kaizoku001 on 2011-09-18
Still haven’t tried sharing the folders and getting the USB to run,
Once I have it all set up I'll mark it solved.
Thanks for the reminder.

---

