---
title: "Lucid-changes list open!!!"
date: 2009-11-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-11-02
[https://lists.ubuntu.com/mailman/listinfo/Lucid-changes](https://lists.ubuntu.com/mailman/listinfo/Lucid-changes)  HERE WE GO!!!!  BRING ON THE BREAKAGE!!!!!!!!!!!!!:p:p

---

### Post by Regenweald on 2009-11-02
Subscribed :)

---

### Post by sdowney717 on 2009-11-02
how do you guys keep it going, anytime i tried alphas i was usually left with an unworking system. do you run it virtualized?

---

### Post by bollix47 on 2009-11-02
> **sdowney717 said:**
> how do you guys keep it going, anytime i tried alphas i was usually left with an unworking system. do you run it virtualized?


In my case, yes, I'm using VirtualBox to test so that I can create snapshots as I go and revert to same when breakage occurs that cannot be easily fixed.  ;)

---

### Post by ranch hand on 2009-11-02
Nope, I run two of the buggers and try everything on one of them first before hosing the other.

There is always a way to get updates into the hosed one (chroot at least) and they usually have it fixed pretty quick.

---

### Post by meborc on 2009-11-02
a small 20 gig testing partition is what i use

VB is not good for testing (unless you want to test how system works under VB) :D

---

### Post by autocrosser on 2009-11-02
I keep 2 testing installs--1 gets updates as they come in(unless I have looked at the forum & hear about something bad--or if the update "looks" wrong) & 1 install I update once a week when things look "clear" as my backup in case things go wrong. I ALWAYS run with it as my main system---The only way you can find bugs is to use it in real time--every day. Running as a Virtual machine only will catch some things....Running it as your main system catches a Lot more (and you are more motivated to look for bugs.....)

I've only been out of my main system 10~12 times in the last 4 years & I bet everyone here that has been testing as long would be able to remember each time--The worst one I remember was in Jan a couple of years ago when Xorg b0rked in a major way.....I lost my main & backup that time...:D

---

### Post by 23meg on 2009-11-02
The RSS feed is also now online:

[http://feeds.ubuntu-nl.org/LucidChanges](http://feeds.ubuntu-nl.org/LucidChanges)

---

### Post by Starks on 2009-11-02
I'm running Lucid on my main laptop.

Fun stuff and I've been covering my *** with the same stale /home partition for over a year.

---

### Post by sim-value on 2009-11-02
I also have a Test partiotion and since my stable install of Karmic also a /home ... how probable is it that an Alpha will hurt my /home ?
(being 80% sure nothing will happen is ok)

---

### Post by Regenweald on 2009-11-02
> **sdowney717 said:**
> how do you guys keep it going, anytime i tried alphas i was usually left with an unworking system. do you run it virtualized?

I have an 8gig Xp partition for printing and emergency forum access, but honestly, the only time I had to use it Karmic related was when I installed the nouveau driver set.

best advice, if it's a production machine, as in my case, check the testing forum before applying updates.

---

### Post by autocrosser on 2009-11-02
> **23meg said:**
> The RSS feed is also now online:

[http://feeds.ubuntu-nl.org/LucidChanges](http://feeds.ubuntu-nl.org/LucidChanges)

As usual you are right on the tip my friend!!!!  Thank You!!!!  

Sim-value--I do a separate / & /home for both of my testing installs--I do as noted above with the / partition & I sync the /home(s) whenever they fall too far apart--that way I have a "safe-haven" to fall back on in case of a major b0rk....

---

### Post by alphacrucis2 on 2009-11-02
> **sdowney717 said:**
> how do you guys keep it going, anytime i tried alphas i was usually left with an unworking system. do you run it virtualized?

Nope. My test machine has been updated continuously since Intrepid. It was a near thing around Karmic alpha 5 time though;)

---

### Post by ronacc on 2009-11-03
I run a separate test box right next to my "stable" box .

---

### Post by NCLI on 2009-11-03
I just have one machine with an Ubuntu partition(always testing) and a Win7 partition for emergency access to the web if my testing partition fails.

---

### Post by jfernyhough on 2009-11-03
I run a testing system on my home (main) laptop with a Karmic Kubuntu backup system running in VirtualBox.

*cough*

Not really.

I have a triple-boot layout on this machine (Testing, Win7, OSx86), a 500GB external 2.5" USB HDD running Karmic with a recent copy of my /home, a 40GB external 2.5" USB HDD running Jaunty with an older /home copy (from an old laptop), and my work laptop is running Karmic with a recentish copy of my /home. I use Dropbox to sync in realtime my important documents (which then sync with my work laptop, using ecryptfs as necessary), every so often push those to a second online backup (Yummy Mixed Grill Lifetime Strongspace from Joyent!), and I have BackInTime running an hourly rsync backup.

I think that just about covers it. :D

Though I do have Kubuntu running in a VM, along with Win7, XP, Haiku, and a plain "minimal" Karmic.

Do I get a prize for having a completely excessive and convoluted setup? :D

---

### Post by afv on 2009-11-03
Subscribed too, some days ago.

I run the testing on my laptop (production machine), upgrading it daily since Karmic pre alpha, almost 6 months ago. :)

---

### Post by Regenweald on 2009-11-04
The following NEW packages will be installed:
  linux-headers-2.6.32-2{a} linux-headers-2.6.32-2-generic{a} 
  linux-image-2.6.32-2-generic{a} 
The following packages will be upgraded:
  alacarte alsa-base base-passwd binfmt-support bleachbit clamav 
  clamav-base clamav-freshclam consolekit cpp-4.4 gcc-4.4 gcc-4.4-base 
  gconf-editor gedit gedit-common gnome-disk-utility gnome-keyring 
  lib32asound2 lib32gcc1 lib32stdc++6 libacl1 libasound2 libattr1 
  libck-connector0 libclamav6 libenchant1c2a libgcc1 libgcr0 libgdu-gtk0 
  libgdu0 libgfortran3 libgnome-keyring0 libgomp1 libgp11-0 libgudev-1.0-0 
  libnautilus-extension1 libpam-ck-connector libpam-gnome-keyring 
  libsmbclient libstdc++6 libudev0 libwbclient0 linux-generic 
  linux-headers-generic linux-image-generic linux-sound-base nautilus 
  nautilus-data samba-common samba-common-bin tcpdump udev winbind 
53 packages upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 50.3MB/92.9MB of archives. After unpacking 202MB will be used.

Yay :P

---

### Post by ricsi-pontaz on 2009-11-05
Subscribed too. I think the time is here to upgrade my testing OS. :)

---

### Post by ranch hand on 2009-11-05
Well, there is still room for late comers.

Let us have FUN.

---

### Post by slakkie on 2009-11-05
68 updates waiting... Will not install it right now, need to get some work done, but once I get home.. wowoowow :)

---

### Post by philinux on 2009-11-05
> **ranch hand said:**
> Well, there is still room for late comers.

Let us have FUN.

I just joined the party. Totally reinstalled karmic to disk 1. Lynx on disk 2. I knew I was missing something.

!!Updates!!

---

### Post by VMC on 2009-11-05
Have no idea what what to expect, but I subscribed and also saved that RSS link.

 Not sure, but I didn't check to receive email on daily basis. Fear of mail flooding.

---

### Post by autocrosser on 2009-11-05
I have it sent in digest form--comes in nice bite-size bits:p

---

### Post by philinux on 2009-11-05
> **autocrosser said:**
> I have it sent in digest form--comes in nice bite-size bits:p

Ah thanks for that.

---

