---
title: "debian to ubuntu"
date: 2005-11-06
forum: Installation &amp; Upgrades
---

### Post by wwbdd on 2005-11-06
I've been having a lot of trouble trying to get ubuntu installed and no one seems to be able to help.  I had the thought of installing debian and then doing an apt-get distro-upgrade after editing the sources.list file.  Will this work? is it a good option?

---

### Post by adwait on 2005-11-06
NOT a good idea, although Ubuntu is debian based, right now debian and ubuntu are waaaaaay out of sync.

---

### Post by matthew on 2005-11-06
[quote=wwbdd]I've been having a lot of trouble trying to get ubuntu installed and no one seems to be able to help. I had the thought of installing debian and then doing an apt-get distro-upgrade after editing the sources.list file. Will this work? is it a good option?[/quote] Will it work? Hmm...yeah, I think so. The question is will it work easily and therefore becomes your second question, "is it a good option?"

My answer (as a user, not a developer/programmer/total linux guru) is that it depends on how much of an adventure you are prepared for and how urgent it is that you get a working system.

Can you try a different install cd for Ubuntu? Are your problems specifically Ubuntu related or will they exist in Debian as well? Are you willing to do the (more technically challenging) installation of Debian?

One side of me says, "Try it, it could be fun!" The other side says, "If an Ubuntu installation was difficult and had too many difficulties, installing Debian first and then dist-upgrading is likely to drive you insane."

Well...I didn't tell you what to do, but I hope I was able to help you find what you need to think about to be able to answer your question.

EDIT: BTW, I feel that adwait's short answer above is pretty much on-target.

---

### Post by wwbdd on 2005-11-06
by different install cd do you mean downloading and trying again (which ive done with 2 seperate downloads and at least 3 maybe 4 different cds) or do you mean trying kubuntu instead of ubuntu?  Would there be any difference?

---

