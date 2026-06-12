---
title: "Installation problem"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by Ferdi on 2006-06-27
I'm new to linux, so you'll have to bear with me. I do have a little experience with unix, but it was very limited. I have tried to install 2 different (SuSE 10.1 and Ubuntu) distributions of Linux on my computer, and have had problems with both installations. I've tried SuSE 10.1 (which was a purchased version) and was able to get it installed and to the KDE desktop. However, upon reboot it gave me a service module error and took me to the login: but it would not let me login. I know the login and password, because i used the same thing for both. Anyways, I then gave up (after 2 reinstalls and a repair) and tried Ubuntu, which I just download from the site the other day. It installed, however when I restart the computer it boots up and goes to a screen saying, **"Server Authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but is not owned by user root and group gdm. Please correct the ownership or GDM configuration and restart GDM." **It then goes to 

[B]Ubunta 6.06 LTS ferdi tty1
ferdi login:[/B]

(The word "**ferdi**" above is my name which I used to keep everything simple for myself during the installation process.) Can anybody help, I really want to get Linux to work on my computer and don't want to purchase a Windows XP OS. Any advice will be appreciated. Keep in mind that I'm new to this and will need some detailed advice if possible. Thanks.

I also posted this in the desktop support forum.

My system consists of the following:

AMD 700 Mhz processor (Athlon, I believe)
35 gig harddrive
256 MB memory
FIC motherboard (I believe)
Sis based graphics card
Linsys 10/100 ehternet card
unsure of which sound card.

It was put together by a store, so there is no "brand".
I downloaded the ubuntu cd that is for the x86 versions, since the processor is not 64 bit. The computer is probably 6-7 years old if that helps at all. Please let me know if you need anything else. Thanks

---

### Post by kzutter on 2006-06-28
hmmm... I do not even have this directory on my dapper box.
:EDIT: Oh, that's right - I don't use Gnome - duh!

To change the ownership and group of the dir to what it wants takes just one command.

sudo chown root:gdm /var/lib/gdm

---

### Post by Ferdi on 2006-06-28
After I logged in it comes to:

-bash: cannot create temp file for here document: Read-only file system
ferdi@ferdi:~$

Then I proceeded to type in the command "**sudo chown root:gdm /var/lib/gdm**" it asks for my password which I type in and it says **chown: changing ownership of '/var/lib/gdm' : Read-only file system**.  I then turned off my computer and re-booted and the same initial message comes up.  I've used the command **su root** to try and change to the root user, but when it asks for my password it says **su: Authentication failure**.  I've used the same password for the root as for the local user, so there shouldn't be a problem there.  Any other ideas as to why I can't log on as a root user or ideas on how to fix this problem so the program will start with the graphical interface?  What should be the exact command line to start the GUI?  Please let me know if I'm typing something incorrectly.  Thanks.

---

### Post by Ferdi on 2006-06-28
I've posted a thread in the desktop area as well if anyone wants to take a look at what some other people wrote and my follow-up replies.  I have got a little further along, but haven't quite solved the problem.  Just run a search using "ferdi" and you'll find my other post.  Thanks for the help.

---

