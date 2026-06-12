---
title: "Messed up screen/graphics..."
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by hh511jas on 2011-03-16
[FONT=Tahoma][SIZE=2]I'm a Windows Vista user but I decided to try Ubuntu 10.10 for the first time, I installed it using Wubi (duel boot), finished installing and rebooted. Once Ubuntu started, the screen and graphics were messed up. I notice it was too big, a lot of lines a lot of distortion etc. Once it finished installing, it rebooted and went to the Ubuntu log on [/SIZE][/FONT][FONT=Tahoma][SIZE=2]screen and it was severely distorted too. Maybe it has to do with my system not meeting the requirements, the following are my system specs:

**32-bit HP Pavilion dv6500 Notebook**[/SIZE][/FONT] [B][FONT=Tahoma][SIZE=2]

Processor:     AMD Anthlon(tm) 64 X2 Mobile TK55[/SIZE][/FONT][FONT=Tahoma][SIZE=2]

Graphic Card:  NVIDIA GeForce 7150/ nForce630M[/SIZE][/FONT][FONT=Tahoma][SIZE=2]

X86 Based PC[/SIZE][/FONT][FONT=Tahoma][SIZE=2]

1.80GHz[/SIZE][/FONT][FONT=Tahoma][SIZE=2]

1GB RAM[/SIZE][/FONT][FONT=Tahoma][SIZE=2]

140 GB of in my C Drive[/SIZE][/FONT][FONT=Tahoma][SIZE=2]
117GB of free space

Monitor Resolution 1200 by 800 pixels[/SIZE][/FONT][/B]       [FONT=Tahoma][SIZE=2]

I'm pretty sure it meets the requirements but just in case.[/SIZE][/FONT] [FONT=Tahoma][SIZE=2]
Can somebody please give me a solution because I'm unable to do anything in Ubuntu with the messed of graphics. Thank you...[/SIZE][/FONT]

---

### Post by nxpx on 2011-03-16
I think what you mention is the same problem I had when I first installed Ubuntu a month ago.

What fixed it for me was enabling Nvidia drivers.

Try go "System" -> "Administration" -> "Additional Drivers" and enable Nvidia drivers, then restart.

---

### Post by hh511jas on 2011-03-16
Can you tell where that is since Im completely new to Ubuntu and the screen is to messed up, any hot keys to open that up?

---

### Post by nxpx on 2011-03-16
If it is that messed up, I am not sure anymore, if its the same problem as I had.

try open a terminal with shortcut keys ctrl + alt + t and type in /usr/bin/jockey-gtk

Should bring it up the window I am talking about.

---

### Post by hh511jas on 2011-03-16
[SIZE=2][FONT=Tahoma]Hello again, it doesn't work. It says 

"*Downloading*[/FONT][/SIZE]* package indexes failed, please check your network status. Most drivers will not be available*"

[SIZE=2][FONT=Tahoma]I'm not connected to the internet in Ubuntu, that's another problem...
Anything else I can do?
[/FONT][/SIZE]

---

### Post by nxpx on 2011-03-17
As far as i can see from a quick Google search the drivers for the  Realtek RTL8101 network card is built in to the system.

Are you using cable or wireless?

You can check what network controller you have with this command:
*lspci | grep Eth*

I think you can check if the driver is loaded with this command:

*dmesg | grep Eth*

Check IP configuration with

*ifconfig*


Sorry im not much help, I only started using Ubuntu a month ago, hopefully somebody else can chip in with some ideas.

Thanks

---

### Post by hh511jas on 2011-03-21
[FONT="Tahoma"][SIZE="2"]It's alright, still apreciate the adive thanks. I posted a new thread, here it is link... [http://ubuntuforums.org/showthread.php?t=1709227](http://ubuntuforums.org/showthread.php?t=1709227)[/SIZE][/FONT]

---

### Post by hh511jas on 2011-03-22
[FONT="Tahoma"][SIZE="2"]Yes it's fixed. First I connected the internet (wired connection), then I went to terminal and put ```
aptitude show nvidia-glx-180
``` It showed me that I have two options which I can install (don't remember it), I chose one and put the install code that it gave me, installed, then I went to additional drivers and there was nvidia and my wireless broadcom. Updated then restarted and I got my graphics and wireless.:P[/SIZE][/FONT]

---

