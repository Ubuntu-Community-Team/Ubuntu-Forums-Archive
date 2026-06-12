---
title: "Does not install!"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by Jayesh on 2005-10-03
I tried to install version 5.04 for Intel x86 from the CD I received a short time ago. My Dell desktop is old but meets the stated requirements of 32 MB RAM and 1.8 GB on hard drive.
The installation proceeds for a while and every time the PC hangs up (a dash flashing on a black screen) after the following was displayed, "_unpacking nic-firmware-2.6.10-5-36-di_". 
I even tried to use the live CD and the PC also hung up after a similar message was doisplayed, "_unpacking nic-pcmcia-modules-2.6.10-5-386-di_".
I do not know what to do next. I can use some help installing the software.
Thanks.

---

### Post by darkmatter on 2005-10-03
[QUOTE=Jayesh]I tried to install version 5.04 for Intel x86 from the CD I received a short time ago. My Dell desktop is old but meets the stated requirements of 32 MB RAM and 1.8 GB on hard drive.
The installation proceeds for a while and every time the PC hangs up (a dash flashing on a black screen) after the following was displayed, "_unpacking nic-firmware-2.6.10-5-36-di_". 
I even tried to use the live CD and the PC also hung up after a similar message was doisplayed, "_unpacking nic-pcmcia-modules-2.6.10-5-386-di_".
I do not know what to do next. I can use some help installing the software.
Thanks.[/QUOTE]

Is 32 MB of RAM all the volatile memory you have? If so, the hang 'could' be caused by the lack of available memory.

You could use the server install as a workaround (no GUI), then use apt-get from the command line to install the remaining packages.

---

### Post by Jayesh on 2005-10-04
[QUOTE=darkmatter]Is 32 MB of RAM all the volatile memory you have? If so, the hang 'could' be caused by the lack of available memory.
You could use the server install as a workaround (no GUI), then use apt-get from the command line to install the remaining packages.[/QUOTE]

I also tried that and ended up with the same problem! Does that mean I need more than 32 MB RAM? Is there a way to workaround this situation?

I thank you for your response and would appreciate if you'll respond to my follow up questions.

---

### Post by darkmatter on 2005-10-04
[QUOTE=Jayesh]I also tried that and ended up with the same problem! Does that mean I need more than 32 MB RAM? Is there a way to workaround this situation?
I thank you for your response and would appreciate if you'll respond to my follow up questions.[/QUOTE]

If it is still doing it with a server install, I doubt that the problem is RAM, as you should have sufficient to get a basic setup running.

Have you done a check on the media (CD) to see if it is intact. The Installer allows you to do this. Just delect back at the start of the installer, and it will display a list of options that you may choose from to perform various installation tasks.

One of those is an option to check the integrity od the CD.

Perhaps the CD is coaster material. Just a guess, but that may be the problem.
You may have to download an burn the ISO.

---

### Post by Jayesh on 2005-10-04
[QUOTE=darkmatter]If it is still doing it with a server install, I doubt that the problem is RAM, as you should have sufficient to get a basic setup running.

Have you done a check on the media (CD) to see if it is intact. The Installer allows you to do this. Just delect back at the start of the installer, and it will display a list of options that you may choose from to perform various installation tasks.

One of those is an option to check the integrity od the CD.

Perhaps the CD is coaster material. Just a guess, but that may be the problem.
You may have to download an burn the ISO.[/QUOTE]

Thanks again. Here is what happened...

At the start I'd to press F1 to get installaqtion options. The only way to check integrity of the CD was to select "expert" install option [given my skills that is a laugh]. The CD checked out OK. However, even in the expert mode for both the full and servr install options, the pc hung up at the same place as before! I'm thinking of downloading and burning a CD and try again. Will report how that works out. At present I am at my wits end.

I wonder if anyone else have had a similar problem, and if they mabnaged to solve it.

---

### Post by Revolution on 2005-10-04
I really wouldnt install on anything less than a Pentium3 with 64MB Ram and a 4 GB drive.

A pentium3 means you aren't waiting appreciable time for things to happen.
64MB ram gives what I consider the absolute minimum for running anything meaningful without constantly using HD swap space.
When you do a standard install it uses up 2GB of space - so even a 3GB HD gives you a GB left.

If you dont have these requirements - spend $30 on Ebay for a second hand P3 (500MHz minimum)

Cheers

---

### Post by Jayesh on 2005-10-05
The latest ...
I downloaded  version 5.10-preview and tried to install under both the "full" and "server" modes. In both the cases the pc hung up while unpacking "nic-firmware"  file, as before with version 5.04!

Seems to me that, as someone pointed out, the pc does not have the "right hardware". Since I have other pcs [but not available for ubuntu experiemntation], spending money to upgrade this pc is not an option I want to pursue. Unless someone has other idea to make ubuntu work with this pc, I am ready to hrow in the towel, and getrid/give away this pc.

Thanks to all those who offered help with my problem.

---

### Post by RamiroS on 2005-10-28
Hi. It happened to me... the CD was not working ok... I burned it again (also checked the iso checksum) and worked ok.

---

