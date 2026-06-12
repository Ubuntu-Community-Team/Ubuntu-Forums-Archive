---
title: "Ubuntu won't install"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by NZKevin on 2010-08-22
Hi, thought I'd give Ubuntu a try so I downloaded the file and created a CD. Put it in my laptop, re-booted and it all started OK. I got an "Ubuntu" logo on the screen with a series of five dots changing from red to white and back under it. Then the dcreen flickers, and goes black. Then.....nothing!
 
The computer is a Fujitsu C series Lifebook, which was running windows XP -in fact it still is, as Ubuntu refuses to load!
 
Any suggestions?
 
Thanks
Kevin

---

### Post by bcbc on 2010-08-22
> **NZKevin said:**
> Hi, thought I'd give Ubuntu a try so I downloaded the file and created a CD. Put it in my laptop, re-booted and it all started OK. I got an "Ubuntu" logo on the screen with a series of five dots changing from red to white and back under it. Then the dcreen flickers, and goes black. Then.....nothing!
 
The computer is a Fujitsu C series Lifebook, which was running windows XP -in fact it still is, as Ubuntu refuses to load!
 
Any suggestions?
 
Thanks
Kevin

10.04 has some issues with certain graphics cards. Which one do you have? Check this link [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by NZKevin on 2010-08-22
That could be the problem, but the workaround instructions are meaningless to me.  Which screen is the "installation screen", pressing F6 at any time doesn't get me to anywhere I can enter anything.  What I get on screen never looks anything like any of the instructions

---

### Post by bcbc on 2010-08-22
> **NZKevin said:**
> That could be the problem, but the workaround instructions are meaningless to me.  Which screen is the "installation screen", pressing F6 at any time doesn't get me to anywhere I can enter anything.  What I get on screen never looks anything like any of the instructions

Put the CD in, boot from it. When you see a little keyboard icon on the bottom press any key. Then it will ask you for your language and take you to the main menu (with some additional options). At the bottom you'll see F6. Press it - and there are a few boot options or you can supply your own custom options.

---

### Post by NZKevin on 2010-08-24
Aaaaaarghhh!!!! This is like pulling teeth, I'd have stuck with windows if I wanted trouble like this.
 
I have installed Ubuntu, but cannot run it.  I have to type in the i915.modeset=1 to make the graphics work.  I can do this when booting from CD, but it won't let me edit the GRUB file on the hard drive when I've booted from CD.  I can't boot from the hard drive, as the graphics won't work until I've added the line to the GRUB file, that I can't get to without booting from the hard drive.  Is there some way to stop the boot process and add the line I need to the startup, or is there some way to edit the GRUB file when booted from CD?

---

### Post by bcbc on 2010-08-24
> **NZKevin said:**
> Aaaaaarghhh!!!! This is like pulling teeth, I'd have stuck with windows if I wanted trouble like this.
 
I have installed Ubuntu, but cannot run it.  I have to type in the i915.modeset=1 to make the graphics work.  I can do this when booting from CD, but it won't let me edit the GRUB file on the hard drive when I've booted from CD.  I can't boot from the hard drive, as the graphics won't work until I've added the line to the GRUB file, that I can't get to without booting from the hard drive.  Is there some way to stop the boot process and add the line I need to the startup, or is there some way to edit the GRUB file when booted from CD?

If you see the grub menu when booting from the hard drive, then hit 'e' on the first entry (instead of enter). Then use the arrow keys to navigate to where it says 'quiet splash' and add your i915 workaround there e.g. quiet splash i915.modeset=1
After that hit CTRL+X to boot the modified entry.

If you don't see a grub menu, then hold down the SHIFT key while booting and it should show.

Once in ubuntu, go to a command prompt and run:
```
gksudo gedit /etc/default/grub
```
Change the line 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
```

Then run:
```
sudo update-grub
```

After that you don't need to supply the workaround. (You will still need it when booting a live CD)

If you're trying to edit files when booting from the live CD, you need to use sudo or gksudo (for running gui programs as root) to elevate your privileges (even though there is no password required when in live CD). If you are booting your normal install, you supply your own password.

Yes, it may be like pulling teeth - I won't disagree.

---

