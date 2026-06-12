---
title: "'home' folder questions"
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by Adam Lee on 2005-09-23
Hi, I've been using Hoary for a couple of months now and I'm very satisfied it's performance. However, since Breezy is planned to be released on Oct. 13th, I'm getting ready for myself for a fresh new installation.

So I searched this forum on 'Breezy', and I found many of linux users are keeping a seperate patition for 'home' folder and mount it when they change distro or install a newest release.

Does that mean I don't have to spend a day or two configuring clear-type font, printer, wireless, mouse and etc again by simply copying current home folder to newsly installed Breezy?

Won't there be any compatibility issues due to difference of program version?

Having used Windows for years, it's hard to grasp the whole "copying home folder to new intallation' concept. So I'm sorry if my questions don't make sense at all.

---

### Post by phex on 2005-09-23
Two things i will mention:
1) Yes, it is possible to use your home folder untouched. but this has only effect on programs, which use you home folder to store the configuration. Since all programs normaly use this, your configuration is saved. but you have to configure cups, samba fstab again because their configuration files are in etc directory. but you can simple copy the files to your home directory and after installation, you can copy it to the right place. ;)

2) You can simple upgrade your ubuntu version from 5.04 to 5.10. the old packages will be replaced by newer ones. thats it. ;)

---

### Post by tktreload on 2005-09-23
only the programs that have individual settings for each user have their settings stored in the home folder.
so the wireless things probabely wont be saved, but some of the other things may be saved. Also if there are compatability problems with some of the configs in the backedup home folder you can just delete the problematic files and reconfigure the program.
So all in all it seems that you should give it a try

---

### Post by aysiu on 2005-09-23
Well, you're not really copying the /home folder. If it's a separate /home partition, it's being mounted, not copied. But, yes, it should be fine to do a dist-upgrade and keep the settings in /home as they are. However, if you do a fresh install (as opposed to a dist-upgrade), you'll have to reinstall all your programs and all your codecs, etc.

---

### Post by mlomker on 2005-09-23
Most of your desktop (i assume gnome) settings are kept in /home.  The system settings are kept in /etc.

My thoughts on [partitioning](http://ubuntuforums.org/showpost.php?p=350596&postcount=7) and [backing up](http://www.ubuntuforums.org/showpost.php?p=361622&postcount=4) your current configuration.

You won't want to do a full restore of /etc if you are upgrading to a newer version, though.  You could instead open the archive and pull out individual files later if you realize that something was missing.

---

### Post by phex on 2005-09-23
exactly what i tried to say. ^^ but what i do if i install a new linux is:

copying to home directory: 
/etc/fstab
/etc/init.d/firewall (my firewall script ;))
/etc/X11/xorg.conf

then i reinstall linux, formating all partitions except the partition where i have specified /home as mount point and install all files again.

I must mention that I have apache2, tomcat, mysql, firefox, thunderbird and some java programs for programming on my home partition and i have not used synaptic or apt-get to fetch it. the advantage is, that I simple can copy the whole home partition to my laptop and I have exactly the same programs there. if you modify .bashrc you can start each programm over the terminal from the laptop and from the desktop pc exactly the same way. 

thats all. ;)

---

### Post by Adam Lee on 2005-09-23
Oh wow thank you all for such a quick reponses!
I guess I will back up my home folder and save some files from etc folder, and use only configs that I need since current home folder also contains configs for programs I no longer use.

Again, thank you all!

---

