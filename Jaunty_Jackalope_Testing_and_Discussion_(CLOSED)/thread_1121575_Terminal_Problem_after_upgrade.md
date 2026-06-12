---
title: "Terminal Problem after upgrade"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by awam66 on 2009-04-10
Hi,
Yesterday I upgraded to Jaunty beta from intrepid on my Dell C521 with amd athlon 64bit. Since then I cannot open a terminal as I get "There was an error creating the child process for this terminal" and the terminal opens with a blank window. I have searched the forums for similar and found a few but none offer a solution. Now the odd thing is I have a second installation of jaunty on an external USB drive and there is no problem on that.
Also if I try to open a root terminal from "Applications>System Tools>Root Terminal" the hourglass thingy runs for about twenty seconds and then nothing happens.
Any ideas please

---

### Post by ronacc on 2009-04-10
try opening synaptic and see if there are any broken packages , also try reinstalling gnome-terminal .

---

### Post by awam66 on 2009-04-10
> **ronacc said:**
> try opening synaptic and see if there are any broken packages , also try reinstalling gnome-terminal .

Done all of these things and no joy.

Tried reinstalling gnome-terminal again but synaptic returns "error failed to fork pty".

---

### Post by llamakc on 2009-04-10
Will xterm run? If it isn't installed, do so through Synaptic and then try using xterm.

---

### Post by awam66 on 2009-04-10
Xterm wont run either although it is installed. I cannot install anything either as synaptic returns "error failed to fork pty"

I think I'll do a clean install

---

### Post by Aenima99x on 2009-04-10
Had the same problem, here's how to fix it -

ALT+F2 to bring up the run dialog
type in gksudo gedit /etc/fstab
add in the following ath the bottom of the file
devpts    /dev/pts    devpts   (rw,noexec,nosuid,gid=5,mode=620)
ALT+F2 and type in sudo mount -a
see if terminal now works, if not, reboot and then it should work

---

### Post by awam66 on 2009-04-10
> **Aenima99x said:**
> Had the same problem, here's how to fix it -

ALT+F2 to bring up the run dialog
type in gksudo gedit /etc/fstab
add in the following ath the bottom of the file
devpts    /dev/pts    devpts   (rw,noexec,nosuid,gid=5,mode=620)
ALT+F2 and type in sudo mount -a
see if terminal now works, if not, reboot and then it should work

Thanks for that. I am in the middle of a clean install to see what happens. I will bear your suggestion in mind if the problem recurs.

---

### Post by barkerben on 2009-04-10
Hello - I had this problem, and can confirm that, for me at least, the proposed fix worked fine. Thanks :-)

---

### Post by awam66 on 2009-04-10
OK.
I did a clean install and all works OK.
There is still nothing like your fix in fstab but should the problem reocurr I will try the fix above.
many thanks.

---

### Post by Aenima99x on 2009-04-10
> **awam66 said:**
> OK.
I did a clean install and all works OK.
There is still nothing like your fix in fstab but should the problem reocurr I will try the fix above.
many thanks.

Yeah, it normally shouldn't need to be in the fstab. It can also be fixed by making sure that there is a symlink for S11mountdevsubfs.sh in /etc/rcS.d

---

### Post by gacb on 2009-04-15
I just upgraded my main partition from Intrepid to Jaunty and had the same problem. The fix worked fine for me without the need to reboot.

I have been running Jaunty on the smaller partition since Alpha 2 and didn't have a similar problem. Go figure.

---

