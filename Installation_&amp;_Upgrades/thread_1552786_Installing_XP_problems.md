---
title: "Installing XP problems"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by kennerley on 2010-08-14
[SIZE=3]Heres where im at...

Ubuntu will not let me open any .exe file.....  any help?
Or run my xp disk.... when i run the disk i get this error message...

Archive:  /media/WinXP/SETUP.EXE
[/media/WinXP/SETUP.EXE]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/WinXP/SETUP.EXE or
          /media/WinXP/SETUP.EXE.zip, and cannot find /media/WinXP/SETUP.EXE.ZIP, period.


This is my 1st time using ubuntu and so far im not impressed, i cant download anything or use any disk.. feels like im stuck with this, welll.. to me quite rubbish OS.[/SIZE]

---

### Post by and1z360 on 2010-08-14
I get the same thing, but this is when i'm opening an .exe file of a game :confused:

---

### Post by YesWeCan on 2010-08-14
Erm. You are trying to do what exactly?
Ubuntu won't run .exe files any more than Windows will run linux executables.

---

### Post by Rubi1200 on 2010-08-14
Why are you trying to run the WinXP CD on Ubuntu??? (If I understood your post correctly).

How did you install Ubuntu?

And, as YesWeCan already asked, what do you want to do?

We can only help you if you tell us what you are trying to achieve.

:)

---

### Post by kennerley on 2010-08-14
I am trying to install Xp,  i bought my computer rescently from Ebay and it came with UBUNTU.
I have tryed formating the hard drive to start from scratch but it wont even let me do that...

All i want is XP not UBUNTU...  How can i get my disk to work.. which is .exe when ubuntu wont load it... 

I have tryed using ubuntu help which ermmm wasnt really much help, Ive tryed software sources and syneptic package manager w/e... apparantly my xp disk isnt there but i can see the files i just cant open them or use them in any way!
(This OS feels like a virus lol)


Thanks :)

---

### Post by Rubi1200 on 2010-08-14
> **kennerley said:**
> I am trying to install Xp,  i bought my computer rescently from Ebay and it came with UBUNTU.
I have tryed formating the hard drive to start from scratch but it wont even let me do that...

All i want is XP not UBUNTU...  How can i get my disk to work.. which is .exe when ubuntu wont load it... 
(This OS feels like a virus lol)


Thanks :)

First things first, how did you try and format the drive?

Second, to run the WinXP disk you need to boot the computer with the disk after setting BIOS to boot from the CD drive.

You should then be able to access the WinXP disk normally and choose/follow the instructions to install.

Alternatively, boot the computer with the Ubuntu CD and use GParted to delete the current setup, leaving the drive free for XP.

Then, go back to step 2 and boot using the XP CD.

