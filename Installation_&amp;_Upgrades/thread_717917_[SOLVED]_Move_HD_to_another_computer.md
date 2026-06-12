---
title: "[SOLVED] Move HD to another computer"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by neilg4rqn on 2008-03-07
Hi, I would like to transfer my present Ubuntu installation to another PC and thought I could simply move the HD, but no. The new faster machine will not start. Can I do anything or must I do a fresh install?
I guess I could use G4L but without a spare HD it isn't easy.

---

### Post by Bruce M. on 2008-03-07
> **neilg4rqn said:**
> Hi, I would like to transfer my present Ubuntu installation to another PC and thought I could simply move the HD, but no. The new faster machine will not start. Can I do anything or must I do a fresh install?
I guess I could use G4L but without a spare HD it isn't easy.

How are you doing this?
Does your old machine only have the one drive with Ubuntu on it?
Are you simply adding the old drive to the new machine as a slave?

Give us more info please.
Bruce

---

### Post by neilg4rqn on 2008-03-07
Hi Bruce M. I have 2 computers, one has ubuntu on it and nothjing else, it is on a 120g HD. The other has no hd but is faster and bigger etc. Does that help ?

---

### Post by neilg4rqn on 2008-03-07
or to put it another way. I wish tomove the hd with ubuntu on it to another machine.

---

### Post by Pumalite on 2008-03-07
What kind of 'Faster and Bigger'?

---

### Post by koenn on 2008-03-07
> . I wish tomove the hd with ubuntu on it to another machine.
That should be possible. 
One problem could be when the 2 computers have different processors and your ubuntu is using an optimized, processor-specific kernel : then it wont buit because the kernel isn't suitable for the new machine. 

check processors and installed kernel and see if they match. 

possible fix:
put disk in old machine
install a generic kernel, and make that the default
move the disk to the new machine and boot it
install a new kernel that is optimized for the new machine


another problem could be that grub doesn't find the hard disk / boot partition where it expects it, i.e the "root  (hd0,0)" (or whatever) in the boot menu doesn't correspondent with the location of the disk (controller, channel, ...) in the new machine.

---

### Post by neilg4rqn on 2008-03-07
OK. Faster and bigger = 2g or so and more ram slots.
Yes different proc.
When I try it boots so far then says something like "running local scripts" Dont know what this means.
As for installing a new kernel, can I please have a pointer to the instructions.

---

### Post by koenn on 2008-03-07
I thought you said the new machine "will not start".
If it's (trying to) run the local scripts, you're computer has booted succesfully and is in the final stages of initialising its configuration. 
So you kan forget about installing a new kernel for now, it seems

you're going to have to be a lot more precise than "it says something like ... " :
what does it say **exactly**? What **exactly** happens next ? ...

---

### Post by neilg4rqn on 2008-03-07
Hi Koen and others, first my apologies for not being very precise, I will try to give more detail now.

When I try to start the other machine using the HD from this one I am using now the following happens.

The ubuntu logo and orange bar appears on the screen and all looks hopeful for a time.
The screen goes black and after a few seconds some text appears, it reads :-

*Starting periodic command scheduler cron                                     [ok]
*Starting mldonkey: mlnet to be started (use force-start)
*checking battery state
*running local boot scripts (/etc/rc.local)                                          [ok]

There was more text but that was what was left that I could read and write down by hand.

The machine then appears to hang with the HD led giving brief flashes every few seconds. This situation continues for some time. So far I have waited about 30 minutes but no further progress.

I will have to give iin for the night in about 15 minutes, back tomorrow.
Cheers all, thank you for your patience so far

---

### Post by koenn on 2008-03-08
see if you can boot in recovery mode.
My guess would be that either your new computer fails to start X and/or has trouble with video display because of differences in hardware (video card, monitor specs, ...)

You can also try to diagnose the problem further by looking at the bootlog on one of the 6 TTY's (don't remember which one : hit Alt+ctrl and F2 or F3... to F6 while your computer is booting)

---

### Post by Pumalite on 2008-03-08
In theory, the kernel is supposed to load the modules according to the hardware that it faces, but in practice that sometimes doesn't happen and one ends up reinstalling or at least reconfiguring the xserver

---

### Post by Bruce M. on 2008-03-08
What's your partition information?  [Check this out]("http://www.psychocats.net/ubuntu/partitioning")

Reason I ask is if your /home folder is on a [separate partition]("http://www.psychocats.net/ubuntu/separatehome") and you have a free available partition you can [make a back-up]("http://www.psychocats.net/ubuntu/backup") of /home on the FREE partition or check our QuickStart in my sig.  Also back-up all other personal data and files you want to keep.

Then pop the HD into the new machine and use an ALT CD to:

[LIST=1]
[*]reinstall /root - reformatted to ext3
[*] set your /home to wherever it is - **DO NOT** reformat - keep the data
[/LIST]

and Ubuntu will set-up using the new hardware.

Just a thought
Bruce

---

### Post by neilg4rqn on 2008-03-08
Thanks Koenn I will have a go as soon as I can. Some other work has come my way so it may be a few days before I respond to this forum again but work means money!

---

### Post by neilg4rqn on 2008-03-09
A change of plans, I now have time to play ubuntu.
When I boot into the 'recovery' mode the reaction is the same as I described previously. I can press Ctrl/Shift/fn key and go to the command line log on etc. but I do not know the commands from there, I will have a surf around now but I am (obviously) new to all this. Any detailed info greatly appreciated. I did see something about 'X' but I am sorry I didn't get a chance to write it down and I can't seem to repeat it.
Should I uninstall the nvidia drivers in which case perhaps you could remind me of the correct command.

At least the weather is nice
Neil

---

