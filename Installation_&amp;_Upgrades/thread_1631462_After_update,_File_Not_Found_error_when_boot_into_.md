---
title: "After update, File Not Found error when boot into Ubuntu, Windows boots fine"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by emeraldinspirations on 2010-11-26
I have Ubuntu 10.10 installed on my Acer Aspire One using wubi.

Today there were new updates (I check every day) that required a re-boot.

After re-booting, my computer passed the boot.ini and hung when GRUB is supposed to run.

I powered down the computer, and tried to boot again, passed the boot.ini and got a 'File Not Found' instead of the GRUB interface.

I am not able to run the Live Disk on my computer because it does not support booting from flash media and does not have an optical drive.

If I understand what wubi does correctly, the entire contents of my Ubuntu 'hard-drive' are in a single root.disk file.  So I am not sure how to go about proceeding.

Since GRUB seems to be where the error is occurring, I went to the C:\ubuntu\disks\boot\grub folder and it is empty.

Until this update everything worked great.  What can I do to fix this?

---

### Post by Hippytaff on 2010-11-26
Unfortunately the updates (especially grub ones) break Wubi...try here for some help
[https://wiki.ubuntu.com/WubiGuide#Troubleshooting](https://wiki.ubuntu.com/WubiGuide#Troubleshooting)

if you need further assistance post back

BTW If you intend to use ubuntu long term it is much better to do a 'real' install, ie dual boot with windows :-)

---

### Post by emeraldinspirations on 2010-11-27
Thank you,

I stumbled upon the same page while trying to fix the problem.

What I ended up doing was:  
[LIST]
[*]I booted into Windows
[*]I then copied the C:\ubuntu directory to a different location (C:\Copy of ubuntu), which took all night.
[*]I then tried to re-install Wubi hoping it might repair the issue
[*]Wubi required an un-install and purged the original C:\ubuntu folder
[*]I completed the Wubi installation and booted into the new Ubuntu installation
[*]I then booted back into Windows
[*]I renamed the new root.disk and swap.disk inside the new C:\ubuntu\disks to a different extension
[*]I then moved the root.disk and swap.disk from copied location (C:\Copy of ubuntu\disks) to the new installation (C:\ubuntu\disks)
[*]I then booted back into ubuntu just fine
[/LIST]

Is there a way to see if I am using the correct version?  I think I am because Wubi said it installed 10.04 and the command line shows 10.10:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

```

The problem is I can't tell for sure if the update is included.

---

### Post by Hippytaff on 2010-11-27
looks like your using 10.10 - there are a few cosmetic differences that might confirm this one being synaptic package manager now has a pay bit for software you can buy :-) but lsb_release -a is normally right :-)

Good work btw - impressive stuff :-)

Edit -> Forgot to say to remember to mark the thread as solved in the thread tools at the top of the page so that others who come across the same issue can see how you overcame it :-D

---

### Post by emeraldinspirations on 2010-11-27
Yah, I am not sure how to articulate my question.  Too new to linux to know all the correct verbage.

Essentially my question was, the update was like 10.10.26 or something.  I had upgraded to 10.10 a long time ago.  I know I am using at least 10.10 but I don't know if I am using the update that caused the problems in the first place, or some older update.

Also, I would do a full duel boot of Ubuntu if I could.  Unfortunately my computer will not support booting from flash media, and being a netbook does not have an optical drive.

If only I could boot from flash media, my 'baby' would be perfect.

---

### Post by emeraldinspirations on 2010-11-27
> **Hippytaff said:**
> Edit -> Forgot to say to remember to mark the thread as solved in the thread tools at the top of the page so that others who come across the same issue can see how you overcame it :-D

Thank you, I forgot.

---

### Post by Hippytaff on 2010-11-27
If you can't install the usual way (ie cd or usb) you can try a net install [https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)
:-)

---

### Post by emeraldinspirations on 2010-11-27
Thanks.  Will have to try that when I am not so close to the release of my current project.

---

