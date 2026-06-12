---
title: "upgrade to karmic, borked x-server &amp; update manager"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kadafi69 on 2009-10-08
Ok so I tried to upgrade to Karmic. The installation process ran and everything seemed to go ok. I rebooted and I was greeted with an X-server error and ubuntu is running in low graphics mode, error is:

> (EE) Failed to load /usr/lib/xorg/modules/drivers//radeon_drv.so
(EE) Faled to load module "radeon" (loader failed, 7)
(EE) No drivers available.

(note at this point the mouse-pad is working fine)

Next I select 'Run ubuntu in low graphics mode for just one session' (all the options just loop in a restart prompt.

I then get an error saying X-server is already running on display :0... yes or no. Selecting yes lets me move futher on. 

At this point the normal desktop loads, however by now the mouse no longer seems to work. Ive managed to check the mouse preferances and the touch pad is enabled.

I cant seem to get X to work in the server, it keeps giving me the first (EE) error from before.

I have also notice if I run sudo apt-get upgrade in the terminal, it reports 0 upgraded, 0 newly installed, 0 to remove and 455 not upgraded.

It seems like these upgrades are for Karmic, and I cant seem to force the upgrade either, it just crashes.

any ideas?

---

### Post by Peter09 on 2009-10-08
I think Karmic has a problem at the moment in that it sometimes reboots in the middle of an upgrade .....

Try going to recovery mode and selecting the command prompt. Then do the following.

```
apt-get update
```
```
apt-get upgrade
```

This will ensure that the update is complete. Then try rebooting.

---

### Post by kadafi69 on 2009-10-08
no joy there, it fails to find any of the packages, then aborts the process.

---

### Post by Peter09 on 2009-10-08
you could try

```
apt-get -f install 
```

this will try and fix any broken packages

---

### Post by Peter09 on 2009-10-08
if that does not help try removing all files in

> /var/cache/apt/*.bin or/and files in /var/lib/apt/lists

---

### Post by kadafi69 on 2009-10-08
that just tells me > 0 upgraded, 0 newly installed, 0 to remove and 455 not upgraded.

:(

---

### Post by Peter09 on 2009-10-08
Did you see the post regarding deleting the files?

Try that and the update, upgrade etc

---

### Post by Claus7 on 2009-10-08
Hello,

the message you received was exactly what I saw following exactly the same procedure of update as you did.

What happened? Your old xorg.conf file is altered.
What you have to do? You have either to create a new xorg.conf file on your own or search in /etc/X11/ the old xorg.conf which is supposed to be backed up, and put it as the original xorg.conf file. Don't care if you run in low graphics mode in order to do so. This is normal... Of course you can also alter these things butting from recovery mode.

I would suggest you not to delete anything from your new and shiny update.

edit:always lspci will help us to see if the new kernel has still the drivers of your graphics card...

Regards!

---

### Post by kadafi69 on 2009-10-08
just tried that and it now says > E:  Could not open lock file /var/lib/apt/lists/lock - open (2 No such file or directory)
E: Unable to lock the list directory

I think I may have deleted the 'lock folder in /var/lib/apt/lists/lock by accident. :/ its going from bad to worse!

---

### Post by Peter09 on 2009-10-08
Hi, while his x problems may be to do with the xorg.conf problem, his inability to upgrade from the command prompt in recovery mode is indicative of a larger problem.

---

### Post by kadafi69 on 2009-10-08
> **Claus7 said:**
> 
I would suggest you not to delete anything from your new and shiny update.

thing is, its not a new shiny upgrade, its still same old jaunty.

---

### Post by Peter09 on 2009-10-08
hi, looks like you deleted the lists directory, just do the following

> mkdir  /var/lib/apt/lists/lock

---

### Post by Claus7 on 2009-10-08
Hello,

> **Peter09 said:**
> Hi, while his x problems may be to do with the xorg.conf problem, his inability to upgrade from the command prompt in recovery mode is indicative of a larger problem.

I have faced problems during my update and in order to fix them I had to run the aforementioned commands of update as root. I still do not think that an update is necessary, yet if it is done, it should be done with root privileges. 

Now the fact that he erased the lock files I do not know which problems might have caused...

Regards!

---

### Post by Peter09 on 2009-10-08
HI Kadafi69 - my impression is that the system crashed or rebooted or something halfway through an update/upgrade - perhaps the op can confirm. If this is the case there will be lots of packages that are in an indeterminat state.

---

### Post by kadafi69 on 2009-10-08
> **Peter09 said:**
> hi, looks like you deleted the lists directory, just do the following

done that. now I get >  E: Could no open lock file /var/lib/apt/lists/lock - open (21 Is a directory)
E: Unable to lock the list directory

---

### Post by Peter09 on 2009-10-08
Hi Claus - he is doing this from recovery mode so he should be in superuser mode by default.

---

### Post by kadafi69 on 2009-10-08
> **Peter09 said:**
> HI Kadafi69 - my impression is that the system crashed or rebooted or something halfway through an update/upgrade - perhaps the op can confirm. If this is the case there will be lots of packages that are in an indeterminat state.


yeah the system rebooted, I just figured it was 'doing its thing'.

---

### Post by Claus7 on 2009-10-08
Hello,

> **kadafi69 said:**
> thing is, its not a new shiny upgrade, its still same old jaunty.

You mentioned at your first post that you installed the new karmic above jaunty. You rebooted your system and you were welcomed with a low graphics screen.

If something went badly then you you should follow this post:
[http://ubuntuforums.org/showpost.php?p=7905787&postcount=10](http://ubuntuforums.org/showpost.php?p=7905787&postcount=10)

Now, if your installation went ok, then the low graphics mode I think that is irrelevant with it. You have to see if the new kernel supports your pci graphics card driver and then to configure your xorg.conf file accordingly so as to take advantage of your graphics card.

Regards!

---

### Post by Peter09 on 2009-10-08
right lets do

```
rmdir /var/lib/apt/lists/lock
```
and then
```
touch /var/lib/apt/lists/lock
```

---

### Post by kadafi69 on 2009-10-08
ok, that worked but when I run sudo apt-get update I just get the W: failed to fetch *package* Could not resolve 'gb.archive.ubuntu.com'    etc etc

---

### Post by Peter09 on 2009-10-08
You will need to be on a wired network to do much from the recovery command prompt - can you get to a wired network?

---

### Post by kadafi69 on 2009-10-08
ok, so ive come out of recovery mode and went back to the desktop (low graphics mode) and ran sudo apt-get update and upgrade, it has now installed 2 new python packages, there are still 453 packages its not upgrading tho.

---

### Post by Peter09 on 2009-10-08
try the command

```
update-manager
```

se if you can get any more information on what is happening

---

### Post by kadafi69 on 2009-10-08
update manager scans, then gives me the option to partially upgrade or close. Choosing to partially upgrade just hangs on the update manager.

---

### Post by kadafi69 on 2009-10-08
well ive resigned my fate to a reinstall. :/

---

### Post by Peter09 on 2009-10-08
Sorry - got called away - did you get any further?

---

### Post by kadafi69 on 2009-10-08
I was going to give up and re-install. except the pc im on wont write an iso to disc. so ive had to scratch that idea, and if I dont fix the laptop by the time the g/f gets home I'll be in the dog house! so im giong back to the drawing board.

Ive tried Claus's solution to fix the xorg.conf and what a surprise no luck!

---

### Post by Peter09 on 2009-10-08
Are you sure the update manager is hanging and not busy?

---

### Post by kadafi69 on 2009-10-08
well it just goes back to the update panel being grayed out and the close button selected. 

is it worth trying to do a downgrade? if so how do i do that?

---

### Post by Peter09 on 2009-10-08
try - in a terminal issuing

```
sudo update-manager -d
```

perhaps it never got far enough to actually setup karmic

---

### Post by kadafi69 on 2009-10-08
ive just noticed when I run sudo update-manager and error pops up in the terminal
>  on_battery returned error: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.DeviceKit.Power was not provided by any .service files

same thing happens when I do update-manager -d. also when in the update manager, selecting either the 'check' or 'setings' just crashes it.

---

### Post by Peter09 on 2009-10-08
now that we have fixed apt try

```
sudo apt-get -f install
```

---

### Post by kadafi69 on 2009-10-08
no luck there either. reports '0 upgraded, 0 newly installed, 0 to remove and 455 not upgraded.'

---

### Post by Peter09 on 2009-10-08
Ahh well lets see if apt can upgrade

```
sudo apt-get -u dist-upgrade
```

---

### Post by kadafi69 on 2009-10-08
I thought i'd try and install one of the things from the list. So I did sudo apt-get install ubuntu-desktop, it ask to install a bunch of dependancies so i said yes. it installed and the asked me to restart, now it gets half way through the boot process and just hangs on a flashing curser. ARGH!!!

---

### Post by Peter09 on 2009-10-08
You need to get back to the recovery mode with a wired connection amd try the dist-upgrade.

---

### Post by kadafi69 on 2009-10-08
yep, just tried to get to recovery mode, it runs through a bunch of commands then stops at 'done' then I get a flashing curser. I've truely fubar'd it now!

---

### Post by Peter09 on 2009-10-08
Ouch ....... looks like its well and truly screwed. If you have an alternate CD there is an option to fix a broken system ...... other than that I think its a reinstall.

---

### Post by kadafi69 on 2009-10-08
yep, i think its a re-install as well. I'll have to try download a iso. Thanks for your help.

---

### Post by Peter09 on 2009-10-08
Hope all goes well

---

