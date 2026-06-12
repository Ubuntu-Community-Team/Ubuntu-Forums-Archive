---
title: "Live CD not root"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by kaspar_silas on 2010-05-11
Hi,

Has anyone ever ran into problems with permissions from a live CD.

Grub is messed up on a 9.10 server machine. Somehow all the kernel images are now missing from /boot/ . Very mysterious as it only went off due to a power cut so I would have expected it to bounce back. 

Anywho I used my 10.04 live CD (well USB really) to load in with the intention of restoring grub. Feel free to point out if this won't work by the way.

Whilst the live CD loaded I got a warning saying something like: getpwuid_r() failed due to unknown reason.
This was then followed by about 20 lines of: 
stdin: ERROR
this finished with the not so pleasing line:
HDIO_GET_IDENTITY failed for /dev/sdc

Then normality resumed and the live CD loaded and everything seemed okay. However it wasn't I didn't have administrator priviledges and attemping to use sudo gave the line.
MUST BE SETUID ROOT

Any ideas as I am baffled.

---

### Post by byStanderone on 2010-05-11
...haven't done a thorough permission privelege probing of a live cd (or usb), but would guess they have no privilege as root, unless perhaps the installed system had granted such beforehand...for one main reason, that would be a severe security risk.

---

### Post by kaspar_silas on 2010-05-11
But if they don't have admin privileges you could never use a live CD to restore anything. It would be pretty useless. 

Live CD certainly used to have root/sudo privileges. Are you telling me the modern live CD only log you in as a unprivileged user.

A live CD is indeed a massive security risk but it always has to be (ignoring encryption and boot locking in bios). It's exactly the same risk as putting all your hard drives in a computer over which you have total control.

---

### Post by axel_2078 on 2010-05-11
I ran into the same problem a couple days ago with my 10.04 Live CD. I needed to modify /etc/default/grub and it wouldn't let me. So, I did a su - (or maybe sudo su -) to become root and then I tried to modify the file with gedit, only to find out that you can't modify files with graphical utilities even as root. It kept giving me access denied errors. So, I opened up the file with nano and it let me edit it just fine. Command line works, graphical tools don't.

---

### Post by bumanie on 2010-05-11
To do things with root privileges in graphical mode, in terminal > gksudo nautilus alternatively,>  sudo -i will give root privileges for cli mode.

---

### Post by axel_2078 on 2010-05-11
> **bumanie said:**
> To do things with root privileges in graphical mode, in terminal  alternatively,will give root privileges for cli mode.

I tried gksudo gedit, which is the same thing....it pulls up a graphical tool for editing, but I still did not have permission to edit /etc/default/grub as the root user (while running from the LiveCD). So, it doesn't always work.

---

### Post by bumanie on 2010-05-11
With 10.04, grub 2 has a config file named /boot/grub.cfg, but it is read only. Read [here]("http://ubuntuforums.org/showthread.php?t=1195275") for how to edit it - it is different to grub-legacy, one does not directly edit the file as before with /boot/grub/menu.lst

---

### Post by axel_2078 on 2010-05-11
> **bumanie said:**
> With 10.04, grub 2 has a config file named /boot/grub.cfg, but it is read only. Read [here]("http://ubuntuforums.org/showthread.php?t=1195275") for how to edit it - it is different to grub-legacy, one does not directly edit the file as before with /boot/grub/menu.lst

I wasn't trying to modify /boot/grub.cfg. I was trying to modify /etc/default/grub. Once I was able to do that, I just ran update-grub and it modified /boot/grub.cfg as necessary.

---

### Post by bumanie on 2010-05-11
The things in /etc/grub.d are the individual sections of /boot/grub/cfg that need to be edited via the instructions in the link I sent. Things in /etc/grub.d are also read only and have to edited individually via the correct method. Grub2 is completely different to grub-legacy - to edit /etc/grub.d you need to follow those instructions at the link already sent. Editing /boot/grub.cfg according to that thread will then change the contents of /etc/grub.d upon updating grub once /boot/grub.cfg has been edited.

---

### Post by aeb1 on 2010-06-05
I just used a ubuntu LIVE! CD to fix a broken 8.04 LTS system which lost the /auto directory in an upgrade.

The key was to run sudo su in a terminal window and use the CL to replace the missing /auto directory.

---

