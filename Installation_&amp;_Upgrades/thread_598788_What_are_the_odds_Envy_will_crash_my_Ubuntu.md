---
title: "What are the odds Envy will crash my Ubuntu?"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2007-10-31
I'm trying to help someone get Compiz Fusion going on their PC.  All we know so far about the card is that it's an nVidia with dual monitor output and that it does support direct rendering.  I don't know what the command is to probe the card and find out what model it is (searching for that in a separate thread).  So I  was wanting feedback about Envy.

I tried it once in the past, and it crashed my system.  This makes me very apprehensive about using it, but I from the looks of things, it's gotten a lot better.

This persons computer is far far away from me, and the last thing I want to do is use a script that causes their computer to crash and make it next to impossible for me to troubleshoot.  I've never known what to do after a crash such as the one I experienced after using Envy, and I don't want to tell someone they have to reinstall their OS.

The goal is to get Compiz working, and I'd like to take extra caution in doing so.  Thanks in advanced for the help!

---

### Post by forestpixie on 2007-10-31
I used it and it didn't crash mine. But the driver it installed didn't allow me to use nvidia-settings to get ny tv out working - although I've got an old card so maybe that didn't help. I ended up uninstalling with envy and then using restricted driver manager to get it going. I've finally got compiz going - didn't bother on feisty. 

Does the restr driver manager not do the job?

---

### Post by Pumalite on 2007-10-31
The best way to install drivers is the old fashion way. Download from Nvidia the appropriate driver and install following guidelines.

---

### Post by Cochise on 2007-10-31
to idendify the gpu terminal > lspci

---

### Post by Dark Hornet on 2007-10-31
--from many of the posts I have read...there is a good possibility that it can crash your box....with that said, I have used Envy in the past, and had no issues.  Now that I did a clean install of Gutsy, I had no need for Envy....good luck.

---

### Post by ruibernardo on 2007-11-01
I used envy in edgy and when I upgraded to feisty I didn't have xorg. This will happen even with the official drivers from nvidia website.

It's normal, since when you upgrade to another kernel version, you have to compile the modules of the drivers for that new kernel. Envy or nvidia official dirvers will not do that (nor will any modules you have compiled yourself).

If you use the official drivers from the repositories, they will get upgraded on the upgrade process, as will all the official repos packages, and nothing will break.

Just be prepared when you reboot and compile the modules yourself (for nvidia official driver) or check the envy website to know what to do about it *before* you dist-upgrade.

---

### Post by Bakon Jarser on 2007-11-01
I also didn't need to use envy for gutsy.  If it installed the restricted driver for you and the tv out isn't working (shouldn't be by default) try opening the terminal and typing 
nvidida-settings

This will open the nvidia control panel.

---

