---
title: "Loss of video on boot after 12.04 upgrade"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by andrewkirk on 2012-09-08
I upgraded my PC from 10.04 to 12.04 LTS.

Now the monitor loses the signal from the PC after the screen with the 'Ubuntu 12.04' label and the four orange or white dots. Nothing I do seems to bring the video back and I have to do turn the power off and restart.

My system is a 32 bit i386 dual processor PC with 4MB RAM and 500GB HDD, with several partitions, including two Ubuntu versions and one Windows.

On the first boot after upgrade it wouldn't let me login, not accepting the password. After searching for solutions I found one that said to go to command line and 
rm ~/.Xauthority*
sudo apt-get install --reinstall xorg

That came from here:
[http://askubuntu.com/questions/129246/after-12-04-upgrade-cant-log-in-although-password-is-correct]("http://askubuntu.com/questions/129246/after-12-04-upgrade-cant-log-in-although-password-is-correct")

After that I was able to login and operate in the upgraded 12.04. Then I downloaded and installed the Proprietary Drivers for my graphics card because the layout shown wasn't right for my screen. When I rebooted after that the problem of losing the video signal on boot happened.

I am at a loss as to what to do. I've tried booting into failsafe graphics mode and can get a bit further that way but it's always ended up crashing or hanging. 

I can access log messages from the boot via other OSes on the system. I'll attach the /var/log/syslog file and the /home/username/.xsession-errors file from the latest boot attempt. I've had to cut out the bits of the syslog that didn't look relevant because the forum limited me to 19KB per attachment file. the third of those files contains log messages all the way up to when I turned the power off.

I hope somebody can help. Thank you.

---

### Post by lincoln32 on 2012-09-08
what type of video card? I have had simular issues with the latest NVIDA
it will work with the basic driver but when adding the updates  it failed to a black screen. I just did not install the updated driver and all is well till they figure it out.):P

---

### Post by andrewkirk on 2012-09-08
The video card is ATI:

01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]

I would happily revert to the basic Open Source driver at this stage but don't know how to do that if I can't boot into the OS.

---

### Post by andrewkirk on 2012-09-08
I think this error log file may be the key one. 
/var/log/Xorg.failsafe.log
It's what happened when I tried to go into failsafe graphics mode from the Recovery boot option in GRUB.

I'll attach it to this post.
I hope  someone can help.

---

### Post by andrewkirk on 2012-09-09
Well I finally cracked it. I ran a purge of fglrx files by the following command.

sudo apt-get remove --purge fglrx*

Then a reboot and I had my video signal back, albeit without 3D graphics or the correct screen resolution. I'm still working on that.

---

