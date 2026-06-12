---
title: "trouble upgrading to Ubuntu 11.04, don't have the right hardware?"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by bill23 on 2011-09-24
**trouble upgrading to Ubuntu 11.04, don't have the right hardware?** 			 			 			 		 		  		  		[FONT=Book Antiqua][SIZE=2][COLOR=Navy]I  presently have Ubuntu 10.10 having upgraded from 10.04 a few weeks ago.  This is not the first time i have upgrade between these two but that is  a story for another post. i have attempted to upgrade to Ubuntu 11.04  each time it end in disaster. My PC is an old Gateway Profile all in  one. The last times  tried to upgrade I went through the Synaptic  Packager Manager and let it go through its routine. When it was through  it told me that 11.04 had been successfully installed on my PC. However  no sooner had i closed out of SPM when i was greeted with a message  about changing from Classic to and here I forget what the other choice  was, in any case i did not know where to look to change or keep what I  had. That in and of itself would not have been so bad, but for my not  being able to open anything. I would place the cursor on the Firefox  icon and click. instead of it coming up there would be a millisecond of  lights and I could see the Firefox browser then it was gone. I tried  again an the result was the same. A brief flash then a black screen.  This would happen with every icon i had.
I could not even reboot it, for even that was but a brief illumination  then gone before I could click anything. In the end i had to shut down  the Computer by the power button. I restarted hoping this would fix  whatever was the matter? It did not. It was then i remembered the last  time before this when i tried to upgrade and saw something about not  having the proper hardware? It was something like that unfortunately i  can not give the exact wording. The only way to find it would be for me  to go through the installation process again, which is something I will  not do until this mystery is solved. 
I had a Ubuntu which I could not access in effect a useless PC. I had  and still have the Ubuntu Cd disc for 10.04 which i had used to install  Ubuntu over a year ago. i used it to write over the 11.04. Since then i  have successfully upgraded through the Synaptic Package Manager to what I  have at present the Ubuntu 10.10. I would like to upgrade to 11.04 but i  don't want to end up where i was before? had anyone heard of an upgrade  being hindered or in some manner caused to go awry because of the PC  not having the 'right' or correct hardware? This is what my PC had: 
Gateway Profile 5S, Celeron 2.6 Ghz, 1GB RAM, 160 GB HD
Can someone enlighten me as to what hardware I might be missing and why  when i have had no trouble upgrading from my earliest Ubuntu a 9.04  through my present 10.10? Is it because of the age of my PC or is it  something that this 11.04 has thrown in to give me grief? i am being  sarcastic about the giving me grief line,  almost [IMG]http://static.linuxquestions.org/questions/images/smilies/smile.gif[/IMG]  Has anyone heard of someone else having a similar problem? Did they  find a solution or did they like me rewrite over the offensive one? Hope  someone can point me in a direction for an answer?

I found this in an old notebook it may be of some help: 
"The configuration default Gnome Power Management has not been installed correctly. Please contact your computer administrator?"

bill23
[/COLOR][/SIZE][/FONT]

---

### Post by Paddy Landau on 2011-09-24
Download 11.04 and burn a CD.

Boot from the CD and try Ubuntu without installing. If it works, Install 11.04 instead of going through an upgrade process.

If it doesn't work, wait for 12.04, which will be the next LTS. Rather stick with what works than with what doesn't (10.04 was the last LTS).

---

### Post by bill23 on 2011-09-26
[COLOR=Blue][SIZE=3][FONT=Book Antiqua]Paddy Landau,

Thanks for the suggestion. I am not all that familiar with burning CD's. Could you give me an  idea of what I may need besides a blank usable CD to accomplish this burn? As I am not all that proficient with stuff like this, if you could give me or direct me to a guide which in simple terminology will tell me what step I should take?
TIA
bil23
[/FONT][/SIZE][/COLOR]

---

### Post by Paddy Landau on 2011-09-26
You can burn a CD or create a USB if your computer supports USB's. (A USB will be faster than a CD.) If you use a USB, you need one at least 2Gb large.

