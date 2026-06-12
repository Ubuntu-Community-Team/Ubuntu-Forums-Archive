---
title: "Unable to Load the 12.10 Live Installer"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by JaceMan on 2013-01-07
I am trying to install Ubuntu 12.10 on an older VIA Pentium 4 with Integrated SiS graphics, but every time I make it through the boot loader screen, the graphics are jumbled and distorted very badly beyond recognition.  They only take up the top portion of my LCD.

I read some tips here about starting the installer with nomodeset checked, but that doesn't change anything for me.

I have tried the Ubuntu 12.10, and Lubuntu 12.10 live installers both with the same issue.  I'd be glad to help you help me if you can give me tips on what information you need and how I get that information for you.

Thanks.

---

### Post by JaceMan on 2013-01-08
Nothing?

Hmm... I guess I'll trying an older version of Ubuntu or Linux Mint.  I know I have some older installation CD's around here.

---

### Post by darkod on 2013-01-08
You can try 12.04 which is LTS release and might have better driver support. Also, for 12.04 there is Alternate Install image, which has text installer and should let you install but I don't know if it will boot first time or give you graphics problems too.

For 12.10 there is no alternate image yet, I don't know why and I'm not sure if they will release one.

---

### Post by JaceMan on 2013-01-08
> **darkod said:**
> You can try 12.04 which is LTS release and might have better driver support. Also, for 12.04 there is Alternate Install image, which has text installer and should let you install but I don't know if it will boot first time or give you graphics problems too.

For 12.10 there is no alternate image yet, I don't know why and I'm not sure if they will release one.

Thanks for the follow-up.  I did try 12.04.  I got the same from it that I got with 12.10.

I was able to boot into Linux Mint 12 LXDE and see the screen.  I'm currently waiting for the install of it to finish.

---

### Post by upptown on 2013-01-08
I have had the same issue.  Mouse over to the top right and "feel" around for the settings drop down menu and go to display settings.  I was able to adjust the screen resolution to 800x600 which fixed the issue.  It required a bit of "feeling" around to click on the buttons but worked.Good luck

---

### Post by JaceMan on 2013-01-08
> **upptown said:**
> I have had the same issue.  Mouse over to the top right and "feel" around for the settings drop down menu and go to display settings.  I was able to adjust the screen resolution to 800x600 which fixed the issue.  It required a bit of "feeling" around to click on the buttons but worked.Good luck

Assuming i was lucky enough to click on the settings drop down menu, how do i get to display settings?  And then how do I get to 800x600?

After driver updates were you able to increase your resolution?

800x600 would be unusable and a huge waste of real estate for my 23" LCD.

For the record, the Live CD of Mint 12 LXDE loaded fine and installed without error.  It is currently running, but if I could upgrade to Ubuntu 12.10 I would like to make the switch.

---

### Post by upptown on 2013-01-08
> **JaceMan said:**
> Assuming i was lucky enough to click on the settings drop down menu, how do i get to display settings?  And then how do I get to 800x600?

After driver updates were you able to increase your resolution?

800x600 would be unusable and a huge waste of real estate for my 23" LCD.

For the record, the Live CD of Mint 12 LXDE loaded fine and installed without error.  It is currently running, but if I could upgrade to Ubuntu 12.10 I would like to make the switch.

The 800x600 setting is only for the "Live" session that you are in.  Once you have installed everything works fine at your display's default setting.  If you are using a laptop, I also found that hooking up an external monitor sometimes works.

Also, it's more patience than luck.

---

### Post by JaceMan on 2013-01-08
> **upptown said:**
> The 800x600 setting is only for the "Live" session that you are in.  Once you have installed everything works fine at your display's default setting.  If you are using a laptop, I also found that hooking up an external monitor sometimes works.

Also, it's more patience than luck.

It's a desktop.

I haven't used Gnome 3 or Unity before.  I was a long time XFCE guy coming over from Gnome 2 a long time ago.  I have since used LXDE more and more.

I say this to say that I don't really know what to do when you say to "Mouse over to the top right and "feel" around for the settings drop down menu and go to display settings. I was able to adjust the screen resolution to 800x600 which fixed the issue."

Could you provide the keyboard equivalents perhaps so that I don't have to "get lucky" with my mouse cursor?  Or at least let me know that when I click over the settings drop down menu which option is "display settings"?  1st one, second, third, etc. And after I am in there, what do I need to do to change the resolution since I will be unaided by visual help on screen.

Thanks ever so much.

---

### Post by darkod on 2013-01-09
If the installed system works fine and only the live session gives issues, it would probably work if you use the alternate cd. It doesn't have a GUI during install so it won't get stuck on it. But again, there is an alternate image only for 12.04 LTS.

---

### Post by JaceMan on 2013-01-09
> **darkod said:**
> If the installed system works fine and only the live session gives issues, it would probably work if you use the alternate cd. It doesn't have a GUI during install so it won't get stuck on it. But again, there is an alternate image only for 12.04 LTS.

I don't know if the installed system would work or not since I can't see the Live session to complete an install.

The current installed session that works is from Linux Mint 12 LXDE (based on Ubuntu 11.10) not Ubuntu 12.10 or 12.04.  Furthermore, I was able to see the screen fine and use the live CD installer from Mint 12 LXDE without pause.

The issue is that I would like to use the Ubuntu 12.04 or preferably 12.10 code-lines and it is with those variants that I encounter these graphics issues.

---

### Post by darkod on 2013-01-09
And if you select Install Ubuntu instead of Try Ubuntu, does it also fail?

I was refering to the upptown post that even when he had issues in the live session, once installed the system worked with the default settings.

First, you can install without fully loading the live session by selecting Install Ubuntu from the main menu instead of Try Ubuntu. That starts the installer right away.

Second, you can also install 12.04 LTS using the alternate cd which doesn't load live session. So, in case the issue is with the live session only, you avoid it.

Basically you could have tried it by the time we are discussing it. :)

---

### Post by gordintoronto on 2013-01-10
How much memory is in the computer? Have you reviewed the system requirements?

---

### Post by upptown on 2013-01-12
> **gordintoronto said:**
> How much memory is in the computer? Have you reviewed the system requirements?

Don't think the issue has much to do with system resources.  I have experienced it on newer AMD and intel systems as well as my pentium D system.  Variety of different video cards and still have the same issue.

To the OP.  What I had to do is hard to explain, but if you are experience the same problem I have had your display appears to be "jumbled" kinda like the screen is in three vertical partial sections.  I have found that there is a drop down menu accessed when you put the mouse pointer over the the top left corner of the screen where the time is displayed on a standard ubuntu setup.  One you hit the right spot you'll get the dropdown and see "Displays" as one of your options.  From there, like I said, you'll have trial and error.

Sorry I can't give you the magic fix.

---

