---
title: "Sound problem after fiesty upgrade"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by maethor on 2007-04-23
I've upgraded to fiesty and sound has stopped working. It's an old compaq deskpro with an ESS AudioDrive ES1869. When I try to unmute the the master control in Volume Control, nothing happens, other than a brief change in the icon at the bottome from muted, to unmuted to muted again. 

A quick check of dmesg ais showing a lot of "dsp_command: timeout (0xc0)" errors. There's also this:
[7011003.615267] es18xx: unable to grap ports 0x220-0x22f
[7011003.617804] pnp: Device 00:07 disabled.
[7011003.617829] es18xx-pnpbios: probe of 00:07 failed with error -16

---

### Post by pepsi_max2k on 2007-04-23
>> es18xx: unable to grap ports 0x220-0x22f

sounds like something else might be using the port range that your sound card needs. i think there's a way to reserve an i/o port range somehow, but i forget now and dunno if it'd work anyway :|

---

### Post by klwtamu91 on 2007-04-25
I have the same issue with that sound card. It worked fine with Edgy but Feisty is a no-go. I've checked the mdoules and modprobe.d/soundcard files and they havent changed.

The soundcard file has the following: 

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

I open alsamixer, but am unable to change anything. The master and Hardware Master are both muted and are staying that way.

Is there any way to find out what is using the 0x220 port? My dmesg shows the same as maethor's.

---

### Post by LDRoamer on 2007-04-28
The same thing has happened to me but so far I have not been able to fix it. If anyone has any suggestions I would appreciate it.

---

### Post by LDRoamer on 2007-04-28
I just checked the bios of my machine (an old Comaq Armada 1750 laptop). It looks like I can change the default port range in the bios  but I have no idea what I would put in there. If anyone can suggest something I can try I would appreciate it.

> **pepsi_max2k said:**
> >> es18xx: unable to grap ports 0x220-0x22f

sounds like something else might be using the port range that your sound card needs. i think there's a way to reserve an i/o port range somehow, but i forget now and dunno if it'd work anyway :|

---

### Post by Loki-uk on 2007-04-28
Newer kernels have the sound disabled by default to prevent crashes during installation all you have to do is re-enable your sound card.

This is for SB16's but it tells you at the end what to change for different sound cards. This is very easy.

[http://www.aotk50.dsl.pipex.com/install-ubuntu-sb16/install-ubuntu-sb16.htm](http://www.aotk50.dsl.pipex.com/install-ubuntu-sb16/install-ubuntu-sb16.htm)

Loki

---

### Post by LDRoamer on 2007-04-28
I wish it were so easy but it is just not the case. In my case I had this working perfectly with Edgy 6.10.  When I upgraded to Feisty it retained my configuration so it was loading the snd_es18xx driver using the correct parameters. Although the sound card shows up no sound comes out except for what sounds like a feedback howl. In my case at least there is definitely a hardware conflict that did not exist in Edgy. When I boot with the sound driver loading the computer gets very sluggish and takes a long time to load the desktop. It will take it a minute or more just to open a terminal window. If I comment out the sound driver the machine boots and works normally but of course no sound.  

Something is, in my opinion, broken in Feisty that is causing this problem.

QUOTE=Loki-uk;2553394]Newer kernels have the sound disabled by default to prevent crashes during installation all you have to do is re-enable your sound card.

This is for SB16's but it tells you at the end what to change for different sound cards. This is very easy.

[http://www.aotk50.dsl.pipex.com/install-ubuntu-sb16/install-ubuntu-sb16.htm](http://www.aotk50.dsl.pipex.com/install-ubuntu-sb16/install-ubuntu-sb16.htm)

Loki[/QUOTE]

---

### Post by dr_gap on 2007-04-28
Steps 1. 2. and 3. from 

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Getting_the_ALSA_drivers_from_a_.2Afresh.2A_kernel](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Getting_the_ALSA_drivers_from_a_.2Afresh.2A_kernel)

worked for me after weeks of poking and prodding.

Summary:
1.
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
2.
sudo apt-get install linux-sound-base alsa-base alsa-utils
3.
reboot

