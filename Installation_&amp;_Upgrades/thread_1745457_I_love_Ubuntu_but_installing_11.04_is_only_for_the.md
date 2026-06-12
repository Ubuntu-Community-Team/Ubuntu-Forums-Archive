---
title: "I love Ubuntu but installing 11.04 is only for the technically minded"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by gewin on 2011-05-01
Just purchased a new Acer 4750 with Sandybridge and nVidia GT540M, it comes with Windows 7 which works really well (I am surprised). Thought I would install ubuntu 11.04 since it has now reached production. That is where my problems started. I downloaded and burnt a production CD. Booted from CD and installed as per instructions taking the defaults to run alongside Windows 7. All looks good in the install it sets up a partition of approx. 250G and I expect grub to write a boot menu so I can select Windows 7 or Natty. On first reboot it goes directly to Windows 7, no grub??. After much searching I find that grub has probably written to the SD card in the notebook not the correct place. I follow the instructions to reboot on the install CD, do some technical mounting, grub reinstalls and reconfigs/update, then reboot. Now I have the grub boot menu.
Boot natty - I have an external monitor plugged in so when it boots the resolution is all screwed up and the default setting is to mirror displays - there is no ability to change from 1024x768.  Decide to deselect mirror screen and at lease I have some control over the resolution.
Next I am prompted to install a 3rd party driver, there a 2 options one nvidia tested and recommended and the other in beta. I select the recommend one and install it. Reboot to find I have no 3d capability and Unity won't start. I go to Nvidia setting and it says Nvidia not active run some nvidia config program which I do. On reboot I have nothing ie X won't start. Go to recovery mode and uninstall nvidia driver and reboot. At least I am back to where I was.
Now I decided to forget about nvidia drivers and just run the intel graphics. Next I want to set the external monitor as my default display when it is plugged in (basic stuff that easily available in windows). Instead I have to run a number of xrandr command and setup a startup script to make that happen.

Now I want to get sound working through the HDMI -- heaven help me -- it will be a few more days before I have got this setup right.

CAN WE REALLY ASK NON TECHNICAL PEOPLE TO GO THROUGH THIS type of install

---

### Post by Dale61 on 2011-05-01
I now laugh off the changes this upgrade has made.  I also have an Acer (5745G), and when I was running 10.10, everything was working perfectly - wireless, compiz, etc,.  Now, I don't have wireless, but cable (ethernet) works fine, and compiz just doesn't want to know about it, even with the restricted drivers installed (but neither activated nor required - ??WTF!), so I can't even run Unity.  However, FF4 seems to run better than FF3.x (already FF4 has had an update!), but ManDVD is not yet compatible with 11.04.  Unless you want to compile a version of 2ManDVD, which I'm not as there are other important issues to sort out first, you have to use one of the defaults.

This upgrade appears to be just like when the whole kernel was released faulty, and thousands were left with blank screens.  I remember that time and still, to this day, upgrade with trepidation.  It seems my concerns were once again confirmed!

---

### Post by gewin on 2011-05-01
All is not lost 
HDMI sound working OK - just need to select the hardware.
Wireless working OK.
Connection to samba shares working OK.
VLC working fine.
Scared to tackle the Nvidia again but don't want to try xbmc until I have that working.

---

### Post by gewin on 2011-05-01
Frustrated

My HDMI port has now magically changed from HDMI1 to HDMI2 when there is only one HDMI port on the laptop. So now my startup xrandr command to make the external monitor primary does not work. Edited the command to HDMI2 and it worked for a while, but on reboot sometimes the laptop screen becomes primary again - seems to be random. Now xrandr -q shows HDMI2 as active but trying to set it as primary doesn't work. 

Also now reboot shows grub menu on external monitor but if I select ubuntu the startup screen goes blank on both screens, lots of disk activity but nothing happens waited for 10 minutes and gave up. Restarted selecting windows 7 and everything works fine. Need to give Ubuntu 11.04 a rest before I get so frustrated I give up on it.

---

### Post by gewin on 2011-05-03
Slowly getting used to Unity by why the inconsistencies Firefox, Banshee, Nautilus VLC move the file edit ... menus to the top task bar, but Libre Office apps, Synaptic Package Manager,Thunar retain these menus in the application? Very confusing.