### Post by matthew on 2005-11-06
[quote=wwbdd]by different install cd do you mean downloading and trying again (which ive done with 2 seperate downloads and at least 3 maybe 4 different cds) or do you mean trying kubuntu instead of ubuntu? Would there be any difference?[/quote] I meant downloading and trying again or signing up for the free cds from shipit and waiting for them or buying one from somone like [http://www.osdisc.com]("http://www.osdisc.com")

Since you have kind of done this already I can only ask if you checked the download and burn and confirmed they were good. Did you try burning the cd at a lower speed? Some cd drives are a little finicky. Hmm...it doesn't seem like I have much more to offer on that. It doesn't sound like this is the real problem.

You wouldn't see any real difference between a Kubuntu installation vs an Ubuntu installation until all was said and done and you booted into the desktop.

---

### Post by wwbdd on 2005-11-07
Well here's the thing, i've used this same cd to install ubuntu before on a different computer.

---

### Post by matthew on 2005-11-07
[quote=wwbdd]Well here's the thing, i've used this same cd to install ubuntu before on a different computer.[/quote]Then it sounds more like a hardware issue. Your cd must be okay. I wish I had some advice for you. If you have already started other threads and asked about the specific problems you have encountered during the installation and not been able to find answers for these issues you may be out of luck.

Just out of curiosity, what is the hardware configuration that you are trying to install on? (processor, memory, hard drive, just whatever you can think of)

---

### Post by wwbdd on 2005-11-07
It write the kernel but then when it is updating the packages it runs into a problem about 64% of the way through. It says it getting libgstreamer0.8-0. I went into a console terminal thing and tried again (after a reboot so that it wasn't trying to install elsewhere) with apt-get install and it gives me this error: fontconfig error: Cannot load default config file. i pressed control + c and it seemed to skip over it but then everything else says something like dependancy problems unconfigured and then gets hung up again on the same Fontconfig error.

I have a p4 2.8ghz ht with an asus p4p800 delux board (it think thats the model but i might be totally off) 1 gb or ram (2x512) an 80 gb hdd (dont know what kind).  cd+/-rw drive and a dvd drive (again i dont know what brand).  Does that explain any of my problems???

---

### Post by matthew on 2005-11-08
[quote=wwbdd]It write the kernel but then when it is updating the packages it runs into a problem about 64% of the way through. It says it getting libgstreamer0.8-0. I went into a console terminal thing and tried again (after a reboot so that it wasn't trying to install elsewhere) with apt-get install and it gives me this error: fontconfig error: Cannot load default config file. i pressed control + c and it seemed to skip over it but then everything else says something like dependancy problems unconfigured and then gets hung up again on the same Fontconfig error.

I have a p4 2.8ghz ht with an asus p4p800 delux board (it think thats the model but i might be totally off) 1 gb or ram (2x512) an 80 gb hdd (dont know what kind). cd+/-rw drive and a dvd drive (again i dont know what brand). Does that explain any of my problems???[/quote]
This isn't making sense to me...not your description, but that the problem exists at all. I can't see any reason the installation should be failing unless there is a hardware problem (like bad hard drive, bad sectors, something like that).

It seems you are able to boot to a command prompt, so that's good anyway. One thing you could try is boot, then issue the commands for apt-get to fix installation problems. Try this, hopefully it will work. First, let's make sure you have your apt cache up to date. Make sure the cd is in the drive before we do this. (If you know how/want to update your sources.list you can do it now, but since we are just trying to get a working installation I would recommend leaving it stock for the moment.)
```
sudo apt-get update
``` Then try this first
```
sudo apt-get dist-upgrade
``` If that doesn't work, try
```
sudo apt-get -f upgrade
``` and if that doesn't work, finally you can try
```
sudo apt-get -f dist-upgrade
```
I wish you luck. If this doesn't work, we will have moved beyond my knowledge and skill level.

---

### Post by wwbdd on 2005-11-08
I tried what you said and it went balistic. It eventually returned an error something like /usr/bin/dpkg returned an error code(1).  During the whole process the moniter blinked on and off with this blue error message (to much like the bsod for my liking) that said

"The display server has been shut down about 6 times in the last 90 seconds.  It is likely that something bad is going on.  Waiting for 2 minutes before trying again on display :0."

It's good though that at least the computer told me exactly what's wrong so i can go in and fix it.... not.

oh and btw the video card is an nvidia gfx5600, i dont know if that means anything.

Is it time to resort to a debian-->ubuntu upgrade? Or would i just be better off just totally switching to another distro?  Furthermore would a different distro have any affect on the installation or does my box just totally reject any os that is not windows?

---

### Post by matthew on 2005-11-08
Actually this has me really hopeful. It sounds like the problem is possibly not the entire installation, but now just with the X server (the graphic display program). Let's see if something less radical than starting over can work. We will still have that option available if this doesn't do anything.

Quick question: which command from the above list stirred up all the activity? Okay, back to the next idea to try...

Get all the information you can about your monitor and have it near you then try to boot. You may have to watch it blink several times like before. If at some point you can hit ctrl+c and stop the attempt to start the x server you should be able to get a command line log in. If you can't, boot in recovery mode. In either case, once booted do this
```
 sudo  dpkg-reconfigure xserver-xorg
``` You will be asked lots of questions. Just about all of the time you can choose the default answer. When it asks you what display resolution you want make sure and select that (use the arrow keys to move, the spacebar to select and the tab key to jump from box to box when necessary).

If you are asked something you don't know the answer to, choose the default answer or take your best guess. It may work. If it doesn't, run it again and try something else. Give it at least 4 or 5 tries if necessary. 

If we get this to work then going back and finding/completing anything remaining from the installation will be pretty easy.

Okay, it's late here. I'm off to bed. I will check in tomorrow. Hopefully you will have had success!

---

### Post by az on 2005-11-08
[QUOTE=adwait]NOT a good idea, although Ubuntu is debian based, right now debian and ubuntu are waaaaaay out of sync.[/QUOTE]

Actually, Sarge is now just behind Breezy, so you can easily and safely dist-upgrade from Sarge to Breezy.  What you are refering to is keeping both Debian and Ubuntu repositories together - that is never a good ides.  But dist-upgrading will work fine.  It is like going from testing to Sid, just that Sid is a stable Sid.

Before you do anything else, have you tried memtest?  You can run it from the Breezy installer.  Perhaps that is your problem?  Maybe it could be that your box/CPU is overheating after a while?  Can you check the temperature?

---

### Post by shandar on 2005-11-08
I know this sounds odd, but the same happened to me, when copying packages it stuck at 64%. What happened to me was that after a few minutes it told me that this part of the install had failed and allowed me to continue on to the next step (setting the time, creating users etc). After rebooting it returned to the copying packages screen and downloaded them of the ubuntu servers instead (AFAIK, the cd wasn't in the drive) et voila! Now I have a fully working Breezy install.

---

### Post by wwbdd on 2005-11-08
during the boot up process where the ubuntu logo comes up and it checks stuff it said mounting local filesystem failed.  I'd never noticed that before and it doesn't sound good.  As far as the last steps and their success

apt-get update didn't yell at me

apt-get dist-upgrade didn't do anything but say that i should try apt-get -f install.  The following packages have unmet dependencies: ubuntu-desktop.

apt-get -f upgrade dpkg: all in all didn't work at all.  last line said E: Sub-process /usr/bin/dpkg returned an error code (1)

apt-get -f dist-upgrade same thing

sudo  dpkg-reconfigure xserver-xorg didn't work either.  Just about all of these things said something somewhere in their error message about a "corrupt filesystem tarfile - corrupted package archive: Success"

about the memtest thing i stoped it when it was at like 11000 errors, i dont know what any of them mean, but it didn't sound good.  Windows gets it to work though so i dont know.

---

### Post by corruption on 2005-11-08
Sounds like you've got some bad RAM... I ran into a similar issue recently, after a complete install of Breezy, I started having random errors and kernel panics.. Gnome panels would drop randomly, all stability was gone... I went through my 2 512mb sticks one by one, running memtest86 on them, to find that one of them was riddled with errors. Once I removed the offending stick from the bay, all was right in the world again.

Just a thought, Good luck!

---

### Post by matthew on 2005-11-08
Oh! You have some bad ram. Remove the sticks (while the computer is off) one by one and reboot to memtest each time until you find the bad one. Then replace it and all should be good.

EDIT: corruption beat me to it

---

### Post by az on 2005-11-08
If you have so many errors, you may have the timing or ECC set improperly.  Sometimes, just switching the sticks around will solve it.  

If you run a kernel with the badram patch, linux can *use* a stick of bad ram (bad bits, not bad timing or ecc) and just ignore the bad areas.  You have to config it with memtest.  Neat, huh?

---

### Post by wwbdd on 2005-11-08
UBUNTU WORKS, thanks to everyone who helped me get it up and running.  I wound up taking the bad stick out and replacing it with a stick from another computer that isn't being used anymore (but maybe it will now that i can install linux).  This is so great!  Thanks again!

---

### Post by corruption on 2005-11-08
[QUOTE=azz]If you run a kernel with the badram patch, linux can *use* a stick of bad ram (bad bits, not bad timing or ecc) and just ignore the bad areas.  You have to config it with memtest.  Neat, huh?[/QUOTE]

Do you have any kind of links to share on this information? I've currently got 2 bootable, but markedly 'bad' 512mb sticks sitting next to me itching for an answer!

---

### Post by az on 2005-11-08
[QUOTE=corruption]Do you have any kind of links to share on this information? I've currently got 2 bootable, but markedly 'bad' 512mb sticks sitting next to me itching for an answer![/QUOTE]

[http://rick.vanrein.org/linux/badram/](http://rick.vanrein.org/linux/badram/)
[http://rick.vanrein.org/linux/badram/download.html](http://rick.vanrein.org/linux/badram/download.html)

Install build-essential, gcc-3.4, linux-tree and patch the kernel.  Build the custom linux-image.  Install your linux system on a box using good ram and switch to the bad ram and run memtest.  Edit your grub.conf to include the mentest badram parameters.  You are good to go.

Ideally, the stock kernel could be patched this way so that you could boot and install the system with a badram stick.

I tried this with Hoary (2.6.10).  The 2.6.12 patch is untested, so if it works for you (it should) write to Rick vanRein.

---

### Post by corruption on 2005-11-08
Awesome, thanks.. I'll put it to the test later on tonight =D

---

### Post by matthew on 2005-11-08
[quote=wwbdd]UBUNTU WORKS, thanks to everyone who helped me get it up and running. I wound up taking the bad stick out and replacing it with a stick from another computer that isn't being used anymore (but maybe it will now that i can install linux). This is so great! Thanks again![/quote]Very glad to hear it! Congratulations.

---