** there are special notes for Gnome and Xubuntu users.  on Kubuntu, the three steps above were enough.

-gary

UPDATE:
My Thinkpad went mute again, but this time my "fix" didn't work.

---

### Post by LDRoamer on 2007-04-28
Thanks for the tips. Unfortunately it didn't work for me. My sound driver is loading but its just not working.

lspnp -v reports:

05 ESS0006 multimedia controller: audio
        io 0x0250-0x0257

06 CPQb0ac multimedia controller: audio
        io 0x0220-0x022f
        io 0x0388-0x038b
        io 0x0300-0x0301
        irq 5
        dma 0
        dma 1

And then aplay -l lists:

**** List of PLAYBACK Hardware Devices ****
card 0: ES1869 [ESS AudioDrive ES1869], device 0: ES1869 [ESS AudioDrive ES1869]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

I can unmute the sound but all I get is some screeching noise out of the speakers.

---

### Post by otiina on 2007-04-29
have the same problem.... soundcard is being detected but the mixer wont unmute.

---

### Post by LDRoamer on 2007-04-29
I noticed the same errors in dmesg as was posted here earlier including the unable to grap 0x220. I went into my bios and change that port to 0x240. Now dmesg shows unable to grap 0x240. Something is broken - its more than just a configuration thing. I wonder if this bug has been reported.

---

