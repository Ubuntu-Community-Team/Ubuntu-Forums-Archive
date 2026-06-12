---
title: "Ubuntu 10.10 will not finish install."
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by HPMSRM on 2010-10-14
[SIZE=4]I am definitely a Linux beginner.  But I'm retiring my desktop from regular use and decided to try Ubuntu and learn what I can about Linux.
     I downloaded version 10.10, 32 bit version from the first page of the web site.  I burned the ISO to a CD at 10X speed.  When I ran the trial from the disc everything seemed to work just fine.  So I elected to go ahead and install it.  Everything seemed to go just fine up to what appears to be the completion of copying files. (not sure)
Then everything comes to a halt and the message right above the progress indicator says "Ready when you are..."   The "Forward" button does not function.  I have absolutely no idea where to go from there.  I've tried the 64 version.  Same story.  I think, unless someone can tell me what to do, I'll just give up.
     I tried Red Hat's Fedora and it installed just fine.  But very little in the way of apps included.  I'd rather have Ubuntu.
     I did a search on here and discovered I'm not the only one with this problem or some variation of it.
     These attempts to install were clean installs...not alongside Windows.
     My desktop is HP with ASUS mother board. 2 gb of DDR and a 200 gb hard drive.  The processor is Athlon  64 x2 - 4400+.  Separate Nvidia (sp?) card with 256 mb of RAM.  Phoenix bios I think but don't remember the version.
     I've spent a lot of hours trying to use this Ubuntu OS.  Some of you have said that version 10.4 installed ok.  Where do I go to download it?
     Any and all help and/or suggestions are very welcome.        Phil
[/SIZE]

---

### Post by krishnandu.sarkar on 2010-10-14
Well the point you got stuck is just end. Just remove the CD and restart your PC, but it should be automated when you press forward, which is not working in your case. So don't worry, just do it manually.

---

### Post by VMC on 2010-10-14
The only time I had problems with the "Forward" not advancing was in the early stages of Maverick.

If you boot up using the livecd and then click on install from there, you can check the installation log files "/var/log/installer" to see if you can make sense out of any of the files in there. If the ubiquity is listed copy that file back here.

Also did you try the method of not using the livecd and going straight to install ubuntu? Try that, if you haven't.

Also do you see any progress when you push the "Forward" button, any hard drive lights going on/off.

There is terminal display near the bottom of the installer that if you click on it will open to a 4-line display. Go to the end to see if any indication as to why it stopped.

---

### Post by HPMSRM on 2010-10-14
> **VMC said:**
> The only time I had problems with the "Forward" not advancing was in the early stages of Maverick.

If you boot up using the livecd and then click on install from there, you can check the installation log files "/var/log/installer" to see if you can make sense out of any of the files in there. If the ubiquity is listed copy that file back here.

Also did you try the method of not using the livecd and going straight to install ubuntu? Try that, if you haven't. [COLOR=Red]I tried both ways.  Didn't help.[/COLOR]

Also do you see any progress when you push the "Forward" button, any hard drive lights going on/off.  [COLOR=Red]No progress, no lights.  Except for being able to move cursor everything seemed frozen.  "Forward" button was grayed out.

I also tried pulling the disc out and restarting the computer.  All I ever got was a blank screen.  Ubuntu did not boot up.
[/COLOR] 
There is terminal display near the bottom of the installer that if you click on it will open to a 4-line display. Go to the end to see if any indication as to why it stopped.

[COLOR=Red]OK...let's see if I can get this right:
    Ubuntu [2867]: debconffilter_done: ubiquity.component install(current): ubi-usersetup

Then everything stops cold.

I found 10.04. Have downloaded it and as soon as I finish here I'm going to go try installing it.

All offered help is really appreciated.     Phil
[/COLOR]

---

### Post by HPMSRM on 2010-10-14
[SIZE=4]OK.  I have version 10.04 installed successfully.  No problem.  Everything went smoothly.

Now why won't 10.10 do that?  Wonder if I do an upgrade to the new one....would the install proceed to the end?

I'm on line now and writing this from the desktop.  Got lots of investigating and experimenting to do to learn the ins and outs.

Phil
[/SIZE]

---

### Post by Tioe on 2010-10-15
Hi,

