---
title: "Installation issues"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by deafdigit on 2012-04-13
Hi everybody


A month ago I bought a new desktop computer and shortly after, I learned about Ubuntu. Since I do a lot of web application development and general webdesign, it is my impression that Ubuntu will make life a lot easier than Windows, so I tried to install it yesterday. In fact, I tried to install three different versions. All installs failed.

**11.10**
Downloaded the image and burned it (yes, properly - installation with this same disc worked just fine on my 5-year old labtop). Booted from the CD (which in this case was actually a data-dvd cause that's all I had lying around). I got to the pretty orange-ish colored splash screen with the two logos in the bottom, then the screen turned black with some white text running down over it and I got this error:
[http://ubuntuforums.org/showthread.php?t=1946528]("http://ubuntuforums.org/showthread.php?t=1946528")
(See the thumbnail in that post).

Then I tried installing via Wubi inside windows. Everything worked fine untill I was asked to reboot my system. Then I got the exact same thing as above.

I've looked through the above thread, but I haven't been able to solve the problem.

By the way, at this error I'm forced to press Ctrl-Alt-Del, which outputs something like "Stopping all md devices" and reboots the computer.


**12.04**
On some other forum, someone said they had the same problem, and the solution was installing 12.04 LTS instead, so I downloaded it (beta 2), burned it, used wubi, installed inside Windows and rebooted. This time it got to "Completing Ubuntu installation..." and then nothing further happens.


**Further randomness**
Then I remembered - oh wait, I'm running 64bit windows (by the way does that mean I have a 64-bit processor? - yeah, I'm not really into herdware lol), so I downloaded the 64bit 12.04 LTS hoping it'd make the difference. Same procedure as with the regular 12.04 and same error.


What do I do? I just want to work in Ubuntu like I understand the pros do...


Any help would be appreciated.

//Deafdigit

---

### Post by darkod on 2012-04-13
First make sure you can boot with the cd in live mode (Try Ubuntu). If it doesn't work, most probably it will not work after you install it too (as you noticed).

This might be video driver issue with your video card. Try this:
1. Boot with the cd (don't matter 11.10 or 12.04 Beta).
2. When the first splash screen shows, press Esc. That should display the older type start menu.
3. Hit F6 to display advanced options. Select 'nomodeset'.
4. Select the Try Ubuntu option from the main menu.

Does it boot correctly to the desktop?

If yes, you can continue and install it, but the first time it will not boot unless you add the 'nomodeset' parameter.

First see if this helps to boot it in live mode, later we can discuss how to add the parameter on first boot after the install.

And also, I recommend to boot windows and remove the wubi install from Programs, like you remove any other software. It's much better to use proper dual boot and wubi doesn't help your issue anyway, as you noticed.

---

### Post by deafdigit on 2012-04-13
Hey Darko,



Thanks for your reply.

I did the nomodeset-thing, and it worked - it booted to the desktop live-cd-style! Only one problem (and I don't know if that's actually supposed to happen): the internet (wired connection) didn't work...

Also, when I restarted to boot back into windows, it told me to remove the cd, close the tray and hit Enter. I did, but nothing happened, so I had to force-reboot it. I suppose that'll change once I do the installation though.

So - next step - what do I do? (spell it out for me please ;))


//deafdigit

---

### Post by darkod on 2012-04-13
Hmm, wired internet should work in most cases.

OK, if you want to install a dual boot, you need to have unallocated space not belonging to any partition. So, if you don't have unallocated space, first you will need to open Disk Management in win7 and shrink (or delete) a partition to create unallocated space.
Also, make sure you are not using all of the 4 primary partitions that are allowed. If you already have 4 partitions in Disk Management you can't install right now until you decide which partition to delete.

So, once the disk is prepared with unallocated space, boot with the ubuntu cd the same way with nomodeset, and this time select the Install option from the main menu, not Try Ubuntu.

That should start the install process which should finish fine.

But on the first restart you will have to:
1. When the grub2 boot menu shows, highlight the ubuntu entry but don't hit Enter. Instead hit 'e' and that will show the boot lines you can edit.
2. With the arrows keys, position the cursor in the line starting with linux just after quier splash. There add nomodeset.
3. Press Ctrl + X to boot. That should allow it to boot.

Once it has booted, hopefully your wired connection will work, you can install the drivers for your video card and this issue should go away.

If it still continues, there is a way to add the parameter permanently, but until you do that you will have to edit the boot line on every boot because editing it like that is temporary. When you shut down, it goes away.

As I said, if the driver doesn't fix it, you can make this parameter permanent.

---

### Post by deafdigit on 2012-04-13
Thanks again, Darko.

I did most of what you said, and here's the result.

The installation ran fine, and Ubuntu now seems to be installed as intended.

Wired connection is still not working ("Wired connection disconnected - you are now offline"), so I can't install the video drivers.

Computer still freezes on both restart and shut down.

What seems to be the next step?


//Deafdigit

---

### Post by darkod on 2012-04-13
Did you install 12.04 or 11.10?

If you installed 12.04 it is still in development and not intended to be used as your main OS. It will be released towards the end of this month. That might be the reason for these problems.

If you installed 11.10 and the ethernet is not working, first google around if there are any known issues with your network card and ubuntu 11.10.

---

