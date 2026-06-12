---
title: "[SOLVED] hotplug subsystem problems"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by Cloudy on 2006-07-04
Hi.

I know this topic's been done to death - I searched for solutions here on the forum and using google search. I just as recently as today installed Ubuntu Breezy Badger 5.10 on my Sony Vaio Desktop PC. I've tried most methods posted here and elsewhere to get around the problem of the bootup freezing at the "hotplug subsystems" part; I tried ctrl + c to bypass it (no luck), attempted to disable USB 2.0 functionality (once again, no luck) and could not disable the sound/modem option in BIOS (the closest I could get was to disabling the audio controller in BIOS). When I rebooted after that it wanted to try to completely reinstall Ubuntu? :confused: :-# 

I've yet to edit the boot-line in GRUB as has been suggested in another topic here (and I know I probably should try to do that before I make this topic) but I would like to know if there's anything I should know or if there are any other solutions to my problem that I may not know of before I go doing something I'm unfamiliar with like editing the boot-line. :-# 

Thanks! :D

---

### Post by Cloudy on 2006-07-05
well, I tried editing the boot-line but I get past the "rw init =/bin/bash" bit and it still freezes at the hotplug subsystem part after I boot, so I can't add snd_hda_intel & snd_hda_codec to the blacklist with nano. :S

---

### Post by Cloudy on 2006-07-05
ok!

I tried ctrl + c again and it worked this time! I know now that it was just trying to finish installing Ubuntu (I said in 1st post I thought it was trying to reinstall :-x) 

however, when it tries to finish installing packages it says that some packages could not be installed and stops at around 5% then brings me to a command line, no X or anything, with "ubuntu login:" prompt. I thought maybe I should try "sudo dpkg-reconfigure xserver-org" but I can't! When I try I get "sudo: unable to lookup ubuntu via gethostbyname()"

what should I do? :s

EDIT: I cant log in to root but i thought my user is supposed to have root capabilities? >.< maybe I misunderstood somewhere. always happens. XD

---

### Post by Cloudy on 2006-07-05
Help? :D
I really want to use Ubuntu on this PC. I have another PC that runs Ubuntu but the modem doesn't work and it's underpowered compared to this one. :-#

---

### Post by Cloudy on 2006-07-05
ok!

I ran the recovery mode thinking maybe I installed server somehow on accident & going off of [http://www.psychocats.net/ubuntu/nox.php](http://www.psychocats.net/ubuntu/nox.php)

I cd'ed into /init.d and did "gdm start" but I got 

**** (process: 7929): critical **: ve_config_get_sections: assertion 'config != NULL' failed**

I have my Ubuntu 5.10 CD in.
I'm really not sure what to do. Should I just try to reinstall all over again? #-o

---

### Post by Cloudy on 2006-07-06
Help :D? 
I really don't want to have to reinstall but that looks like it may be it.. >.<
Or I may have to wait on my Dapper CDs. Dialup makes me a saaad panda. ;(

---

### Post by Cloudy on 2006-07-07
Help? D;

---

