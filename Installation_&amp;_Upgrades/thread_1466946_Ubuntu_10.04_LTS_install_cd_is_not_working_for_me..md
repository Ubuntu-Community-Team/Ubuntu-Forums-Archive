---
title: "Ubuntu 10.04 LTS install cd is not working for me."
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by D-Farmer on 2010-04-30
Hello
   I burned the ubuntu-10.04-desktop-i386.iso to a cd using winders xp and ISO recorder V2. When I boot from the cd it will freeze at the screen with the picture of a keyboard = and a person in a circle at the bottom if I do not press anything(the word ubuntu and the logo never appear in the middle of the screen). If I press a key before that screen I get the language select menu and after I select english, the menu appears showing options such as try without installing and install etc. At this point all of the function keys work fine and do what they should. The only option on this menu that works is to boot from first hard disk. All other options causes it to freeze and I have to press ctrl+alt+del to reboot. I am unable to check cd for errors because that freezes it too. This is on a hp dc7100 sff. I have also tried on a compaq c700 and it seems to work fine until it gets to that menu and then it won't let you select any options. like your not hitting the enter key at all. It doesn't freeze though. Afterwards you can still highlight another option but again, hit the return key and nothing...
  Is this common? Does anyone know how to fix it? I have really been looking forward to this and will appreciate help.

I have never used ubuntu before, I used freespire once... I forget what version. I have been a slackware user for several years now. That is about the extent of my experience.

---

### Post by D-Farmer on 2010-04-30
I wasted my first post on embarrassment.

I just looked at the size of my iso...... 210MB, I believe the full image would be about 699.4MB. That's what I get for leaving the house while it was downloading.

Sorry guys.

---

### Post by aysiu on 2010-04-30
Here are a couple tips:

[Use BitTorrent to download the .iso instead of just downloading it straight](http://www.psychocats.net/ubuntu/getting). That has an auto-check for image integrity. It also allows you to stop and resume the transfer without affecting the download quality.

Most computers these days can boot from USB. You can save yourself a blank CD by ["burning" the .iso to USB](http://www.psychocats.net/ubuntu/usb).

---

### Post by Dondorp on 2010-04-30
I got the same 2 images, but it just freezes here (image is recognised in windows 7 other pc, but in the laptop it just freezes there (HD led keeps flickering, same with the cd-drive led)
Anyone got an idea what I'm doing wrong?

---

### Post by happ on 2010-04-30
Are your hard disk(s) in AHCI mode?

---

### Post by Dondorp on 2010-04-30
It's a single HD, I'm installing it from windows itself now, but that can't be good.
But strangely it just freezes also when unpacking, might be a corrupted download.
I'm doing a new one as we speak, will update.

---

### Post by Dondorp on 2010-04-30
64 bit -> failure
32 bit -> failure

Same @ both installs:
The keyboard images and the person in the circle. 

Keyboard = Person, that's the 'error'

I can change the language to anything, but when I use anything in the menu it freezes (And now I've enabled AHCI mode just to give it a try)

---

### Post by asw24 on 2010-04-30
I had the same. So I re-installed the previous version to follow with the 10.04 upgrade. This I now use to write you this message. Not exactly the way to go, but it works.

---

### Post by wojox on 2010-04-30
I had this problem. I had to press F6 and set "nomodeset". Hopefully it's the same for you.

---

### Post by Dondorp on 2010-04-30
Well, I'm using a different burning program and giving it another go, really want this one on my laptop :)
But thanks for the information, I'll try when this will fail.

8.04 Hardy Heron is installing now, works fine.....
Upgrading to 10.04.....
All looks well.

---

### Post by giruzz on 2010-04-30
> **wojox said:**
> I had this problem. I had to press F6 and set "nomodeset". Hopefully it's the same for you.

It didn't work for me...

...

giruzz

---

### Post by Octanen on 2010-04-30
Ran Ubuntu 9.10, burned out Ubuntu 10.04 LTS x64 on my other machine, the dude with the keyboard logo popped up, pushed arrow key. 

Language menu popped up, pressed "Install Ubuntu" and then it simply just instead of installing it "Booted from CD"... So seems like its a quite major bug :)

Anyhow hope it gets sorted... was really looking forward to a new release, tried everything with same results. So the only way for now, is to run the upgrade through administration... if you can well... live with that :)

Anyways... just a heads up, for all the others experiencing same issues.

---

### Post by Dondorp on 2010-04-30
Ok update:
Installed 8.04, updated, upgraded, he was whining so I updated all possible => network device no longer works..... lovely.

Nomodeset doesn't work for me either
Ah well, I'm going to wait a week or 2 and try again then.

---

### Post by navin.mistry on 2010-05-01
I have dell inspiron and i'm having the same problem,

i just finished ISO download using torrent client.

checked the hash and it was perfectly fine.

burned the cd using NERO in windows and successfully burned.
but as soon as i reboot and choose CD for installation only keyboard = help icon appears until i press any key on keyboard.

i'm not sure if it's not accepting the keyboard enter key or it just freezing.
if this is so, it looks a major bug on day of release.

i'll just try it using nomodeset if it works.

---

### Post by navin.mistry on 2010-05-01
i tried using nomodeset and selecting appropriate keymap but everything is just same
still stuck and not progressing at all.

it this something execute permission related error because of that kernel is not booting up the system on enter key for install ubuntu?

---

### Post by Don1500 on 2010-05-01
If you want to load from the CD, just put the CD in the drive, turn on the system and go have a cup of coffee or something. It will load without any help. Then you can hit the INSTALL icon and it will install itself (after the normal questions).

---

### Post by navin.mistry on 2010-05-01
i tried burning my cd again but still got the same issue.
( there was no error in CD as i burn 3 CD till now and all gave the same output)

luckily i got a workaround..

i installed uNetBootin software on my windwows ( available for linux as well) from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

and burnt my ISO directly to USB drive. ( now its a bootable USB) it worked like a charm.

---

### Post by darthweder on 2010-05-24
I had the same problem, freezing on screen with keyboard and guy in the circle.  I switched out the dvd drive I was using and that fixed it.  Weird thing is, I made it halfway through the setup on the first drive, stopped because I had to get some stuff off of the harddrive, then it wouldn't start the install again.

---

### Post by trisys@hotmail.com on 2010-05-25
I'm having the exact same issue with the ubuntu-10.04-desktop-amd64.iso, i've tried both typical and torrent downloads. My machine is brand new and my burner/software isn't the issue. I'll attempt the nomodeset but I'm not very hopeful.

---

### Post by mjbernier on 2010-05-25
I'm having the same issue with 10.04 desktop 32-bit. It installed fine alongside Windows 7 and Windows Vista, but will not install with Windows XP. However, all three machines (XP, Vista, and 7) will accept a 9.10 disk without a problem. Same burner and same software used to make the 9.10 and 10.04 disks, tried both download sources (direct and torrent), same results -- 9.10 works, 10.04 doesn't. The only thing I can guess is there's something wrong in the .ISO file; could someone try recompiling and reposting it?
 
Mike

---

