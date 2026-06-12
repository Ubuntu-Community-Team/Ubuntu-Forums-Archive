---
title: "No Root File Error.  Installed on 2nd Hard Drive"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by danny1010 on 2010-12-23
I have installed ubuntu onto a 64 bit Windows 7 machine using Wubi.

[Note: I thought that I was downloading 10.10, but the installer said it was 10.04]

When Wubi gave be a choice of which drive to install on, I choose my second drive (B) My Windows 7 resides on (C)

The install seemed to take a long time, but I think that was because it was downloading the whole operating system install files.

When it was finished downloading it asked me if I wanted to reboot, I selected yes (reboot).  Then the boot screen gave me the choice: Windows or Ubuntu.  I choose Ubuntu and then I get the error:

"No root File system is defined.  Please correct this from the partitioning menu. "

Damn that Ubuntu splash screen was so beautiful and I thought I was home free.

I have read a few threads here and other places on line.  I have read that I may have to partition the drive.  

Was my mistake in choosing the B: instead of the C: drive?

If I partition can I partition from inside windows using the computer management software it provides?

Do I need to partition at all?  Or can I just move the installed files to the C:  Are the files movable?

In the ubuntu directory I see a file: uninstall-wubi.exe.  Should I use this and try a reinstall onto the C:

I hope these questions allow you to understand my current level of understanding.

---

### Post by Rubi1200 on 2010-12-23
Hi and welcome to the forums :)

We need to get a better overview of the current state of your setup.

To that end, please boot the computer with a LiveCD, choosing to try not install Ubuntu.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

Thanks.

---

### Post by danny1010 on 2010-12-23
Hi,

I would happily boot my computer with a LiveCD.  Unfortunetly, I do not know what a LiveCD is.  I will search to find out what the LiveCD is and attempt to follow your instruction.

Danny

---

### Post by danny1010 on 2010-12-23
When I installed ubuntu, the following file was placed in a directory.

ubuntu-10.04.1-desktop-amd64.iso


Can I use this to create a LiveCD?

---

### Post by dino99 on 2010-12-23
i'm not a fan of wubi, so for a serious experience:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

more info below

---

### Post by danny1010 on 2010-12-23
Dino,

If you read my questions in my original post you may have realized my current level understanding precludes me from a "serious experience" - at the moment. 

Dan

---

### Post by Rubi1200 on 2010-12-23
I assume you can boot Windows normally?

Here are instructions on how to download and create/use a LiveCD:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Scroll down the page for instructions on how to burn the image etc.

Make sure to try not install when you get things up and running.

Let me know if this is clear or if there is any other help you need.

We really need to see the results of the script to know what the current state of your setup looks like.

Thanks.

---

### Post by danny1010 on 2010-12-23
Thank Rubi,

When I installed ubuntu, the following file was placed in a directory.
ubuntu-10.04.1-desktop-amd64.iso
Can I use this to create a LiveCD?

Regarding your question.  I have no problems booting into windows.

You asked if your instructions were clear.  They seem fine, but on the page you directed me to, it says nothing about creating a LiveCD.

Can I also create a USB drive boot thing.  Would that be a LiveUSB?

Thanks for all your help.  Please tell me if I can use ubuntu-10.04.1-desktop-amd64.iso

---

### Post by danny1010 on 2010-12-23
I am going ahead with creating a LiveUSB stick instead of a LiveCD
using: ubuntu-10.04.1-desktop-amd64.iso from the original install.  Send me a message if I'm going down the Dark Path.

Danny

---

### Post by Rubi1200 on 2010-12-23
The instructions on the page showed how to burn the image to CD = means making a LiveCD.

LiveUSB is also good.

Your idea sounds fine as long as you are sure the image is not corrupted in any way.

---

### Post by danny1010 on 2010-12-23
Hey,

I have successfully used the LiveUSB to boot into the Ubuntu desktop.   Cool. Does this mean that Ubuntu is compatible with my system then?

It looks good and I like a lot of the functionality.  

The drivers for the wireless and the drivers for audio were not working.  I am back inside Windows.

I understand that there are patent restrictions for the use of drivers, but I think I can do it manually.  Correct?

Dan

---

### Post by Rubi1200 on 2010-12-23
Good news then!

I thought you wanted to fix your Wubi install?

We still need to see the results of the boot info script I mentioned previously.

Also, post the _full_ specifications for the computer so we can better answer the question about wireless and audio drivers.

---

### Post by danny1010 on 2010-12-23
Hi,

I have no pragmatic need to run Ubuntu now.  It is merely that I feel philosophically drawn to open systems right now.  For starters I have started using Open Office even though I have purchased Microsoft Office.  As a next step, I want to enter the alternative OS system.  Ubuntu was attractive because they began using it at the office.

I will run the script soon and send the results. 

Dan

---

