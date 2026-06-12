---
title: "How can I copy file from ubuntu to winodws 7 installed on virtualBox ?"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-06-03
I have a host ubuntu 11.04 with guest window 7, I have installed ubuntu OSE then install windows 7.
Now I want to copy some files to windows 7 running on OSE on windows 7.
How do I do this ?

---

### Post by Davaross on 2011-06-03
Just configure a network between the two in the same way you would 
if you were physically networking an ubuntu box to a windows box.

Hope this helps,
Davaross

---

### Post by SeijiSensei on 2011-06-03
Use [Shared Folders](http://forums.virtualbox.org/viewtopic.php?t=15868).

---

### Post by YesWeCan on 2011-06-03
> **SeijiSensei said:**
> Use [Shared Folders](http://forums.virtualbox.org/viewtopic.php?t=15868).
That's for Ubuntu guest on Windows host, which is much trickier.

For Windows guest, you just create a share folder either in the VB manager window before you boot Windows or using the share icon (bottom right) when running Windows. The folder automatically appears in the networking section somewhere. Can't recall the exact path but you'll find it.
[http://www.virtualbox.org/wiki/Downloads#manual](http://www.virtualbox.org/wiki/Downloads#manual)

---

### Post by slooksterpsv on 2011-06-03
[http://ubuntuforums.org/showthread.php?t=1668920](http://ubuntuforums.org/showthread.php?t=1668920)

[Quote=http://ubuntuforums.org/showthread.php?t=1668920]
HOW DO I ACCESS SHARED FOLDERS?
NOTE: You can now have Shared Folders automatically mount/try to mount on the OS. To do this, when you create the Share via Devices -> Shared Folder, there's an option called Auto-mount - try this option if you're having trouble mounting shared folders.

Depending on the OS, you would do the following:
Windows, navigate to: \\VBOXSVR
Linux, mount it via (after installing Guest Edition), in terminal:

sudo mount -t vboxsf SHARENAME /path/to/mount/to

Where SHARENAME is the name of the share (you typed it in when setting up the in VirtualBox via Devices -> Shared Folder)
And /path/to/mount/to - is the location where you want to mount it to. E.g. you could make directories under /media to have it mount to.
[/quote]

I gotta say I never realized how bad the fonts look in Windows compared to how they look on Ubuntu. My eyes were stunned at the ugliness when I clicked on my thread about VBox 4.0

---

### Post by SeijiSensei on 2011-06-03
> **YesWeCan said:**
> That's for Ubuntu guest on Windows host, which is much trickier.

Sorry.  I thought it was a generic HOWTO, not specific to Linux hosts.

I've used shared folders with my Windows guest on an Ubuntu host.  I don't recall doing more than designating the directory to be shared in the machine's definition.  Of course, you also need the Guest Extensions installed.

---