[http://support.microsoft.com/kb/978307](http://support.microsoft.com/kb/978307)

---

### Post by dmizer on 2010-08-14
> **kennerley said:**
> which is .exe

If your disk is .exe, it's not a Windows OS install disk. If you want to replace Ubuntu with Windows, you'll need a full Windows OS install disk, a recovery disk will not be sufficient.

---

### Post by kennerley on 2010-08-14
Thank you very much you are proberbly right...  I thought it was because on the disk was Setup.exe and the 25didgit key.

Do you possibly know anywhere to download Xp 
If not i will have to find my other disk lol.

---

### Post by elliotn on 2010-08-14
25 digit key must be the cd key, if u downloaded the Xp u need to burn it on the CD the go to bios and set ur pc to boot on cd then put the disk in tray and reboot

---

### Post by Icarus315 on 2010-08-14
If you are having such basic issues with understanding Ubuntu and booting from a CD-ROM and such then you are going to have plenty of fun when it comes time to find and install the drivers for your potential Windows XP install..  Perhaps you should find a friend who is knowledgeable about computers to assist you?

---

### Post by rollin on 2010-08-14
> **kennerley said:**
> Thank you very much you are proberbly right...  I thought it was because on the disk was Setup.exe and the 25didgit key.

Do you possibly know anywhere to download Xp 
If not i will have to find my other disk lol.

Anywhere to download XP? I seriously hopes no-one posts an answer. When you find your disc just boot from the CD, everything will be clear after that. Part of the installation formats the HD then installs all the files.

---

### Post by kennerley on 2010-08-14
> **Icarus315 said:**
> If you are having such basic issues with understanding Ubuntu and booting from a CD-ROM and such then you are going to have plenty of fun when it comes time to find and install the drivers for your potential Windows XP install..  Perhaps you should find a friend who is knowledgeable about computers to assist you?

I am fine on XP and finding drivers thank you very much... 

1. UBUNTU dosent run .exe files... thats a problem for me... i can't download itunes/winrar or anything like that off the internet, why i dont know... i guess thats just ubuntu.

2. Yes this is my 1st time using UBUNTU but im getting the hang of it, even if everything is backwards, atleast it was when i got it.

3. I never thought it could be so hard to find a solution, all i want is to do is install XP and ill be well on my way, and i have never seen so many errors in so little time lol.

Oh and if your going to reply to someones post you should really think about reading them... 
To the question it concerns - No i havent downloaded it, i have it on CD... i have already possibly been corrected on using the wrong CD... thanks for the usless input...

---

### Post by dmizer on 2010-08-14
> **kennerley said:**
> Thank you very much you are proberbly right...  I thought it was because on the disk was Setup.exe and the 25didgit key.

Do you possibly know anywhere to download Xp 
If not i will have to find my other disk lol.

You can get downloads for any of Windows currently supported products here: [http://www.microsoft.com/windows/downloads/default.aspx](http://www.microsoft.com/windows/downloads/default.aspx)

---

### Post by kennerley on 2010-08-14
> **rollin said:**
> Anywhere to download XP? I seriously hopes no-one posts an answer. When you find your disc just boot from the CD, everything will be clear after that. Part of the installation formats the HD then installs all the files.


Thanks alot, this helps... I guess noone probs will.. ill find my CD later lol. 
Ive had an issue earlier trying to format the hard drive.. thanks for the XP CD info :)

---

### Post by rollin on 2010-08-14
> **kennerley said:**
> Thanks alot, this helps... I guess noone probs will.. ill find my CD later lol. 
Ive had an issue earlier trying to format the hard drive.. thanks for the XP CD info :)

No problem. You could also look into Virtualbox, this will enable you to install XP within Ubuntu as a virtual machine. Links here for more info [http://www.virtualbox.org/](http://www.virtualbox.org/) To install search the Ubuntu Software Centre under your Applications menu, then you can enjoy the best of both.
Good luck with whatever you choose!

---

### Post by kennerley on 2010-08-14
> **dmizer said:**
> You can get downloads for any of Windows currently supported products here: [http://www.microsoft.com/windows/downloads/default.aspx](http://www.microsoft.com/windows/downloads/default.aspx)

Ive downloaded windows installer but it is .exe... What can i do to win, arghhh lol

---

### Post by dmizer on 2010-08-14
> **kennerley said:**
> 1. UBUNTU dosent run .exe files... thats a problem for me... i can't download itunes/winrar or anything like that off the internet, why i dont know... i guess thats just ubuntu.

Most things, including unzipping nearly any archive format, can be done by Ubuntu without installing anything off the internet. There's no need for winrar. iTunes is a problem, and if you absolutely need it, then you'll certainly need Windows or run it in a virtual machine as has been suggested earlier.

Obviously with a community the size of the one you've joined here to help you solve your problem, there are plenty of people who use Ubuntu and get by just fine without the programs you need.

Windows doesn't work for everything. Mac doesn't work for everything. Ubuntu doesn't work for everything. However, if you're willing to put forth a bit of effort, any one of them can provide a perfectly satisfactory computing experience.

While you look for your Windows CD, you might try posting something like: > In Windows I used XXX program to do YYY. How can I do YYY in Ubuntu?

This will improve your experience with Ubuntu significantly.

---

### Post by dmizer on 2010-08-14
> **kennerley said:**
> Ive downloaded windows installer but it is .exe... What can i do to win, arghhh lol

Because "Windows installer" is not Windows OS. It's a program that runs in Windows.

---

### Post by kennerley on 2010-08-14
> **dmizer said:**
> Because "Windows installer" is not Windows OS. It's a program that runs in Windows.

 o rite lol.. thanks... ur being a real help for me... i guess ill just find my CD and everything will be fine... if i have any problems along the way i know who to ask :D

---

### Post by dmizer on 2010-08-14
> **kennerley said:**
> i guess ill just find my CD and everything will be fine

Then I will consider this thread's question answered.

Thank you all for participating. :popcorn:

---

