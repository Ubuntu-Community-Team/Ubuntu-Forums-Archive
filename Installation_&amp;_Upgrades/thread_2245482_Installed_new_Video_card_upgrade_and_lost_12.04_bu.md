---
title: "Installed new Video card upgrade and lost 12.04 but Win 7 runs fine"
date: 2014-09-23
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2014-09-23
Wanted to upgrade the Video card on the Dell i7 in signature below that is almost 5 years old and dual boots with Windows7 and 12.04 and still runs excellent.
Believe I screwed up and was wondering what is needed to get 12.04 running again.

The Dell i7 has two drives. W7 is on a 1TB HDD and 12.04 was on a 128GB SSD. They both used to run excellent. When upgrading to new vid card I followed NVIDIA instructions but disconnected the SSD thinking it would be helpful....here's where I think I messed up. Anyhow the upgrade went fine using NVIDIA CD & instructions. Got and installed the needed vid driver and all went well and W7 runs better than ever but 12.04 won't boot anymore. 

Not knowing what to do, decided to install 14.04 on the SSD. Did a dual boot on SSD. Split SSD in half with 12.04 and 14.04 because I really liked 12.04 which ran like a charm and didn't want to lose files on 12.04. 14.04 installed and now both W7 and 14.04 can run but 12.04 is still there but won't run! I can go into 12.04 and save anything needed but was wondering if it can get up & running again as a triple boot setup?




FWIW have been using 14.04 awhile on my laptop in signature below and am not overly impressed with it. 12.04 was Rock Solid!  While 14.04 doesn't seem as stable, it froze and locked up a couple times so far. 14.04 is a little bit different but not hard to figure out the changes made. So figured it was time to install 14.04 on the i7 to see if it ran better. So far the results have been mixed for me. Like some of the 14.04 changes, just wish it was more stable like 12.04 was.

---