### Post by dr_gap on 2007-04-30
Another clue:
While trying to find out if anyone is addressing this as a bug (not as far as I can tell from
[https://bugs.launchpad.net/ubuntu/feisty](https://bugs.launchpad.net/ubuntu/feisty)
but I don't know if that's an authoratative list) I ran across this rejected bug report:
[https://bugs.launchpad.net/ubuntu/feisty/+source/alsa-driver/+bug/84639](https://bugs.launchpad.net/ubuntu/feisty/+source/alsa-driver/+bug/84639)

I'm on a Thinkpad T41.  I went into the bios.  There was no specific entry for modem.  I've never used the serial port or parallel port, so I disabled them.  My sound came back.

-g

P.S.
I think I see different symptoms being reported.  Some hear screeching, some hear nothing and can't unmute, others can unmute but still hear nothing. I'm in the later category.   (And I plead guilty to not describing my system/symptoms fully.)

Is there one problem, or do different people have different problems?

--------------------------
UPDATE 5 May 07:
Again, my fix was temporary.  Apologies.

My latest:  perhaps I have the hibernate/sound kernel bug. There's a different hibernate system, outlined here:
[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

This simple work-around gets excellent reviews, and works for me for the time being.

---

### Post by LDRoamer on 2007-04-30
I am running Ubuntu on an old Compaq Armada 1750 laptop. Just for sh*ts and giggles I tried disabling stuff in my bios but no joy here. 

In terms of the screeching and no sound thing I should elaborate that if I change around the bios settings or I load the sound driver but without the approiate parameters I can unmute and get screeching. If I load the same configuration that worked under Edgy I cannot unmute. However no matter what I have done with configuration switchs or with changing bios parameters does not get me sound.  So far as I am concerniied Feisty has broken the sound on my old compaq with an es1869 chip. It worked perfectly under Edgy and it continues to work fine when I boot windows. Since this is not my only computer I can wait for a fix but it is a bit annoying.  The rest of Feisty is working just fine.

---

### Post by thelog on 2007-05-06
Hi,

I had the same problem when upgrading from 6.06.1--> 6.10 (probably working)--> 7.04
The faulty computer is an old COMPAQ DESKPRO with an es1869 chip (ISA bus)

With 6.06 it was difficult to made it works but it was possible with some modifications of etc/modules : adding "snd-es18xx" to the file.
and adding an  etc/modprobe.d/soundcard/snd-es18xx file containing :

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

And the sound was working at this time.
Don't remember if I made other modifications...

But after upgrade to feisty 7.04. The sound control was muted and i wasn't able to unmute.

==> dmesg : show an ...unable to grab IRQ.. message

And I wasn't able to find a solution with a configuration file change.

So I decided to try the "hard way" : 
I rebooted and change the BIOS configuration for the sound device to use a different free IRQ and memory zone.
Then I booted feisty and was able to unmute the sound control (beware : sound should be cranked !!)
:confused:  This made me think that the etc/modprobe.d/soundcard/snd-es18xx file is not used anymore because of the options... 

Now I'll try a reboot to check if it will always work.

Hope this helps...

[Edit]
After a reboot the sound was automatically muted but always ok...
So I had the following lines to the /etc/rc.local before the "exit 0" ;-)

amixer -q set Master 100% unmute 
amixer -q set PCM 40% unmute  

And now the sound is automatically unmuted at boot time...
I miss the tribal sound of the logon screen but now sound is working...

PS : I had install some alsa package but I don't think it change anything at this time.

Hope this "solution" will work for you...

---

### Post by LDRoamer on 2007-05-09
Thanks for this. I have tried what you have suggested here and have had no luck whatsoever getting my sound working (Armada 1750 laptop).  The best I can get is to get it to the point where I can  unmute the sound but then I get a terrible screeching. I tried changing everything I could i the bios but that got me no where. In my case I see, among other things, a message in dmesg that says cannot grap 0x220. So I go into the bios and change that to 0x240. I then get the message that "unable to grap 0x240".  I also see a message that the probe of the pnp bios failed and I may have to run with pnpbios=off. I tried that but it didn't work for me.  I did find out thought that it is still usiing the snd-es18xx file though as with pnpbios=off if I boot with just the snd_es18xx driver in the modules line and no configuration file that the driver does not load at all. If I include the snd-es18xx configuration file in modprobe.d then the driver loads but it doesn't work.  I have a few more combinations to try with the pnpbios=off option but I am not overly optimistic.

---

### Post by yotam on 2007-05-14
See my solution post in
[http://ubuntuforums.org/showthread.php?t=415115&page=2]("http://ubuntuforums.org/showthread.php?t=415115&page=2")

---

### Post by LDRoamer on 2007-05-17
Thanks for the suggestion. It doesn't seem to work with Fiesty however. I think the issue is deeper than that and only an operating system fix is going to solve this problem.

---

### Post by thelog on 2007-05-26
Finally, my solution wasn't very good.
I had sound but the quality was very poor a high volume (hiss, scrhhhh...)

I attempted to recompile the kernel with the es18xx driver directly in the kernel (not as module)
After a long (very long) build time... I booted on the new kernel but I had a message that indicated that i can't log (don't remember the exact message but it was like "cant load profile or disk full..." but my disk wasn't full.
The old kernel couldn't be use too... arghhhh... :(

So I decided to completely reinstall my system and stay on 6.06.

But I hadn't sound to because I needed to redo the actions i've done some time ago to make the sound work (recompile es18xx module from alsa-project and install it)
But at this moment, I realized that this was my problem : I needed to recompile the module with the latest kernel sources from 7.04.

So second install from scratch (a 6.10 this time I don't have the 7.04 CD burned), set 6.10 up to date (approx. 120Mo to download) and directly upgrade to 7.04 (about 650Mo...)
And reboot....

AND SURPRISE :p !!!!
**The sound is working with out any manipulation from the new system.**

Hope it will be your case.... There was probably an feisty upgrade recently that added sound to old ISA chip...

(?) Just a thing I need to look at : my system is a French one (as i am...) and the Update Manager is now in English....

Good luck.......

---

### Post by tsunamio on 2007-06-13
After upgrading from 6.1 to 7.04 I lost all sound.  The system still recognizes the soundcard, an onboard Intel, and alsamixer claims not to be muted.  I've also tried messing around with the switches and various inputs, turning them each and all on and off, but to no avail.  I don't have the dmesg errors listed above, and I've tried just uninstalling and reinstalling alsa-base etc.  Any suggestions?

herodotus@fragglerock:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

herodotus@fragglerock:~$ cat /proc/asound/modules  0 snd_hda_intel

---

### Post by tsunamio on 2007-06-13
Well, I "fixed" my problem by just going to the previous kernel.  Feels like cheating, though.

---

