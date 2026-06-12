---
title: "Hardy Heron SO SLOW can't use computer... Having to write this in Lynx!"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Miikee on 2008-04-25
Please help me.  I just got done installing Hardy Heron...  It crashed at the very end of the installation and I had to hard reboot my computer.
It ended the installation process, but never made it to the clean up process, or the reboot step.
Now it has restarted and it is so slow that I can't even open applications in the GUI.
About the only thing I can do is switch to another TTY.  Which is where I am right now, typing through lynx.
I am a beginner in Linux only have had it for a few months.  Therefore, you may need to spell somethings out for me.
I try to use terminal as mush as possible so, i know most navigation commands and basic file manipulation commands.
Please help me with this probably it's really disappointing... I need to work on this computer for school.
I have a test tomorrow and need to be getting to sleep, so I may not respond to posts tonight.
Sorry about how this may look through your browser.  I'm typing how it looks best in Lynx.
PLEASE HELP.  7.10 ran fine, so i figure I should have the requirements for 8.04 although I don't know them off the top of my head.

---

### Post by gtdaqua on 2008-04-25
Dont panic. What was the error message you saw? Can you simply try reinstalling it? 

If it doesn't work, simply install Gutsy again and download the alternate CD for 8.04 and do an upgrade.

---

### Post by gtdaqua on 2008-04-25
> 
It crashed at the very end of the installation and I had to hard reboot my computer.


At what point did this happen?

---

### Post by Miikee on 2008-04-25
Also I only have a very limited amount of space left on my Linux partition.
What I think has happened is that I don't have any space left on it since the clean up process never happened.
7.10 once slowed way down (not as slow as it is right now) when I used up the last amount of space accidently.
Another think I noticed when booting up for a 2nd was that my Swap Partition failed to mount.
The shut down button in 8.04 also causes it to freeze and require me to manually turn off the computer.
Any help is appreciated.

---

### Post by Archmage on 2008-04-25
I did experiance when I upgrade a PC via hand from Feisty to Gusty. Since Edgy was something enabled that was slowing down the harddrive EXTREM.

Please tell us what are the top prosseces in the top program.

(Switch to the console via CTRL+ALT+F1, log in and than enter top.)

---

### Post by kerry_s on 2008-04-25
it's a clean install that screwed up, just try again. no need to mess around with a borked install. pop your cd in and give it another go. don't forget you can use the live cd to get help.

---

### Post by Miikee on 2008-04-25
I installed via the update manager and don't have a live CD. 
Also I don't know how to get back to the 7.10 version.
The last thing that it was doing was having trouble with the network-manager.  It failed somethings with tht, but that was the only thing that I really noticed.
I ran top.
the top programs are : xorg, top, init, firefox (I tried running this), compiz.real, xgl, kthreadd
They aren't all up at once, they keep changing.
Thanks for all the fast replies, it's really appreciated.

---

### Post by Miikee on 2008-04-25
The installation crashed at the end of the installation, and write before the clean up and restart steps.
It seemed like it was pretty close to done.  I let it sit for about an hour because I really didn't wanna mess with it, and this is the reason.
I have no problem doing another installation.  But I just don't know How I'd go about doin it in the best way.
I have most of my stuff backed up on a seperate partition.  If I need to wipe the Linux partition and reinstall, then my stuff would still be safe right?
I'd rather just run through the update manager style installation again, if that's possible.

---

### Post by Patsoe on 2008-04-25
If lack of free disk space is indeed the problem, you may want to go to single user mode  ("sudo init 1"), because there should be an extra 5% of disk space for the root user (note: this will terminate your X session and apps, and maybe your ethernet connection).

(edit: I mean the above may make your system useable, and then you can do the stuff below)
(edit: another thing - in single user mode you are root, so be extra careful!)

You can use "apt-get clean" to get rid of the downloaded deb archives.

You can also use apt-get to check for broken packages from the unfinished installation (although I use aptitude, which gives you an interactive interface).

---

### Post by Skokie on 2008-04-25
Ok I would like to say that this is probably something more fundamental.

