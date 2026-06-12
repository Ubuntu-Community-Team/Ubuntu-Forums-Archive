---
title: "ubuntu Screen on Installation"
date: 2015-09-19
forum: Installation &amp; Upgrades
---

### Post by Robk29 on 2015-09-19
I've just installed ubuntu for the first time and booted from my USB. The result is an ubuntu screen which looks normal and the five 'dots' turn white in turn then start over, this has continued for two hours. Help!

---

### Post by grahammechanical on 2015-09-19
It would help if you told us the specifications of your hardware and the version of Ubuntu that you downloaded. Was it i386 or amd64? Trying to run the 64 bit version of Ubuntu on a 32 bit CPU will not work. Also, you may need to make some changes to the boot parameters of the live session. Check out this wiki page and go to the heading with the label "Changing the CD's boot options." and go to Section 6 - F6. You may need to try some of the F6 options. Perhaps, nomodeset. You may even need to try a combination of those options.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by Robk29 on 2015-09-19
Sorry, it was the default desktop version  - amd64 and I selected the try option from the first screen not a full installation. I changed my BIOS settings to allow a USB boot and this was fine. I have a 64 bit Acer laptop - quad core Pentium. I just tried F6 and this works so at least it's not hung. l'll  look at this in more detail thanks.

I have looked at the script generated via F6 and there appears to be a series of errors starting with problems creating an SSL certificate. Can anyone offer a solution or do I need to abandon Ubuntu before I've even used it and go back to Windows? Is there anyone skilled in reading installation script error logs?

---

### Post by Robk29 on 2015-09-20
Is anyone experienced in acting on errors generated in the installation log (via F6) during installation?

---

### Post by Bucky Ball on 2015-09-20
Welcome. When the machine is booting and you have the icon at the bottom of a purple screen, hit any key. That should get you to an options screen. Hit F6 there and then choose the option 'nomodeset' from the pop-up menu. Continue with 'Try Ubuntu'. Any luck?

Which release? As in 12.04 LTS, 14.04 LTS? From where did you download the ISO and how did you create the install media? There is an option to 'Test disk for defaults' at the options when you boot from install media. Have you run that?

By the way, you haven't installed Ubuntu. You've create a live installer on USB or DVD by the sounds of it. You install Ubuntu from that. At the moment you are just trying to try a Live session from the install media.

There are a lot of experienced folk here in lots of areas but let's start at the beginning with some known remedies. Smells like graphics, which is common. :)

* Get the [ISO from here]("http://www.ubuntu.com/download/desktop") if you didn't. 14.04 LTS is supported until 2019, 15.04 until January 2016.

---

### Post by Robk29 on 2015-09-20
Hi,

Thanks for the response. I downloaded 14.04.3 from the official site and the USB installer 1.9.6.1 then re-configured my BIOS to boot from a USB. I then ran the USB executable to install on the USB, this appeared to be successful. 

On restart it booted from the USB and I selected the try ubuntu option. It began looking at my network config etc then stopped. While it has clear errors in the log there is no indication on how to resolve them. 

I'll have a look at the 'nomodeset' etc.

---

### Post by Bucky Ball on 2015-09-20
> **Robk29 said:**
> It began looking at my network config etc then stopped.

Sounds like it is choking on the wireless. Have you got an ethernet cable plugged in? Weird, though, as I thought it should just tell you that you have not available wireless connection. It should still boot to 'Try Ubuntu' without an internet connection of any kind.

---

### Post by Robk29 on 2015-09-20
This might be a 'Red Herring' as it did that on one attempt however not every time, more recently I have received no on-screen notifications at all. One error that appears every time in the log relates to an attempt to install a SSL certificate, then a cascade of errors follow.

---

### Post by Bucky Ball on 2015-09-20
Try what I described in post 5 and get back to us.

---

### Post by Robk29 on 2015-09-20
Solved! Thanks Bucky Ball.

 I tested the disk for faults as you suggested and two errors were found. I then re-formatted the USB, downloaded and ran the utility again. I'm now looking at the Ubutu Desktop, excellent! The end of Windows for me is in sight.

---

### Post by Bucky Ball on 2015-09-20
Great news! :D

Have a look at the first link in my signature, enjoy the forums and the OS.

---