First, get the Ubuntu iso.


[LIST=1]
[*]Go to the [Ubuntu home page]("http://www.ubuntu.com/").
[*]Select [Get Ubuntu]("http://www.ubuntu.com/download").
[*]Select [Download and install]("http://www.ubuntu.com/download").
[*]Under section 1 (*Download Ubuntu*), in "Download options", select either 10.04 (if you want the LTS version) or 11.04 (if you want the up-to-date version). Select 10.04 LTS if stability is your greatest desire, or 11.04 if you prefer cutting-edge.
[*]Select 32-bit unless you specifically want 64-bit (your computer would need to support 64-bit if you choose the latter).
[*]Press _Start download_ to start the download and save it to your computer.
[/LIST]

Now, create the CD or USB.


[LIST=1]
[*]Scroll down to section 2 (*Burn your CD or create a USB drive*).
[*]Select CD if you are burning a CD, or USB stick if you are using a USB stick.
[*]Select Windows if you are currently on Windows, Mac if you are currently on Mac, or Linux if you are currently on Ubuntu.
[*]Press _Show me how_.
[*]Scroll down and read the instructions.
[*]Post back here if you have any problems.
[/LIST]

Finally, try it.


[LIST=1]
[*]Scroll down to section 3 (*Try it!*).
[*]Press _Show me how_.
[*]Read the instructions.
[*]Reboot your computer and be sure to boot from your CD or USB.
[*]Post back here if you have any problems.
[/LIST]

---

### Post by MAFoElffen on 2011-09-26
> **bill23 said:**
> **trouble upgrading to Ubuntu 11.04, don't have the right hardware?** [FONT=Book Antiqua][SIZE=2][COLOR=Navy]
Gateway Profile 5S, Celeron 2.6 Ghz, 1GB RAM, 160 GB HD

I found this in an old notebook it may be of some help: 
[/COLOR][/SIZE][/FONT]
Does your 5S have the GeForce FX 5200 or the Integrated Intel® Extreme Graphics2 GPU?

Both GPU's will not run Unity 3D. both will run Unity 2D (would have to install) and Ubuntu Classic (Gnome 2).

Does the GDM screen load at boot asking for the user and password?  If so > click on the user > when the password dialog pops up, look at the bottom screen bar and find a pulldown box :that probly says "Ubuntu". Click on it and select "Ubuntu Classic" > enter password and start up > should bring up the Gnome 2 panels.

Did gnome come up and does your pointing device in X work correctly?

If not, with a successful X-Session, but mouse action failing in X and affecting X... I'd need to know which GPU you have and What it might say in you xorg.conf (which also has what "input" driver are being used in X or if hal or other PNP utils look for it).

What info would be handy for this would be 
```

lspci -nn | grep VGA

```
And post "/var/log/Xorg.0.log" and "/etc/X11/xorg.conf".  The lxorg og I need to see is one that was created while you were booting into and had the problem.  The Xorg.0.log would be current, with 1, 2, 3, 4 and 5 being previous logs. in that order.

If you can't succesffuly get to a text console, boot from HDD, shutdown and post from a LiveCD.

Burning a LiveCD?  Download your ISO image.  Start Brasero. Pick ISO as source, Blank disk as Target > Options > Burn at slowest speed of your drive.

---

### Post by rob45 on 2011-09-26
hi its just telling you to use log in screen available in system/admin,to choose ubuntu classic rather than ubuntu...thats all...then once your vid drivers are updated maybe you will be able to use ubuntu log in.

---

### Post by MAFoElffen on 2011-09-26
> **rob45 said:**
> hi its just telling you to use log in screen available in system/admin,to choose ubuntu classic rather than ubuntu...thats all...then once your vid drivers are updated maybe you will be able to use ubuntu log in.
Actually-- Since 11.04, using the instruction above, that capability is added to the login screen... and it remembers the last option your choose from there.

---

