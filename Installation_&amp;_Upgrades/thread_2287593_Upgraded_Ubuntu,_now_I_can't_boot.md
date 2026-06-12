---
title: "Upgraded Ubuntu, now I can't boot"
date: 2015-07-20
forum: Installation &amp; Upgrades
---

### Post by roymastboom on 2015-07-20
Hi,
I have been using Ubuntu 14.04 LTS as my only OS on my Dell Inspiron N4110 laptop. It was buggy with updates, and every time I booted up, it would have an error mounting a partition (i forget which one) the desktop wallpaper wouldn't show at the login screen (correct me if it is supposed to do that) and directly after logging in I would get numerous error messages about internal error/system error.
I then decided to leave LTS and venture on to 15.04. I enabled distro version upgrading in update settings and followed the instructions starting with 14.10 (I even read the EULA wtf). I then rebooted and it didn't work (it also had the same mounting error as before). After the ubuntu loading screen I got a black screen with numerous lines of white text all ending with ok.
I need the data on my home directory (several hours of filming that would be awkward and difficult to redo), allong with my music library (backed up to the "cloud" but the playlists are important info for me). And the catch... I encrypted my hard drive during my original install and can not find the passphrase anywhere.
I suppose recovering the encrypted data is near impossible so fixing the upgrade will be the sollution.
Please help me, I don't even know where to start.

---

### Post by Bucky Ball on 2015-07-20
Welcome. I can't help but just a tip. Upgrading a broken system has little to no chance of fixing it. No a solution. Better to attempt to fix the problems with 14.04 LTS after the update. 

Good luck. You could boot from live media and backup your data before proceeding any further, but as you have an encrypted partition and no password for it, unsure how you'll go with that. I have no experience of encrypted partitions/data. 

Haven't helped but I have bumped your thread. :)

---

### Post by ian-weisser on 2015-07-21
Oh, dear.

The descriptions of your problems ('buggy with updates', 'numerous error messages') are much too vague and brief to offer help.

I suspect your best bet is to *really* think about that passphrase. Try hard to remember it. Spend some time getting into the same frame of mind as when you installed.
There is no secret trick to recovery, nor any backdoor. Your data, without the key, cannot be decrypted and is gone forever. That is the ***only*** purpose of encryption.

If you can rediscover your passphrase and decrypt your data, the simplest solution to fixing your system is to backup your decrypted data and reinstall the entire system from scratch. Much faster and less frustrating that mucking about under the hood for days or weeks trying to diagnose and repair.

If you want to fix your system in the hope that your /home will automount and magically decrypt (so you can promptly back up your data), we can certainly try.
First step: Describe the LAST thing you see when you boot your system. What happens after all those lines ending in 'OK'? Does the screen stop? Or change color? Or go black? Or freeze?
Do you get a login prompt?
After all the OKs are done, if you hit CTRL+ALT+F1, do you get a text login prompt?

---

### Post by roymastboom on 2015-07-23
I know my login info, but just not the encryption passphrase that is lots of random numbers and letters that i didn't write down

the screen goes black

I further messed things up with boot repair, now i don't have an os anymore and im trying my best to grab my data via live-usb

---

