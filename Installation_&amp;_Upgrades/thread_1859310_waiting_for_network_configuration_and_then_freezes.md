---
title: "waiting for network configuration and then freezes"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by skatona on 2011-10-13
upgraded from 11.04 to 11.10.  on reboot the system goes to ubuntu screen and then says waiting for network configuration, then for another 60 seconds, then goes black.  

I have also done a clean install from a cd and all works just fine.  however I would like to get my upgraded drive working as it has all my data and info on it.

any idea what needs to be fixed on the upgraded disk?  

Thanks.

---

### Post by megocode3 on 2011-10-13
I'm having the exact same issue. I upgraded now I can't boot. Same messages as you.

---

### Post by skatona on 2011-10-13
and then to add insult to injury, the hard drive that I did a clean install on, I also tried to install VMWare so that I could at least move my image(s) over.....  but noooooo, vmware would install but not configure in 11.10.  so here I am again back on windows.  if I stay on windows for a week I will have things back to normal and wont be coming back to ubuntu as my main os.  just too much trouble switching back and forth. I'm hoping someone can help out before that though.  I am able to get to the terminal once it goes to black screen, so hopefully it's not lost and can be fixed to actually boot.

---

### Post by teluma on 2011-10-14
Help! I am having the same issue.  "Waiting for network configuration" followed by an interminable message "Booting system without full network configuration".  I booted once into 11.10 upgrade, as the system did finally boot, however today it is seemingly not going to boot at all.

It wouldn't be such a HUGE problem if it wasn't for the fact that the home directory is encrypted so I can't get to my files via live cd or other installation.

---

### Post by PerroLOL on 2011-10-14
I'm having the same problem. I got it when upgrading to 11.10. I hope I can find a fix. This is pretty annoying.

---

### Post by robert shearer on 2011-10-14
I have had this occour on a couple of occasions recently and it is fixed by switching my router off, waiting a moment or two and switching it back on.

Sometimes a reboot is needed as well.

---

### Post by morgajx on 2011-10-14
Ive just got this error after upgrading from 11.04.

The reboot router thing didn't work for me

Andy

---

### Post by teluma on 2011-10-14
Has anyone here tried in Recovery Mode? This isn't working for me either, it just hangs on the recovery menu, or the recovery menu screen cracks up when I select an option from it!
One thing that is mysterious is that the system did manage to boot, once, after the upgrade. It took a while, so I don't understand what has changed since then.
 
Also, disconnecting the router has no effect whatsoever, my machine is STILL stuck on "booting without full network configuration".......

---

### Post by skatona on 2011-10-14
recovery mode does not work for me either.

---

### Post by schattenjager on 2011-10-14
Same here... With an if down - ifup sequence I get it to work again, but this is a server machine that runs headless...

---

### Post by petzoldf on 2011-10-14
[https://bugs.launchpad.net/ubuntu/+s...us/+bug/811441]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441")

Post #24 works perfect to resolve the problem

---

### Post by kentish on 2011-10-14
> **petzoldf said:**
> [https://bugs.launchpad.net/ubuntu/+s...us/+bug/811441]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441")

Post #24 works perfect to resolve the problem


And for me too :)

---

### Post by skatona on 2011-10-14
worked one time after one reboot and then the next one went right back to the black screen.

---

### Post by teluma on 2011-10-14
> **petzoldf said:**
> [https://bugs.launchpad.net/ubuntu/+s...us/+bug/811441]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441")

Post #24 works perfect to resolve the problem

Yes, this works great if you can log onto your ubuntu to carry out this task. The problem a lot of people are having, seemingly, is not being able to get into their system, therefore they can't carry out this fix!

I managed to do this by running Ubuntu from another partition, and then using the terminal, as owner of the problem installation, to follow the instructions given in post 24 of  [https://bugs.launchpad.net/ubuntu/+s...us/+bug/811441]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441")  Not an easy task, especially as my home folder was also encrypted.  Anyway the good news, for me, is that I have been able to boot into the problem Ubuntu, and have spent the last few hours moving all my precious folders to another partition!

If you want to try the method in the above link, try pressing ctrl+alt+F1 when the screen message gets to "booting system without full network configuration".  This will take you to the terminal command line.

GOOD LUCK!

---

### Post by skatona on 2011-10-15
unfortunately it does not work for everyone. I was able to do it and it started ....  once, then the next boot it was back to the black screen.  spent all day yesterday rebuilding a 1104 system. was able to move most of my files so I am back up.  but for some reason I am now experiencing over heating problems, to the point where it shuts down the system.  it might be time to find another distro or god forbid, go back to windows ....  oh well, can't win them all.

---

### Post by teluma on 2011-10-15
> **skatona said:**
> unfortunately it does not work for everyone. I was able to do it and it started ....  once, then the next boot it was back to the black screen.  spent all day yesterday rebuilding a 1104 system. was able to move most of my files so I am back up.  but for some reason I am now experiencing over heating problems, to the point where it shuts down the system.  it might be time to find another distro or god forbid, go back to windows ....  oh well, can't win them all.

Sounds like we had a similar day yesterday, Skatona, but so far the fix worked for me.  I am playing safe and installing 11.10 as new installation, upgrades always give me some degree of problems.

Is your Ubuntu on a laptop?  I am only asking as I have dual boots on my laptop, Windows 7 works great however Ubuntu (since 10.04) overheats and powers off randomly. So I am forced use Ubuntu only on my desktop, where it works great (except on days like yesterday :icon_frown:) and Windows 7 on the laptop.  Shame as I find Windows so clunky and time consuming!

---

### Post by skatona on 2011-10-15
> **teluma said:**
> Sounds like we had a similar day yesterday, Skatona, but so far the fix worked for me.  I am playing safe and installing 11.10 as new installation, upgrades always give me some degree of problems.

Is your Ubuntu on a laptop?  I am only asking as I have dual boots on my laptop, Windows 7 works great however Ubuntu (since 10.04) overheats and powers off randomly. So I am forced use Ubuntu only on my desktop, where it works great (except on days like yesterday :icon_frown:) and Windows 7 on the laptop.  Shame as I find Windows so clunky and time consuming!

Yes, I'm on a laptop. I have an ultrabay where I can put the 1110 drive in and the newly rebuilt 1104 in the main c drive. this allows me to move files back to the 1104 drive so that I could get back up and operational.  for the most part, I am done with that.  I will next install from disk 1110 and then try to move files to it in hopes that I can get a 1110 fully operational drive. only concern with that is that I have tried it once and could not get vmware to install due to the new kernel, but will give it another try today or tomorrow.  if I can get vmware to work on 1110 then I will move completely over to 1110.  

and I too seem to always have upgrade install issues.  never seems to work, always have to do a new install and then reinstall all my apps and files ....  a real pain.

Edit for the over heating:

I am on a lenovo W500 laptop, so I installed the ATI drivers and then also did the grub fix and so far the temp has not gone above 70C.  still a little warm, but has not shutdown .....  so far :)

---

