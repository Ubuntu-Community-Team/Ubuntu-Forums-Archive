---
title: "Won't install in VirtualBox ??"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by gddeluca on 2008-09-12
I've got Ubuntu HH installed as dual boot with my Vista system, but flipping back and forth right now is a pain as I still have so much 'stuff' I need in Vista.  I've got VirtualBox installed already so I thought creating another VM for Ubuntu would be a snap.  That way 'playing' with Ubuntu and experimenting becomes a lot easier than constant re-booting.

However, I can't get the install to run under VirtualBox, either from the physical CD or from the mounted ISO image.

Ubuntu boots from the CD fine.
I Choose the language.
I Choose install.
Popup box telling me the kernel is loading.
Screen goes blank and the VM just sits there.

Using some monitors (TaskInfo) the VM machine is doing absolutely NO I/O, but is looping flat out (using 1 of my quad processors).

I've let it sit there for a long time (1/2 hour) with no change. 

Anyone experienced this?  Any thoughts on how to kick-start it?

George

---

### Post by Oldsoldier2003 on 2008-09-12
try using the alternate installer. I haven't had issues in the past installing Hardy in virtualbox, the latest intrepid Alphas are problematic for me, so I switched to VirtualBox 2.0 and it seemed to solve the problem for intrepid.

---

### Post by gddeluca on 2008-09-12
I did some further searching, and VirtualBox 2.0.2 has just been released (Today!) and contains a specific fix for this Linux boot problem. Only problem, the download is not quite there yet on the Sun site.

Oh well, I can hold my breath for a while.

Update: 
I held my breath.
2.0.2 came available.
I downloaded and installed it.
The problem is still there!
Sigh!

---

### Post by b0bby88 on 2008-09-15
I have the same problem. VirtualBox worked fine and now it just doesn't. I start virtual machine and it's screen remains just black. The interesting thing is that the virtual machine seems to boot and load fine (see the screenshots below).
I've tried to create some other virtual machines, but it didn't work either.
gddeluca, I have figured out, that if I wait for about 2 minutes and then try to close the virtual machine window (when "Close Virtual Machine" dialog appears) I can see some parts of it's "working" screen in grayscale. That's so strange.
I've tried already purging and reinstalling VirtualBox - nothing changes.
Guys, if somebody knows what to do - let us know.
Screenshots:
[IMG]http://img440.imageshack.us/img440/255/vb1pe1.png[/IMG]
[IMG]http://img440.imageshack.us/img440/1638/vb2ka9.png[/IMG]

---

### Post by b0bby88 on 2008-09-15
Hey, I've figured out how to solve this problem.
My problem was because of broken SDL libraries (VirtualBox uses them).
After I've purged libsdl1.2debian package with all of its dependencies, then used "apt-get autoremove" and then installed it again everything works fine.
Tell me if this helps you.

---

### Post by gddeluca on 2008-09-17
Hi,

Well, there's no such thing for me as replacing libraries, my boot failures are occurring with the LiveCD trying to do the install.

I gave up on VirtualBox and went to VMWare, it's doing the trick quite nicely.  Too bad, VirtualBox had some nice features. But I can't sit around waiting for a fix.

Beats me how virtual **MACHINE** software can have this kind of problems with different OS's. Sure I can see problems with the Tools add-ons for different OS's, but with basic system booting?  Shouldn't happen.

George

---

