---
title: "Help - Upgraded to Ubuntu 10.04 through VMware Player 3.0 from Ubuntu 9.1"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Troxer on 2010-05-01
I need help urgently. I had installed Karmik Koala on VMware® Player 3.0.1 build-227600 and it ran perfectly well for four months. 

Today I upgraded to Lucid Lynx (lts) from within the VMware Player. The virtual machine restarted after the installation, now I can't direct my keyboard input to log in to my Ubuntu account. The mouse works but not the keyboard. How do I resolve this mess?

My email id is [email]forprotection2525@gmail.com[/email]

---

### Post by jackashe on 2010-05-03
hi. same problem here.  saw it with a 10.04 beta but didn't complain anywhere.  now I updated a 9.10 version and I see the problem.  its not specifically keyboard because if you click power icon and choose console login, the keyboard works.

---

### Post by wandernot on 2010-05-03
> **Troxer said:**
> I need help urgently. I had installed Karmik Koala on VMware® Player 3.0.1 build-227600 and it ran perfectly well for four months. 

Today I upgraded to Lucid Lynx (lts) from within the VMware Player. The virtual machine restarted after the installation, now I can't direct my keyboard input to log in to my Ubuntu account. The mouse works but not the keyboard. How do I resolve this mess?

My email id is [email]forprotection2525@gmail.com[/email]

i just ran into the same problem. I was running vmwareplayer 3.0.0 so finally upgraded it and it shows the same problem. Unfortunately I don't have the console login option showing on the power button. a windows XP install with the same player versions have had no problems. The host is ubuntu 9.10-64bit

---

### Post by jackashe on 2010-05-04
in Kde at the login prompt there's that button to power down (red) and if you click it then one of the options is a console login.  then you can login.  I tried to find how one could enable KDE auto-login via command line tools, but I only found GUI tools... :(

---

### Post by wimmme on 2010-05-04
same here :confused:

---

### Post by jackashe on 2010-05-05
crap.  from the command line, I installed ubuntu-desktop (alongside kubuntu-desktop) to see if that has the same problem.  It does, and in grm there's no more "console login" option that I can find!! There's an option for an on-screen keyboard but it hides the keyboard immediately (presumably because one is not logged in).  Sucky

---

### Post by jackashe on 2010-05-06
I found some kind of work around!  in gdm, theres a way to open the accessability options as I mentioned earlier.  if you turn on the virtual keyboard, it disappears.  But if you leave it on and reboot, it is there on login!  now you can click-type your password (feels crazy insecure!) and after login the keyboard works ok!!!!!!!
EDIT: keyboard works in gnome, but not in KDE.

---

### Post by pintod on 2010-05-06
> **jackashe said:**
> I found some kind of work around!  in gdm, theres a way to open the accessability options as I mentioned earlier.  if you turn on the virtual keyboard, it disappears.  But if you leave it on and reboot, it is there on login!  now you can click-type your password (feels crazy insecure!) and after login the keyboard works ok!!!!!!!
EDIT: keyboard works in gnome, but not in KDE.


If you use the procedure above and then once logged in the system update the keyboard settings system-->preferences-->keyboard

select the layout tab.  I noticed the keyboard model type is blank.  I updated mine to be generic 101-key PC since I didn't see anything remotely related to my laptop.  After I did this my keyboard worked as expected and upon reboot I was able to type my password into the gina

but even though I've been able to get into the system the response time is extremely slow and the system seems to hang... not sure if it's due to the upgrade or what...  may be time for a clean install.

Hope this helps others

---

### Post by mkramer on 2010-05-07
Thanks, I hit the same problem.  This got me in to VMWare, but I couldn't get my keyboard to stick by using generic 104

---

### Post by Crimm on 2010-05-10
For a fresh install this is what I did:

[http://debugge.com/articles/ubuntu-9/no-keyboard-with-vmware-playerworkstation-and-ubuntu-1004-11/](http://debugge.com/articles/ubuntu-9/no-keyboard-with-vmware-playerworkstation-and-ubuntu-1004-11/)

For a currently running one; this helped:

[http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/)

The idea being to use the Virtual keyboard to get in and edit this file:

> /etc/default/console-setup

Find and replace:

> <from original file>
XKBMODEL=”SKIP”
XKBLAYOUT=”us”
XKBVARIANT=”U.S. English”
XKBOPTIONS=”"

<changed to this, matching other linux installs>
XKBMODEL=”pc105&#8243;
XKBLAYOUT=”us”
XKBVARIANT=”"
XKBOPTIONS=”"

I haven't tried that; the only thing I got working was the new installation.

Good luck to all!

---