### Post by Dreamer Fithp Apprentice on 2014-09-24
12.04 won't boot at all? Or just won't start X, leaving you with a command prompt on a tty, kind like a terminal that fills the whole screen? Is there an error message? Do you get a grub option to boot 12.04 when you start up? If so, exactly what appears on the screen after you select it? I'm not sure I'll be able to help (or even how soon I'll be back by this way) but anybody who can help is probably going to want to know these things so you'll likely get a useful answer sooner if you post this kind of information. In general the more detailed specefic info you post, the more likely you are to get a useful reply sooner.

---

### Post by cybrsaylr on 2014-09-24
12.04 won't boot or start, leaving me with a black/purpleish type terminal screen filling the whole screen.

On restart the GNU GRUB 2.02 beta 2 boot loader comes up with the regular options listed below:

*Ubuntu
 Advanced options for Ubuntu
 Memory test
 Memory test (counsel something)
 Ubuntu 12.04 LTS
 Advanced options for Ubuntu 12.04 LTS
 Windows 7



When 'Ubuntu 12.04 LTS' is selected, the tty full terminal like screen with blinking white cursor come up and stays that way with nothing further happening.... endlessly.
When 'Advanced options for Ubuntu 12.04' is selected, the tty full terminal like screen with blinking white cursor come up asking for 'login' and password. Not sure what to put in for login and when I put in my password, it keeps kicking it out saying it is the wrong password and doesn't start 12.04


*Ubuntu when selected starts up 14.04 normally.
Windows 7 when selected starts up W7 normally.

---

### Post by cybrsaylr on 2014-09-25
Anyone have any ideas to help here?

---

### Post by Dreamer Fithp Apprentice on 2014-09-27
> **cybrsaylr said:**
> When 'Advanced options for Ubuntu 12.04' is  selected, the tty full terminal like screen with blinking white cursor  come up asking for 'login' and password. Not sure what to put in for  login and when I put in my password, it keeps kicking it out saying it  is the wrong password and doesn't start 12.04That's a misleading error message. It's saying that because you didn't enter your user name where it asked for login.

When it ask for login type in your user name and press enter. Then it should ask for your password. Type that in and press enter. It can be tricky since it doesn't echo the key entries as asterisks like some password dialogues do. I also have the impression that my keyboard is flakier in a tty like that than it is in some X11 application, seeming to type two characters when I meant to type 1 a lot more often than it does in a graphical environment. The point is you may have to try carefully several times. Be careful to notice when it's asking for login (your user name) and when it is asking for password. Hopefully eventually it will let you log in. At that point, hopefully, you'll have a prompt, which if you haven't modified it, should look something like:
username@machinename:~$
If you get that, try typing
startx
and then press enter.
It may tell you something indicating you don't have something installed that you need for startx. If so, install whatever it ask for with
sudo apt-get install whatever-package-name-you-need
and try
startx
again after that is installed. It may or may not work, and if it does it still hasn't solved the problem, but if it does work, you'll get a normal graphical environment, with which might make it easier to figure out the problem.

---

### Post by cybrsaylr on 2014-09-27
Dreamer Fithp Apprentice tried what you suggested and got into Advanced options for Ubuntu 12.04.
Normal would not work at all, however got in, in 'recovery section' of advanced options for Ubuntu 12.04.
Put in name & password several times before it let me in getting:  username@machinename:~$

Type in: 
startx
hit enter and get a whole page of teminal text that basically say this:

> Fatal sever error
No screens found

server terminated with error (1). Error log file

several seconds later this pops up:

> xinit: giving up
xinit: unable to connect to X server no such file or directory
xinit: server error

Got some terminal 'help options'
One said it would attempt to repair problems.
Ran that, it did its thing looking like it was repairing things, then said to resume normal boot. Did that to the same results above popping up again.

End result 12.04 still will not start.....

---

### Post by Dreamer Fithp Apprentice on 2014-09-27
Could be X is hosed. Might just be your graphics driver. Let's try getting rid of the NVIDIA driver. Maybe the default driver is still installed and will take over. Get into a command line enviroment on the 12.04 like you did above and try this:```
sudo apt-get purge nvidia*
```Again, it may take several tries to get it to take your password. That seems to be a shortcoming of the tty I never have figured out. Apparently after X gets going something kicks in that interprets keystrokes more consistently. Make a note of anything that looks like an errror message. Then, after crossing fingers, do this to reboot:```
sudo shutdown -r now
```If it doesn't work make careful note of error messages.

---

### Post by oldfred on 2014-09-27
Did you have nVidia before you installed new card? What model new card?
If you did not have nVidia before you may not have the correct driver. Always best to uninstall all video drives before changing video cards and then install new correct drivers. 
But in the past I was able to update from an old nVidia to a newer nVidia and system just worked.

It may be just like any new install to a system with nVidia card. I have that and have to use nomodeset until I do install the nvidia driver from the repository. I prefer to install from system settings, but a nomodeset boot puts me in low quality graphics and sometime entire screen is not shown.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by cybrsaylr on 2014-09-27
> **Dreamer Fithp Apprentice said:**
> Could be X is hosed. Might just be your graphics driver. Let's try getting rid of the NVIDIA driver. Maybe the default driver is still installed and will take over.
Question? If this is done will it mess up Windows 7?



NVIDIA GeForce GTS240 was the OEM card on this i7 desktop.
NVIDIA GeForce GT 630 was the upgrade card just installed.

Did complete graphics card installation using Windows 7, after disconnecting the SSD which had 12.04 LTS on it.
All went well following NVIDIA instructions and using their CD to install the new graphics card driver.
On completion W7 ran OK, in fact better than before.

Then I reconnected the SSD with 12.04 then tried to reboot and 12.04 refused to start.

At this point I installed 14.04 LTS on that SSD as a dual boot by splitting that SSD in half with 12.04 and 14.04 on it.
After this W7 and 14.04 both run but 12.04 which is still there and shown on the GRUB boot-loader refuses to start.

---

### Post by Vladlenin5000 on 2014-09-28
Please follow the instructions of post #8 to add nomodeset. Then login and install the correct drivers for your new card. What you've been experiencing is the typical result of trying to boot with an older nvidia's driver version (which was good for the old card). You should also purge any drivers before installing new ones as mentioned in post #7.

And no, anything you do in Ubuntu won't impact your W7, obviously.

---

### Post by Dreamer Fithp Apprentice on 2014-09-28
> **cybrsaylr said:**
> Question? If this is done will it mess up Windows 7?No. Each bootable system on the machine has its own seperate drivers installed, normally in the "/" partition. Windows probably calls its "/" something else, I forget what, but the principle is the same. I suppose in theory it is possible to set up a multiboot system otherwise, but I've never heard of it being done. Possibly if you had the Ubuntu system connected, your Nvidia software might have updated the driver in it when it did so with your Windows (one could hope), but since it wasn't connected it didn't have a chance. So 12.04 is trying to use the old driver. Generally though, it is probably safer to use the drivers in the repository. If it were me, for 12.04, I'd just install the metapackage "nvidia-current" and let it keep you up to date automatically. That's assuming 12.04 is still supported to the extent of HAVING a repository, I don't actually know it that's true off hand.> **Vladlenin5000 said:**
> Then login and install the correct drivers for your  new card.
Just to make that explicit I believe what Vlad has  in mind is to type in```
sudo apt-get install nvidia-current
```  and press enter. It will ask for your password. Type that in and press  enter again. Vlad, please correct me if I'm mistaken.
> **Vladlenin5000 said:**
> And no, anything you do in Ubuntu won't  impact your W7, obviously.Once upon a time a mathematician was  lecturing to class of graduate students with numerous scribblings on the  chalkboard. Said the Prof, "From equation 7 it is obvious that . . ."  whereupon he stopped, chalk hand frozen in the air, with an abstracted  look on face. "Wait a minute," he said and sat down at his desk and  began to write on a legal pad. Every few minutes he would stare into  space for a few seconds and then scribble some more, covering page after  page. Almost the whole hour was gone by when he grinned and jumped to  his feet, chalk in hand, and turned to the blackboard, saying "Yes, I  was right! From equation 7 it IS obvious that . . ." :)

---

### Post by cybrsaylr on 2014-09-29
SUCCESS!!!!! Thanks guys, I now have a fully functioning Triple boot system!!!
Win7, 12.04 and 14.04 all show up on boot loader and start/run when selected.

Dreamer Fithp Apprentice, I did what you suggested when getting into Advanced options for Ubuntu 12.04. 

code:
> sudo apt-get purge nvidia*

Then code:> sudo apt-get install nvidia-current

Let terminal do its thing, then reboot with:> sudo shutdown -r now

And 12.04 started up as in the past.....using it now.

Am sort of weak on command line, terminal stuff. In fact didn't use DOS at all until learning how to use it with help from our Ubuntu Forums here. Thanks guys but that said don't use CL that often....so it took a bit to get refreshed on what to do in this case.


There were a couple reasons for wanting to get back into 12.04:
12.04 after using it again still appears/runs more rock solid than 14.04 IMHO.
Had lots of programs/apps installed to 12.04 that I liked.
Had 100s of bookmarks in the 12.04 browsers I used that I couldn't remember all of them and now they are all there again to be copied to 14.04....lol

Again thanks for the help guys.....):P



PS: FWIW after running 12.04 for over an hour now, I can confirm that 12.04 definitely runs snappier and loads pages FASTER than 14.04 does ....at least on my rig.

---

