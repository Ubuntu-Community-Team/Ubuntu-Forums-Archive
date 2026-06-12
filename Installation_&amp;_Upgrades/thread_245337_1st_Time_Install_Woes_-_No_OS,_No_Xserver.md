---
title: "1st Time Install Woes - No OS, No Xserver"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by oatmeal_stout on 2006-08-27
I've been wrestling with trying to install this OS for some time. I have the latest CD (6.06.1), and while I can use the LiveCD portion, I can't install the OS permanently on my machine. 

I'm receiving the "Failed to start the Xserver" error message. The Corrective Action described in the Sticky Thread (The Latest Updates Break the Xserver!) seems to be aimed at an already installed OS. The machine in question has no OS, and therefore no (known) username and password.

How do I install Ubuntu on this machine in the first place?
Any help out there would be greatly appreciated.

Thanks!

---

### Post by adds2one on 2006-08-27
At what point in the installation are you getting this message?

---

### Post by oatmeal_stout on 2006-08-27
After I boot from the CD, choose Install Ubuntu, and the install files are copied.

---

### Post by MunchyBugs on 2006-08-27
I have similar problems.

On my laptop it would not install of a burned CD-ROM so I had to use a DVD-ROM.  On my other desktop  it would not install off of a DVD-ROM...it kept hanging while coping files.  I had to use the CD-ROM disc to get it to install on there....wierd.

---

### Post by MiThRaZoR on 2006-08-27
> **oatmeal_stout said:**
> I've been wrestling with trying to install this OS for some time. I have the latest CD (6.06.1), and while I can use the LiveCD portion, I can't install the OS permanently on my machine. 

I'm receiving the "Failed to start the Xserver" error message. The Corrective Action described in the Sticky Thread (The Latest Updates Break the Xserver!) seems to be aimed at an already installed OS. The machine in question has no OS, and therefore no (known) username and password.

How do I install Ubuntu on this machine in the first place?
Any help out there would be greatly appreciated.

Thanks!

I'm getting kinda the same problem. I want to know how to install it.

Here's the whole thing.

> Failed to start Xserver (your graphical inter). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
I choose yes it shows something like this:
> X Window System: Versions 7.0.0
Release date: 21 December 2005
X Protocol: Versions 11, Revision 0, Release 7...
...
....
Using config: /etc/x11/xorg.conf
Then it says,
> Would you like to view detailed X server output as well?
I choose yes and then it shows the same thing from before.
> X Window System: Versions 7.0.0
Release date: 21 December 2005
X Protocol: Versions 11, Revision 0, Release 7...
...
....
Using config: /etc/x11/xorg.conf
Then it says
> X Server is now disabled. Restart GDM when it is configured correctly.

Now what I'm thinking is that this has to do with my nVidia graphics card. If I switch to my Integrated Intel, would that work? Then I could use the sticky and upgrade it and then switch back to my nVidia.

Can I do that?

Any help is appreciated.

---