I have installed Kubuntu 8.04 clean and upgrade on a few machines now and ONLY the HP dc7700 is a HUGE problem like this.

So there is something very wrong with something low level.

On the HP it takes about 2 minutes to load an app.  goes 100% on both CPUs for the simplest of things, which then take 2 minutes to do.

This is more than an install issue I think.

I have done some searching but 8.04 is a little new to have hit more people yet.  I think we may be stuck for some days :(

HP Compaq DC7700 workstation
Intel Core Duo 2.4Ghz (now feels about 100Mhz) sniff
2 GB ram
Motherboard chipset Intel Q965
Graphics card Intel GMA 3000 

Further, Kubuntu 7.10 was never great (in X) but every second boot was fine.  This new slowness doesnt feel like a graphics problem, since redrawing is slow like before but not terrible.

Could be IO access at pre 1970s frequencies?

Could be CPU in perminant sleep (but honestly an Intel doesnt go as low as this machine seems now).

Any further news?

---

### Post by Skokie on 2008-04-25
Sorry one other thing.  The install CD also ran at 0.0001 kph... but from some digging people said the "installed was fine".  So I upgraded the HP from 7.10 desktop (the only way it was possible to do, if I wanted to see the result in my lifetime).

I figured it was a kernel problem with the CD kernel version (quite common).  But alas the installed one is as bad.

---

### Post by Patsoe on 2008-04-25
Hi Skokie. Could you start a new thread for this problem?
Otherwise we'll end up talking about two different problems and get things mixed up.
After starting the new thread you can of course leave a message here to say where the new one is. 
Thanks!

---

### Post by Skokie on 2008-04-25
Thanks for the quick message and sorry for jumping in here :)

I have created a new thread at
[http://ubuntuforums.org/showthread.php?p=4789167#post4789167](http://ubuntuforums.org/showthread.php?p=4789167#post4789167)

with very very very slow in the title :)

I hope the average joe (likely to have these machines) doesnt get too frustrated. sniff.

I will continue to see what I can find out.

---

### Post by Miikee on 2008-04-25
Thank you very much for everyone's help.  I still don't know what the problem was.  However when I got up this morning and rebooted, it began running alot better.
I had rebooted a couple times yesterday, so I don't know what difference it made this morning.
The only problem I notice now is that it running very choppy and sluggish.  Also, I've noticed some of my firefox plug-in's no longer work (such as mouse gestures).
I ran the apt-get clean, but it didn't really show whether or not anything was done.
I'm hoping that the upgrade did in fact install completely and that nothing too wrong with it in the future. 
Thanks for everyone's help with the problem.  I wish I had a better closure, but I'm glad the problem went away.

---

### Post by Patsoe on 2008-04-25
> **Miikee said:**
> Thank you very much for everyone's help.  I still don't know what the problem was.  However when I got up this morning and rebooted, it began running alot better.
I had rebooted a couple times yesterday, so I don't know what difference it made this morning.
The only problem I notice now is that it running very choppy and sluggish.

Begins to sound like a hardware problem... how is the CPU fan doing? My guess: because you did all the installing stuff yesterday you loaded the machine more than you usually do and the CPU, overheating, started throttling. Overnight it cooled down of course. It's only intermittently sluggish today because you're not pestering the CPU as much.

When you notice slowdowns you could check the throttling state through "cat /proc/acpi/processor/CPU#/throttling" where # is probably 1 (maybe 0?).

> Also, I've noticed some of my firefox plug-in's no longer work (such as mouse gestures).

Probably unrelated to the other problem; I'm assuming you mean they worked in 7.10 but not in 8.04?

> I ran the apt-get clean, but it didn't really show whether or not anything was done.

No that's right, it just removes all cached deb packages without printing anything to screen. On my box it just freed well over 900MB of space on /.

---

### Post by licorice_sticks on 2008-05-02
Hi, I posted about a similar problem. How do I go about doing a clean update? What do I have to do on the terminal etc.? And will it delete compiz-fusion, amarok, and whatever else i downloaded for ubuntu?

---

