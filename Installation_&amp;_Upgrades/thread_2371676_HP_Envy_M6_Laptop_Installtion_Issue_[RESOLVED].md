---
title: "HP Envy M6 Laptop Installtion Issue [RESOLVED]"
date: 2017-09-17
forum: Installation &amp; Upgrades
---

### Post by ninzombie2017 on 2017-09-17
Hey Gang:

I just wanted to touch base with everyone and thank you for the help with installing Ubuntu 17.04 on my laptop.  I am finally Windows 10 free, and it is rather liberating!  No solutions work, but for some reason the Live USB stick picked up all the third-party drivers, installed without a hitch, and worked.  I did post the issue a few weeks ago under a different username - but since I ditched all social-media as well, I cannot for the life of me remember where I put the post.  

So, thank you again to everyone, and glad to be back with the community!

Sincerely,

Paul

---

### Post by RobGoss on 2017-09-17
You are most welcome glad it worked out for you Ubuntu is a great OS

---

### Post by ninzombie2017 on 2017-09-17
Ok, strike that...it worked for one boot, and that was it.  Same problems as before....UGH

Ubuntu 17.04 did its system updates and would not reboot again.  Back to the drawing board...

---

### Post by RobGoss on 2017-09-17
Have you tried Ubuntu 16.04 to see how it works might b a better choice

With 17.04 are you using the proprietary drivers provided by Ubuntu?

---

### Post by ninzombie2017 on 2017-09-17
Ok, here is a list of things that before and after...

1) This unit had the hard drive replaced in July (little over one year old), losing the recovery partition provided by HP.
2) Using the Windows USB Media Creator, I was able to create a Windows 10 (x64) to recover the computer, thus being able to use the entire hard disk capacity.
3) Got sick of watching Microsoft tank, drop their phones, drop all support for their Band and Band 2 products, phones, etc..  (used to own one of their Lumia 950 XL phones and a Band 2)
4) Developers jumped ship or never bought into UWP, so I wanted out.
5) Tried Ubuntu 16.04.3 LTS, as well as 17.04, creating my installation media using the most current version of Rufus following Ubuntu's wiki on how to create the boot USB.
6) Live version of Ubuntu (both versions) works every time.
7) Installation goes flawlessly each time - using third-party drivers or not.  Need the third party for my onboard AMD graphics as well as my WiFi - but I tried it both ways for giggles.
8) Reboot the computer and get a ton of errors or a black screen - expect for this afternoon - it has never rebooted into Ubuntu after installation.

I am beginning to wonder if it is a UEFI issue, or maybe just not compatible with Ubuntu at all.  

One thing to note though - the computer did the same thing trying to boot up the live install version of LinuxMint 18.2...I know the core of LinuxMint is Ubuntu, so I can see how this would happen on both builds of Linux - question is, what is fouling it up?

---

### Post by Geoffrey_Arndt on 2017-09-19
The installing of 3rd party drivers is not always accomplished by checking the "install 3rd party xxx" in the install welcome screen.  So, upon a reboot, your video drivers are not actually installed to the internal disk.   You may have to use "nomodeset" to reboot into a lower res login & desktop.   But that allows you to go to the settings and "additional drivers" tab.    Generally, it's not recommended to install graphic drivers direct from the manufacturer.

---

### Post by ninzombie2017 on 2017-09-19
As previously mentioned, choosing "install third party drivers" or not, the same thing happens...numerous errors or nothing at all....

---

