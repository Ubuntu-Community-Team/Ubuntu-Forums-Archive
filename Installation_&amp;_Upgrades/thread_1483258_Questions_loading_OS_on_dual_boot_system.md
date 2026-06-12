---
title: "Questions loading OS on dual boot system"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by gauchotodd on 2010-05-14
I recently installed ubuntu 10 on my Win7 machine, and am wondering why it loads soooooo slowly when powering on.  I have both OS's on an OCZ Vertex SSD, and Win7 loads in 10 seconds flat, whereas ubuntu takes a solid minute, possibly longer, to get to the desktop.  When I select ubuntu, it stays on the black screen with the cursor for about ten seconds or so before starting to load.  Is this normal/is there a way to make this faster?

Also, since Win7 is the default OS, I would like to switch that to ubuntu so if I push power I don't have to manually change it.  Is this done in BIOS?  I'm really new to this still.

Thanks in advance; let me know if you need more information from me!

---

### Post by darkod on 2010-05-14
Do you have a HDD too or only the SSD? I don't know why yet, but on my computer (with HDD) 10.04 does the same thing with sitting a bit with the cursor on screen, and then once it starts to actually load it does it fast.

For selecting ubuntu as default in grub menu, boot ubuntu and open:

sudo gedit /etc/default/grub

if ubuntu is on the top of your grub menu, in the line GRUB_DEFAULT=n, make the value 0. It starts counting them from 0, top to bottom. Save and close the file.

To update the grub.cfg file after that run:

sudo update-grub

---

### Post by oldfred on 2010-05-14
You can check the logs to see if something is giving warning messages or repeatedly trying to load something and then timing out.

system, administration, log file viewer
there are a lot of logs try dmesg, kern.log or messages 
It does not hurt to look at everything.
I look for obvious errors first, then for long time differences between entires.

---

### Post by darkod on 2010-05-14
> **oldfred said:**
> You can check the logs to see if something is giving warning messages or repeatedly trying to load something and then timing out.


I got my message if you can help. My quick search turned up nothing, maybe it's a new error with 10.04.

It gives a string that I can't read fast enough. i plan to remove the 'quiet' but still haven't tried that. Otherwise, before continuing to load, for a split second you can read:

[xxxx numbers] CANNOT RESERVE MMIO REGION

It might even be the same error but SSD is faster and you don't have time to read it.

---

### Post by oldfred on 2010-05-14
the log files are the messages it posts as it is booting.

the xxx is the time (i think seconds) from start of boot so you can look for long time differences to see if something takes too long. Somethings do take longer than others.

---

### Post by darkod on 2010-05-14
> **oldfred said:**
> the log files are the messages it posts as it is booting.

the xxx is the time (i think seconds) from start of boot so you can look for long time differences to see if something takes too long. Somethings do take longer than others.

My question was do you know anything about CANNOT RESERVE MMIO REGION? I can't find anything.

It's not a big issue, but if I can make ubuntu not to stop for that message, why not. It will boot faster.

---

### Post by oldfred on 2010-05-14
darko did you just steal gauchotodd's thread? :) I missed you helping out on all the boot problems for the last month or two as I cannot see everything. Fortunately there are a lot of users willing to help. Did you just move to Spain?

I found this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577842)

some other comments on USB devices

and this 
[http://lwn.net/Articles/308348/](http://lwn.net/Articles/308348/)

---

### Post by darkod on 2010-05-14
> **oldfred said:**
> darko did you just steal gauchotodd's thread? :) 

Yes :) 

>  Did you just move to Spain? 

Sort of, hoping to make it a permanent move. :) And I just waited 6 weeks to get ADSL... :(

Strange, but when I used the 'e' in grub menu and deleted 'quiet', I couldn't notice that message about MMIO. Maybe it got lost in all the text. :) I'll have to do few more reboots to see what will happen.

If even it stays as it is, it's not bad.

---

### Post by gauchotodd on 2010-05-15
First of all, I'm takin' it back :)

> **darkod said:**
> Do you have a HDD too or only the SSD? I don't know why yet, but on my computer (with HDD) 10.04 does the same thing with sitting a bit with the cursor on screen, and then once it starts to actually load it does it fast.

For selecting ubuntu as default in grub menu, boot ubuntu and open:

sudo gedit /etc/default/grub

if ubuntu is on the top of your grub menu, in the line GRUB_DEFAULT=n, make the value 0. It starts counting them from 0, top to bottom. Save and close the file.

To update the grub.cfg file after that run:

sudo update-grub

I do have a HDD for storage; Win7 and Ubuntu10 are on the SSD.  I tried running "sudeo gedit /etc/default/grub" and it didn't do anything.  I remember when I did a software update this morning it didn't want to install grub, or it took it off, something like that.  It didn't give me any other options to keep it.  How do I get it back? :)

---

