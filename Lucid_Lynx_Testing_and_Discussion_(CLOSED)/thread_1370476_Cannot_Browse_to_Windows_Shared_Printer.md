---
title: "Cannot Browse to Windows Shared Printer"
date: 2010-01-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2010-01-02
Method:
* Open System -> Administration -> Printing from the gnome panel
* Select New
* Network Printer -> Windows Printer via SAMBA
* Browse
* The workgroup MSHOME is shown. The machine sharing the printer is part of MSHOME
* Trying to Open the MSHOME sub-tree I am greeted with a "Authentication" Dialog box.

When I do the same thing on my Karmic installation it will browse to my printer.

If I put the same path as in Karmic for the printer in the SMB Printer box the printer works.

My question is what to file a bug against.
 
Printer configuration?
Samba? 

Bill

---

### Post by techdude3177 on 2010-01-03
I have the same issue

---

### Post by plun on 2010-01-03
A new Samba version is just uploaded for Lucid

[https://lists.ubuntu.com/archives/lucid-changes/2010-January/002507.html](https://lists.ubuntu.com/archives/lucid-changes/2010-January/002507.html)

If it doesn't work, file a bug against Samba

```
ubuntu-bug samba
```

---

### Post by sparker256 on 2010-01-03
> **plun said:**
> A new Samba version is just uploaded for Lucid

[https://lists.ubuntu.com/archives/lucid-changes/2010-January/002507.html](https://lists.ubuntu.com/archives/lucid-changes/2010-January/002507.html)

If it doesn't work, file a bug against Samba

```
ubuntu-bug samba
```
I did see the new version come in my updates but it did not change the behavior even after a reboot. I will file a bug report against Samba.

Thanks Bill

---

### Post by sparker256 on 2010-01-03
> **techdude3177 said:**
> I have the same issue

I have filed this bug report. Please add yourself as affected.
Are you also using Karmic? If so did you copy the path to get Lucid working?

Thanks Bill

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/502607](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/502607)

---

### Post by ubername on 2010-01-03
Hi

Can you browse through your workgroup in Nautilus (i.e. not using the printer functionality)?

This seems to be a known problem but there is no consensus on which package is the problem.

[http://ubuntuforums.org/showthread.php?t=1341141](http://ubuntuforums.org/showthread.php?t=1341141)

---

### Post by sparker256 on 2010-01-03
> **ubername said:**
> Hi

Can you browse through your workgroup in Nautilus (i.e. not using the printer functionality)?

This seems to be a known problem but there is no consensus on which package is the problem.

[http://ubuntuforums.org/showthread.php?t=1341141](http://ubuntuforums.org/showthread.php?t=1341141)
I also have that problem but not sure where I would put a path like I did to make my printer work.

Bill

---

### Post by ubername on 2010-01-03
if you are using nautilus, on the address bar is an icon which looks like a notepad and pen (to me, anyway!) If you click on that it will change the address bar from a set of buttons to a text field with the path in it. I use this a lot to cut and paste paths to things. you can also type in there.

---

### Post by sparker256 on 2010-01-30
As of yesterday (01-29-10) I can now browse to my Windows XP shared printer.

Bill

---

