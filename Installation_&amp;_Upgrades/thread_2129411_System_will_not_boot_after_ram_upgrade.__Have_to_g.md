---
title: "System will not boot after ram upgrade.  Have to go back 2 versions of Ubuntu"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by huberthickey on 2013-03-26
I have an HP pavilion a1010y which was running Ubuntu 12.04.  I added two sticks of Ram which upped my system to 3 GB ram.  I then sought to boot and got nothing.  I then tried again and saw the Grub menu come up.  I attempted to boot into Recovery mode and -- nothing.  After playing around I found that I had previous versions of Ubuntu in my system and was able to boot into the version of 3 releases ago.  Later I booted into the recovery version and went through all the options on that page without fixing anything.  My son and I searched for help on the Internet and tried several solution possibities, but nothing worked.  
At this point, because I have never experienced anything like this,  I am stumped.  I have tried reloading Ubuntu only to find out that my version on the thumbdrive does not offer repair.  I have run through a couple of repair possibilities, but nothing resulted.  Since I do not understand what was damaged, or how, I am even more in the dark.  
Thanks for any help!
Hubert Hickey

---

### Post by dino99 on 2013-03-26
the easiest solution to know whats happening when you are booting, is to remove "quiet splash" from the boot line. Is your bios identifying all the ram sticks ? Are they identical : same model, same cas ? Depending on the sticks order on the mobo, results can be different (check your mobo doc), but /var/log/dmesg & boot.log might help you .

---

### Post by huberthickey on 2013-03-26
dino99[INDENT]                              Re: System will not boot after ram upgrade.  Have to go back 2 versions of Ubuntu
                          the easiest solution to know whats happening when you are booting, is  to remove "quiet splash" from the boot line. Is your bios identifying  all the ram sticks ? Are they identical : same model, same cas ?  Depending on the sticks order on the mobo, results can be different  (check your mobo doc), but /var/log/dmesg & boot.log might help you .         
Bios is identifying ram sticks and the correct amount of ram shows up in stats.  Both ram sticks are identical.  When I removed the new sticks and put in the old configuration,  the problem remains.
How do I remove "quiet splash"?  What do cas, mobo, mean? How do I access boot.log? 

Found boot.log :
fsck from util-linux 2.20.1 
/dev/sda1: clean, 711359/2346512 files, 2991915/9379328 blocks 
modem-manager[770]: <info>  ModemManager (version 0.5.2.0) starting... 
  
modem-manager[770]: <info>  Loaded plugin X22X 
  
modem-manager[770]: <info>  Loaded plugin Ericsson MBM 
  
modem-manager[770]: <info>  Loaded plugin Huawei 
  
modem-manager[770]: <info>  Loaded plugin Option High-Speed 
  
modem-manager[770]: <info>  Loaded plugin ZTE 
  
modem-manager[770]: <info>  Loaded plugin Samsung 
  
modem-manager[770]: <info>  Loaded plugin Wavecom 
  
modem-manager[770]: <info>  Loaded plugin Longcheer 
  
modem-manager[770]: <info>  Loaded plugin MotoC 
  
modem-manager[770]: <info>  Loaded plugin Gobi 
  
modem-manager[770]: <info>  Loaded plugin AnyData 
  
modem-manager[770]: <info>  Loaded plugin Option 
  
modem-manager[770]: <info>  Loaded plugin Linktop 
  
modem-manager[770]: <info>  Loaded plugin Novatel 
  
modem-manager[770]: <info>  Loaded plugin SimTech 
  
modem-manager[770]: <info>  Loaded plugin Nokia 
  
modem-manager[770]: <info>  Loaded plugin Sierra 
  
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd 
 * Starting AppArmor profiles       [240G  [234G[ OK ] 
Loading the saved-state of the serial devices...  
speech-dispatcher disabled; edit /etc/default/speech-dispatcher 
saned disabled; edit /etc/default/saned 
Starting preload: 

I looked at DMESG and could not understand any of it, but the last three lines say:
[   28.113610] hda_codec: ALC880: BIOS auto-probing.
[   28.828262] init: kdm main process (957) killed by TERM signal
[   28.880835] init: gdm main process (1000) killed by TERM signal 

Are there any key words to search for in dmesg that might help?

[/INDENT]

---

### Post by fantab on 2013-03-26
Most of the MOBO's have specified RAM slots to fill first. Like suggested see your Mobo's manual. Generally it is recommended to update your BIOS before any hardware upgrade.
The "two sticks" you've added; are they paired? or are they different sticks of same brand and specs?

Have you tried to reboot after you have removed the installed RAM? What happens if you remove the older RAM and just use the new 'two sticks'?

I have recently upgraded by adding more sticks and both Linux and Windows boot fine.

---

### Post by MAFoElffen on 2013-03-26
Just a word of experience from hard-knocks- 
I upgraded my RAM on on of my boxes... Had same problem with 12.04. Earlier versions would boot... My BIOS would see the memory... But-- It still turned out to be a defect in one of the chips- a spendee 2GB ECC registered and it was bad. Doing the memory test, it would get about 3/4's into that chip (enough that I started to think to end the test. thinking it was good) and it started throwing errors.

See if you can boot a LiveCD and test the memory. The LiveCD first menu and/or grub boots in minimal memory. If you can get it to boot to one of those... Another is you might find that not "all" memory chips from all manufacturers are compatible with all mobo's. Some are fennicy about who's memery they are using. (Example- IBM, HP and Gateway.) I do a lot of recycling and rebuilding. I usually look at the mobo RAM recommendations for vendors manufacturers/part numbers and crossover from there. I also look at the compatability lists from the RAM Manufacturers to see if they say there product works on a certain make /model board. 

Not as much an issue if I'm at the recycler- just grabbing another stick from the bin... but If I'm ordering for myself- that's one of the things I check and triple check.

Just a thought...

---

