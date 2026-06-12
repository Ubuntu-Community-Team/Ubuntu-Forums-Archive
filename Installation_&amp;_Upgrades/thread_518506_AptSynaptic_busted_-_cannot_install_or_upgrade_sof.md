---
title: "Apt/Synaptic busted - cannot install or upgrade software now!"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by kulturloseramerikaner on 2007-08-05
I tried installing Virtualbox last night from their website (they've got a .deb file just for Feisty.) I saved it to the desktop and then opened it with the package manager to install. The install seemed to hang, but I let it keep running and went to bed. I woke up to find it at the same spot, so I killed it and tried to do a reinstall.
No love. I got an error saying another package manager was running. I restarted GNOME; same error.
Restarted the system. Same error. I get this when I try runnng Synaptic or apt:
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
I can't reinstall as it says there's another package manager running when I do, though running top doesn't show any others! Now I can't update or install/remove software!
I found a similiar similar post; it happened to a guy running Breezy with a different program, but the fix he came up with doesn't apply to Feisty as the files specified to delete are no longer present.
Please help!

---

### Post by PaulFr on 2007-08-06
In Feisty, AFAIK the apt-get lock file is at **/var/cache/apt/archives/lock**, did you check/remove that ? Also, what is the output of **sudo apt-get check** ?

---

### Post by kulturloseramerikaner on 2007-08-06
Thanks for the reply, I was getting worried!  Here's what I got:
brian@HAL:~$ sudo apt-get check
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
brian@HAL:~$ 

I found the lock file you were referring to; are you saying I should delete it?  It won't let me run it...
Thanks again.

---

### Post by PaulFr on 2007-08-06
As far as your VirtualBox .deb file goes, you can try ```
dpkg -C
``` to audit your installations, and suggest fixes. After fixing these, try running ```
sudo apt-get update
sudo apt-get upgrade
``` to upgrade your system.

You should only remove the lock file if you get the error that another package manager is running (and there is no such process running). Running apt-get again creates the lock file.

---

### Post by Seisen on 2007-08-06
If you downloaded the Virtual Box .deb have you tried to reinstall it?

---

### Post by kulturloseramerikaner on 2007-08-06
> **PaulFr said:**
> As far as your VirtualBox .deb file goes, you can try ```
dpkg -C
``` to audit your installations, and suggest fixes. After fixing these, try running ```
sudo apt-get update
sudo apt-get upgrade
``` to upgrade your system.

You should only remove the lock file if you get the error that another package manager is running (and there is no such process running). Running apt-get again creates the lock file.
brian@HAL:~$ dpkg -C
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 virtualbox           

Nothing there; and yes, attempting to reinstall the .deb gives me the "another manager running."

---

### Post by PaulFr on 2007-08-07
This is what I would suggest: Please run ```
sudo fuser -v /var/cache/apt/archives/lock
``` to check if there are indeed any real processes that are accessing the lock file. I expect there to be no output. If there is any output PID, then please terminate that process(es). Then ```
sudo rm -f /var/cache/apt/archives/lock
sudo dpkg --remove --force-remove-reinstreq virtualbox
``` to forcibly remove the partial installation of virtualbox. Now run ```
dpkg -C
``` to see if things have cleaned up. If there are no errors reported, and you want virtualbox to be installed, then ```
sudo dpkg -i <path_to_your_downloaded_virtualbox_deb_file>
```N.B. Please remember to replace  **<path_to_your_downloaded_virtualbox_deb_file>** by the actual path on your system to the virtualbox .deb file.

---

### Post by kulturloseramerikaner on 2007-08-07
We got it!  Thank you!

---

