---
title: "Several problems after upgrading from 12.04 to 12.10"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by rolfinator on 2013-03-16
Hey there ubuntu forums!

After upgrading from 12.04 to 12.10 I can't use my notebook anymore. (sounds hard, but it is true...).
Okay, first of all, this is my setup: I have  a Lenovo TP x230 and a ultrabase 3 docking station. Now, as the title says, with ubuntu 12.10, 64bit.

When I received my new notebook a few months ago I installed 12.04 with the installation CD. Yesterday I decided to upgrade to 12.10. Unfortunatelly. Since the upgrade I can't boot sometimes:
First Problem: When the notebook is not mounted in the docking station the notebook tries to boot but after some seconds of doing nothing (this is also not normal, since my ssd normally boots within seconds into the desktop) a screen appears that says "running on low graphics". Okay, then I press ctrl+alt+F1, login mount the notebook in the docking station and "sudo reboot".
Then the computer reboots and tries to boot up...but just a terminal appears that asks me vor my login. *sigh* I try to startx but nothing happens...when I press ctrl+C the notebook comes to the ubuntu (graphical) login screen (I dont know why -.-). But when I try to login -> Screen splashes like it would log me in -> comes back to login screen. WTF???

Second problem: Sometimes it is possible to start the X-server, like it worked now...thanks god, so I can post here...
But I have no gnome panel (yes, I am using gnome3 fallback).

So, you see, I am very frustrated, since I moved from Windows to Ubuntu about 6 months ago.

I hope, that a fresh install is not the only option! Please let me know if you need any system details (if the notebook boots the next time, I try to support you with the needed information :) ).

Thanks in advance for your help!


- rolfi

---

### Post by solarghost on 2013-03-16
I've been reading these forums a bit these past few days and it seems like a large amount of issues are around upgrades from 12.04 to 12.10.

I know this is not what you want to hear but I would recommend you do a clean install, back up all your required data and start fresh. I have no doubt that there will be a solution to fix your specific problem and you could get your system up and working again, but I would be willing to bet that unless you get face to face help from some Linux Guru you will save time and lots of frustration doing a clean install.

On a side note I prefer doing a clean install and will probably never upgrade from one major version to another (personal preference).

---

### Post by rolfinator on 2013-03-16
> **solarghost said:**
> I've been reading these forums a bit these past few days and it seems like a large amount of issues are around upgrades from 12.04 to 12.10.

I know this is not what you want to hear but I would recommend you do a clean install, back up all your required data and start fresh. I have no doubt that there will be a solution to fix your specific problem and you could get your system up and working again, but I would be willing to bet that unless you get face to face help from some Linux Guru you will save time and lots of frustration doing a clean install.

On a side note I prefer doing a clean install and will probably never upgrade from one major version to another (personal preference).

Thanks for your reply, solarghost :)

Yeah, i thought that this would be the wisest option...i fortunatelly used duplicity before upgrading and backed up my entire homefolder.

- rolfi

---

### Post by solarghost on 2013-03-18
Cool, good luck rolfinator.

Also 13.04 is coming out soon :) so make sure you have a backup ready, if you plan on installing that.

---

