---
title: "Problem installing Ubuntu 5.10 on Pentium 2"
date: 2006-05-02
forum: Installation &amp; Upgrades
---

### Post by dion on 2006-05-02
I am trying to install Ubuntu 5.10 on a PC with a pentium 2 Klamath processor.  I have previously run Ubuntu 4.10 and 5.04 on this machine and they install and run perfectly.  The system does not have an on-board graphics card and initially I did have installation problems with a few linux distros and getting the X-server to run, however I changed the graphics card and the new one seems compatible with Ubuntu as I have then managed to install both earlier versions of Ubuntu.  
The installation for version 5.10 goeas fine during the first part of the installation and it then ejects the disk and says that the PC needs to reboot to complete the installation.  Once the PC reboots, it continues loading and gets to 71% where it just hangs.  I have tried leaving the machine on like this overnight in case it was just slow, but the following morning it was still at the same point.  I have tried re-installing but it always hangs at that exact same spot.  I have dropped back to Version 5.04, but would like to get 5.10 running.  
If I then reboot the machine at this spot, it starts up, tells me that some packages maybe broken and then presents me with a command prompt login.  After typing the user name and password I then get a command prompt.  I have tried typing help at the command prompt but there do not seem to be any commands to start the X-Server or GDM.
Any ideas ???  ](*,)

---

### Post by bosun on 2006-05-02
This is the exert thing that happened to be i got stuck at 71% and i tried to restart allover again but whenever i get to base system errors will be coming up.

---

### Post by barbarian on 2006-05-03
Ubuntu Breezy needs 128 Mb RAM minimum. Try to choose *server * install and then *apt-get install xubuntu-desktop*. Or maybe, you better wait till Xubuntu Dapper release.

---

### Post by dion on 2006-05-05
I have 2 X 128mb ram chips in this machine, it is reasonably fast for a pentium 2.  I think the problem is when the installer tries to configure the X-Server.  However your suggestion of doing a server install and then loading X may just work.  Also I was just doing a standard install of ubuntu which uses the gnome desktop, maybe kde would work better.  I will post the results here after I try this.  Thanks for the suggestion.

---

### Post by barbarian on 2006-05-05
Slight correction:

*sudo **aptitude **xubuntu-desktop*

IMHO, here aptitude is better choice then apt-get because it installs all necessary packages for comfortable desktop.

---

### Post by dion on 2006-05-05
Thanks, I will try aptitude instead.  Just wondering, this seems to be a common problem with Ubuntu freezing at 71%, there is another thread about it as well, exact same symptoms experienced by a number of people, has anyone figured out what is causing the problem, and what are the chances of it being resolved with Dapper.

---

### Post by niteshade on 2006-05-05
I hope I'm not threadjacking, but I too am having issues installing on a PII.  I posted this in another thread (the absolute newbie thread), but I figured it might be better placed here... sorry if it's clutter.  At any rate,

System is a 400 mHz Pentium II, with a 4.3 GB HD and a 256 MB RAM.  Ubuntu 5.10 Breezy.

I'm getting a couple of exceptions when I try to install.  These are:

```
[!!] Install the base system
Unable to install initrd-tools
An error was returned while trying to install the initrd-tools package onto the target system.
Check /target/var/log/bootstrap.log for details.
<Go Back> <Continue>
```

```
[!!] Install the base system
Installation step failed
An installation step failed.  You can try to run the failing item again from the menu, or skip it and choose something else.  The failing step is: Install the base system
<Continue>
```

Hitting <Continue> brings me back to the Ubuntu installer main menu.

I looked in /target/var/log/ but didn't see any file named bootstrap.log.  Not that the built-in shell has vi, pico or emacs installed to view it anyways.

Any ideas?  Do I need network access for this to work?

---

### Post by barbarian on 2006-05-06
> [!!] Install the base system
Unable to install initrd-tools
An error was returned while trying to install the initrd-tools package onto the target system.
Check /target/var/log/bootstrap.log for details.
<Go Back> <Continue>

I had this error, when I have been trying to install Ubuntu on Pentium 200MMX with 2 gb hard drive. I have spent a lot o time to find out about this error and finaly I have tested Hard Drive - it was mechanicaly corrupted. I tested it with Seagate HD diagnostic tool, and there was many input/output errors.
So maybe you will try to test your HD on errors.
I find interesting link, btw:
[http://www.tacktech.com/display.cfm?ttid=287](http://www.tacktech.com/display.cfm?ttid=287)

---

### Post by Sef on 2006-05-06
Niteshade: it would be best if you started your own thread.  You would have more people see it.

---

### Post by niteshade on 2006-05-06
Thanks Sef.  I'll do that.

---

### Post by niteshade on 2006-05-06
Thanks Bar.  Best explanation I've heard so far.

---

### Post by dion on 2006-05-09
Hi Barbarian,

Just to let you know that the server installation and then X-Server using aptitude worked great.  Wonder why the default installatin doesn't do it though?  Wonder if you can help with another problem.  The sound does not work, the machine has an on-board soundpro card.  Google reveals that this was a troublesome card even for windows users as the manufacturer didn't pay much attention to releasing drivers for the hardware.  However, ubuntu comes with alsa and even on other distros I couldn't get the card to work using alsa.  However Mandrake also had a utility 'sndconfig', when I used this utility and set the card as soundblaster 16 it worked fine.  Any ideas if ubuntu supports this?  If not, any options other than getting another sound card?

---

