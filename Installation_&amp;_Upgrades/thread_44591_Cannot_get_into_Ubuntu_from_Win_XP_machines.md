---
title: "Cannot get into Ubuntu from Win XP machines"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by Ray Fried on 2005-06-26
I just installed 5.04 but cannot get into Ubuntu from a Windows machine.
Set the following:
	sudo apt-get update 
    	sudo apt-get install samba
	sudo apt-get update 
    	sudo apt-get install smbfs

Went to System/Administration/Networks and set the General Tab
Configured for DHCP
Went to System/Administration/Shared folders and set as follows:
path:  /home/ray
Share with: SMB
Name: RayLinux
Allow browsing

Windows sharing settings
Host description server (Samba, Ubuntu)
Domain/Workgroup HOME
Do not use WINS server

When I go to a Windows XP machine and look at My Network Places I can find the Ubuntu machine but when I attempt to get into it, Windows presents a dialog box called Connect to localhost.localdomain and asks for a user name and password. When I fill in my Ubuntu user name and password, the dialog box returns with my Windows username then \ <slash> then the Ubuntu username and will not let me in.  For example it presents RAYLAPTOP\ray for the username. ray is my Ubuntu user name. My Windows Full computer name is RaysLaptop.

What additional things must I do to gain access to my Ubuntu files from the XP machine?

---

### Post by jarrett.wold on 2005-06-27
This got me first time out as well.  You have to add a user to samba via the smbpasswd command.

Check out the man page on smbpasswd.

---

### Post by Ray Fried on 2005-06-27
Thanks so much! Smbpasswd solved the problem! 

You mentioned to "check out the man page on smbpasswd". I am not sure what you implied with "man page". I found informaiton at the Wiki site. Is there a manual page or something?

Ray

---

### Post by kvidell on 2005-06-27
[QUOTE=Ray Fried]Thanks so much! Smbpasswd solved the problem! 

You mentioned to "check out the man page on smbpasswd". I am not sure what you implied with "man page". I found informaiton at the Wiki site. Is there a manual page or something?

Ray[/QUOTE]
 open up a terminal and type the following:
man smbpasswd

You can do man mostcommands/programs-here
It's a neat little quick reference :)
- Kev

---

### Post by edacsac on 2005-06-27
[QUOTE=jarrett.wold]This got me first time out as well.  You have to add a user to samba via the smbpasswd command.

Check out the man page on smbpasswd.[/QUOTE]

And when that doesn't work?

---

### Post by jarrett.wold on 2005-07-03
Google and Google Groups are your best friends...

---

