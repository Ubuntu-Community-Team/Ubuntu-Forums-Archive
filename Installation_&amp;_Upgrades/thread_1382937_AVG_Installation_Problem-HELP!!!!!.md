---
title: "AVG Installation Problem-HELP!!!!!"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by bmesta on 2010-01-16
Hello,

I just downloaded the AVG Anti-Virus Free Edition for Linux (deb) and installed it successfully. Unfortunately, when i got to Applications>Accessories AVG for Linux Workstation doesn't appears. whats going on? I cant find it anywhere. The installation guide that i followed is [http://techreviews.in/free-avg-anti-virus-for-ubuntu/](http://techreviews.in/free-avg-anti-virus-for-ubuntu/) It will be great if someone can help me out. I'm a newbie in Linux

---

### Post by 73ckn797 on 2010-01-16
If you know the name of the start-up filename you can create the menu choice using System/Preferences/Main Menu.

Avast also has a Linux version and will install the menu selection for you.

Any other answers you need may be easily found at [http://www.uboontu.com](http://www.uboontu.com)

---

### Post by forsaken_pariah on 2010-01-16
Antivirus software actually isn't generally necessary for Linux. I've been using Ubuntu for more than 3 years w/o antivirus and I haven't had a problem yet.

Note that Linux isn't really immune to viruses, it's just that nobody takes the time to write them, and even if they did, it would only be hours before they were foiled by the community.

AFAIK the only purpose of antivirus for Linux is to remove Windows virus from your computer. It saves on disk space, but they won't hurt you if you leave them there.


But as far as your problem w/ AVG, I have no idea. Good luck though. ;)

---

### Post by bmesta on 2010-01-16
how can i find out the start up file name so i can do what you suggested?

---

### Post by bmesta on 2010-01-16
> **forsaken_pariah said:**
> Antivirus software actually isn't generally necessary for Linux. I've been using Ubuntu for more than 3 years w/o antivirus and I haven't had a problem yet.

Note that Linux isn't really immune to viruses, it's just that nobody takes the time to write them, and even if they did, it would only be hours before they were foiled by the community.

AFAIK the only purpose of antivirus for Linux is to remove Windows virus from your computer. It saves on disk space, but they won't hurt you if you leave them there.


But as far as your problem w/ AVG, I have no idea. Good luck though. ;)
the reason i wanted is to remove windows virus. I constantly using both operating systems. Plus it doenst hurt having it.

---

### Post by nerdy_kid on 2010-01-16
i *think* that AVG's linux version is CLI only.  AVAST! however has a nice GUI.

---

### Post by bmesta on 2010-01-16
> **nerdy_kid said:**
> i *think* that AVG's linux version is CLI only.  AVAST! however has a nice GUI.
whats cli? u think i installed the wrong one?

---

### Post by nerdy_kid on 2010-01-16
> **bmesta said:**
> whats cli? u think i installed the wrong one?
Command Line Interface       i.e. no buttons.
i dont think the linux avg has anyother version, so id go with AVAST!.

as a sidenote, ubuntu has a opensource virus scanner in the software channel -- clamtk.  could try that also.

---

### Post by bmesta on 2010-01-16
i want to install avg. i had to good experience with it. Anyoen knows why it isnt working?

---

### Post by nerdy_kid on 2010-01-16
ahh i am horribly wrong....nice interface!
i am currently installing it, and will help as soon as it is done.

[edit]

never mind, i was correct.  There is no GUI with AVG.  I dont know where that guy got that package, because it isnt on AVG's site.
however, it is possible to install a 3rd party 'unofficial' GUI with these directions:    [http://forums.avg.com/us-en/avg-free-forum?sec=thread&act=show&id=30551](http://forums.avg.com/us-en/avg-free-forum?sec=thread&act=show&id=30551)

---

### Post by 73ckn797 on 2010-01-16
Avast would be up and running and finished with a system scan by now.

---

### Post by nerdy_kid on 2010-01-16
> **73ckn797 said:**
> Avast would be up and running and finished with a system scan by now.
this

---

### Post by bmesta on 2010-01-16
> **nerdy_kid said:**
> ahh i am horribly wrong....nice interface!
i am currently installing it, and will help as soon as it is done.

[edit]

never mind, i was correct.  There is no GUI with AVG.  I dont know where that guy got that package, because it isnt on AVG's site.
however, it is possible to install a 3rd party 'unofficial' GUI with these directions:    [http://forums.avg.com/us-en/avg-free-forum?sec=thread&act=show&id=30551](http://forums.avg.com/us-en/avg-free-forum?sec=thread&act=show&id=30551)
hey bro did it work?

---

### Post by nerdy_kid on 2010-01-16
> **bmesta said:**
> hey bro did it work?
i didnt try it, sorry :S  if you read more of the thread i gave you, it says why they dropped the gui support, and has some links to the old packages.  it should work ok, give it a shot if you want :)

but seriously, not to sound like a broken record, but go with avast or clamav.  simpler, no compiling, less bugs, etc.  check out some screenies of klamav (interface for clamav) here: [http://sourceforge.net/project/screenshots.php?group_id=102171&ssid=7051](http://sourceforge.net/project/screenshots.php?group_id=102171&ssid=7051)

even if you do get AVG working, it wont be anything like the windows version.

---

### Post by 73ckn797 on 2010-01-17
> **nerdy_kid said:**
> i didnt try it, sorry :S  if you read more of the thread i gave you, it says why they dropped the gui support, and has some links to the old packages.  it should work ok, give it a shot if you want :)

but seriously, not to sound like a broken record, but go with avast or clamav.  simpler, no compiling, less bugs, etc.  check out some screenies of klamav (interface for clamav) here: [http://sourceforge.net/project/screenshots.php?group_id=102171&ssid=7051](http://sourceforge.net/project/screenshots.php?group_id=102171&ssid=7051)

even if you do get AVG working, it wont be anything like the windows version.

YES!

Clamav does a good job also when you have the need to check a Windows installation or just to kill a little time scanning Ubuntu for the peace of mind of it.

---

### Post by spiritofelric on 2010-01-19
> **73ckn797 said:**
> Avast would be up and running and finished with a system scan by now.

Where can i get it?  I searched the Avast website but there doesn't seem to be a linux free version.

---

### Post by 73ckn797 on 2010-01-19
> **spiritofelric said:**
> Where can i get it?  I searched the Avast website but there doesn't seem to be a linux free version.


Here: [http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)

Get the "deb" download. Once you have it right click on the file and install with Applications/System/GDebi Package Installer. If you do not have the Applications/System choice go to System/Preferences/Main Menu to enable it to show up in the menu.

---

### Post by Thelinuxgeek on 2011-10-05
I wouldn't even bother with anti-virus software for Ubuntu unless you have VERY private information on your machine (i.e, social security numbers, tax information).

---

### Post by sffvba[e0rt on 2011-10-05
Back to sleep thread...


404

---

