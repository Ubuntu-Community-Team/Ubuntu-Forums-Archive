---
title: "Will not install from usb stick"
date: 2014-01-17
forum: Installation &amp; Upgrades
---

### Post by john135 on 2014-01-17
Hi, 

I've been thinking of switching from Windows 7 to Ubuntu (any linux really but I was thinking of starting with ubuntu). Unfortunately, any installation method I've tried has been met with failure. 

So far I've only used my usb because i don't have a blank cd with me right now. When I try to boot my pc from the usb and finally get to this [screen]("http://www.pendrivelinux.com/wp-content/uploads/ubuntu8-boot-menu.jpg") (well not exactly since i just googled that picture, but pretty close) and I choose the option 'try ubuntu without installing' - after a few seconds all I get is a black screen and  have to hard-reboot my computer. I've tried this many times and I get the same result, even when i select the 'nonmodeset' option.  I've tried both 12.04 and 13.10 --> 12.04 will give the black screen while while 13.10 will not even start because of some file missing. Note that this is not the first time that I install ubuntu, I've done it before on many of of friends' computers using the same exact way and i got no problem. So I'm really confused.

The md5sum on the iso file turns out to be fine. On the USB boot I tried to check for disk defects (which by the way it only works if I select 'nonmodeset'; if I don't then I will get the same exact black screen) and after the disk check is done i get the message that either 2 or 3 files are missing (different results on different runs). I've tried making the usb bootable using a couple of different software and still no go. 

So, if anybody can help it would be great. If not, please recommend me a different linux distribution similar to ubuntu

---

### Post by fantab on 2014-01-17
Sounds like a USB drive issue... try a different USB drive.
What graphics card/cards do you have?

---

### Post by john135 on 2014-01-18
I've tried two different usb sticks and I still got the same problem. As for my graphic card, based on Device Manager I have Intel HD graphics - hope that helps.

---

### Post by fantab on 2014-01-18
Give us more info about your laptop/desktop with more hardware details. Some OEM need different pre-install settings than others.

Is your Windows hibernating? If it is then disable it.

---

### Post by bertan2 on 2014-01-18
Does it work with the latest build of trusty? I have that installed on a laptop. Somewhere I read that Mark Shuttleworth himself uses trusty already because the QA process is getting so efficient that you can use an alpha for most purposes. Here's the daily build page: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by john135 on 2014-01-18
Sorry fantab - I intended to do that when I started the thread but I forgot.

I have an HP Pavillion DV5 laptop currently running Windows 7 64bit; Intel Core i3 CPU @ 2.27GHz (4x), 4 gb or Ram; Intel HD Graphics. 

And I have no idea if it's hibernating but it looks exactly like it is - though it doesn't come back if I press any button.

---

### Post by john135 on 2014-01-18
@bertan2 - That actually worked; the first iso from your link worked out fine. I tried ubuntu and I even went through the installation (did not complete it, just went up to the part where you can assign different partitions) and everything seemed to work fine.

However the "Check disc for errors" option still returned 1 error - Is that safe to ignore?

and secondly is this version of ubuntu (I think 14.04) good to install permanently? or is it still in testing?

---

### Post by bertan2 on 2014-01-18
Glad to hear you got it working. I don't know what "check disk for errors" means, so can't help you with that one. As for 14.04, it is very definitely still being tested. If you install it on your main machine at the stage, you are definitely taking on more risk than you would be with the official beta test version, which in turn will be riskier than the production, long-term support version of 14.04 when it comes out in April.

---

### Post by john135 on 2014-01-18
"check disk for defects" (not errors - my bad) is one of the options when you boot from usb, you can see it here  [http://static.howtoforge.com/images/the_perfect_desktop_ubuntu7.04/1.jpg](http://static.howtoforge.com/images/the_perfect_desktop_ubuntu7.04/1.jpg)

Secondly, I only have one computer so whatever version of linux that will be my main machine. But what am I supposed to do if that's the only one that will work lol?

Maybe I'll try an alternative like lubuntu or xubuntu...

---

### Post by john135 on 2014-01-18
**Additional note**:  I just tried Lubuntu 13.10 and I got the same exact issues; which leads me to believe that I'm doing something very wrong!!

---

### Post by bertan2 on 2014-01-18
It may be a problem that has only been fixed very recently, which would explain why only 14.04 works. Another one that's good and up to date is Fedora 20. That is an official release, so you might have more luck with that one. As with Ubuntu, there is a try-before-you-buy feature in the installer.

---

### Post by john135 on 2014-01-18
If I can't fix ubuntu (or Lubuntu) I'll have no choice but to try something like fedora. 

Too bad though cuz I really liked ubuntu

---

### Post by john135 on 2014-01-18
It turns out that if I type acpi=off on the command line, Ubuntu will run fine, though the functional keys on the  keyboard do not work. I was told that it might not be a good idea to install ubuntu with acpi=off

---

### Post by john135 on 2014-01-18
I resolved the issue but not sure what happened. I think updating the Bios and other drivers did the trick

J.

---

