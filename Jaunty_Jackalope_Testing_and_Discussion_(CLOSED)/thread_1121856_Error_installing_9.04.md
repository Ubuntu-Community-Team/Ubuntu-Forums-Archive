---
title: "Error installing 9.04"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by fixxxer50 on 2009-04-10
Hi everybody I am new here. I tried to install ubuntu 9.04 the beta(alpha) version which is available for download. I boot through the Live CD. The whole install process is fine except for when it reaches 90% when it starts detecting my hardware. The screen goes blank for a second(I think it tries to detect my display card) and then I get logged off the live cd. After 10 Seconds I am automatically logged back in but the setup is gone everytime. Please help what am I suppose to do. When I reboot my system I get the Xp boot menu options. No Grub. I tried to build grub from the live cd, but was not able to . Please Help!:cry:

---

### Post by fixxxer50 on 2009-04-10
> **Gambitt said:**
> Why dont you try installing through wubi. [http://wubi-installer.org/](http://wubi-installer.org/)

Thanks for the quick reply! Thats what I tried initially but that gets stuck at making virtual drive.:(
Any other suggestions?

---

### Post by fixxxer50 on 2009-04-10
> **fixxxer50 said:**
> Thanks for the quick reply! Thats what I tried initially but that gets stuck at making virtual drive.:(
Any other suggestions?

Can someone please help! Is there anyway to disable hardware detection during install so The install can finish and then I can detect/install my hardware later on. Or maybe just someway to not detect video card during hardware detection. Can someone please help I have been waiting for hours. Thanks!!!

My Computer:
AMD 2600+ Athelon Xp with MSI - 6777 Motherboard 1.5 GB Ram NVIDIA GeForce4 MX integrated GPU. I have had issues installing 8.10 on it before(was not able to install -- Even the Live CD didnot work) but with 9.04 live cd works perfectly.

---

### Post by markbuntu on 2009-04-10
I ran into this problem with jaunty alpha. It was a migration assistant crash causing grub to not get loaded.There is a ton of bug reports on this. 

Try this. Run the live cd and open a terminal and type

ubiquity --no-migration-assistant

---

### Post by fixxxer50 on 2009-04-10
> **markbuntu said:**
> I ran into this problem with jaunty alpha. It was a migration assistant crash causing grub to not get loaded.There is a ton of bug reports on this. 

Try this. Run the live cd and open a terminal and type

ubiquity --no-migration-assistant

So I just type that in the Terminal and Install using the Install Icon on the Desktop? Anything else I need to do?

Edit when I type that in Terminal the install started still going on lets see what happens

---

### Post by markbuntu on 2009-04-10
You may need to 

sudo ubiquity --no-migration-assistant

I don't remember if it made me do sudo or not but anyway if you run the command in a terminal the installer (ubiquity) will just start up and run as usual and skip the migration assistant.

---

### Post by fixxxer50 on 2009-04-10
> **markbuntu said:**
> You may need to 

sudo ubiquity --no-migration-assistant

I don't remember if it made me do sudo or not but anyway if you run the command in a terminal the installer (ubiquity) will just start up and run as usual and skip the migration assistant.

I ran install with ubiquity --no-migration-assistant without the sudo, it gave me an option to skip network time settings, but then went on to detect hardware, and then screen splash and I got logged out and the session was lost with an incomplete install, Now I am going top gpart the partition and try with sudo again. 
Thanks for trying to help. Really appreciate it. And lets hope it works~~!!

Edit:
Ok just added one more step. Everytime My computer logs out when install tries to detect my Video hardware. So Now before starting install I just installed my NVIDIA video driver on the go in the live session. Hope fully this will prevent the log off.

---

### Post by fixxxer50 on 2009-04-10
> **markbuntu said:**
> You may need to 

sudo ubiquity --no-migration-assistant

I don't remember if it made me do sudo or not but anyway if you run the command in a terminal the installer (ubiquity) will just start up and run as usual and skip the migration assistant.

It didnot work please help it freezes again at detecting hardware and loggs me off. then the install has to started all over again. Anyway to disable hardware detection.?

---

### Post by markbuntu on 2009-04-10
OK, when you get the first menu on the live cd screen hit F4 and choose safe graphics mode. This will use the VESA driver. Do not install the nvidia driver until after you get all the updates.

---

### Post by fixxxer50 on 2009-04-10
> **markbuntu said:**
> OK, when you get the first menu on the live cd screen hit F4 and choose safe graphics mode. This will use the VESA driver. Do not install the nvidia driver until after you get all the updates.

I had tried that before I posted here the same thing happens. 
What do you  think is causing this. I had an earlier version of ubuntu on this computer about maybe 2 years ago, which had no problem installing. Now in 8.10, I couldnot get the NVIDIA driver to be installed. Some issue with the Kernel. Now the display driver works if I install it but on hardware detection the session crashes.

---

### Post by kjaada on 2009-04-10
I had the same problem with my old desktop which is running 8.04 as 8.10
had a problem with my video driver.I have 9.04 running and,chuffed with it on my Toshiba laptop.It installed no problem and runs great.
Will be following this tread with interest

---

### Post by cariboo on 2009-04-10
The only thing I can add to this thread is that maybe you should try the alternative install cd. It is text based, so you don't boot to a gui until after the installation is finished. The alternate install iso is available [here]("http://releases.ubuntu.com/releases/9.04/"). You have to use the tab, arrow enter keys to navigate through the installation.

Jim

---

### Post by fixxxer50 on 2009-04-10
> **cariboo907 said:**
> The only thing I can add to this thread is that maybe you should try the alternative install cd. It is text based, so you don't boot to a gui until after the installation is finished. The alternate install iso is available [here]("http://releases.ubuntu.com/releases/9.04/"). You have to use the tab, arrow enter keys to navigate through the installation.

Jim

Sounds promisting, It think it will be worth a try.  Will post the outcome here later on. Right now where i live its late at night. Thanks for your time guys!!! 
Appreciate it!

---

### Post by fixxxer50 on 2009-04-11
Hi Mark and Jim ! I downloaded the alternate cd and Installed the system in 1 go, no problem at all. 
Thanks guys for your help.
Really Appreciate it.

---

