---
title: "No DVD burner with kernel 2.6.31.2-generic"
date: 2009-07-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chrismine on 2009-07-08
Since installing the new kernel my LG SATA DVD Writer is not detected properly anymore. I have tried Brasero, Gnomebaker and K3b.

Gnomebaker does detect the DVD writer but it is not burning. The other two programs does not detect it.
Can somebody please confirm?

---

### Post by budluva04 on 2009-07-08
i burnt the A2 cd with my writer on 2.6.31-2 yesterday....

---

### Post by Hobbes on 2009-07-08
Confirmed.  Actually since the last 2.6.31.2 update and a reboot I can now "see" a blank dvd on my desktop, but if I try to burn an .iso to disk using brasero, etc. it still is undetected.  I'll go see if a launchpad bug has been filed yet.

peace.

---

### Post by Craigy90 on 2009-07-08
I have a MATSHITA DVD-RAM UJ-850S ATA, and Ubuntu doesn't recognize it at all now. Not sure if this is the same problem, I might have to submit a different bug report.

---

### Post by Hobbes on 2009-07-08
I couldn't quite find a bug that seemed to relate to a regression in Brasero lately... others had problems but most were during jaunty or intrepid or earlier. But my knowledge and experience with bug reporting / searching is minimal.

Mine is also a LG-writer, possibly SATA (I forget but could check to confirm, hehe).

---

### Post by Craigy90 on 2009-07-08
Strange, after a reboot the drive is now recognized.

If I put in an Ubuntu Live-CD it comes up normally. However, when I press the physical eject button on the drive nothing happens. Also, when I right click eject a window pops up asking for a password and saying "Authentication is required to unmount devices mounted by another user" then an error message comes up saying "Unable to eject [CD Name] DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

When I put a music CD in, however, it tries to read it for a while, then the entire drive disappears. It can be ejected after logging out and back in.

What should I file a bug against?

Sorry to hijack the thread, but I'm thinking that maybe you have a permission error like it appears that I do?

---

### Post by Reiger on 2009-07-08
If the CD/DVD is mounted you should not be able to eject it. First make sure that it is unmounted, then try to eject it.

If you can't get that to work you may also want to try the eject command from the terminal.

---

### Post by Craigy90 on 2009-07-08
> **Reiger said:**
> If the CD/DVD is mounted you should not be able to eject it.I guess that makes sense, although I don't remember ever having this problem before.> **Reiger said:**
>  First make sure that it is unmounted, then try to eject it.OK, so I unmount the drive, (which requires a password). But then if I try to press the eject button on the CD drive, nothing happens. If I right click on the drive and eject it there, it works (no password required).

> **Reiger said:**
> If you can't get that to work you may also want to try the eject command from the terminal.When I run the eject command as a normal user, the CD is unmounted, but not ejected. I get the following error.
```
eject /media/cdrom1
eject: unable to eject, last error: Inappropriate ioctl for device

``` When I run it as sudo, it is unmounted and then ejected.

So that leaves me confused about a few things:

- Why do I need to type a password in order to unmount using the GUI, but when I run the eject command as a user, the CD is unmounted?
- If the GUI can eject the disk without needing elevation, why does the eject command need it?

I mean, if permission is an issue here, I can see a way to unmount and eject it without being root. But that could just be my stupidity. :confused:

Also, none of this solves the problem of the music CD causing the drive to disappear.

Thanks for your help, but now I'm more confused than I was at first. :lolflag:

---

### Post by caryb on 2009-07-10
When I fire up K3B it fires up the setup & wants to add me to the burning group but the fails when it discovers there is no burning group?


Cary

---

