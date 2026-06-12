---
title: "Lost internet during Update, error message."
date: 2012-08-31
forum: Installation &amp; Upgrades
---

### Post by Gemneroth on 2012-08-31
Unfortunately I'm not blessed with a good internet connection, compounded by BT having some problems of their own. I ran a reasonably small ~50mb update but lost connection during the process. Now when I go to the updater I get an error message looking like this:

[img]http://i1187.photobucket.com/albums/z383/Gemneroth/Screenshotfrom2012-08-31143043.png[/img]

And also have a WARNING type logo permanently in my top bar... The drop down talks about 'unmet dependencies'.

Basically, I don't know what to do as I'm really more into graphics than programming. If anyone has any ideas, I would appreciate that greatly.

Thanks

---

### Post by Gemneroth on 2012-09-01
Bump. Need help here guys, I can't run any further updates without this resolved.. :/

---

### Post by darkod on 2012-09-01
Depending where it failed, try two things to try configure pending packages, or fix broken ones:
```
sudo dpkg --configure -a
sudo apt-get install -f
```

See how that goes. You can also try to update the apt-get with:
```
sudo apt-get update
```

---

### Post by Gemneroth on 2012-09-01
> **darkod said:**
> Depending where it failed, try two things to try configure pending packages, or fix broken ones:
```
sudo dpkg --configure -a
sudo apt-get install -f
```

See how that goes. You can also try to update the apt-get with:
```
sudo apt-get update
```

Thanks, with the first pair:

```
gemn@gemn-desktop:~$ sudo dpkg --configure -a
gemn@gemn-desktop:~$ sudo apt-get install -f
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

I'll reboot and see where that gets me...

---

### Post by Gemneroth on 2012-09-01
Okay, so those terminal commands didn't fix the problem unfortunately, but thanks.
Also found that I couldn't open the Software Centre any more...
Is there anyway to roll back an update and re-run them??

---

### Post by darkod on 2012-09-01
And what if you try to delete that file it mentions? You have the exact full path in that message.

Just to be sure, in case it's needed, don't delete it, just move it to your home folder for example. If you need to open the file browser with root permissions so you can move system files, do it with:
gksu nautilus

That will open the browser with root permissions, you can move that file to your home folder. Just be careful about touching other files since with root permissions you can really make a mess if you delete wrong files.

After that file is moved, try again in terminal something like:
sudo apt-get update
sudo apt-get upgrade

---

### Post by Gemneroth on 2012-09-01
> **darkod said:**
> And what if you try to delete that file it mentions? You have the exact full path in that message.

Just to be sure, in case it's needed, don't delete it, just move it to your home folder for example. If you need to open the file browser with root permissions so you can move system files, do it with:
gksu nautilus

That will open the browser with root permissions, you can move that file to your home folder. Just be careful about touching other files since with root permissions you can really make a mess if you delete wrong files.

After that file is moved, try again in terminal something like:
sudo apt-get update
sudo apt-get upgrade

You're fantastic! Thank you so much, that worked great :D

---

