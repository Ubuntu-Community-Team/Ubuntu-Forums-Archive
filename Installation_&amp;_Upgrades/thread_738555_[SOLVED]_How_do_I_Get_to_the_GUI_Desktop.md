---
title: "[SOLVED] How do I Get to the GUI Desktop?"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by ElkHoundHawk on 2008-03-28
I am trying to get to the **GUI desktop** of Ubuntu Studio. 

When the Ubuntu Studio DVD booted up it provided the following **Installation choices**:

	Install in text mode

	OEM install (for manufacturers)

	Check CD for defects

	Rescue a broken system

	Memory test

	Boot from the first hard disk	

I chose **Install in text mode**. That worked for me with the Ubuntu 7.10 CD.

When I **boot **into Ubuntu Studio from the **hard disk** I get a black DOS like screen with a **command **interface and **prompts**. First it says “Boot Menu: Ubuntu 7.10, kernel 2.6.22-14-rt.”

Next I get the following promts. 

	1. ubuntuComputerName login: _
	2. Password: _ 
	3. UserName@ubuntuComputerName:~$ _ Now What

All of the commands work but I want to get to the **GUI desktop** and use **video and audio editing **programs like Kino. How do I do this?

Thanks for your help.

ElkHoundHawk

---

### Post by upthelum on 2008-03-28
Try startx.

---

### Post by talsemgeest on 2008-03-28
When you installed you get choices about what to install. Stuff like audio editing tools, video production, and most importantly, ubuntu studio desktop.

You choose these using the up and down keys and spacebar to select the ones to install.

I am guessing you didn't install the desktop, because that is what happened to me the first time I installed it.

I would suggest reinstalling with the desktop enabled, but if you just can't be bothered, you can type this: ```
sudo apt-get install ubuntustudio-desktop
```

Good luck!

---

### Post by Sef on 2008-03-28
> sudo apt-get install ubuntustudio-desktop

First you should update the repositories:

```
sudo apt-get update
```

then type in the code in the quote.

---

### Post by ElkHoundHawk on 2008-03-29
**Everything Works!!!**   I'm using it now!!!

It took (**sudo apt-get update**) and (**sudo apt-get install ubuntustudio-desktop**). 

(sudo apt-get update) did not work properly until today. Is that because there is less internet traffic?

**Thanks** Upthelum, Talsemgeest, Sef, and anyone else that I may have overlooked.!

ElkHoundHawk

---

### Post by Aiden327 on 2008-03-29
Hi, I am haveing a similar problem. 

Yesterday I downloaded ubuntu studio. The package was intact when I put it on the cd. After 3 attepts to install I finally got through without errors. No matter how many times iv'e tried this i cannot get any software packages to install. I just get a red screen. I chose to finish the install scince I gave up reformatting and now it boots into text mode. I have tried the Sudo apt-get install ubuntustudio-desktop. That gives me an E: Broken packages error. 

The computer is an old Optiplex server, it has a riva tnt2, and has a hard time finding my dvd drives in the bios (ive tried 3-4 with difrent jumper settings). Every 3 times I power on does the drive work lol.

Is there anyway for me to get to the gui and install the packages or am I stuck? I don't know to much about linux btw. :confused:


Sorry if I was sopposed to make a new thread.

Thanks.
Aiden

---

### Post by upthelum on 2008-03-29
Have you un-commented sources.list?

---

### Post by Aiden327 on 2008-03-29
what does that mean lol 


very sry, im not used to linux at all ](*,).

---

### Post by upthelum on 2008-03-29
Ok can you use terminal?

---

### Post by Aiden327 on 2008-03-29
yes, but not very well....

---

