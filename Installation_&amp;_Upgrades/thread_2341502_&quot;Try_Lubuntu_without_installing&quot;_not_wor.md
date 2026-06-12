---
title: "&quot;Try Lubuntu without installing&quot; not working"
date: 2016-10-28
forum: Installation &amp; Upgrades
---

### Post by rdb3 on 2016-10-28
My desktop runs Ubuntu 16.04 without problems.
I wanted to check out Lubuntu and I created an ISO image of Lubuntu 16.04 on a usb drive using Startup Disk Creator.
When I boot from the usb drive I get as far as the Lubuntu options menu.
When I click on the "Try Lubuntu without installing" option, it goes to a blank screen with a blinking dash on the top left corner and stays there.
When I click on the "Test Memory" option, that works.
And when I click on the "Install Lubuntu" option, it proceeds to the correct screens.  I never go as far as installing it because I am just interested in checking it out.
Any suggestions are appreciated.  Thanks!

Compaq Presario  SR5210NX
Memory  2 GiB
Graphics  Intel® 945G x86/MMX/SSE2
Processor  Intel® Celeron(R) CPU 420 @ 1.60GHz 
Disk 25 GB
OS type  32-bit

---

### Post by Geoffrey_Arndt on 2016-10-28
Verify iso download

Use Etcher to create the Media (versus Startup Disk Creator)   [https://www.etcher.io/](https://www.etcher.io/)

[URL="https://help.ubuntu.com/community/VerifyIsoHowto"]https://help.ubuntu.com/community/VerifyIsoHowto

[/URL]

---

### Post by rdb3 on 2016-10-28
I downloaded Etcher but I don't know how to execute it.

In the past I have used Startup Disk Creator for other Linux ISO creations w/o a problem, that's why I am stumped about this one.

---

### Post by vasa1 on 2016-10-29
Try mkusb: [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Sudodus, a member here, will surely help you if you have any difficulties.

---

### Post by Bucky Ball on 2016-10-29
*Thread moved to **Installation & Upgrades**.*

Unsure why this was in ***New to Ubuntu***. Much better chance of support here. :)

Lubuntu is without some of the stuff that comes in a regular Ubuntu ISO. Do you remember needing to install drivers in your current Ubuntu for video? 

As this is booting fine and getting you to the option screen and the issue is occurring after that, wondering if this has actually got anything to do with a faulty USB creation. 

Have you tried booting with the nomodeset option set? Try that and see if it gets you any further. Follow the [first answer in this link]("http://askubuntu.com/questions/135515/set-nomodeset-in-usb-installation-efi-loader-with-iso"). It has pictures. You need to get to the advanced options screen at boot and hit F6. That will bring up the options and choose 'nomodeset'. Proceed. Generally used for NVidia, but you never know ...

---

### Post by bearlake on 2016-10-29
Seen the same thing as the OP but since it was going to my test drive, I just went a head and installed it.

It only happens with Lubuntu (try live without installing) and not any other of the flavors.

Running a full Intel system and never really looked into the problem.

---

### Post by howefield on 2016-10-29
> **rdb3 said:**
> I downloaded Etcher but I don't know how to execute it..

Have you downloaded Etcher as a zip file from the Etcher website ?

Simply double click the zip file which will open it in the Archive Manager and extract to where ever you want it eg, the Downloads folder. It is only a single appimage file, then open a terminal and change to the Downloads folder and run the appimage file.. eg.

```
cd ~/Downloads
```
```
./Etcher-linux-x64.AppImage
```

---

### Post by rdb3 on 2016-10-29
I am writing this from my live Lubuntu desktop.  Well I got it to work, and here is how:

I went ahead and installed mkusb and created the Lubuntu iso.

Then I booted, and I was getting the same results as in my opening post.... I could not "Try Lubuntu without installing."

I booted back to the Lubuntu menu, and I clicked (F6 other options) this time.

I saw nomodeset as an option and clicked on it.  Hit esc, back on the menu, clicked on "Try Lubuntu without installing" and it came up.

The only reason I clicked on nomodeset was because someone mentioned it (Thank you).  I don't know what nomodeset does, but would be glad to 
understand if someone can explain in layman's terms.

I believe it woud have worked from the Startup Disk Creator iso also had I followed the above steps.

Thank you to all who have posted!

---

### Post by Bucky Ball on 2016-10-29
I suggested nomodeset and now I have one more question. Can you reboot the machine back to Ubuntu with no issue? If not, you will need to make the nomodeset option permanent. Let us know and we can let you know how. :)

Thanks for marking as solved and sharing the fix. nomodeset, I think, avoids the machine looking for a GPU driver that isn't there, to put it simply. Someone else may give a technical explanation. :)

---

### Post by rdb3 on 2016-10-30
You are welcome, and thank you for the nomodeset tip.  Yes, I can reboot back to Ubuntu.
The only thing I have found with Lubuntu is that webpages and videos are not as sharp as on Ubuntu.
On Ubuntu, the display resolution is 1920 x 1080.
On Lubuntu it is 1280 x 1024, and I don't know how to change it.  I went to the display panel, but no luck.

---

### Post by Bucky Ball on 2016-10-30
Go to Additional Drivers. Is there an Intel driver there for it? If so, install, reboot, check Display again and see if the right resolution is there.

If not, probably best, and will improve your chances of support, to post a new thread about this after attempting to hunt down a fix. My suggestion comes from the [last answer here]("http://askubuntu.com/questions/767429/ubuntu-16-04-graphics-crashes-with-intel-graphics").

---

### Post by rdb3 on 2016-10-31
Software & Updates > Additional Drivers

The only option was the following... I clicked it, and things seem to be sharper..

Using Processor microcode firmware for Intel CPUs from intel-microcode

Thanks!

---

### Post by rdb3 on 2016-11-02
UPDATE:  The above ^^^^^ did not really resolve my problem.

I went to the link below and used UNetbootin, as recommended, to create a live-usb.  This resolved the problem in my opening post without having to choose the nomodeset option.
It also came up with my  correct display resolution 1920 x 1080.   

[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

---

### Post by ajgreeny on 2016-11-02
I am happy that you have now got this figured.

If your machine uses an older Intel integrated video chip the problem was probably related to a bug of Lubuntu not installing the xserver-xorg-video-intel package.  Booting using nomodeset to get a GUI and from that installing the missing xorg package usually solves this completely, but it can be a bit of a show-stopper if you're unaware of it.

See post #13 of [https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460) where I mention the solution I used.

---

### Post by rdb3 on 2016-11-02
Thanks for pointing that out.  Now we have two options available.

---

