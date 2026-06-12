---
title: "Ubuntu Installer Hang"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by Jonapedia on 2011-03-21
Hi all,

I am quite new to Ubuntu. I've tried it once before for a short period of time. Currently, I am installing Ubuntu 10.10 from a LiveCD on an old desktop. It's not ancient, it is able to run Windows XP at the moment. While this may be ridiculous, I do not know how much RAM the computer has, nor do I know much else about system specs. So far, this is what has happened:

1. Booted from CD and selected "Install Ubuntu"
2. Went through the installation process. Allocated 18+ GB of the tiny hard drive (around 45 GB) to Ubuntu. Got stuck at the "Who are you?" section because I had used capital letters in the username. Fixed that and went on to the next step.


Now, I am on the step where the installer window says "Welcome" in the top left hand corner and there is a slideshow onscreen to act as a "guided tour". Here's the problem: The progress bar is about 5/6 filled and apparently, the installer is "Detecting file systems". The progress bar is just frozen there. It isn't moving at all. Also, the computer itself is silent. What I am referring to is the sound of things like the processor or something moving within the desktop tower. On old desktop towers, when the processor is in use for a heavy amount of work, the sound is usually quite audible. The progress bar has been hanging there for a long time and I have no idea whether this is normal. However,assuming that this is not normal and is actually a problem, does anyone have any suggestions for me as to how I can fix this problem. I hope that if there is a solution, it does not have a high risk of wrecking my entire system.

Thanks in advance

---

### Post by Quackers on 2011-03-21
Welcome to UF.
Does moving the mouse create any HDD activity or on screen difference?

---

### Post by Jonapedia on 2011-03-22
Sorry, I wasn't at the computer just now, so I didn't see your reply. What do you mean by screen difference? And...erm...what's HDD? Hard Disk Drive?

In any case, if you mean screen difference as in changes in the look of the screen, the answer is no. Nothing changes unless I move the cursor over the "Detecting file systems" part of the installation window. Then, the mouse cursor changes to a circle with a set of dots going around in a loop. That's it. Does that answer your question?

---

### Post by Quackers on 2011-03-22
What I meant was that on occasions, with some operating system's installer, the screen will freeze and a progress bar will not fill up. Sometimes moving the mouse will "unfreeze" the screen and it will jump to where it has actually got to in the installation. But, in truth, I have not heard of it happening with an Ubuntu installer.
Your problem could indeed be an insufficency of available ram.
Have you tried selecting "try ubuntu" rather than "install ubuntu" from the screen and seeing if the live desktop can load?

---

### Post by Jonapedia on 2011-03-22
Yup, I have tried to load the Live CD desktop before. It works fine. I haven't tested all the applications from the Live CD desktop, but the desktop itself and the file browser certainly seem to work.

---

### Post by Quackers on 2011-03-22
Ok, that's good :-)
It may help if you would boot to the live desktop again and go to System > Admin > gparted and, if that picks up your current partition layout, post a screenshot here please.
Also, are you trying to dual boot Ubuntu with an existing Windows installation?

---

### Post by Jonapedia on 2011-03-22
Yes, I'm trying to dual boot with Windows XP. As for the rebooting process, I'll try it, thanks. From past experience, this is actually the second time the Ubuntu installer has started lagging randomly and freezing up. I had to keep rebooting my computer over and over...

---

### Post by Quackers on 2011-03-22
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Have you also checked the cd for errors? 
At the first purple screen press any key, then choose language then on the next screen choose "check for errors"

---

### Post by Jonapedia on 2011-03-22
I have booted up again. I am re-trying the installation now. If it fails again, I'll try checking for errors. I'm at the step "Allocate drive space". I am currently looking at all the partitions in my computer. I am trying to install to the partition created for Ubuntu previously. However, I keep getting asked to define a root file system. How do I do that? I have already told the installer to use the partition as an ext4 partition. So how do I define a root file system? :confused:

---

### Post by Jonapedia on 2011-03-22
Ok, never mind, I have figured out how to set the root file system. But, I ddon't know what to choose. Here's a list of the possible choices I can make now, according to the installer:

/
/boot
/home
/tmp
/usr
/var
/srv
/opt
/usr/local

I think I should choose either "/" or "/boot". Any suggestions?

---

### Post by Jonapedia on 2011-03-22
Argh...Forget it. Once again, I return now  back to the previous question: how to set root file system? I thought I had figured it out, but I was wrong...help, please, anybody? I have no idea what to do. The installer is still asking me to set the root file system.

---

### Post by rahulkumarc on 2011-03-22
Yes, / is the root filesystem, and /root will be the home folder of the root user(there is a difference, which is why I mention it;).

---

### Post by rahulkumarc on 2011-03-22
You could try this :- 
```
http://hubpages.com/hub/Ubuntu-1004
```


WARNING: Just found it, haven't gone through myself, at one glance looks good to me, similar to ubuntu installs I have done.

---

### Post by Quackers on 2011-03-22
root is the only one that is absolutely necessary ( mount point "/").
A separate home partition can be preferrable (mount point /home) but not necessary, as such. This holds all your personal settings and files, but would default to the root partition if you don't have one.
A swap partition (no mount point) is usually made too.

---

