---
title: "unattended install with preseed.cfg"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by barboles on 2010-09-15
Hello, i'm trying to do an unattended install, but I don't get elude the questions. The parameters are changed correctly , but the installer stop in the steps.
My preseed file:

#Step 1
d-i debian-installer/locale string es_ES 


#Step 2
d-i time/zone string Europe/Madrid

#Step 3
d-i console-setup/layoutcode string es

#Step 4
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-auto/choose_recipe select atomic
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true

#Step 5
d-i passwd/user-fullname string SISTEMAS
d-i passwd/username string sistemas
d-i passwd/user-password password sistemas
d-i passwd/user-password-again password sistemas
d-i user-setup/allow-password-weak boolean true
d-i netcfg/get_hostname string lubuntu
d-i passwd/auto-login boolean true

#if you want to start commands after the installation
#ubiquity ubiquity/success_command string yourcommands

#Step 6
ubiquity ubiquity/summary note  


ubiquity ubiquity/reboot boolean true
//------------------------------------------------------
And my text.cfg:

label instalacion
	menu label ^Instalacion Automatica
	kernel /casper/vmlinuz
	append initrd=/casper/initrd.lz file=/cdrom/preseed/firewall.seed   
     boot=casper only-ubiquity auto=true priority=critical quiet splash --

---

### Post by barboles on 2010-09-16
I have the same problem. But when it starts the live session, I open a console and  I write "ubiquity --automatic" as root, And the instalation start without questions and take the parameters correctly. My question is, How can I get launch the instalation automatically.

---

