---
title: "Grub Problems/Crashed PC"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by Christie_k22 on 2011-07-09
I have searched the forums and the web for 4 days now and have found  next to nothing about my problems. Someone Please Help me b4 I go  insane. . . . 

Move thread if needed please. I am unsure if this is the place for it.

History - the past month -
I had recently  upgraded to 11.04 and found my wireless not working. After over 3 weeks  of searching for a solution and trying everything I could think of I  finally reinstalled 10.04. About a week ago I decided to upgrade to  10.10. In the middle of the upgrade the electricity went out. It took me  a couple hours to fix everything (as far as I knew) and do the upgrades  and all. (I am not sure if that had anything to do with my problems). 

Everything  seemed to be working fine (inc the wireless) so I moved everything from  my 2nd and 3rd hdd (backups) back over to main hdd and proceeded to  install my usual programs which also included PlaneShift. I noticed  there was an issue within PS where icons were showing up as white boxes.  I continued playing for a few hours and the whole computer froze on me.  I got on my laptop and did some research finding that it was probably a  graphics card issue. I tried the integrated and it worked fine on that  but ran extremely slow so I decided to try a graphics card a friend gave  me and installed it. 

Everything seemed to work fine for a  couple days then one night while playing PS everything froze again. I  restarted again and within 20 minutes of being on the computer (not on  PS tho) I was browsing the web and it froze on me again. 

Problem -

This  time when I restarted I got "error: unknown filesystem, grub  rescue>". After searching for 2 days  (in between college) for  multiple "solutions" I sat down today to try and fix it. With every  solution I would get stuck. I could not mount sda1 in order to reinstall  grub. When I boot to live cd I can use the disk utility to see the HDD  and the partitions on it however I can not mount it still. I ran a scan  which said that it is healthy and then tried to click on edit or  something of that sort and the live cd froze on me. After rebooting to  live cd I went to gparted and it shows file system is unknown there. One  of the things I found said that I needed to take the "boot" flag off.  It let me but didn't do anything to allow me to mount the drive. I am  now into my 5th week of not having a working desktop. I need to resolve  these issues as soon as possible. 

Resources -

[http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/](http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-unknown-filesystem-grub-rescue-781125/)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://www.dedoimedo.com/computers/grub-2.html#mozTocId842078](http://www.dedoimedo.com/computers/grub-2.html#mozTocId842078)

Issues - 

I  have no problem going back and reinstalling everything and 99.9% of my  data is backed up on my other 2 hdd's still so that isn't a big deal.  What is a big deal is that I have saved a few important things  (totalling no more than 50mb) on that drive and really need to get those  things off the drive before reinstalling. 

Hardware - 

Dell Inspiron 530
2.66ghz Intel core 2 duo
4 GB of Ram 
ATI  Radeon X300 SE, 128MB - old graphics card
ATI Radeon B276 HD 2400xt 256MB - new graphics card

As always any help is much appreciated!

I just gave up . . . my papers are due tomorrow and the other things I worked on aren't important enough to spend even more time than it would take to redo them in trying to fix this thing. I reinstalled and rewrote my papers and am now working on redoing the other things and re-setting-up my computer again. I hope someone finds out what happened and a solution for it in case it ever happens again to me or anyone else for that matter.

---

### Post by Christie_k22 on 2011-07-10
So I reinstalled and have been working for a few hours on setting everything back up and everything has worked fine . . . I was on firefox trying to DL PS again and it went to black screen with mouse showing loading but stuck in one position and said . . . 

speech-dispatcher disabled: edit /etc/default/speech-disatcher
*pulseaudio configured for per-user sessions
saned disabled: edit /default/saned
*enabling additional executable binary formats binfmt-support /dev/sda1: clean, 154900/38330368 files, 3474498/153318400 blocks 
*starting apparmor profiles 
skipping profile in /etc/apparmor .d/disable: usr.bin.firefox

*setting sensor limits

*checking battery state


Sorry if that is not exact I was trying to read it from a picture I took while posting in a different room. 

so Im guessing there is still a problem . . . 

Now that I am getting something more than before I will look for that but again any help is much appreciated.

---

