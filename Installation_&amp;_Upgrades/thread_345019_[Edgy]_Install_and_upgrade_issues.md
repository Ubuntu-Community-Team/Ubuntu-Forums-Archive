---
title: "[Edgy] Install and upgrade issues"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by Jarik on 2007-01-23
When I try to install new software I get this error message :

jarik@jarik-desktop:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.

I installed Automatix and I managed to install a few programs, but the majority wouldnt.

I attached my sources.list if that helps.

---

### Post by aysiu on 2007-01-23
I don't think it has anything to do with your sources.list. Sounds as if that file is just corrupted somehow.

Can you try these commands? ```
cd /var/lib/apt
sudo mv lists lists.corrupt
sudo mkdir lists
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by Jarik on 2007-01-24
Thanks for your reply.
Typing those commands gives me this:

jarik@jarik-desktop:~$ cd /var/lib/apt
jarik@jarik-desktop:/var/lib/apt$ sudo mv lists lists.corrupt
Password:
jarik@jarik-desktop:/var/lib/apt$ sudo mkdir lists
jarik@jarik-desktop:/var/lib/apt$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Lists directory /var/lib/apt/lists/partial is missing.
jarik@jarik-desktop:/var/lib/apt$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  ubuntu-minimal 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  ubuntu-minimal: Depends: wpasupplicant which is a virtual package.
Resolving dependencies...
E: Lists directory /var/lib/apt/lists/partial is missing.
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-minimal

Score is -301

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  ubuntu-minimal 
The following packages will be REMOVED:
  ubuntu-minimal 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 45.1kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: Lists directory /var/lib/apt/lists/partial is missing.
E: Couldn't lock list directory..are you root?
jarik@jarik-desktop:/var/lib/apt$ 

I now seem to have access to synaptic, but I cannot install anything as the option for install is greyed out on all the software listed, using apt-get to install software seems to still be broken. Neither Amarok, Opera or NVU will install, it says 'Package not found'.

Automatix gives me the same error message.

---

### Post by aysiu on 2007-01-24
Try this: ```
sudo mv /var/lib/apt/lists.corrupt/partial /var/lib/apt/lists/partial
```

---

### Post by Jarik on 2007-01-24
> **aysiu said:**
> Try this: ```
sudo mv /var/lib/apt/lists.corrupt/partial /var/lib/apt/lists/partial
```

You beautiful man you.  
If I could give you a kiss over the internet, I would. Thank you so much.

---

### Post by aysiu on 2007-01-24
So it's working again?

---

### Post by Jarik on 2007-01-24
More or less.

I got the updater working and it installed over 300 updates. I got to install Amarok, Opera, and some other stuff.

However, some xserver updates and some software available in Automatix will not install.
I get an error message saying they could not be located.

But I can live without that for now.

Thanks again.

---

### Post by Jarik on 2007-01-25
All looked so rosy for a whille, but now my system is farked.

I changed some settings in my config file to adjust settings for my Logitech mouse, and when I rebooted the screen freezes at the progress bar. The bar is at 99 percent, and then a green and blue line comes in horizontaly. Then nothing happens.

Is there a way to fix this in the recovery mode ?

I booted from a the Ubuntu disk and it ran fine, so I dont think there is a hardware issue.

All help appreciated.

---

