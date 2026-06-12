---
title: "Gui broken after upgrade to 12.10"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by dragonboss on 2012-04-27
My current upgrade to 12.04 is partially working with the console only and it seems like the upgrade didn't download or install all files and the computer rebooted. I have tried apt-get update, but it only shows broken dependencies and i tried apt-get -f install and it shows an error and stops and finally i tried apt-get dist-updgrade -f and it finished dowloading the updates but then when it starts to install this eroor message appears:

dpkg: parsing file '/var/lib/dpkg/status' near line 38667 package 'lexmark-08z-series-driver:i386':
 blank line in value of field 'Description'
E: Sub-process /usr/bin/dpkg returned an error code (2)

Any suggestion on how to fix this other than fresh install?

---

### Post by dragonboss on 2012-04-27
I can't upgrade or finish the dist-upgrade because of the above error and it seems it is due to the computer restarting in the middle of installing the packages.Anyone? I have 600GB of stuff on the hardrive I'd rather not lose and I can't transfer it.

---

### Post by kewlman on 2012-04-28
Same problem im having here, i searched around and nothing so far is fxing it. This is the first major problem i have had with ubuntu. I also have alot of important files in my home dir.

---

### Post by kewlman on 2012-04-28
> **dragonboss said:**
> My current upgrade to 12.04 is partially working with the console only and it seems like the upgrade didn't download or install all files and the computer rebooted. I have tried apt-get update, but it only shows broken dependencies and i tried apt-get -f install and it shows an error and stops and finally i tried apt-get dist-updgrade -f and it finished dowloading the updates but then when it starts to install this eroor message appears:

dpkg: parsing file '/var/lib/dpkg/status' near line 38667 package 'lexmark-08z-series-driver:i386':
 blank line in value of field 'Description'
E: Sub-process /usr/bin/dpkg returned an error code (2)

Any suggestion on how to fix this other than fresh install?

i gave up and backed up the status file, and deleted the whole package information section at that line.. and did a apt-get -f update, apt-get -f install, etc. don't know if it was the right thing but it let the update continue and i am now upgraded and booting as normal.

---

### Post by darkod on 2012-04-28
I don't know if it would help in this case, but if the configuration of packages is interrupted you can make it continue with:
sudo dpkg --configure -a

That will continue configuring all packages pending to be configured.

---

### Post by chadmkidner on 2012-04-28
I had this same problem, this worked for me..

[LIST=1]
[*]From root command line type 'vim /var/lib/dpkg/status'
[*]When vim opens page down until you get to the line mentioned in the error OR use the command '/lexmark-08z' to have vim jump you ahead.
[*]press the insert key on your keyboard and delete the blank line(s) -I had two blank lines that needed deleted.
[*]To save, use the command ':w' than quit ':q'
[/LIST]

You will need to do the above steps again for /var/lib/dpkg/available so open this file in vim, use the search command '/lexmark' to jump you forward, delete the blank line(s), save, than quit.

Now you should be able to run 'apt-get -f install' without error.

---

### Post by garydem on 2012-04-28
I have the same problem with the GUI.  All looked normal until the reboot... getting a blank screen and no panels ore Unity bar....not good.

---

### Post by dragonboss on 2012-05-15
This did not work for me.
Ended up using a live usb to salvage what i could and fresh installed. Not my best upgrade experience :(

---

