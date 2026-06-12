---
title: "having bit of trouble figuring things out, little help?"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by Camillejansen on 2007-12-15
hi there,

first of all id like to say i love Ubuntu a lot, looks very prof and is way better than Windows, besides, i hate Bill Gates.

all right, lets get to the issues.

after installing Ubuntu from the livecd (all went perfectly, no problems at all), i rebooted my computer. as i saw during the installation, Ubuntu works with GRUB. no problem, but it doesn't dual boot. from the moment my computer is turned on, it goes directly to Ubuntu without even showing a little sign of life of my previous OS, windows. id like to have a loader who gives me the choice, a dual boot. but right now i cant acces my windows (where all my files are stacked and id sure love to get to them). so can anyone here give a noob like me the advice (preferably in the form of a tutorial:popcorn:) on how to make me get the best of both worlds?

i also have a couple of other beginner problems. the only actual programs i used in windows (accept for gaming) were MSN messenger, Itunes, Firefox and Bitlord. in Ubuntu there is a great media player, so i don't have to worry about my tunes. :guitar: but i also like to download stuff and that is something im missing. so i typed torrent downloader in google et voila, god gave me bittornado. i downloaded it, and when i open it i see a hell of a lotta PY and TXT files and a couple of images, but no setup. can anyone explain me how to install this program and how to get it runned properly? if you can i have one more reason to use windows as less as possible:)
by the way, i have a problem which looks like it when i download aMSN, the msn for Linux, i download it, and when i open it a program says that it cant open the file because its in a language linux never heard of:lolflag:

anyway, i truly love it sofar and despite the notably handicaps i still have to conquer i remain to have good faith in the fact that ill be as good as you guys in this someday:confused:


thanks for your help.

---

### Post by llamakc on 2007-12-15
The next time you reboot, hit the escape key right after BIOS loads. You'll get the grub menu. Do you see an entry for Windows?

After you do this, we'll edit the grub/menu.lst file so that you ALWAYS get the menu.

Open Synaptic (in the menu: System | Administration | Synaptic Package Manager) and search for bittornado. Install software in THIS manner to begin with.

---

### Post by Camillejansen on 2007-12-15
hey, thats great. seem that i accidentally erased my entire HD during the installation, windows included. what now? reinstall windows?

okay, i did what you said, i installed Kmess (an MSN program for linux) over synaptic, but now that it is installed, i cant find the shortcut anywhere. i cant even find the map. where does synaptic put the files after installation?

and as a last question, i accidentally put my keyboard on the dutch settings, but i hate them.. how can i change it back to the US style?

---

### Post by rene53 on 2007-12-15
For your keyboard settings in Ubunt 7.04 you go to " system" => Preference and then to keyboard and tab layout., sorry  For the other things,i im also a noob

---

### Post by llamakc on 2007-12-15
> **Camillejansen said:**
> hey, thats great. seem that i accidentally erased my entire HD during the installation, windows included. what now? reinstall windows?

okay, i did what you said, i installed Kmess (an MSN program for linux) over synaptic, but now that it is installed, i cant find the shortcut anywhere. i cant even find the map. where does synaptic put the files after installation?

and as a last question, i accidentally put my keyboard on the dutch settings, but i hate them.. how can i change it back to the US style?

No, all that means for starters is that Windows isn't in your grub menu. Windows *MAY* still be there, but that's a big maybe. You can check by doing this in the terminal:

```

sudo fdisk -l

```

Note that is a lower case letter L for the option. Cut/paste what the output is here.

If Windows was deleted, it is because when you installed you told the installer's partitioner to do that. Unfortunately this happens often when clicking through the installer.

So once we see the output of the command above, we'll know if Windows is still there.

As for the keybindings, you'll have to change them in the same fashion that you switched to Dutch I believe.

---

### Post by Camillejansen on 2007-12-15
where can i find the terminal? and if i go to system, preferences, keyboard i can only change things like the speed of typos and stuff... furthermore nothing.

---

### Post by Camillejansen on 2007-12-15
and where can i find the files synaptic installed for me?

---

### Post by llamakc on 2007-12-15
> **Camillejansen said:**
> where can i find the terminal? and if i go to system, preferences, keyboard i can only change things like the speed of typos and stuff... furthermore nothing.

Applications | Accessories | Terminal

Well where did you change it to Dutch? System | Administration | Language Support?

You should look in the Menu for installed applications.

If you installed something that was amsn-like, it will be in Applications | Internet.

---

