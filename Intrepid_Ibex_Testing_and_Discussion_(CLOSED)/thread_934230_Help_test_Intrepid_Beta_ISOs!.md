---
title: "Help test Intrepid Beta ISOs!"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by castrojo on 2008-09-30
Hi everyone, 

It's that time (again):

[https://lists.ubuntu.com/archives/ubuntu-devel/2008-September/026620.html](https://lists.ubuntu.com/archives/ubuntu-devel/2008-September/026620.html)

Instructions are here: [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

---

### Post by castrojo on 2008-09-30
Here's a tip that saves a ton of time, I got this ISO downloading script from here:

[https://wiki.ubuntu.com/Testing/Isoscript](https://wiki.ubuntu.com/Testing/Isoscript)

And then I tailor the iso.cfg to only download the ISOs I am testing (currently I am signed up for kubuntu-kde4 and ubuntustudio) - I run the script, when it finishes I check the MD5sums to make sure it's the right ISO, then I go through all the tests. Next day, repeat. :)

---

### Post by kansasnoob on 2008-09-30
Sounds like a blast, and I have a spare hard drive.

Looks like this is the image I want:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) 

Eh?

---

### Post by castrojo on 2008-09-30
The specific image is linked from the ISO tracker at [http://iso.qa.ubuntu.com](http://iso.qa.ubuntu.com).

Click on the ISO you want to test; then click on the ISO title which will take you to a page similar to this:

[http://iso.qa.ubuntu.com/qatracker/info/1983](http://iso.qa.ubuntu.com/qatracker/info/1983)

You'll want to check md5sums to make sure you're testing the right ISO, don't always assume that the one in the current directory is linked to the right one.

---

### Post by kansasnoob on 2008-09-30
> **whiprush said:**
> The specific image is linked from the ISO tracker at [http://iso.qa.ubuntu.com](http://iso.qa.ubuntu.com).

Click on the ISO you want to test; then click on the ISO title which will take you to a page similar to this:

[http://iso.qa.ubuntu.com/qatracker/info/1983](http://iso.qa.ubuntu.com/qatracker/info/1983)

You'll want to check md5sums to make sure you're testing the right ISO, don't always assume that the one in the current directory is linked to the right one.

Thank you. Got it, just wanted to be sure.

---

### Post by kansasnoob on 2008-09-30
Going well here, of course I'll file my reports properly when I'm done.

So far I've tried installing using the "Use largest continuous free space" and it went great, then I deliberately tried something that should fail using "resize", and then "guided use whole disc", but there's one annoying thing every time:

The disc does NOT eject properly when the process is done!

It doesn't matter if you're installing or just running the Live CD, the disc does not eject properly!

Anyway, I have a couple of install methods to try out yet, but other than the eject problem I think you have something here!

I like the new art work!

Now I'm going to try a proper Guided Resize!

---

### Post by kansasnoob on 2008-10-01
Sorry to be a pain. I filed my reports (hopefully did it right). Tester name = Lance.

I encountered only one problem that was persistent throughout all test procedures: The CD does NOT eject properly on restart! It starts to eject but then goes right back in, so I must eject just as BIOS completes ........... it could be fiddly for the common user.

I also tried my previous Alpha 6 disc and it works fine, so it seems to be just this build. MD5 checked OK as did the test disc feature.

Again, sorry to be a pain.

---

### Post by Gina on 2008-10-01
That script is great - using it now to update my ISOs and download a couple of new ones.

---

### Post by Ub1476 on 2008-10-02
Wasn't this supposed to be released today, and not yesterday? :confused:

---

### Post by blakamin on 2008-10-02
This is for *testing the isos*

---

### Post by phidia on 2008-10-06
I dl-ed the desktop x86_64 version & checked the md5 which is ok.

Can't boot and can't check the integrity of the iso either (it just reboots).
I burned at slowest speed. 

Not a request for help-I will report this at the qa site when I can.

---

### Post by craggsy on 2008-10-08
The version I downloaded (on Monday), wouldn't write to a disk,then when I got a copy that did it kept saying their were errors in the disk and rebooted.

---

### Post by TheValk on 2008-10-13
The Daily i386 ISO I downloaded yesterday (12th) locks up during a manual partitioning both on a hard drive install and during a VirtualBox install.
I have opened a BUG on it but so far no response.
Seems similar to a bug that affected Hardy and Feisty....

---

### Post by Richard-g8jvm on 2008-10-17
Hi

I downloaded all the AMD 64 isos, desktop, server and alternate.
Checksums were OK,
They all booted and crashed straight after the language selection page.
I've posted on the dev mailing list....and no-one has even acknowledged it.
Machine here is a AMD 64 dual core Athlon +4400, 8 GB of ram.
I've upgraded via the approved route with the upgrade manager, but I'm not able to load any of the later kernels, I'm stuck with 2.6.24.
Everything selected in the grub menu gives error 15, except the kernel listed above.
I'm suspicious the kernel failures are due to the attempted installs with the beta isos


Richard

---

### Post by jerrylamos on 2008-10-17
Intrepid Beta iso's do not boot on IBM Thinkpad R31.  See bug 277344.

compiz is on by default on the iso's.  compiz fails on the very first attempt to show the desktop.

The workaround on CD Live is to quick do Ctrl-Alt-F1 after X windows has started but before the desktop is attempted to be displayed.  Then quick do sudo apt-get remove compiz & compiz core, then Ctl-Alt-F7 to resume.

Install works from the initial choices menu because it doesn't use compiz, Boot rescue mode then remove compiz, resume boot O.K.

The REAL BUG is compiz being on by default with NO CHOICE ON CD Live boot menu.  Yes, The only method is to do System Preferences Appearance Visual Effects None however the desktop has to be up using compiz code successfully to get there.

Yes, the very same Beta CD's boot O.K. on Compaq Presario so the CD's are O.K.  I try a new daily build again every day or so, Xubuntu Beta iso which doesn't use compiz runs O.K.  Alpha 5 NOT UPDATED runs O.K.

Since Launchpad has this bug rated "low", I assume Release Code won't run on IBM Thinkpad R31's either.  Looking at the posts, there are a number of people reporting booting to black screen or wallpaper, which could be the same bug but I don't have their hardware to test.

Jerry

---

### Post by jerrylamos on 2008-10-17
Intrepid Beta iso's do not boot on IBM Thinkpad R31.  See bug 277344.

compiz is on by default on the iso's.  compiz fails on the very first attempt to show the desktop.

The workaround on CD Live is to quick do Ctrl-Alt-F1 after X windows has started but before the desktop is attempted to be displayed.  Then quick do sudo apt-get remove compiz & compiz core, then Ctl-Alt-F7 to resume.

Install works from the initial choices menu because it doesn't use compiz, Boot rescue mode then remove compiz, resume boot O.K.

The REAL BUG is compiz being on by default with NO CHOICE ON CD Live boot menu.  Yes, The only method is to do System Preferences Appearance Visual Effects None however the desktop has to be up using compiz code successfully to get there.

Yes, the very same Beta CD's boot O.K. on Compaq Presario so the CD's are O.K.  I try a new daily build again every day or so, Xubuntu Beta iso which doesn't use compiz runs O.K.  Alpha 5 NOT UPDATED runs O.K.

Since Launchpad has this bug rated "low", I assume Release Code won't run on IBM Thinkpad R31's either.  Looking at the posts, there are a number of people reporting booting to black screen or wallpaper, which could be the same bug but I don't have their hardware to test.

Jerry

---

### Post by spsf on 2008-10-19
Intrepid-No Events Sounds nor Logout Sound
I filled some bugs about it in launchpad, the latest one is here:

[https://bugs.launchpad.net/ubuntu/+bug/285549](https://bugs.launchpad.net/ubuntu/+bug/285549)

Unfortunately no developer cared to answer any of the reports :(
There is also an active discussion here in the forum:

[http://ubuntuforums.org/showthread.php?p=5990754#post5990754](http://ubuntuforums.org/showthread.php?p=5990754#post5990754)

Anyway, i think it sounds so unprofessional for the Ubuntu team to release a new version with the new Gnome sound events not working :(

Is it the right way to report bugs? If not, please let me know, because I'd like to see the 8.10 shine!

---

### Post by tatewaki on 2008-10-20
Okay i have tried installing the desktop version (x86) on a dell hybrid and got a bunch of I/O errors and then a busybox promt. Nothing really happened after that. The i tried the Alt version and still got a lot of I/O errors but got to the installation promt. It was a hell lot slower then 8.04, not sure why...

---

### Post by pachequin on 2008-10-21
Hi! I downloaded the Intrepid iso for AMD64 (I have an HP pavillion dv6420 laptop with Opensuse 11.0 installed). I can boot from CD but at the time when the partitioner gave me the options to partition my hard drive, any partition was detected. I have a Windows vista partition, a / (root) partition, a home partition, an other partition that I use as "ssafe partition".

Does anyone have seen this error before?

Thank you.

---

### Post by tatewaki on 2008-10-24
Today i tried installing 8.10 Alt again on Dell Studio Hybrid, still got a lot of I/O errors but then when i got to the screen where it was trying to detect my hardware I got a error saying it could not find any mount point for the CD, I shutdown and tried again and this time I choose a OEM installation and that worked.

---

