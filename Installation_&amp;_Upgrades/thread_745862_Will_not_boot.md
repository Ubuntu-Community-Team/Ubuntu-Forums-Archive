---
title: "Will not boot"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by Shastadad on 2008-04-04
Have posted this on the Absolute Beginners thread but so far have only received one response telling me that it should work.  Maybe I need some "old hands" to solve my problem.

Don't usually jump into forums with request for help but this has me stumped.

My Computer:
Intel Dual Core 1800 MHz
2 Gigis of RAM
Intel DP35D Motherboard
NVIVIA Geforce 8400 GS Video card
I 250 Gig HD with Windows XP
1 80 Gig HD for Ubuntu

After my first disastrous attempt to install my live Ubuntu 7.10 Hardy Heron CD onto my XP drive where it corrupted my Windows XP boot partition I gave up and used and then purchased a separate hard drive to install Ubuntu on.

Have my bios set to boot from CD for install purposes then go in and change boot order to boot from HD that SHOULD have Ubuntu installed. (I physically disconnect the XP hard drive just to insure that I don't format the XP HD again) so the boot is from the 80GB HD.

I will get the message "GRUB loading stage1,5" Then "GRUB loading, please wait,,," " Press 'ESC' to enter the menu...0". I then get "Starting Up and then I will get a quick message that starts out " PCI failed to allocate memory resources,,,,,,,, " and I cannot stop the screen to read the full message. I will see the Ubuntu logo and a status bar which will start but then my screen will go black and all I will have is the animated round mouse cursor.

Here is what I have done to try and help myself. Have downloaded both versions of Ubuntu 7.10 the original Live CD and the Alternate Text ISO. The original live CD works great on my system and I have tried to install it two ways. Using the INSTALL icon on my desktop and using the Install option on the drop down menu in Administration. That did not work so I downloaded the Alternate CD (text ISO) and tried that. I have checked both CD for defects and both have passed the check. Have run a Memtest86 v1.70 but it will only get to test #7 and will then reboots.

I have attempted the ESC and chosen the "Safe mode" and it will do a whole bunch of checks, all OK and then will stop at "root@ubuntuDuck:~# " With a blinking cursor

I have tried this installation on two different hard drives. An old IDE that had Win 98 on it that I was able to FORMAT and a new SATA 2 hard drive listed above and I am ready to pull out what remaining hair that I have since I cannot get Ubuntu to load from a hard drive. I don't think that it is my video card since the live CD works so well. My video card is listed above. 

When using the live CD I can do everything like set the clock, use Firefox browser, change desktop themes, etc. but it is just slower since in must read from the CD.  For the life of me I cannot figure out why the live CD would work so well but installing it to a hard drive is a no go.

What is my problem and how do I solve it ? PLEASE :confused:

---

### Post by tamoneya on 2008-04-05
that PCI resource i think is your video card.  I have a similar echo at startup and have a 8600GTS.  I however have not had a problem with it not booting.  It does however take a long time.  It may seem kind of stupid but how long are you letting it sit at the screen with the animated round cursor?

---

### Post by Shastadad on 2008-04-05
> **tamoneya said:**
> that PCI resource i think is your video card.  I have a similar echo at startup and have a 8600GTS.  I however have not had a problem with it not booting.  It does however take a long time.  It may seem kind of stupid but how long are you letting it sit at the screen with the animated round cursor?

Well once I let it sit all night and it never booted.  BUT I accidentally solved my problem.  I installed a switch to control the XP hardrive so that I don't have to go into the BIOS every time I boot up and to check it I disconnected my monitorS.  With the emphasis on multiple monitors.  Evidently that is what caused the blank screen and boot hang.

[COLOR="SeaGreen"]**[SIZE="4"]Once I removed the second monitor Ubuntu booted right up.[/SIZE]**[/COLOR]  So you were correct in your diagnosis and I am writing this on a hard drive install of Ubuntu. Of course now I will have to learn how to set up multiple monitors but that is the subject of a future post.:)

 Thank you for your assistance.  I am hoping that I can edit the title to show Solved.

---

