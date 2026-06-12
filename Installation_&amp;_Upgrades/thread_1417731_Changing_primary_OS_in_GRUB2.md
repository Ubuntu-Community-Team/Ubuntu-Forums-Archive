---
title: "Changing primary OS in GRUB2"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by Drejcek on 2010-02-27
Hi!

I'm using Ubuntu 9.10 and Windows 7. The problem is I share computer with my brother and sometimes with my girlfriend (but computer is still mine basically). 

Now I'd like to set Windows 7 as primary OS, since they don't have much knowledge about computers. When I had Windows XP and Ubuntu 8.04 that wasn't a problem but now I don't know how to do it with GRUB2.

So what I want is s simple explanation how to change GRUB2.

I'm sorry for my bad English.

Regards

---

### Post by darkod on 2010-02-27
The easiest is to write down the full title of your win7 entry as in the grub menu, exactly as it is.

Then open:

sudo gedit /etc/default/grub

and in the line GRUB_DEFAULT=n change

GRUB_DEFAULT="the exact title of win7"

Run

sudo update-grub

and it should be done. Also, if you use the name of the entry, and not the position it will remain default even after with kernel updates you add ubuntu kernels and the position of win7 changes.

---

### Post by oldfred on 2010-02-27
Must be getting late for Darko, I never feel like I have to add anything to his comments (He corrects me most of the time).

Just to clarify, I prefer to copy the entry rather than write it down as Darko said it has to be exact:

find your windows entry in this and copy to grub default like this Vista entry 
gedit /boot/grub/grub.cfg
and copy here
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by Drejcek on 2010-02-28
Thanks both of you. 

It worked.

---

### Post by jfarnold on 2010-04-12
I'm fairly new to Ubuntu, but was very glad to stumble across this thread.  I tried what was suggested, but couldn't find the relevant information, and even when I found the correct document and changed the default accordingly, it didn't do anything at all upon reboot.

I discovered that because I have multiple OSes installed, I was just trying to change the bootloader in the wrong Ubuntu installation (I had a bad install because of a poorly configured liveUSB), and thus had to load up the first OS listed in the bootloader in order to change it.

Now that I figured that out, though, it worked.  So thanks, guys!

---

