---
title: "several errors on upgrade"
date: 2008-07-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wbutchart on 2008-07-31
Hi on my spare ubuntu install i upgraded from 8.04 to 8.10 i use the package manager to do it.

I am getting the following errors when i attempt to start up -
On Batch Kernel 2.6.26-4-generic
[ 0.156009] PCI: Not using MMCONFIG
[ 0.744000] Kernel panic - not syncing: VBS: Unable to mount root fs on unknown - block (0,0)

On Batch Kernel 2.6.24-16-generic
It loads the graphic 3/4 of the way then goes to text. At the bottom it has -
Start-stop-daemon: unable to open pidfile '/var/run/klogd/kmsgpipe.pid for writing.

I dont know if these errors are known or not. Im using a Medion Mim2120 laptop.

---

### Post by thelostsoul on 2008-07-31
Package manager as in "update-manager -d" ?

That's what worked for me...

---

### Post by wbutchart on 2008-07-31
> **thelostsoul said:**
> Package manager as in "update-manager -d" ?

That's what worked for me...
Yup thats what i used.  It downloaded and installed everything via a graphical interface, then reset the computer.  When it tried to restart i got these errors.

---

### Post by thelostsoul on 2008-07-31
Ah okay...thought you were saying you got that while trying to install...

[ 0.744000] Kernel panic - not syncing: VBS: Unable to mount root fs on unknown - block (0,0)

I'm no expert, but that seems to say its having issues mounting you hard drive.  While you wait for a more knowledgeable person to respond than myself, I'd recommend booting to a live disk (or another OS if you have one installed) and running some file system checks or chkdsk in windows...

---

