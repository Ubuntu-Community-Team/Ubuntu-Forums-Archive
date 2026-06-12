---
title: "Installation Issue with monitor"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by Travatan on 2009-11-16
Im trying to install Ubuntu OS on my desktop PC, and it goes to the language selection screen, then the ubuntu icon screen, then it just goes blank....Ive tried on 2 different monitors with the same result (a 42" LCD TV With PC input, and a simple 14" monitor) On the monitor it gives me the "Attention: Out of Range". After a few it just shuts down the PC and ejects the boot CD. I'm sure this is something retarded on my end. Should I remove my Nvidia card and go with my onboard video on my mobo? Thanks!

---

### Post by CBDSteve on 2009-11-16
Hi - I'm getting the same problem:

I tried installing from the LiveCD, but after choosing Install at the Ubuntu menu and seeing it get a little way into the bootup process, my monitor blacks out with the "Mode out of range" error (just as if I'd chosen a resolution too high from the display settings).

So instead I tried the alternative CD, and installed through the text-only system.  However after it asked me to reboot and continue, I just get the same problem.

I've tried running in Safe Graphics mode, and I've the 'Use Driver CD' option, but in each case it always loses the monitor in the same place.

I can use recovery mode to log in as text-only, and I've trawled some of the forums but nothing has worked so far.  Any suggestions?  I had Ubuntu 8 sucesfully installed on this machine, might try reinstalling that but I'd prefer to have v9!

Thanks

ps - My machine as a P4 3.06 Ghz Packard Bell, the card is an NVidia GeForce 7300 GT.

---

### Post by Travatan on 2009-11-16
I think I have the same graphics card...Id have to check it later. But I know its a Nvidia 7 series card.

---

### Post by Travatan on 2009-11-16
Bump...Where the gurus at :)

---

### Post by Travatan on 2009-11-16
Steve, have you tried using the alternate disc?

---

### Post by stadubu on 2009-11-17
Hi guys
I have the same problem. I had release 8 suc/ly installed in an old laptop - no problems. Now trying to install 9.1 in a desktop, and at the choose language screen, the monitor displays only on the left half of it, and the msg 'out of range' flashes every 2 sec. 
Read some previous posts about similar problems, but I cant seem to be able to stop the installation script choosing a too high resolution for my monitor ("if" that is the problem). 
My monitor now runs windows with 1024x768, and the graphics card if I remember correctly is a 3D Banshee something...

So, lets see what the gurus say.

br/stad

---

### Post by Travatan on 2009-11-18
Ya where are the gurus at??

---

### Post by stadubu on 2009-11-19
anybody out there ?  
c'mon guys, somebody should know something about this...

---

### Post by Paul D on 2009-11-19
Unfortunately, it appears that the gurus all have their installations working and have no reason to visit this forum. They are off playing games and doing more advanced things.
I am not an Ubuntu expert, so I don't get too exited during my blabbing. I do work in electronics and dabble in software writing. I am just trying to help.

So if you start over with the Ubuntu boot disc, you can repeat the process over and over up to the language point you mentioned? I say this to prove that something didn't coincidentally break at that time. But you did mention two monitors.

I assume the disc does the check thing where it validates the contents of the disc before the install?

It might be worth a try using the MOBO video, pending any better ideas. Another MOBO even?

A few years back I tried installing Fedora, I think it was, on a Dell machine, and it didn't seem to like it. But had success with the same discs in a different PC. I never got an explanation for that. I assume that the Dell BIOS didn't like something.

I wonder what the next screen after the language one would be? Perhaps it hangs there?
I recall a screen where it does something with DHCP. I wonder if there is a list of the install screens somewhere? I only think this to try to figure out what might be hanging it up and crashing the install.

---

### Post by CBDSteve on 2009-11-20
Apparently my friend has had the same problem - he gave me the same solution as I've seen floating around on the web (edit the xorg.conf file, see [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Install_Latest_Nvidia.2FATI_drivers) ).

No luck so far - but I'll have another go tonight and post back here.

---

### Post by realzippy on 2009-11-20
@ CBDSteve:


...so you are able to go to root shell via recovery mode.
Do so,type:

**sudo apt-get install envyng-core**

**sudo envyng -t**

Try to let envy (its that famous script by alberto milone) install
the needed nvidia driver.Questions during installation should be answered with "yes"

---

### Post by Travatan on 2009-11-21
How do you type the script if you can't see what your doing?

---

### Post by realzippy on 2009-11-21
In CBDsteve's case he is able to start in recovery mode
(*"I can use recovery mode to log in as text-only"*)
where he could install and run envyng in text mode....

---

### Post by realzippy on 2009-11-21
@Travatan:

Do you have a BIOS option to disable the onboard graphics?
If not,try to (as you suggested) unplug extern graphics card,install with onboard graphics.Then try card again (maybe install nvidiadriver before).

I remember some guy here who had a VIA mainboard,he could only install with onboard graphics.Unfortunately there was no way to make extern card run.

---

### Post by realzippy on 2009-11-21
@Stadubu

Can you plug another monitor to install?
If so,you could manually set refresh rate/resolution to your "old" monitors needs when system is up....

---

### Post by stadubu on 2009-11-30
> **realzippy said:**
> @Stadubu

Can you plug another monitor to install?
If so,you could manually set refresh rate/resolution to your "old" monitors needs when system is up....

Hi realzippy,
thanks for the suggestion: unfortunatelly I dont have another monitor floating around.
I installed version 8.04, to confirm there's nothing wrong with the h/w. And so its ok.
Having 8.04 in, is there something that can be done from here? 
thanks again
stad

---

