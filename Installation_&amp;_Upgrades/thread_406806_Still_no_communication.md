---
title: "Still no communication"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by cfpole on 2007-04-11
I am getting ready to dump ubuntu!  I have been trying to get dial-up to work on this laptop for a couple of weeks, and have way too many hours into it.  Everything else seems to work well, but is useless unless I can get on-line.  It is a Compaq Armada 7800, in which I have installed a 3Com 56K PCMCIA modem.  At one time it worked, but intermittently.  I am trying to use wvdial.  I have run scanModem and tried to send the file to [email]discuss@linmodems.org[/email], but it keeps getting bounced back.  I have sent the wvdial results and the wvdial.conf results to this forum, but have not had any useful feedback.  I have gone through the dial-up discussion on this forum, but am getting nowhere.  Sorry for the lengthy diatribe, but thank you for letting me vent.  Is there a solution that I can understand.

Thank you for any help,

Chuck

---

### Post by neilengineer on 2007-04-11
How about try another Linux distro?  Or reinstall Ubuntu and see.

---

### Post by handaxe on 2007-04-11
I understand how frustrating this must be.

Just looked at my /etc/wvdial.conf and it has a line above [Dialer Defaults]. Doubt that's a solution tho'.

Try gnome-ppp if you have not.  Uses wvdial but has the conf file in your home directory (hidden).

If both give the same problem then.... well ... hmmmm

HA

---

### Post by cfpole on 2007-04-12
Thank You Handaxe.  I did find instructions to load the repository, but when I try to run gnome-ppp, I get the message: bash:  gnome-ppp not found.  

When I ran sudo apt-get install gnome-ppp, I got the reply: 
Reading package lists... Done
Building dependency tree... Done

Then, a bunch of messages:

"W:  Couldn't stat source package"  then a bunch of "list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy" etc.

Since I can't get on-line, how am I suppose to access these packages?

Any other ideas?

Chuck

---

### Post by handaxe on 2007-04-12
Ok, a rather fundamental problem then. You cannot take the laptop to an internet cafe (or equivalent) assuming you have a working network interface / wireless? Much easier that way as you can then use Synaptic / apt-get and sort out the issues I mention below.

Also, I believe that a breezy install-**DVD** will have most of the software already on it. The forums can be searched as to how to enter the dvd so as its contents are available to synaptic /apt without having internet access (cf apt-cdrom)

As you posted, you clearly have internet access of some sort.  You can access the repositories through Firefox and grab gnome-ppp that way. 

Gnome-ppp is accessible here (note that hoary to feisty versions are present so ypou must select the right one)
**_[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-ppp/](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-ppp/)_**

My concern however, is that you will first need to use Synaptic, or better yet, apt-cache (type ```
man apt-cache
``` in a terminal to get the manual) to determine which of the gnome-ppp dependencies you already have installed. Those that you do not have you will need to grab as described above for gnome-ppp.

Good luck,  Ubuntu via a modem is a pain in the butt, as the updates can be large but if thats what you have, thats what you have.  Win XP not much different.

HA

---