I have the same problem installing Ubuntu 10.10 Netbook Edition.
I get to the screen where you have to input your name, password etc.
Beneath it, it says: "Ready when you are..." and the "Forward" button does not function.

I'm not able to look at the last lines in the console because i'm limited by my netbook resolution.

Maybe the installation is indeed compleet, but i'm not able to enter it cause GRUB hasn't been set up yet.

---

### Post by Tioe on 2010-10-15
> **Tioe said:**
> Hi,

I have the same problem installing Ubuntu 10.10 Netbook Edition.
I get to the screen where you have to input your name, password etc.
Beneath it, it says: "Ready when you are..." and the "Forward" button does not function.

I'm not able to look at the last lines in the console because i'm limited by my netbook resolution.

Maybe the installation is indeed compleet, but i'm not able to enter it cause GRUB hasn't been set up yet.

=> I just found a workaround

If I wait for the "Ready when you are..." text before going to the screen where you have to enter your name & password, the "Forward" button gets clickable.

---

### Post by kgarbutt on 2010-10-15
I had a case where 10.10 wouldn't recognize the keyboard on a labtop so I wasn't able to finish the installation. It was Ibuypower (Uniwell) 257SA1 labtop. Other than that 10.10 is a hit.

---

### Post by Wp-x on 2010-10-20
@@=> I just found a workaround

If I wait for the "Ready when you are..." text before going to the  screen where you have to enter your name & password, the "Forward"  button gets click-able.
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		 		 		 Seems to make since to me! doing that now,I'm guessing when it was built the (FORWARD BUTTON) highlights ahead of time, and not allowing to complete it's coarse when pressed in advance..Ahey mate?...........Ut ohhh sooo far IT'S NOT WORKING MUTHER #^%%#&*@ lol WTF 
	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=9977345")

---

### Post by Wp-x on 2010-10-21
> **Wp-x said:**
> @@=> I just found a workaround

If I wait for the "Ready when you are..." text before going to the  screen where you have to enter your name & password, the "Forward"  button gets click-able.
                                                                                                  [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                                                Seems to make since to me! doing that now,I'm guessing when it was built the (FORWARD BUTTON) highlights ahead of time, and not allowing to complete it's coarse when pressed in advance..Ahey mate?...........Ut ohhh sooo far IT'S NOT WORKING MUTHER #^%%#&*@ lol WTF 
                                                                [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=9977345")
Ok It's a NEW DAY ! I got nuttin better to do while unemployed anyway lol. After all that reverted back to 10.04 SMOOTH BABY! ...Then I said hummm let's update to 10.10 from there ! DING !:popcorn:.........as time rolls by......DING! all peachy! I reboot ding all peachy! If I remember correctly later asked me to install Nvida drivers ......Meanwhile in my EVIL LAB while rebooting BIONK! now I get stupid black screen asking me to login and use password then I get MONKEY GIBBERISH @#^@%*@*IHAVEYOUNOW-#%^$&*_LUKE-LINUX_WALKER! #$%#%$ -moooohahaha ...Did I mention I also had to install the ndiswrapper also just to get online?:mad: Then I said Son of a B!tC&cha ...Now I said screw it let's try 10.10 again used method above dang it works...Oh what fun.:guitar:

---

### Post by YSP128 on 2010-11-03
Just make sure your username doesn't have uppercase character.

---

### Post by 1stcontact2035 on 2010-11-03
I had the same issue, however I simply turned off the computer and tried again, writing over the original install.  I don't know if that's caused the issues I've posted on these forums about with regards to that install or not.  Basically, I've had shutdown errors and had to turn off the computer manually in shutdown.  I later, after attempting to install NVIDIA drivers, on restart the computer went into some sort of safemode.  Not sure if the shutdown errors happened on that shutdown or not.  I can't be sure.  

I've basically had to stick my Windows hard drive back into this computer to even have a computer because of this.  This was my first Ubuntu install.  I'm hoping to resolve it somehow.

1stcontact2035

---

### Post by warmace on 2011-01-05
> **YSP128 said:**
> Just make sure your username doesn't have uppercase character.


I created an account just to thank you for this fix. :KS:KS:KS

If you type in a username all lower case the forward button becomes enabled, if you add an upper case it vanishes.

---

