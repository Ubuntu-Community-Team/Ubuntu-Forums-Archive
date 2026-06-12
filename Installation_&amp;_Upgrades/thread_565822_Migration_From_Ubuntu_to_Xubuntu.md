---
title: "Migration From Ubuntu to Xubuntu??"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by becatlibra on 2007-10-02
Is there a way to migrate from Ubuntu to Xubuntu?

I installed Ubuntu on my wife's laptop and she has been using it since dapper but Xubuntu would run so much faster (it's an old 300mhz machine.)

She is not really computer literate or I'd just go with fluxbox.

Is this possible (the migration?)

Thanks

Benjamin

---

### Post by Pumalite on 2007-10-02
sudo apt-get install xubuntu-desktop

---

### Post by Gun_Smoke on 2007-10-02
I had install 6.06 on an older dell..  Has a 2.* processor but only 128M of ram.. Dapper actully worked fine for minimal tasks.  After upgrading up to feisty.. Not much worked well anymore.. So I tried first Xbuntu and still not much improvement.. Ended up with flux.  At least until I buy some more memory..  

But as above.. apt-get intall xbuntu-desktop will do it.. Although I heard using aptitude is much better if you will ever be removing it.  

OH, last thing.. after you do it.  Choose the Xfce session in login menu

---

### Post by srkelley on 2008-02-29
So this will keep all personal files and user accounts?

---

### Post by sstusick on 2008-02-29
Yes, installing a desktop environment doesnt' touch your files or application settings.

---

### Post by srkelley on 2008-02-29
Thanks a lot. I never assume anything, because I have made fatal errors in the past and assumed that something that would be harmless would be. A year ago I would have just entered the line of code above without understanding anything on ow it worked. Thanks.

---

### Post by srkelley on 2008-02-29
I think it just finished, should these be the last lines:

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
shirondale@shirondale-desktop:~$


shirondale is my user account. I;m sure it's over, but I eed to be sure.

---

### Post by sstusick on 2008-02-29
Looks like it's done, now log out, and select XFCE for your session and then log in.

---

### Post by srkelley on 2008-03-01
Thanks, that definitely helped. i had to restart for firefox, but afterwareds the opening scren aand everything else changed and things are fster now. I do get this problem while logging in. Should I search other parts of the forum or would you know the answer and be willing to give it? 

Could not look up internet address for shirondale-desktop.
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
shirondale-desktop to the file /etc/hosts on your system.

---

### Post by sstusick on 2008-03-01
Hmm I'm not sure about that error, sorry. Try searching the forum, and see what you can come up with. I am sure you're not the only one who has had this particular problem.

---

### Post by Pumalite on 2008-03-01
gksudo gedit /etc/hosts
Add your new Desktop
Save, exit
Backup your file first.

---

