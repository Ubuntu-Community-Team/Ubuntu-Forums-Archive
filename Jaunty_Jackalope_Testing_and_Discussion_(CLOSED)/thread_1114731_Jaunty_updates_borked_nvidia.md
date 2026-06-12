---
title: "Jaunty updates borked nvidia"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by robfish on 2009-04-03
I was happily using Jaunty Beta (Kubuntu) until tonight with the latest updates KDE would not start.
I think there was a kernel update.

Eventually I realised that the Nvidia driver was not loading so I edited xorg.conf as follows:-
Section "Device"
        Identifier      "Configured Video Device"
#       Driver  "nvidia"
        Driver  "nv"

and now KDE works.

How do I get nvidia working again?

---

### Post by Sef on 2009-04-03
Moved to Jaunty.

---

### Post by forumache on 2009-04-03
> **robfish said:**
> 
How do I get nvidia working again?

restart system.
log on
change xorg.conf back to nvidia
log off

gdm will restart, using nvidia (hopefully)

---

### Post by robfish on 2009-04-03
> **forumache said:**
> restart system.
log on
change xorg.conf back to nvidia
log off
gdm will restart, using nvidia (hopefully)

No, KDE will only start with "nv" (not "nvidia")

Am I the only one with this problem?
Should I try manually loading a downloaded nvidia driver?
I have tried to stick to the Kubuntu tools (System > Hardware Drivers)

---

### Post by 4ebees on 2009-04-04
> **robfish said:**
> No, KDE will only start with "nv" (not "nvidia")

Am I the only one with this problem?
Should I try manually loading a downloaded nvidia driver?
I have tried to stick to the Kubuntu tools (System > Hardware Drivers)

Hi there,

If you're going to manually install the nVidia drivers the make sure you run:

> uname -a 

to find out which kernel you're using.

Then run: 

> apt-cache search kernel-source


to identify which package you need and then:

> sudo apt-get install linux-source


Otherwise the nVidia installer won't be able to create a kernel module.

---

### Post by robfish on 2009-04-04
I have found the problem on my machine.

The update included a kernel update but Grub was not updated correctly.
There was no Grub entry for the new kernel.
Fixed that and now nvidia drivers are working again.

---

### Post by forumache on 2009-04-04
@robfish, glad to hear that it's working again.

usually this kind of problems are due to the fact that the actual kernel (which was booted) has no nvidia module.

In your case, the nvidia module was compiled for the new kernel (updated), but you were using the old one (since grub was not updated). Or something like that :)

---

### Post by 4ebees on 2009-04-04
> **robfish said:**
> I have found the problem on my machine.

The update included a kernel update but Grub was not updated correctly.
There was no Grub entry for the new kernel.
Fixed that and now nvidia drivers are working again.

How exactly did you update Grub?

---

### Post by robfish on 2009-04-04
> **4ebees said:**
> How exactly did you update Grub?

sudo nano -w /boot/grub/menu.lst

First check which kernel is being used
uname -r
then check that the newer kernel is installed
(files should be in /boot/)
then edit menu.lst

---