### Post by eldragon on 2009-07-11
does this have something to do with it? [http://patchwork.kernel.org/patch/34735/](http://patchwork.kernel.org/patch/34735/)

good luck...i havent tested it myself

---

### Post by caryb on 2009-07-11
I just updated & had a kernel update for 2.6.31-2 but the fix isn't in there yet:-( 

From the previous post (eldragon) the the kernel patch site the perpetrator got a written smack!


Cary

---

### Post by crimsun on 2009-07-11
The fix was merged on July 10th. It will appear in the July 11th crack-of-the-day builds ([http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/)).

---

### Post by chrismine on 2009-07-15
Since updating to kernel 2.6.31-3 K3b and Gnomebaker can see the burner - Gnomebaker gives errors and K3b burns but does not verify correctly. Brasero still does not see the burner.

I see there is a new update for the kernel - downloading now...

---

### Post by chrismine on 2009-07-27
Running kernel 2.6.31.4 - Brasero still cannot detect the DVD burner - I have made a sucessful CD with Gnomebaker. With k3b it seems the burn is successful but it gives a verification error.

---

### Post by amano on 2009-07-27
Did you file a bug so that a developer can look into it?

---

### Post by chrismine on 2009-07-27
No I did not yet because the problem is basically solved with the new kernel - I have a burn facility now albeit not with the default Ubuntu program.

I have thought about marking this thread as solved because the burner is now being "seen"

Shall I file a bug against Brasero?

---

### Post by amano on 2009-07-27
Hmm. I would file the bug against the kernel. 2 of 3 programs still don't work properly. The kernel team might re-assign it, if they think that the problem originates in userspace.

---

### Post by nhasian on 2009-07-27
I didnt see any bugs about this on launchpad so i filed one myself:

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544)

I think its more of a linux kernel problem than a brasero problem, but i didnt know what package to file it against.  maybe someone can correct it for me when they confirm it...

---

### Post by martinpm24 on 2009-07-27
i have the same problem

---

### Post by caryb on 2009-07-27
This has been fixed with the 2.6.31-3 & 4 kernel releases just do a ```
sudo apt-get dist-upgrade
``` to get the newer kernels.


Cary

---

### Post by nhasian on 2009-07-27
i just upgraded from Linux Kernel 2.6.31-4.22 to 2.6.31-4.23 and I'm still not able to burn any discs.

> **caryb said:**
> This has been fixed with the 2.6.31-3 & 4 kernel releases 

---

### Post by chrismine on 2009-07-28
I confirmed - thanks for filing.

---

### Post by jppr on 2009-07-28
> **nhasian said:**
> i just upgraded from Linux Kernel 2.6.31-4.22 to 2.6.31-4.23 and I'm still not able to burn any discs.

same here

---

### Post by caryb on 2009-07-28
I Could in -1 not in -2 & -3 but can do it again in -4 ???


Cary

---

### Post by chrismine on 2009-07-28
> **caryb said:**
> I Could in -1 not in -2 & -3 but can do it again in -4 ???


Cary
Is this on the laptop in your sig? Maybe not a SATA burner?

---

### Post by jppr on 2009-07-28
[https://launchpad.net/ubuntu/karmic/+source/brasero/2.27.5-0ubuntu1](https://launchpad.net/ubuntu/karmic/+source/brasero/2.27.5-0ubuntu1)

---

### Post by nhasian on 2009-07-28
i upgraded to the new brasero 2.27.5-0ubuntu1 today but it did not resolve the problem. Brasero still does not detect any media in the drive, even though it says Blank DVD Disc on the desktop.

---

### Post by taavikko on 2009-07-29
> **nhasian said:**
> i upgraded to the new brasero 2.27.5-0ubuntu1 today but it did not resolve the problem. Brasero still does not detect any media in the drive, even though it says Blank DVD Disc on the desktop.

[https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/405924](https://bugs.edge.launchpad.net/ubuntu/+source/brasero/+bug/405924)

---

### Post by nhasian on 2009-08-03
yay looks like we've made some progress:

[http://bugzilla.gnome.org/show_bug.cgi?id=590385](http://bugzilla.gnome.org/show_bug.cgi?id=590385)

---

### Post by chrismine on 2009-08-04
After today's updates for Brasero and the new 26.31-5 kernel the issue still persist.

---

### Post by amano on 2009-08-04
If I understood right, the bug fix will appear with the .90 Update for Brasero. If you can compile Brasero yourself, you are welcome to test a current snapshot.

---

### Post by Vaun on 2009-08-04
Confirming.  This is fixed in git master.  I recompiled and cd/dvd's are recognized again.

---