Also why do items in the Launcher disappear when I have right clicked on them and selected Keep in Launcher.  They stay for a while seems to randomly disappear.

---

### Post by Quackers on 2011-05-03
The File, Edit.....etc appears in the top bar (I believe it's called Global Menu) only when the window is maximised. Smaller windows keep their controls in their own top bar.
I haven't had problems with right-clicking an icon in the launcher and it then disappearing.

---

### Post by gewin on 2011-05-04
This is not the case for me. The file edit menu goes to the top bar for the application that is selected (ie the one you are working on), this is when it is not fullscreen. But this only happens for 50% of the applications the rest behave in the old way. eg Firefox and nautilus send their menu to the top bar, Synaptic Package manager and LibreOffice apps don't.

---

### Post by gewin on 2011-05-04
Applied the lastest updates today. 

Alas -- Now my solution for dual screens doesn't work properly. I used the command "xrandr --output HDMI2 --primary" on startup to make the external monitor the primary screen ie the launcher bar is on the external monitor. Now this command doesn't send the launcher bar to the external monitor it stays on the notebook screen.

Ideally I would like the notebook screen off when I have the external monitor plugged in, but this seems to be too much to ask.

---

### Post by akand074 on 2011-05-04
> **gewin said:**
> CAN WE REALLY ASK NON TECHNICAL PEOPLE TO GO THROUGH THIS type of install

Generally, the same process is required to install Windows on a system not preinstalled or with hardware not specifically tested on Windows. Installing an OS isn't really trivial for most people. Those who are not technical are generally not the ones to do this (they usually get a technical friend or go to a technician to do it). Hence, not particularly Ubuntu's fault. Matter of fact Ubuntu probably has more user friendly options than any other OS for setting it up, though you can't expect it to run flawless for everyone especially with untested/certified hardware.

---

### Post by gewin on 2011-05-04
Sorry I disagree, I have just complete a 30 PC transition to Windows 7 from XP and have had less trouble with that than installing 11.04 on my Acer. Like I said I really like Ubuntu and have tried to get a number of people converted, but the problems they get into with installs/drivers etc. usually result in them giving up. If this process could be easier I am sure we would have a lot more Ubuntu users. Not getting Dual screen on a laptop working, not supporting Nvidia Optimus hardware or not screwing up an installation because an SD card is installed are examples that just should not happen.

---

### Post by Rasa1111 on 2011-05-04
I actually thought installing 11.04 was the easiest yet!
(and the others are already super easy!)

 I can;t imagine it would take a 'technically minded' person to install this.
Answer a few questions with a few clicks,  and it's installed.
How much easier does it need to get?

---

### Post by akand074 on 2011-05-04
> **gewin said:**
> Sorry I disagree, I have just complete a 30 PC transition to Windows 7 from XP and have had less trouble with that than installing 11.04 on my Acer. Like I said I really like Ubuntu and have tried to get a number of people converted, but the problems they get into with installs/drivers etc. usually result in them giving up. If this process could be easier I am sure we would have a lot more Ubuntu users. Not getting Dual screen on a laptop working, not supporting Nvidia Optimus hardware or not screwing up an installation because an SD card is installed are examples that just should not happen.

You're installing Windows 7 on a system designed for windows XP. It just happens that just about all hardware manufacturers support Windows, hence just about all hardware supports windows. While Ubuntu relies on the open-source community often and even the proprietary drivers don't work well or are more difficult to set up for some hardware. Not really including hardware (but possibly) try installing Windows 7 on a Mac. Try doing it WITHOUT damaging the Mac install using only the Windows disk. Or on a system with only Ubuntu installed without affecting Ubuntu. You'd still have to do manual partitioning (assuming it can read the EXT4 partition) and then you'd still have to reinstall Grub as it'll write over it. Installing using the whole disk and wiping every other OS is just as trivial if not easier in Ubuntu as you just select "use whole disk" while windows assumes you only have Windows installed. Drivers/dual monitors can be more difficult (potentially) in Ubuntu. But that's not so much Ubuntu's fault.

EDIT: Just want to note that you wouldn't have to do manual partitioning to install Ubuntu along side any other OS if you don't want to. Something neither Windows or Mac is capable of doing.

---

### Post by gewin on 2011-05-04
Fine, I understand your perspective, but it is technical, yes this is a very difficult job for developers and the product is basically a good one, I am sure they will fix these issues. I started this thread to document my problems in the hope people would not fall into the same holes or provide escapes. Also to prompt developer to fix the issues.

My perspective is non technical, if we want Ubuntu to succeed and be a viable desktop alternative, it has to play in an environment where windows is installed already. If we can get people to try Ubuntu along side windows first, there is hope. However, if they can't do that easily, the battle will be lost and we will be relegated at a Microsoft/Apple dominated world forever.

---

### Post by uaebuntu on 2011-05-04
I too am struggling with the 10.10 to 11.04 upgrade. Different problems from yours it certainly has not been as easy as previous ones.

The upgrade button in update manager did not work, crashed the system

Networking is a problem

Proprietary nVidia drivers seem to be a problem

Unity does not want to work on my hardware

Fonts are all to pot

FF4 freezes occasionally

Luckily this is not my only machine, when all of the above is fixed I'll upgrade the rest

---

### Post by akand074 on 2011-05-04
> **uaebuntu said:**
> I too am struggling with the 10.10 to 11.04 upgrade. Different problems from yours it certainly has not been as easy as previous ones.

The upgrade button in update manager did not work, crashed the system

Networking is a problem

Proprietary nVidia drivers seem to be a problem

Unity does not want to work on my hardware

Fonts are all to pot

FF4 freezes occasionally

Luckily this is not my only machine, when all of the above is fixed I'll upgrade the rest

Ubuntu has an upgrade option in the Live CD now. I'd definitely recommend that. Though, I'd never recommend an upgrade really, with any OS. There is always the chance of problems and it sometimes feels bloated. I recommend keeping a separate /home partition (or data partition) and do a clean install for best performance/results. It also becomes much less of a hassle in the future.

---

### Post by uaebuntu on 2011-05-05
Thanks, didn't know about the upgrade option from the live CD, but I have various other systems to upgrade when the time is right so will look into it.

I just can't get my network bridge to be recognised by 11.04, but it does work when connected directly to the router. I think this sudden loss of network caused the failure of the on line upgrade.

I have an old nVidia card on my test box, guess I'll have to invest a few bucks at the weekend to get a newer one so the drivers and unity problems go away, Maybe also a new high speed NIC.

I suspect that the GPU is the root cause of the fonts issue, which is very obvious on FF4 but also on some of the utilities and I guess it could be the cause of the FF4 crashes.... so just need to sort out the network and I'll be there.

---

### Post by gewin on 2011-05-05
Still struggling.

The command "xrandr --output HDMI2 --primary" used to move my launcer bar to the external monitor and make that primary now it doesn't, even though "xrandr -q" shows HDMI2 is active. Some applications start to launch in the external monitor ( after setting it primary) then revert to the laptop screen (pretty random behavior).

Also still can't figure out why some applications like firefox when not full screen have their file edit ... menus in the top screen bar but other apps eg Libreoffice don't have the same behavior.

---

### Post by gewin on 2011-05-06
Finally starting to understand what I thought was random behavior isn't. For dual screen notebook with external monitor. I use the startup command xrandr --output HDMI2 --primary to try and force the launcher onto the external monitor. This works sometimes and doesn't other times.

It works if I move the mouse on entering the password on the notebook screen to where the launcher would go on the notebook screen ie success the launcher goes to the external monitor.

If I do not move the mouse on entering the password (leave it in the center of the laptop screen) then the launcher goes to the notebook screen.

Definitely very buggy behavior.

Second funny problem is that you cannot move windows from one screen to the other if you have to go through the launcher. You have to change the position of the screens in the monitor setup.

---

### Post by Quackers on 2011-05-06
So your computer has 2 graphics controller chips. This has been a problem for Linux systems to cope with, which shouldn't really be a surprise to you. I believe some headway has been made but it's not sorted out at this time.
It may be that you need to disable the onboard graphics to get the Nvidia board working in Linux. Some googling may help here.
There are plenty of comments regarding Linux and Sandybridge setups for you to have researched first.
Your grub problem may have been self-inflicted. Did you notice what designation your sd card had? (/dev/sda, /dev/sdb etc) The installer tells you where grub will be installed (at the bottom of the partitioning page) and you can change it yourself. 
Your "problems" regarding the File, Edit .... menu bar and the global menu seem to have been a result of your lack of knowledge on that point.
You make comment about Ubuntu needing to "play in an environment where windows is installed already". I would say that Ubuntu is much better at "playing" in such an environment than Windows is at playing in an environment where other operating systems are installed previously. Try installing Windows after Ubuntu and see what happens to grub!
Finally, for someone who has experienced so many "problems" it would seem much more sensible to me to get one screen working properly before attaching a second.
Just my two cents worth.

---

### Post by gewin on 2011-05-07
Quackers, thanks for your 2 cents. 

Unfortunately you have just confirmed the title of this thread. To say I need to do more research, Ubuntu won't support Sandybridge properly, the install will write grub to an SD card unless you understand what you are doing, problems are a result of my lack of knowledge or I have to disable stuff in the bios are all things that the target audience for this release to expand Ubuntu's market share, don't want to know about.

If Ubuntu/linux is every going to get support from hardware and application developers, then it needs to get onto more desktops. Otherwise its going to go backwards. From my perspective canonical have implemented this release to try and make it easier to use and differentiate it from others with Unity. Canonical want to improve  their penetration on the desktop and take Ubuntu out of the realms of the techo's.

What I am trying to highlight is that their needs to be better support for modern hardware, more attention to the install process(no one would install grub to an SD card), better consistency in the Unity environment both in Dual monitor support and the way the user interface works.

By the way this is not an Nvidia/Intel graphics problem it is a dual monitor support issue.  The inconsistency in the way  the file edit ... menu works is common on the 3 different machines I have tested.

I have been an advocate for open systems and have been working with Ubuntu for many years. Unfortunately my experience with 11.04 is driving me to the darkside (windows 7).

---

### Post by Quackers on 2011-05-07
I'm amazed at how much works "out of the box" with Ubuntu. I personally think hardware coverage is quite good.
In all fairness, Sandybridge is quite new, as is dual graphics controllers. You need to realise that your setup is not a "standard" one (although it is becoming more and more common, it's true). In these circumstances the user should make enquires before any installation is made in an attempt to make sure that things will go well - or not.
It may also be reasonable to take into account the fact that the developers have just spent several months building and finalising the unity interface for the launch of 11.04. 
It is unlikely that all hardware types will be supported at any one time. There are just too many, and more appearing all the time.

As for the "inconsistencies" with the File, Edit etc menu, I'm just not seeing any (or possibly just not noticing them, perhaps you could explain those further). The active window has the use of the global menu whether it's shown at the time or not. If it doesn't appear, it will do so with a mouse-over.

---

### Post by mikewhatever on 2011-05-07
> **gewin said:**
> ...
What I am trying to highlight is that their needs to be better support for model hardware, more attention to the install process(no one would install grub to an SD card), better consistency in the Unity environment both in Dual monitor support and the way the user interface works.

...

You are quite right, a moderate amount of technical knowledge is required for installing an operating system (any operating system), but most of the problems you've mentioned seem unrelated to the installation process. Keep in mind that Ubuntu is not the perfect OS that dusts and vacuums. It's a work in progress, and if you think you found a bug, file a bug report.
Last, but not least, please don't pile numerous and unrelated problems into one thread, as answering such threads is a mild nightmare.

---

### Post by gewin on 2011-05-07
Don't get me wrong I really respect the work that the developers have done for this product. I am pointing out (maybe a little too aggressively ) where I thing they need to focus to get to their goal. Support of dual screens, SandyBridge & Nvidia has to be a priority. 

I have found that you can get support for Libreoffice using the global menu by adding another app.
[http://www.howtogeek.com/news/add-global-menu-support-to-libreoffice-in-ubuntu-11-04-unity/4212/](http://www.howtogeek.com/news/add-global-menu-support-to-libreoffice-in-ubuntu-11-04-unity/4212/)

Libreoffice is not the only product that doesn't support this feature.

My point is out of the box, it is confusing for the user.

---

### Post by Quackers on 2011-05-07
I think it's likely that Sandybridge is being worked on as we speak :-)
I suspect that any problems with Nvidia drivers are more to do with Nvidia than the Ubuntu developers (with the odd exception).
I have had very few problems with Nvidia drivers. I actually think they are very well supported. I do appreciate, however, that others have not been so lucky and that a small number of people continue to have problems in this area. Nvidia seem to update drivers fairly frequently so lets hope that these problems can be solved soon.
Your dual screen problem could possibly be related to the graphics problem.
Thanks for the Libreoffice help link :-)  Yes, some screens keep their own menu bar.
Good luck with your system :-)

---

### Post by Rasa1111 on 2011-05-09
> Unfortunately you have just confirmed the title of this thread. No it doesn't.
This thread has an improper title anyway. 

"Installing 11.04" is actually a piece of cake.
Getting it to work on YOUR system, apparently is not. 

So your title is very misleading and just adds to the needless F.U.D. surrounding the Linux community.
Noobs will see your title and automatically think "Ohh that's going to be too hard to install, forget it"..
when the simple fact is that an install is a matter of a few clicks and a few keys, that even a child could follow. 

Spreading FUD is not cool.

---

### Post by gewin on 2011-05-11
Fine  I will close this thread, obviously Ubuntu 11.04 is easy to install and everyone that has posted problems on this forum is mistaken, they should not have problems with installing Ubuntu, it is just there incompetence or that they are using modern hardware.

Ubuntu installation does support SandyBridge, Nvidia, mounted SDcards on install, Dual screen etc. etc. and you don't have to be technical to get them to work. Maybe I should have asked a child to do it.

---

### Post by Rasa1111 on 2011-05-11
No, 
Installing it is easy. 
Configuring it for *your* system (or those who have problems) is "not for the technically minded".

But how is that different than any other Ubuntu, or Linux distro?
It isn't. 
Those who are not "technically minded" always have and always will have difficulty when running into any number of problems that may arise when installing _*any*_ OS. 

11.04 is just as easy to "Install" as 10.10 or 10.04. 
There is no difference in their "ease of install'.

Incompatible hardware has always been a problem.
This is not something new in 11.04. 

This is why I said your title is misleading. 
Is *installing* 10.04 only for the "tech. minded"? 
How about 10.10?
They are no different to *Install* than 11.04 is. 

Configuring and Getting things to work on specific , possibly unsupported hardware..
is another story, but the same old story.  Nothing new. 

But that is not "*Installing*". 

Twisting and playing with words is not real great with this kind of thing, and only causes more confusion and "f.u.d.", Maybe it's due to your own confusion, I don't know. 

Yes I saw that poll, and I also saw how many had no problems with it. 
I believe it was the majority. 
Again, same with any other version.

---

### Post by Dale61 on 2011-05-11
The problem I have is that with 10.10, I had everything I needed working as it should, and configured to best suit me.  Since 11.04, I had to find a work-around to get the wireless side of things working again, compiz no longer does what it did even though I have everything ticked as it was in 10.10, the DVD tray still doesn't open when I press the button (I have to open a terminal and type 'eject' just to access the tray), just to name three things that should not have been so majorly affected from 10.10 to 11.04.

However, I do agree that installing any of the Ubuntu flavours is a relatively easy process, just the setting up to suit the end user is time consuming.

---

### Post by gewin on 2011-05-11
OK I think we are playing with word definitions here. I regard installation as running the CD install (I agree this is easy), then making the system workable for the user or hardware (often difficult).

Bottom line, if Canonical want to get Ubuntu onto 200 million PCs which is their goal. This whole process is going to have to work better.  I want Ubuntu to succeed as well as others on this forum, but if we sit back and say it works like a dream when it doesn't, we won't move forward.

---

### Post by uaebuntu on 2011-05-11
I was one of those having problems to the extent it didn't work. I had two problems the most obvious being the fact I used an old nVidia MX440 GPU, there was no warning that there were nVidia problems.

The other was a weird networking one. I reverted to 10.10. then I bought a new Graphics card, still nVidia and a new Gigabit NIC.

11.04 installed clean OK and I'm loving it so far, still got lots to do but basically its great, now I've got there.

A little warning, and it was not obvious in the release notes that I would have a total screw up, and I would have fixed it in advance and been OK and happy. After all M$ happily trash your hardware on a regular basis with updates and new releases so I'm not against the idea. 

This is the first time since 8.04 I've had a problem, and it could have been avoided, especially as this was a significant release.:o

---

### Post by Dale61 on 2011-05-11
My first major drama with Ubuntu was when the faulty kernel upgrade was released, and I downloaded it.  A complete system failure ensued, so any fault since has been child's play (no, not the Chucky variety!).

---

