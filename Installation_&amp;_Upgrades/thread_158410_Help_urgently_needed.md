---
title: "Help urgently needed"
date: 2006-04-11
forum: Installation &amp; Upgrades
---

### Post by nolongerlivecd on 2006-04-11
I don't remember configuring the sudo password, so what should I put? (I need to install xorg drivers for ATi Mobility Radeon x700). Should I put my user account password, or what should I put?

sudo apt-get install xorg-driver-fglrx

---

### Post by Sef on 2006-04-11
> Should I put my user account password

The password for sudo is your user account password.

---

### Post by Yanagi on 2006-04-11
You know, I had this issue too. I think Ubuntu has a "default" root password.

What I did was System > Administration > Users and Groups
For the password to enter that, I entered my user password, 
Checked Show all Users and Groups at the bottom of the window,
Found root,
Clicked properties and changed the user password there.

Hope this helps.

Edit: in response to Sef's post.
That may be, but whenever I opened bash and did su and typed in my user password (before I found it in users and groups), it would tell me the password was incorrect.

---

### Post by nolongerlivecd on 2006-04-11
But I can only use command line... My graphics card not configured yet

---

### Post by Yanagi on 2006-04-11
Well according to sef, your user password should work.


Either way, though, the installation should have installed a generic video driver at least so that you can boot into Gnome..

---

### Post by Gustav on 2006-04-11
Look at this [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by nolongerlivecd on 2006-04-11
Hey, I don't know if I should continue with this thread, since now, I'm just having problems with a blank screen in ubuntu. I'm using an ATi Mobility Radeon x700. I can't seem to configure it well.

Thanks for all the help

---

### Post by nolongerlivecd on 2006-04-11
Also, how do I make the LED switch in Acer Aspire 5500 for WLAN work? Does ubuntu come with the drivers form Intel PRO/Wireless 2200BG

---

### Post by spandon on 2006-04-11
Hi,
As you are using an ati x700, I assume that you are using a laptop?
If so, you should have entered at boot:
for live cd
l**ive noapic nolapic, hw-detect/start_pcmcia=false, vga=771**
for installation
[B]linux noapic nolapic, hw-detect/start_pcmcia=false, vga=771
[/B]
Try the first command line using a live cd, if this works, the do a restart without the live cd and enter the command the second command line, using the password you entered on installation, if you cant remember the password it means a re installation.
If these command lines work on your machine, then once into gnome desktop after installation, you need to edit your grub  file.
Appending the command line above (without live or linux) to the line starting with kernel.
This works for me using Breezy and dapper flight 6
Don

---

### Post by nolongerlivecd on 2006-04-11
My ubuntu is already installed.

---