### Post by neilg4rqn on 2008-03-09
Hi Bruce M, The original ubuntu installation I am trying to move to another machine uses all of the 120g HD and the various partitions are as auto selected on installing so there is nothing personalised.
I am a bit wary of re-installing unless I can have fairly detailed instructions as I do not have that level of knowledge yet. I have not moved from Windoze all that long.
Neil

---

### Post by koenn on 2008-03-09
just thinking out loud :
when your OS starts, you're att TTY7 where X normaly runs, but X doesn't start so you get nothing. The other TTY's (1 to 6) are text consoles and they work (you get as far as the login, and if you'd log on, you could do (console) work. 
So most likely your problem is X not starting. 

you can try to fix it by running dpkg to (re-)configure X.
Alt+Ctrl F1 to get a console, and log on (username, pass - you see nothing when entering the password, this is normal).
One logged on, try (skip lines starting with # )
```

# become root
sudo -i

# keep a copy of current config
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.oldcomputer

# reconfigure
dpkg-reconfigure xserver-xorg

# alternative : 
dpkg-reconfigure -plow xserver-xorg

# stop being root
exit

#test
startx    #might need sudo, not sure


```
if X works, Ctrl-Alt + Backspace will stop it so you can log out.
if X doesn't work, run dpkg-reconfigure again and try some other values 

the dpkg statement will start an interactive configuration procedure (and with -plow, you might get more questions / configurable options). Use common sense and accept the defaults, especially with things that are already working, eg keyboard.
Things that you might want to change are
* driver / x-server : try vesa - it almost always works and if it gets your computer to start X afterwards, you've found the source of the problem and you can start working at improving it 
* choose a moderate resolution, eg 800x600 - same reasoning as above
* "autodetect monitor refresh rates" is usually a good idea. 

more explanations al over the forums, e.g. here
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)


it may be a good idea to uninstall nvidia drivers first but i don't know how to do that. You can give the above recipy a try and see what gives

EDIT : reinstalling is interesting as "plan B" in case you can't get this to work. It would probably solve the problem but the downsides are
- you'd have to reinstall (and configure) all program's that are not included in Ubuntu by default
- you'd have to be very careful about not loosing /home and any other directory holding personal files. Like Bruce says - this is easier if you have seperate partitions for these things, but you seem unsure / insecure about this.
I'd try fixing X first.

---

### Post by neilg4rqn on 2008-03-09
Hi, I have it !!!!! Thanks to Koenn in particular I have cured the problem and I am now using the new machine with its 220Gig HD etc. The answer in the end was.

1 Allow machine to boot up and get to where it stopped saying "running local boot scripts..."
2 Press <Alt><Ctrl><F1>
3 Type sudo dpkg-reconfigure xserver-org <Enter>
4 Type password<Enter>
5 Accept defaults as suggested - wait for normal logon screen and logon
6 Restart machine in the normal manner from the desktop
7 Reinstall Nvidia drivers and restart
8 Thank the Ubuntu forum
9 Make coffee and have chocolate biscuit as reward
Many thanks

Neil  :)

---

### Post by koenn on 2008-03-09
Great. 
Wanna send some coffee over ? I just ran out. 
:)

---

### Post by Bruce M. on 2008-03-09
> **neilg4rqn said:**
> Hi Bruce M, The original ubuntu installation I am trying to move to another machine uses all of the 120g HD and the various partitions are as auto selected on installing so there is nothing personalised.
I am a bit wary of re-installing unless I can have fairly detailed instructions as I do not have that level of knowledge yet. I have not moved from Windoze all that long.
Neil

When you installed Ubuntu did you use the LiveCD or the AltCD.
LiveCD would allow you to try Ubuntu and has two icons on the desktop. Examples and Install.

If you used the LiveCD, then reinstalling is going to be the same as when you first installed. What you want to be careful about is the programs and information you have aquired since then. DOC files, images, music, videos, email, bookmarks etc.

Here is a [detailed tutorial]("http://www.psychocats.net/ubuntu/installing") on how to install from the LiveCD.  Complete with images.

When it gets to the part that talks about Dealing with Partitions you'll want the second option:

> The second option is ideal for people who do not want Windows any more and just want to erase it and replace it completely with Ubuntu.

It's not hard.  :)

However, look at QuickStart in my sig.
[LIST=1]
[*]Get it and make a backup of your  /home folder ... to you desktop.
[*]Copy the files to a CD.
[*]And copy the **folder**: QuickStart to it as well.
[*]Reinstall Ubuntu
[*]Copy QuickStart to your home folder from the CD.
[*]Copy the /home backup file from the CD  to your desktop.
[*]Restore the your /home folder using QuickStart
[/LIST]

We'll be here for more help as well.
Bruce

**EDIT:**  Oopps!  You got it.  :)  Perfect.  Still, I recommend QuickStart.
Come back and mark the thread as [Solved] > See: Thread Tools.

---

### Post by Pumalite on 2008-03-09
> **neilg4rqn said:**
> Hi, I have it !!!!! Thanks to Koenn in particular I have cured the problem and I am now using the new machine with its 220Gig HD etc. The answer in the end was.

1 Allow machine to boot up and get to where it stopped saying "running local boot scripts..."
2 Press <Alt><Ctrl><F1>
3 Type sudo dpkg-reconfigure xserver-org <Enter>
4 Type password<Enter>
5 Accept defaults as suggested - wait for normal logon screen and logon
6 Restart machine in the normal manner from the desktop
7 Reinstall Nvidia drivers and restart
8 Thank the Ubuntu forum
9 Make coffee and have chocolate biscuit as reward
Many thanks

Neil  :)

Glad you got it working.

---

### Post by Bruce M. on 2008-03-09
> **koenn said:**
> Great. 
Wanna send some coffee over ? I just ran out. 
:)

For me too.
Nice post to resolve this.  :)

---

