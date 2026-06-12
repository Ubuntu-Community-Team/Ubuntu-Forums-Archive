---
title: "dual boot installation on HP pavilion dv7."
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by InQontroll on 2012-11-15
Sorry, i think i posted my first thread in the wrong section.

here it is:
[http://ubuntuforums.org/showthread.php?t=2083750](http://ubuntuforums.org/showthread.php?t=2083750)

I'm having problems installing ubuntu.
I found a few selutions but i do not know how to use them.
Read all posts in the threads as i posted more info each post.

Also i need someone new to help me on this matter because the previous person gave up. Still gratitute to him for trying to help.

Greetings InQontroll.

---

### Post by darkod on 2012-11-15
I don't use wubi, so I can't help with that. And I don't recommend it either.

If you decided to install, do it properly on its own partition, not as virtual inside windows.

You might need to play around with the graphics driver regardless how you install, but I don't think it's impossible because the AMD APUs are out for a long time and there would be more threads of people complaining if it was impossible to make it run.

---

### Post by Mr_JMM on 2012-11-15
Whilst your first thread could have served better in this forum, I think you should stick to that thread. The mods will move it if they feel it's better served in this forum. Cross posting is never a welcome thing.

Again, your first thread seems to be progressing if you stick with it.

[edit] OK then, my bad. I'll go back to my hole now.

---

### Post by darkod on 2012-11-15
Also, you have 4 primary partitions already on the machine so you will have to delete one and maybe shrink another one to make space for ubuntu and to be able to create the ubuntu partitions.

On machines with 4 primary partitions and msdos table (like in your case), you can't make any more partitions which makes installing ubuntu impossible.

---

### Post by Mark Phelps on 2012-11-16
If you're serious about intalling Ubuntu in dual-boot mode with Win7 and retaining the use of Win7, then read through the details below ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by InQontroll on 2012-11-16
So i installed using live usb this time.
Made it have its own partitions so thats no problem either.

Now the same thing happons over and over.
But this time i am able to start up linux anytime only whitout the graphics.
So now all i need is the graphics to work. and save.

---

### Post by darkod on 2012-11-16
It would help if you also posted the graphics card you have?

---

### Post by InQontroll on 2012-11-16
> **darkod said:**
> It would help if you also posted the graphics card you have?

did that in the other post but here:
radeon dual graphics card.

---

### Post by darkod on 2012-11-16
Get the exact model, if you don't know it you can list all PCI devices with:
lspci

Then google around for installing your model drivers on ubuntu. It might be as simple as getting the driver file from AMD website (they have ATI linux drivers) and run it in terminal.

Since the GUI doesn't work good, if I'm not mistaken when you are at the login screen you can open a terminal screen with Ctrl + Alt + F1 (or Ctrl + Shift + F1).

That will allow you to install the driver, if that's what you need.

What you can also try is trying to boot with some parameter added to the boot lines. When at the grub2 boot menu, highlight the ubuntu entry and press 'e' for edit. That will show the boot lines.
Using the arrows keys move the cursor towards the end of the line starting with linux, and after the 'quiet splash' add:
radeon.modeset=1
Press F10 or Ctrl + X to boot.

See if that can boot the GUI better. If not, try also with radeon.modeset=0.
Note, this is only a temporary edit, the next time you reboot it's gone, so don't be surprised.

If you manage to boot once with a good GUI, open Additional Drivers and see if it offers a video driver to activate. If it does, often that can solve the issue.

Let us know how it went.

---

### Post by InQontroll on 2012-11-16
I got it working,
Thanks for replying but i was to late to see it.

Everything works even my graphics all of them.
Now i have one more problem to resolve.

I get an error message at top right

[IMG]http://img716.imageshack.us/img716/5737/screenshotfrom201211161.png[/IMG]

---

### Post by darkod on 2012-11-16
I can't help with that error, sorry. It's out of my league.

Glad you got it working. :)

---

### Post by InQontroll on 2012-11-17
Ok now i thought it worked the whole time my ubuntu was in graphics fail save mode.
Can't turn that of and can't install card drivers...

I'm gonna remove ubuntu and give up.
Its not worth it ******* up my comp for a stuped OS which does not even support all graphics cards.

---

