---
title: "Live CD works, installation fine, won't boot"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by wilbur176 on 2007-11-06
Hi all,

Had no luck searching forums and would really appreciate any help. Previously had 7.04 loaded via Wubi, but have since had a Windows clean install and would like to dual boot 7.10. Linux knowledge is limited but keen to learn more.

Existing formatting on disk is 120GB WinXP Pro NTFS, 16GB free space, 320 GB Data NTFS

Burned AMD64 Live CD @ x4 and it boots into Ubuntu (only worked by removing quiet and splash with F6 option, hangs otherwise with blank screen)

From here i can partition the freespace and install no problem with 1GB swap and 15GB ext3 mounted at /

Installation runs fine, but get blank screen after reboot even trying recovery boot option.

Can anyone point me in the right direction?

Many thanks,

Will

Spec
----------------------------
Q6600 quad G0 Stepping
Gigabyte P35C DS3R
2GB Crucial Ballistix
BFG 8800GTS 320 MB
Liteon DVD
Samsung SATA 500GB
----------------------------

---

### Post by ROBarber on 2007-11-06
Can you boot from the first hard disk using Ubuntu CD Live?

do you have access to grub menu on start up?

is not clear for me what is wrong with your system

---

### Post by wilbur176 on 2007-11-07
Many thanks for replying,

Found last night system booted fine using 'e' in Grub and removing splash & quiet, then booting with 'b'. No access to this system at work so will trawl forums for more help on this later.

Will

---

### Post by AimarZar08 on 2007-11-09
Hi guys...

I think I found a solution...it worked for me (thankfully)

Firstly, you will need to install using the ubuntu-amd64-alternate.iso

Reason:

To set up network connection (will explain as I go on)

e.g. mine was

xxx.xxx.xxx.xxx   IP
255.255.255.0       SUBNET
xxx.xxx.xxx.xxx   GATEWAY

xxx.xxx.xxx.xxx(INSERT 1 SPACE HERE)xxx.xxx.xxx.xxx

where xxx.xxx.xxx.xxx is the appropriate value for IP,Gateway, DNS1 & DNS2

When presented with the installation menu, choose the first option (forgive me for not stating exactly...but it is definitely the very 1st option in the menu)

You will be asked to set language, keyboard type...then the system will try to configure your network connection using DHCP

A. If your cable is out this will fail and give u options to choose from: CHOOSE Manually configure network (i paraphrase)

B. If your cable is in it will likely tell you that the DHCP was automatically configured, do as follows

Choose "Go back" and select manually configure network (again i paraphrase)

After doing this the insatllation will complete the system will:

Prompt you to remove your installation cd
Reboot

On reboot, press esc when the grub menu is loading

Select the second option in the ensuing menu (i.e. recovery mode)


Recovery mode will load and then

u will be at the command line for the root user...


assuming everything went ok with the network config...you shud be conected to the internet (your network cable...if you forgot should now be connected)


*************A Solution for blank screen Ubuntu 7.10 Gutsy*****************


sudo apt-get update     (loads the refreshed list of available system updates)

sudo apt-get install nvidia-glx-new

*******************************************************************

I'm a linux/ubuntu noob so i was at this, searching through forums etc to find the answer, tho now it makes sense.

I really hope this works for all who struggled like me.

PEACE!!!

---

### Post by rsambuca on 2007-11-09
It is your 8800 that is giving you the trouble.  You have to install the latest nvidia driver in order to run that card.

---

### Post by AimarZar08 on 2007-11-09
Sorry missed one last piece...

use

sudo nvidia-xconfig

to update the system, this will correct the settings in the /etc/X11/xorg.conf file

This should be done at command prompt before rebooting

---

