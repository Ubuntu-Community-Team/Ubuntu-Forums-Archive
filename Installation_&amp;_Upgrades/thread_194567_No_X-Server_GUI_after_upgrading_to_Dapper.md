---
title: "No X-Server GUI after upgrading to Dapper"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by Nickb-k on 2006-06-11
Hello,

This morning I tried to upgrade from Breezy to Dapper.  First I updated my sources list to Dapper, then I used:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

The install looked ok, although I am a total Newbie and don't really know what it all means, there weren't any major errors.  Then the install finished and I was left at the shell prompt (still in X-Windows), without any explanation. The only strange thing that happened during the update/install process, was that Firefox kept prompting me about not being able to find a *.png file.  The icons for Firefox, Synaptic and a couple of other programs dissapeared from the top Panel after the install.  

When I updgraded to Breezy, I'm sure it propmted me to reboot.  So I rebooted, which was probably a mistake.  Since then I havent been able to load X Windows (I mean the windows like GUI).

I've tried a few different things as recomended on these forums.  When I try these commands:

```
sudo apt-get install ubuntu-minimal
sudo apt-get install ubutnu-base
sudo apt-get install xserver-xorg
sudo apt-get install x-windows-system-core
sudo apt-get install ubuntu-desktop
```

From the command line, apt tells me that the latest packages are installed.

I also tried

```
dpkg --configure -a
```

as recommended on this forum, but nothing seemed to happen.

I also tried reconfiguring xserver using:

```
dpkg-reconfigure xserver-xorg
```

But all the settings seemed to be correct

If I need to post any config files here I'll get onto it as soon as possible.  Using XP again after a month in Ubuntu is a nightmare :(

Thanks in advance for your help

---

### Post by jørgen on 2006-06-11
Welcome to the club! Dapper sucks!

---

### Post by Lux Perpetua on 2006-06-11
So apparently you have an X server installed, but you can't use it. What have you tried so far to get the X server running, and what errors did you get? Have you tried [list]sudo /etc/init.d/gdm start[/list]or perhaps[list]startx[/list]?

---

### Post by Nickb-k on 2006-06-12
Thanks, I'll try that now.  So far I tried:

```
xinit
```

Which takes me to a weird looking screen, really low res, VGA looking.  It has a terminal in the top left corner.

To fix Xserver I tried 

```
sudo reconfigure xserver-xorg
```

I put in the 'correct' settings as I thought they should be based on the last install.

When thats didnt work I tried re-installing xserver:

```
sudo apt-get install xserver-xorg
```

But apt told me it had the latest package.

Thanks for your suggestion, I'll try it out from uni this morning. No internet access from uni though :-(

---

### Post by Nickb-k on 2006-06-12
Ok, I ran ```
 startx
``` and got the following error, after the system loaded the same low-res x-like environment:

Xsession: unable to start X session --- no "/home/nick/.xsession" file, no "/home/nick/.Xsession" file, no session managers, no window managers, and no terminal emulators found; aborting.

I checked the .xsession-errors file which contained over 250 lines, so I haven't posted it.

So maybe I need to unistall x-server and reinstall it?

Thanks again...

---

### Post by fmo on 2006-06-12
I know that it won't help, but IMHO installing Dapper from an upgrade is really looking for troubble, there is so many thing that can have changed on your Breezy when installing software, especially from unsupported repositories.

The good way for me is to make sure that your /home is on a separate partition that / and then just scrap the existing system away.

---

### Post by Nickb-k on 2006-06-12
[QUOTE=fmo]I know that it won't help, but IMHO installing Dapper from an upgrade is really looking for troubble, there is so many thing that can have changed on your Breezy when installing software, especially from unsupported repositories.

The good way for me is to make sure that your /home is on a separate partition that / and then just scrap the existing system away.[/QUOTE]

Well I have my /home backed up on a seperate partition.  Its all the configs and the time to install everything from scratch.  Maybe I'll give it another 24 hours and hope...

---

### Post by fmo on 2006-06-12
[QUOTE=Nickb-k]Well I have my /home backed up on a seperate partition.  Its all the configs and the time to install everything from scratch.  Maybe I'll give it another 24 hours and hope...[/QUOTE]

I understand completely, I hate having to reconfigure everything, but solutions like Automatix help a lot, but sure, you will still have to install manually some other applications :( 

Good luck with that:D

---

### Post by bram2000 on 2006-06-12
[QUOTE=Nickb-k]Thanks, I'll try that now.  So far I tried:

```
xinit
```

Which takes me to a weird looking screen, really low res, VGA looking.  It has a terminal in the top left corner.
[/QUOTE]

Alright Nick,

That VGA looking thing with a terminal in the corner is X without any window manager (i.e. without Gnome).

Try this:

```

sudo /etc/init.d/gdm restart

```

Then post what happens. This command will restart the Gnome display manager (the interface which asks you for a password when you first turn your machine on).

Bram

---

