---
title: "Build a customized Ubuntu OS"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by vikasvishnu on 2011-08-02
Hello All, 

In the company I work for, we are planning a vast migration of workstations from Windows to Linux (a little more than 500, step-by-step). Considering the user-friendliness for the users (most of whom are not technically sound), we have selected Ubuntu to be used as the alternative. 

The requirement we have is to customise the OS Installation disk to remove softwares/applications that are not necessary for the users. Also it requires to make other modifications to the look and feel : like changing the boot splash, changing the default wallpaper, default theme etc. 

Please do let me know your suggestions/comments regarding this. Also would any of you will be able to guide me to find any docs, howto etc.

Thanks in advance. 

Vikas Vishnu

---

### Post by nickleboyblue on 2011-08-02
It might be simpler to do all that with a shell script.  All you do is make a shell script in a folder with the splash screen image in it, as well as any other media (like desktop backgrounds, etc.) that you want to use.  The shell script can then be written to remove all of the programs you deem unnecessary and install the extra programs you want to install.

...Or you could set up about one server for every ten to fifteen workstations.  That server would have virtual machines on it that every workstation loads on boot.  In order to get the correct virtual machine setup, simply copy-paste it once it is made and configured how you want it.  The downside with this is that every employee will need personal data storage, as virtual machines always load to their initial state.

As a last option, you could set up the server-client system mentioned above, but instead of using virtual machines, set up users on the server and have the workstations log into the server automatically and remotely on boot.  This may not work very fast, but if a problem arises, you can fix it in one place to fix it for fifteen users.

---

### Post by vikasvishnu on 2011-08-20
> **nickleboyblue said:**
> It might be simpler to do all that with a shell script.  All you do is make a shell script in a folder with the splash screen image in it, as well as any other media (like desktop backgrounds, etc.) that you want to use.  The shell script can then be written to remove all of the programs you deem unnecessary and install the extra programs you want to install.

...Or you could set up about one server for every ten to fifteen workstations.  That server would have virtual machines on it that every workstation loads on boot.  In order to get the correct virtual machine setup, simply copy-paste it once it is made and configured how you want it.  The downside with this is that every employee will need personal data storage, as virtual machines always load to their initial state.

As a last option, you could set up the server-client system mentioned above, but instead of using virtual machines, set up users on the server and have the workstations log into the server automatically and remotely on boot.  This may not work very fast, but if a problem arises, you can fix it in one place to fix it for fifteen users.

Thanks a lot for your reply. Yes, I understand your proposal of having a script that can customize the OS after the installation is done. But I am trying to find something similar to an application like "reconstructor". I could see from its screnshots that it can help a newbie to select/deselect packages, upload their own boot logo, customize the live user name, and a lots more. But its not available for the latest Ubuntu 11.10. I wish I could find something similar to that. 

Regards,
Vikas Vishnu

---

### Post by Megaptera on 2011-08-20
Some ideas here, similar topic!
[http://ubuntuforums.org/showthread.php?t=1826856](http://ubuntuforums.org/showthread.php?t=1826856)

Look at the University o/s mentioned, maybe they'll be a source of guidance too?

---

### Post by cbowman57 on 2011-08-20
You might want to look at this [http://sourceforge.net/projects/u-customizer/](http://sourceforge.net/projects/u-customizer/)

---

