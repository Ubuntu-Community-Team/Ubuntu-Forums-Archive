---
title: "Is there a known reason why my 10.04/12.04 dual boot flunks?"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2012-08-15
Running 10.04. Shrunk its partition to half the drive. Installed 12.04. Option chosen was "install along side". Installs but then when I reboot to the boot menu and choose 12.04 I get a black screen with messages about not being able to boot. possible reasons boot timeout, etc, etc, blah, blah.

I have dual booted may times before and never had a problem with it. Any idea whats going on?

---

### Post by sofasurfer on 2012-08-18
I am now able to go to the boot menu and choose my new installation. But when I do I get a black screen with the message "File not found" and "you need to load the kernel first".

Now can anyone answer me...please?

---

### Post by oldfred on 2012-08-18
A black screen with a cursor in the upper left corner is often a video issue. The moved video into the kernel and you often have to add boot parameters to make it work.

But kernel missing is a bigger issue.

Post link from BootInfo report:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by sofasurfer on 2012-08-19
I found info that states that ubuntu 12.04 file is actually too big for a cd and for some reason dvd does not work either. I found "unetbootin" which is a program that downloads a ubuntu version (12.04 or whatever) and puts it on a USB stick. I tried that and it did not work. I am retrying it now and will post and let you know in a while.

---

### Post by sofasurfer on 2012-08-19
Ok, I installed Ubuntu 12.04 to my USB stick with unetbootin. My peoblem was that I had my BIOS setting wrong. I took care of that and when I rebooted I chose USB from my boot menu. The 12.04 opened (running Live CD from the USB stick) and I installed it to my PC alongside of 10.04. Seems to work great so far. Got video working with a couple of clicks. But the rest of 12.04 is so different I will take a long time to figure it out.

---

### Post by oldfred on 2012-08-19
Some that use Unity for a while end of really liking it and others resist change. 

I use fallback or gnome-panel which is close to the old style menu.

12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

