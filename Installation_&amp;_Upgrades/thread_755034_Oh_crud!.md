---
title: "Oh crud!"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by smith_fan on 2008-04-14
I just about finally had my sound problems fixed on a Toshiba laptop with Ubuntu 7.10 when I attempted to add KDE 4.02 to the mix.  Kubuntu wasn't exactly working right (it kept switching to Gnome after logging-in) so I figured I'd take it off and try it again when 8.04 was out.  In Synaptic, I did a search for 'KDE' and went through the list marking for removal every package with a shaded box and Ubuntu logo beside it.  After applying the changes, I no longer have a GUI—just a command-line.  Normally, I'd just do a re-install, but I had made numerous customizations in that installation that I'd terribly hate to lose.

I'm sure that linux has got to have someplace I can go to “undo” my ignorant, hasty, and crippling package actions.  I'm not expecting anything like Windows' System Restore, and I'm willing to do the manual work.  But I'm not sure where I would find such a *change log*.  Can anyone please give me some guidance regarding this situation?  I'd be forever grateful!

Thanks so much!,
Darin

---

### Post by PmDematagoda on 2008-04-14
Execute:-
```
sudo aptitude install ubuntu-desktop
```
and see if that solves your problem.

---

### Post by tvtech on 2008-04-14
try 
username@localhost:~$sudo apt-get install gdm

GDM = gnome display manager  that should reconfigure it as well as reinstall it. the display manager that is.  
 at your command prompt 

if that's not quite what your looking for most of your log files are located in uhh well everywhere do a 

username@localhost:~$ locate log

it will show you where all of them are located and you can check out each one 
your main sys log is located or should be on 7.10  @ /var/log/syslog
along with all your other logs pretty much everything should be in your /var folder.  if you've got lots of customizations you should be able to use a rescue cd back up your /home directory including and especially all hidden files and then reinstall from there.  just double check before you do that some customizations may not be saved using that method.

---

### Post by smith_fan on 2008-04-14
Hey guys,

Thanks so much for your quick responses and excellent instructions!  I ended-up with the following message:  “E:  dpkg was interrupted, you must manually run 'dpkg –configure -a' to correct the problem.”  I tried that, but it gave me some message about being root.  Please remind me--how does one switch to root?

Thanks again!, :)
Darin

---

### Post by Pumalite on 2008-04-14
Run:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by smith_fan on 2008-04-16
I've made some progress using a combination of the previous recommendations.  Unfortunately, system still boots up to a prompt.  When I executed 'sudo apt-get upgrade', I got a flowing textual screen that had some of the following:
“Restarting Squid HTTP proxy squid
FATAL:  Could not determine fully qualified hostname, Please set 'visible_hostname'
Squid cache(Version2.6.STABLE14):  Terminated abnormally.
Aborted (core dumped)
[fail]
setting up rsync(2.6.9-5ubuntu1.1) ...
darin@Belinda:~$
“

The 'sudo apt-get update' command *did* prompt it to download about 60 MB of 'previously deselected packages', but something is hanging it up when it comes to applying the downloaded info.

Now I need help with fully-qualifying a hostname.  Could someone please explain this “Please set 'visible_hostname'” business to me?

Thanks again!,
Darin

---

### Post by smith_fan on 2008-04-18
When I attempt to install ubuntu-desktop, it tells me it's already installed and returns me to a prompt.  Just for kicks, I tried the same command but added a 'k'.  I told it not to change the default window manager, so now it boots with a pretty blue splash screen but still takes me to a prompt.  TV, when I executed your suggestions, it connects with an Ubuntu server and then tells me it's already at the latest version and then takes me to a prompt.

Finally, when I run the last series of commands, it connects to a server and fetches 4B (I assume that's bytes-?) and then ultimately me to a prompt.

I feel completely helpless w/o a GUI.  Can someone please instruct me how to un-screw things up?

Thank you so much!

Darin

---

### Post by Pumalite on 2008-04-18
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by smith_fan on 2008-05-10
I very much appreciate your input, Pumalite and others! I had my linux-using brother-in-law have a look at it. He ended-up installing a bunch of modules and then reconfiguring X. Between my last post and now, I attempted to install Kubuntu but told it not to switch the default window manager. Now, when I choose to boot linux I get a pretty blue 'Kubuntu' splash screen, but to log-in it ultimately it takes me to my familiar gnome desktop. I've tried installing Kubuntu, but the update text tells me that 0 packages are selected to be upgraded.  Also, the Update Manager finds no available updates even though everything is still at a 'Gutsy' version. OOo still launches with a '2.3.0' splash even though I downloaded the 2.4 updates that it finally noticed several days later.

I plan to follow along on that excellent site you referenced and create a dedicated Home partition for my settings. But, I need to figure out what all I want to do in the way of partitioning. My intention is to have XP Pro as my primary Win-32 platform, but I'd like to keep this Vista installation, too. From my reading I figure on needing 2 GB's as swap, but that's as far as I've gotten with the figuring. Currently, there is 31.2 GB used and 16.6 free. That does not include the 10.09 GB XP partition (which I want to resize) or the Ubuntu stuff (14.43 GB with 580 MB swap). Do you have any suggestions for how I should proceed, sir? How big of a 'Home' would you recommend? Would you agree that a fresh linux install would be the easiest way to fix the penguin-related oddities that my ignorant messings have created?

Thanks so much, again, for your assistance!

~D~

---

### Post by PmDematagoda on 2008-05-11
About the splash screen it is something that can be easily fixed by changing the default for usplash-artwork.so(or something similar). About the problem where you log in to GNOME instead of KDE, you need to select KDE in Sessions at the login screen which will choose KDE as the desktop environment.

---

### Post by smith_fan on 2008-05-13
After switching the session to KDE, I've decided that I'm much more comfortable in gnome at this point.  Can you please tell me how I can make it the default so that it shows the orange splash again?

I still haven't figured-out the partition situation, yet, but I was wondering if there was a straightforward way of installing Hardy that leaves my current settings intact?  So far, I've resisted the temptation to try installing gnome via Synaptic, but Update Manager still lists no available updates.  Nothing gets upgraded via a Terminal window.

I would greatly appreciate any good resources and/or references about partitioning & multi-booting anyone might have to pass along.

Thanks!,
~D~

---

