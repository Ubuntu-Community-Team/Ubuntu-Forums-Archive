---
title: "ibex on asus M70vmX1"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by t_e_r on 2008-10-12
My third ubuntu install, first ibex install.
I encountered some problems, but not enough to warrant any bug report. Just wanted to post here to add to the ibex installation history.

This asus machine is no eeepc, very big, very heavy, but cool, literally. It replaces a R40 thinkpad that's having old-age hot flashes, and can go any day.

First dilemma, being a relative new Ubuntuan (still also a Debian), is whether to install heron or ibex. In Debian, where release occurs every 2 years, instead of 6 months, a release upgrade can be quite disturbing. This is an install for a friend who will use it for business, so  I wanted to minimize quantum jumps, and instability. I chose to install the Oct.3 beta ibex, rather than the heron, or the latest daily build. The reasoning is that there will only be one jump, the initial installation. Thereafter, the upgrades should be incremental. The beta release carries a clear statement of the changes and known problems. Short of reading the bug tracker, the daily builds are too hard to characterize. I was able to get some reassurance by asking at freenode#ubuntu+1.

This report is not about how I vetted every jeejaw on this machine, and it seems to have everything, but is about the pits I fell into, and how others can avoid them.

First, if you are dual-booting wista, DO NOT resize its partition in ubuntu. If you do, you will have a long baby-sitting session with the recovery disk. (The surprising thing there is that the drivers are 32bit). You then defrag and shrink it in wista. But you will not be able to get down below 76 GB. That is OK, because the M70 has a 320GB disk. And when you blow it later, you don't get too tiny a partition. You cannot use the pretty orange-green-blue diagrams that the installation partition editor draws, but must manually partition the remainder free space into a generous swap and an ext3 for /.

If you have become irritated from the baby-sitting, there is nothing quite like the fire alarms that go off at random on the numerous times that you have to either boot into the livecd, or into the installed ibex. Frantically pressing the mute or volume down buttons has no effect - you must immediately abort the boot. After a few of these, I realize the alarms will be consistently accidental. The work around is to turn off usplash during boot, by editing the grub menu.lst.

The installation is very smooth, and swift, compared to the prior baby-sitting. Hats off to ubuntu.

My eyes are now hurting from the too-bright big LCD (1920x1200). I bring up the brightness applet - but it has no effect. The brightness is automatically adjusted from the readings of an ambient light sensor. You have no say about it.

Almost immediately, the notificator tells me there are about 280 upgrade already (that's the amount of work accomplished in one week by the release team!). The upgrades go smoothly, except towards the end. The notificator seems to jump the gun by prompting you to reboot before the initrd.img has been completely rebuilt, and then the update manager just sits there, instead of closing and going away. I check to see that the initrd.img has indeed been rebuilt, and the update manager is not doing anything. So now I sheepishly reboot, hoping that I haven't encountered one of those nasty beta bugs that I have been warned about. Somewhere during this, there seems to have been some notice about installing some proprietary driver for the nvidia GeForce 9600M, but you were too hassled to attend to it.

Next I try to activate the fabulous compize special visual effects. It puts up a splash saying it's looking for the driver, and then hangs. I force the preference window to quit. I am prompted to do more upgrades, and now I can show off the special visual to my friend, who is duely impressed. (Looks like they are fixing it as you install!)

Next I tried to configure printing - having had some problems with it before. cups printer are no longer part of the default categories of printers. Specify the full URI of your cups server. Scanning is a breeze, just edit /etc/sane.d/net.conf with your scanner host(s). (This assumes that cups and sane servers are already properly set up on your ethernet.)

openoffice is at the same version as heron's, and so just dropping the .openoffice.org2 folder in place works. Here is when I suspect that by specifying Vancouver B.C. as the time zone, I may have inadvertently implied a locale of English-Canada. I correct the locale by System->Preference->Language Support.

Same for mozilla/firefox.

I leave moving my friend's evolution till the very end. On initial launch of evolution, I ask to restore what I have backed up from the prior evolution. It is a tar.gz of .evolution. After extraction, I read a notice telling me that the summary format has been changed to sqlite (I did not understand what I read), and to be patient while evolution tries to do some kind of conversion. Then that notice disappears and there is an indefinite silence. When I click on evolution again, this same notice flashes for some ms., and disappears again. It looks like evolution-data-server, evolution-alarm-notifier and evolution-exchange are still running. A folder.db file continues to grow in .evolution/mail/local. But apparently evolution has crashed. The amount of mail being converted is about 500MB. Googling nets one post which indicates someone else has also encountered this problem. The workaround is to move the big mail folders out of .evolution. Make plenty of copies of whatever is precious. Delete all *ev-summary*. Now evolution will launch, and everything else besides the big mail folders seems to have been restored. Now put evolution off-line, so that on next launch, no new mail will be processed. Quit evolution, put the big mail folders back in, without the *ev-summary*, of course. Re-launch evolution. Evolution will rebuild the summaries as sqlite databases. Check everything. Now put evolution back online, and do a send/receive.

I see several items in /var/crash. I read that you can use apport-gtk to report these crashes to launchpad, but there is no apport-gtk app, although aptitude shows it installed. The crashes are supposedly in compize, but they did not cause gnome to crash.

---

### Post by kdorf on 2008-10-15
Thanks for posting your experiences with an ASUS machine. I too am running Ibex on one now and things work fairly well if you know how to hack it.

One thing is that I disabled the splash in menu.lst and I still get the "fire alarm" that you describe on ocassion. Any thoughts?

EDIT: Another (minor) annoyance is that when I shutdown using the GNOME gui it emits one loud beep, which is pretty disruptive. However, if I run init 0 in a terminal it does not beep. Could this be a GNOME bug?

---

### Post by Mgiacchetti on 2008-10-20
> **kdorf said:**
> Thanks for posting your experiences with an ASUS machine. I too am running Ibex on one now and things work fairly well if you know how to hack it.

One thing is that I disabled the splash in menu.lst and I still get the "fire alarm" that you describe on ocassion. Any thoughts?

EDIT: Another (minor) annoyance is that when I shutdown using the GNOME gui it emits one loud beep, which is pretty disruptive. However, if I run init 0 in a terminal it does not beep. Could this be a GNOME bug?

you have to disable usplash via startup manager.


I have found that you must use xawtv for the camera and to get the ambient light sensor, just 

```

sudo su
echo 10 > /sys/devices/platform/asus-laptop/ls-level
echo 0 > /sys/devices/platform/asus-laptop/ls-switch

and 
echo 1 > /sys/devices/platform/asus-laptop/wlan
to turn your wireless on

echo 0 > /sys/devices/platform/asus-laptop/bluetooth
to turn your bluetooth off.

```

---

### Post by Mgiacchetti on 2008-10-20
Also, I have yet to get the built in microphone working.

---

