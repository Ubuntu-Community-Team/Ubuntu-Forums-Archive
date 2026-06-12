---
title: "Windows 2000 dual booting with Ubuntu."
date: 2006-05-29
forum: Installation &amp; Upgrades
---

### Post by Scott_Perry on 2006-05-29
Greetings, this is my first post here. The reason being is that for a while now I've wanted to actually learn something about computers and programming from a webpage I read it suggested Linux is the way to go starting with Perl. I was recommended Ubuntu by a user on another forum board. Last week I put in another hardrive to facilitate this. Windows 2000 is on the primary, I downloaded the Ubuntu-5.10-install-i386.iso distribution and burnt it to C.D. Windows 2000 does not recognize iso as an extension. I changed the BIOS to boot from C.D and nothing happend at power on except loading the Window 2000 GUI as normal. What am I doing wrong, can someone please help I would be extremely grateful. Also what other things do I need to bear in my in prepartion for the installation? I know I need to find the correct Linux drivers for my hardware and record IRQ, what other things should I do. Further, is Ubuntu a good platform to learn about programming through (is Perl included with the installation?) or would you recommend another? If this is posted in the wrong area of the boards apologies, I have searched this forum and the Ubuntu documentation for any hints but nothing becomes apparent. If anyone can help, thanks in advance. I'd like to try to learn something am tired of sitting back letting windows do it all for me. 
Regards,
            Scott.

---

### Post by glotz on 2006-05-29
I think Ubuntu is a good platform to learn programming. I don't think that perl is included though, might be wrong there. And Ubuntu's a great OS.

To install Ubuntu, you need to make sure you've made a **bootable cd** of the .iso you've got. You probably need a 3rd party CD burner app on win 2000. Then reboot and goto BIOS setup (usually by pressing del during boot or some other key mentioned) and make sure that CD drive is before HDD in boot order. Then simply insert CD and boot and you should see the installer. I don't think you'll need to know much about your setup, besides your network parameters, like your IP address and such. (depending on how you connect to net)

Welcome to world of Linux!

---

### Post by Quietman on 2006-05-29
Just a thought...
Did you burn the .ISO file as an image to CD? If you did you should see a bunch of folders and files on it with Explorer.
However, if you didn't and there is only the .ISO file on the CD you need to burn as an image, not a file.

---

### Post by Scott_Perry on 2006-05-29
[QUOTE=Quietman]Just a thought...
Did you burn the .ISO file as an image to CD? If you did you should see a bunch of folders and files on it with Explorer.
However, if you didn't and there is only the .ISO file on the CD you need to burn as an image, not a file.[/QUOTE]

Yes that's exactly what I did, which begs the question. How do I burn it as an image?

I'm using Pinnacle systems Instant CD/DVD version 8.3.0 but as far as I can tell it doesn't support creating bootable CDs?

---

### Post by glotz on 2006-05-29
This is what I used to burn my installation disc back in my windoze days it seems [http://www.cdburnerxp.se/](http://www.cdburnerxp.se/)

Were you on Ubuntu, you'd right click the .iso and say burn baby burn and that'd be it... :)

---

### Post by aysiu on 2006-05-29
Follow these directions:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by Rochcom on 2006-05-30
I used RecordNow DX, the application that came with my CD/DVD drive.  It has the option to burn an image rather than a straight data disk.  You should be able to find that option in the menus of your burning program.  If not, here is a link to alternative instructions:

[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

Scroll to bottom for Win 2000 instructions. Warning:  I have not tried them.

---

### Post by Scott_Perry on 2006-05-31
Thanks everyone for your help particularly aysiu for posting that link.Now I have a bootable C.D of Ubuntu, however my problems don't end there. I changed my Bios settings and everything seemed to be going well until I reached the command prompt which determines what type of installation you require: Type 'server' for a base installation or hit ENTER for a full installation.Trying either installation the result is a couple of pages of scrolling information (too quick to read) then the command prompt just hangs, just below a date something like Dec 2004? Nothing else happens, am I missing something or just being impatient?

---

### Post by Scott_Perry on 2006-06-01
I should point out also that it doesn't display the installation screens as shown in this demonstration: [http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

So I'm thinking try something else, is Ubuntu suitable for my purpose of trying to understand programming? Can anybody recommend a more suitable distribution of Linux?

---

### Post by aysiu on 2006-06-01
There are two installer CDs:

Desktop
Alternate

The desktop one is the one I used to create that tutorial.
The alternate one uses the old-school text-mode graphical installer. If you have the alternate one, use this tutorial instead: [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

