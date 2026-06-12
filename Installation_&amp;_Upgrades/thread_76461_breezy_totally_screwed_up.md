---
title: "breezy totally screwed up"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by eewald on 2005-10-15
after using different linuxes for four years and doing a clean breezy install last night i must say i am disappointed and confused: haven't seen so much problems in several years already. 

list of issues: 
* system hangs on bootup process for about 1,5~2 minutes (at the module loading stadium) and falls back to pure text mode without that fancy logo. 

* really bad perfomance occasionally: when hard disk is busy, even mouse starts lagging behind about half a second. 

* no sound at all, altough soundcard is properly detected 

* wrong localisation data: weeks don't start at sundays here in estonia and i **can't **configure it myself. i have ranted several times about this and even reported a bug, but that was marked as "wontfix" (!?)

---

### Post by eewald on 2005-10-15
are there too many questions or are these too difficult questions? :rolleyes:

---

### Post by dcostelloe on 2005-10-15
I think everyone has left.

I had to re-install and now my mail server is down and out of commission over two libs.

Very impressive

---

### Post by az on 2005-10-15
[QUOTE=eewald]are there too many questions or are these too difficult questions? :rolleyes:[/QUOTE]
Well, they are not really questions.  I am sure that most people are not experiencing what you are experiencing.


What happens when you boot?  Does it not boot, or does it just drop you out of bootsplash?  If, for example, hotplug is taking a long time to start something, it will do this.  Do you have any hotpluggable hardware?

Bad perfromance:  How much ram do you have?  If you have at least 128 megs, you should not have bad performance.

No sound:  What card do you have?  Is it muted?

Localisation:  There are always details about a bug that is labelled "wontfix"  WHat are they?

---

### Post by az on 2005-10-15
[QUOTE=dcostelloe]I think everyone has left.

I had to re-install and now my mail server is down and out of commission over two libs.

Very impressive[/QUOTE]

Can you be more vague, too?  What mail server and what libs?  Are you using the proper repositories?

Ubuntu is very impressive, actually.

---

### Post by Samuel on 2005-10-15
i did a fresh install of breezy the day it came out and it was also horrible, net downloads was slow, lots of errors, i reformatted and reinstalled and all was fine, dont have a clue what went wrong but im glad i gave it a second shot, on a clean install you have nothing to loose but 20 mins or however long it takes you to reinstall  better luck next time ;)

---

### Post by dtfinch on 2005-10-16
I'll give it a shot I suppose.

[QUOTE=eewald]* system hangs on bootup process for about 1,5~2 minutes (at the module loading stadium) and falls back to pure text mode without that fancy logo.[/QUOTE]
Probably network related. I can't think of anything that'll wait 2 minutes before timing out though. See how fast it boots with ethernet unplugged.

> * really bad perfomance occasionally: when hard disk is busy, even mouse starts lagging behind about half a second.
Enable dma on the disk if you haven't already. I've had a couple instances of disk I/O stopping a system with dma turned off, but most times things work fine either way. Run "sudo hdparm -d 1 /dev/hda" and see if that speeds things up. If it does, edit /etc/hdparm.conf to make it permanent. They say it's not on by default because it's hard to identify hardware that doesn't support it well. Linux has a blacklist for drives not supporting dma, but sometimes other hardware is a factor. Windows itself uses a trial and error approach towards dma, which for a while lead to many systems slowing down over time until the owner gets fed up and buys a new system.

> * no sound at all, altough soundcard is properly detected
Check the volume. Run "gnome-volume-control". On mine I think I had to increase the headphone volume, which unlike the speaker volume was muted by default. This system is too cheap to have a seperate speaker jack. It's a Dell with amplified speakers plugged into a headphone jack.

> * wrong localisation data: weeks don't start at sundays here in estonia and i **can't **configure it myself. i have ranted several times about this and even reported a bug, but that was marked as "wontfix" (!?)
No idea here. I thought this was app specific. Evolution has this option in its preferences, which on mine defaulted to monday.

---

### Post by ProPilot on 2005-10-16
I have the same boot-up slowness except it 'slows' when trying to set the clock to the ubuntu clock. Whether or not it finally sncyros the clock (network connected or not) it takes 2 to 3 minutes to determine the status.

How does one turn off this boot feature?

Also during this 'slow' period the screen changes from the nice boot screen to a terminal screen - does not affect performance or the boot just a little odd.

---

### Post by mohaham on 2005-10-16
[QUOTE=ProPilot]I have the same boot-up slowness except it 'slows' when trying to set the clock to the ubuntu clock. Whether or not it finally sncyros the clock (network connected or not) it takes 2 to 3 minutes to determine the status.

How does one turn off this boot feature?
[/QUOTE]

install Boot-Up Manager...
check the below link
[http://ubuntuguide.org/#bum](http://ubuntuguide.org/#bum)

---

### Post by ProPilot on 2005-10-16
mohaham

I installed BUM but it will not let me 'turn off' ntpdate. Any other idea?

Thanks

---

### Post by dtfinch on 2005-10-16
sudo chmod 644 /etc/init.d/ntpdate

---

### Post by ProPilot on 2005-10-18
Thank you. I executuded your suggestion however BUM stil does not allow me to 'turn off' ntpdate. Bum produces the following error when trying to turn off ntpdate
"editing in run level S is not allowed! playing with rcS.d symlinks is an administration activity requiring deep knowledge of the runlevel system"

Needless to say I do not have that knowledge.

I would like to turn off the sync function on boot so far I am unable.

I have found the answer to my question execute the following command
sudo update-rc.d -f ntpdate remove

also refer to [http://ubuntuforums.org/showthread.php?t=77422](http://ubuntuforums.org/showthread.php?t=77422) for further info 

sudo update-rc.d ntpdate start 51 S 2 to restore the command when needed.

---