### Post by gauchotodd on 2010-05-15
Also, I have another general question: will rebooting the computer repeatedly (half a dozen times or so within an hour, or a dozen times over the course of the day) have any sort of wearing effects on the motherboard, processor, or drives that I should be concerned about?  I've been doing it enough lately that it's making me a bit uncomfortable compared to what I'm used to.  Most of it was from Windows problems and installing/reinstalling Ubuntu.

---

### Post by darkod on 2010-05-15
> **gauchotodd said:**
> First of all, I'm takin' it back :)



I do have a HDD for storage; Win7 and Ubuntu10 are on the SSD.  I tried running "sudeo gedit /etc/default/grub" and it didn't do anything.  I remember when I did a software update this morning it didn't want to install grub, or it took it off, something like that.  It didn't give me any other options to keep it.  How do I get it back? :)

Hmmm... If some config files are missing, boot ubuntu (you can still do it right even if it takes long?) and try running:

sudo grub-mkconfig

You might also run

sudo update-grub

after that. Other wise I have no clue why /etc/default/grub is not there.

---

### Post by oldfred on 2010-05-15
The preferred command is 
```
gksudo gedit /etc/default/grub
```The gksudo is for graphical apps and sudo for terminal commands.
You typed in your response sudeo - I do not know if that was just a typo in your post or not.

I do not think rebooting will cause any special wear as long as you are warm rebooting and not totally shutting down. The discussion always was startup spikes and cold to warm changes, but warm rebooting is just like running any other program.

---

### Post by oldfred on 2010-05-15
I also just posted this on another thread as a remote possibility:

I did see one post where someone left a CD in the tray and CD was first in boot order. System was trying to fsck the CD and took forever. He removed Cd and boot was very quick. That sounds like a bug but the fix was easy.

---

### Post by gauchotodd on 2010-05-17
Yes, sorry, it was a typo.  I ran the one you suggested and got this:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


Since the Grub default is already 0, what should I do from there?  And I checked my DVD drive, it's empty.

Is the grub timeout of 10 normal?  It normally stays on the black cursor screen for close to 10 seconds.  I'm assuming if I lower the timeout value, it will then timeout and won't load the desktop.

And how do I add the code box for next time?

Edit: I didn't change anything in it, so I didn't run the update code.

---

### Post by darkod on 2010-05-17
> **gauchotodd said:**
> 

Also, since Win7 is the default OS, I would like to switch that to ubuntu so if I push power I don't have to manually change it.  Is this done in BIOS?  I'm really new to this still.


You originally said win7 is default. But that would happen only if win7 is at top in this situation. Is it?

In that case, make GRUB_DEFAULT=1, this will make the second entry in the menu be default, which should be your ubuntu entry.

The timeout value has nothing to do with the cursor showing and waiting. The timeout value is how long it will wait at the menu, before continuing to boot the default entry.

I'm afraid I don't know why it waits for 10sec or so before continuing to boot. I have a small delay myself on my computer and still haven't managed to sort it out (haven't really tried too much to be honest).

---

### Post by gauchotodd on 2010-05-17
Ooookay I see, so if I put default 1 and timeout value 0 it should go straight to it, right?

Thanks again for your patience with me :)

Edit: to clarify:

"You originally said win7 is default. But that would happen only if win7 is at top in this situation. Is it?"

The screen I was referring to only lists ubuntu choices, Win7 is the default on the prior screen, Windows Boot Manager.  See below :) (sorry!)

---

### Post by gauchotodd on 2010-05-17
Okay so the gksudo commands are working and just sudo doesn't seem to. I changed the default value to 1 and it switched to recovery mode, so I changed it back to 0 and a timeout of 1 and it goes right to the cursor screen which is perfect. :)  I'm assuming it may still show the screen with the ubuntu choices but it's too fast for me to see if it indeed does.

I realize another source of my confusion: the screen that came up before the ubuntu choices is Windows Boot Manager, and that of course has Win7 as the default.  My next step is figuring out how to change the default on that to ubuntu and lower the timeout.

One other thing I never mentioned is that when I only had one drive installed, whether it was my HDD or SSD, it would go straight to the boot manager.  When I installed both drives, it displays a screen beforehand giving info on the boot drive, the SSD of course.  I can hit enter or it will proceed by itself after about 3 seconds.  Any idea why this is coming up or how to get rid of it? In BIOS maybe...

---

### Post by darkod on 2010-05-17
Windows bootloader and then grub? In this case you are either chainloading into grub2 from windows bootloader, or all this time we are talking about a wubi install and not full dual boot.

Everything seems to be working fine, but also to clarify the situation for yourself, you might want to run the boot info script. Instructions here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

You don't even have to post the results unless you have any questions. Look around, there is plenty of detailed info about your boot process there. At start it might look like too complicated, but soon you'll be at home with it. :)

---

