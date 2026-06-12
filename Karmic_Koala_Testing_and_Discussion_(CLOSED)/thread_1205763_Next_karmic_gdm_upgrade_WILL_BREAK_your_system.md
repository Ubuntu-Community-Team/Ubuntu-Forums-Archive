---
title: "Next karmic gdm upgrade WILL BREAK your system"
date: 2009-07-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-07-06
Martin Pitt on the ubuntu-devel-announce mailing list:

> **Next karmic gdm upgrade WILL BREAK your system**

Hello Karmic users,

last Wednesday the new gdm 2.26 landed in Karmic and has caused quite
a bunch of regressions and errors. I just uploaded 2.26.1-0ubuntu3
which should fix the nasty ones, the only major one left is the "Does
not support session saving" dialog ([https://launchpad.net/bugs/395324](https://launchpad.net/bugs/395324)),
which I'm going to address next.

One major bug in the first 2.26 packages was that the package scripts
restarted gdm during the upgrade ([https://launchpad.net/bugs/395302](https://launchpad.net/bugs/395302)).
The package scripts got fixed in 2.26.1-0ubuntu3, so that _from this
version on_ further upgrades will go smoothly. Upgrades from 2.20 (i.
e. Jaunty or Karmic Alpha 2) will also work.

But if you upgraded to gdm 2.26 since last Friday, updating your
system under GNOME will kill the upgrade and your session in the
middle of the update again, since there is no way for the fixed gdm
version to override the previous version's prerm script.

Please follow these steps:

 1. Check your gdm version:

      dpkg -l gdm

    If this says "2.20...", you are fine and can ignore this email.

  2. Do

       sudo apt-get update
       apt-cache show gdm|grep Version:|head -n 1

     If the second command says "2.26.1-0ubuntu3", continue;
     otherwise, wait for an hour. The version should be available on
     archive.ubuntu.com at 1600 UTC today, and a bit later on your
     mirror.

  3. Log out from your X session, to get back to the login manager.

  4. Press Control-Alt-F1 to get to a text console, and log in with
     your normal username/password.

  5. Run an upgrade:

       sudo apt-get dist-upgrade

  6. Press Ctrl+Alt+F7 to get back to the graphical login manager.

Thank you and sorry for the inconvenience,

Martin

---

### Post by Elfy on 2009-07-06
moved from "New GDM is uploaded" thread and stuck for the time being

---

### Post by celticbhoy on 2009-07-06
When I use Ctrl-Alt-F1 I have no internet to update!

---

### Post by plun on 2009-07-06
> **celticbhoy said:**
> When I use Ctrl-Alt-F1 I have no internet to update!

Its the same for me.....wireless Laptop.   No Internet from a tty-terminal

Maybe it works with the laptop wired or from recovery, going to test.

---

### Post by yelo3 on 2009-07-06
In fact I would do (from X):
sudo apt-get -d dist-upgrade

this command will download packages without installing them.
the logout and switch to the text console and run:
sudo apt-get dist-upgrade

---

### Post by JohnJackson on 2009-07-06
Stay logged in with an X-session for the wireless connection but do the upgrade in a text console.

---

### Post by plun on 2009-07-06
> **yelo3 said:**
> In fact I would do (from X):
sudo apt-get -d dist-upgrade

this command will download packages without installing them.
the logout and switch to the text console and run:
sudo apt-get dist-upgrade

Worked, Thanks !   ;)

I also needed to restart GDM

```
sudo /etc/init.d/gdm restart
```

---

### Post by kingborel on 2009-07-06
Awesome, everything went smoothly when apt-get update/upgrading from a tty.

---

### Post by jerrylamos on 2009-07-06
I took an easy way out.  Being forewarned, I booted in recovery mode.  With root prompt do dhclient to get the internet.  Then do broken packages.  That got the 2.6.31-2, gdm, the whole bit.

I did have to sudo update-grub to get grub.cfg to see the new kernel.

Thanks for all the warnings.

Jerry

---

### Post by autocrosser on 2009-07-07
No problems here--wired connection....everything went smooth--just rebooted after to get the kernel on line.......

---

### Post by inportb on 2009-07-07
I wonder... is it possible to use screen to get around this?

---

### Post by GeorgeVita on 2009-07-07
Hi to all!  I am still having problems with gdm.

I am using only 3G internet and managed to do all updates as per your instructions.
PC: EeePC 1000H single boot from HardDisk, clean install Karmic Alpha2
Updates: all till last hour from 'Main Server'
kernel: **2.6.31-2-generic #16-Ubuntu**
Gdm: **2.26.1-0ubuntu4**

After boot grub starts above mentioned kernel, the2.26.1-0ubuntu4 login window appears, it shows my username, I type the password and the:
**These windows do not support ... Gdm-simple-greeter** window appears. After a while Gnome loads and the above reappears as "metacity" with the same text. I close it.

The 1st time I am giving my password to a "sudo" command, a "logout" happens (black screen & disconnection) followed by a login window (as above). The "logout" comes ONLY once! After a reboot I can force it again just by opening a terminal window and using any "sudo .." command. The 'logout" comes by pressing the <ENTER> after password entry.

I tried all "tips" from this or other threads (like deleting the metacity.desktop file).

Also I remove/purge/autoclean etc. gdm package and install again with the same results. I noticed an error "the home directory '/var/lib/gdm' already exists. Not copying from '/etc/skel' after Adding group 'gdm'. I did not found this directory after removing gdm package so it is possibly created automatically on installation.

As there is always a possibility that something is going wrong with my installation, do you feel it is better to wait for the full Alpha3 and have a clean install or try next dist-upgrades?

Thanks in advance,
George

---

### Post by dinxter on 2009-07-07
started a thread for workarounds to the gdm random crash when typing bug for ease of finding. 
[http://ubuntuforums.org/showthread.php?t=1206717](http://ubuntuforums.org/showthread.php?t=1206717)

---

### Post by jerrylamos on 2009-07-08
Black screen of death with this gnome update.  Three times this morning bam black screen, no login screen, no command line from Ctrl-Alt-F1 or 2, nothing, dead altogether, no ssh, nothing works except power off.

What I was doing was firefox trying to enter a "Reply to Thread" on the last crash; the previous one was when trying to enter a comment on launchpad.

See launchpad bug #396843.  

I think it's this new gnome update because I got one "black screen of death" on each of three kernels, 2.6.31-2, 2.6.31-1, 2.6.30-10 all from the same boot and same gnome.

I'm entering this from intrepid dual booted....

Jerry

---

### Post by dgf on 2009-07-08
What if I haven't read this and upgraded within X which resulted in a restart of GDM during the update?
Might it something break, or is definitily something broken now?

---

### Post by Darkshade on 2009-07-08
> **dgf said:**
> What if I haven't read this and upgraded within X which resulted in a restart of GDM during the update?
Might it something break, or is definitily something broken now?

You should know better - if you can login normally and use your system then you're fine, if you can't, well, there you have your breakage :D

---

### Post by jerrylamos on 2009-07-08
> **jerrylamos said:**
> Black screen of death with this gnome update.  Three times this morning bam black screen, no login screen, no command line from Ctrl-Alt-F1 or 2, nothing, dead altogether, no ssh, nothing works except power off.
Jerry

I presume the only way to back this level of Gnome off is to re-install Alpha2 and then be very careful not to update gd(anything)?

Thanks, Jerry

---

### Post by Kobalt on 2009-07-09
Or reinstall from a Daily image instead of Alpha 2, so that you get all the recent updates to GDM.

---

### Post by camper365 on 2009-07-09
> **jerrylamos said:**
> I presume the only way to back this level of Gnome off is to re-install Alpha2 and then be very careful not to update gd(anything)?

Thanks, Jerry

Not upgrading gd(anything) could be dangerous, since gdb is not related to gdm at all (gdm is the debugger). You would be safe not upgrading gdm(anything) however.

---

### Post by Gina on 2009-07-09
After update problems, I installed today's daily build of Karmic on my AMD64 but still getting crashes, particularly from Firefox.  Also the grub 2 (1.96) although having found my 9.04 (Jaunty) system, won't boot it.  Meanwhile, I using my laptop for posting.

---

### Post by jerrylamos on 2009-07-10
> **camper365 said:**
> Not upgrading gd(anything) could be dangerous, since gdb is not related to gdm at all (gdm is the debugger). You would be safe not upgrading gdm(anything) however.
Thanks....
Anyway I just did sudo gedit /etc/default/grub, removed splash, did sudo update-grub and no more hangs????  There's an explanation of what damage splash does in launchpad bug#396226.

Since boot takes me 20 to 30 seconds depending on which pc I'm using, I could care less what it is displaying for that length of time, so long as it is not trying to set the lcd to a mode it can't display.

This pc has been up for 24 hours so far without a hang, compared to a few minutes before...

Jerry

---

### Post by dinxter on 2009-07-10
this should be fixed in 
gdm 2.26.1-0ubuntu5

> * Add 81_initial_server_on_vt7.patch: Force initial X server to go to tty7
    instead of tty1. This is an Ugly Hack until we have a cleaner solution for
    getty not to tramp over a running X server on vt1. This bandaids the
    immediate problem of the first X server being killed after a few minutes
    due to getty on tty1 timing out. (LP: [#396226]("https://launchpad.net/bugs/396226"))

 -- Martin Pitt <[ martin.pitt@ubuntu.com]("https://launchpad.net/%7Epitti")>   Thu, 09 Jul 2009 18:08:07 

---

### Post by motio on 2009-07-10
hi i have gdm 2.26.1-0ubuntu5 and steel i get the black screen
any new idea 
also i have the last update

---

### Post by nystire on 2009-07-11
I get a slightly different problem. I get to the log-in prompt in gdm, and after that I simple get a black screen. It's as if gnome-panel doesn't get started. If I manually start it (Gnome-Do DOES for some reason start), then I get my normal desktop, but the menu icons don't appear and the theme which I had selected is not used.

---

### Post by 23meg on 2009-07-25
Bumping this one after unsticking, in case it's still relevant to a few people.

---

