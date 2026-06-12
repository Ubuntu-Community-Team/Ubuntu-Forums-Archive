---
title: "won't boot after upgrade to 11.04"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by brosville on 2011-05-02
yesterday clicked the "update to 10.10" button - after some hours it rebooted and asked if I'd like to upgrade to "11.04" - after several hours of downloads, it was still "at it" so I left it overnight - following the demanded reboot, all I get is a stroppy prompt demanding "login" and "password" - tried everything I can think of in the way of both,still locked out - HELP!!!

Having been a devoted user for some years, am going off it bigtime

---

### Post by dino99 on 2011-05-02
try the recovery mode then select "repair packages" and run update-grub again

---

### Post by brosville on 2011-05-02
if I reboot holding "shift" it just demands the same thing -whatever I enter it says they're "wrong" -

---

### Post by brosville on 2011-05-02
Having wrestled with it for a couple of hours, I have to go out for a while - any simple solutions gratefully received...

---

### Post by brosville on 2011-05-02
just wasted another hour on it - whatever I do it demands that I "log in" - pressing "shift" on bootup alters nothing.......

---

### Post by RafaelL on 2011-05-02
Hi!
Make sure none of the letters in your username are caps. Password is whatever is yours.
I fixed this problem by pressing esc while Ubuntu was loading grub. Then  after selecting recovery mode (and later in a dialog recovery graphics)  I deleted my old nvidia driver, rebooted, installed the newest version  of the nvidia driver, rebooted again and now it works!
I have nvidia 9600 GT, I think... :P
Hope this would be of any help!

---

### Post by brosville on 2011-05-02
another wasted couple of hours - eventually get to "recovery" - try updating grub innumerable times - still demands login - eventually get it running looking most peculiar in "safe graphics mode" - whenever I restart, I have to go through the "esc" nonsense- had it repair the files - same problems - eventually try to open an "odt" file, and some damn fool Calibre books thing then starts churning away - and open office has disappeared, replaced with "Libre" - how on earth do I get back to 10.04 fast? - this is a NIGHTMARE that is coasting me a lot of time and effort - someone should be shot over this!

---

### Post by brosville on 2011-05-02
thanks Rafaell - I don't use a username, so what do I enter?
I suspect you may be right about the Nvidia driver - but all I did was what looked like a simple update, and now my whole computer is trashed, and wasting hours of my time - I really am hopping mad!

---

### Post by brosville on 2011-05-02
after a largely wasted day, I've actually got it working by ignoring most of the advice......... Rebooot whilst stroking "Esc",  rebooted into safe graphics mode, then installed "startup manager" and use it to insist on a "splash screen" - then the blessed thing rebooted properly.
As to whether it's relevant to general problems, I don't know, but I then had to install "Calibre" as it was starting up if I clicked on an ".odt" file to open it, but wasn't listed as installed - after installing it using synaptic, I then removed it by the same means (before I installed startup manager) - clicking on an odt file now starts Libre office

SO, I've wasted the thick end of a day of my life on what?....... an update that has made things worse - "Unity" is horrible (if I wanted Windoze, I'd use bally windoze), and to get there put me through 2 major updates (nearly 3gb of downloads), all for what is to be frank a backward step - it really has put me off Ubuntu bigtime - from being a keen proselytiser for it, I am now thinking that "Mint" may be a far better idea - black marks all round for whoever thought out this ill-conceived and implemented heap of rubbish!

My advice to anyone contemplating the upgrade is simple - "don't!!!!"

---

