---
title: "Upgrade from Warty to Hoary did not work"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by ubuntunewbie on 2005-02-11
Well, I am a recent Ubuntu user and like the OS VERY much ! I have recommended it to all my friends. The other day, I tried to upgrade my system from warty to hoary but it did not work. First of all, when I rebooted, it did not recognize my windows XP installation (it had done that when I installed Warty from a CD). I continued because I knew how to edit the grub menu list and so did not worry about it a lot. But after that, when I logged in, the whole desktop went blank and there was no panel for me to work with. I had to remove my power cord and reinstall the warty version all over again. Did anyone else face the same problem? if not, probably I did something wrong. Here is what I did.
I followed the instructions and changed the word "warty" to "hoary" in the sources.list file.
Then, I reloaded my synaptic package manager. Then I clicked on the "mark all upgrades" installation and then applied the upgrades. After an hour or so, the files were downloaded and installed. I said Y to all questions that were asked in the terminal screen which popped up after I had hit the "Apply" button (basically I said Y to use the package default files and not to use my existing ones). At the end it gave a message saying that the upgrades were successfully applied. So I rebooted but the upgrade did not work. 
Don't know if this is a problem just with me or if it is a known problem - but it's definitely a problem especially for a common user like me - I am not a very Hi tech programmer but am an average one at least. 
Please let me know if there is any website which details elaborately on how to upgrade from warty to hoary...

Long Live Linux !

---

### Post by clparker on 2005-02-11
yeah hoary isn't ready yet

---

### Post by KiwiNZ on 2005-02-11
It has been my experience that upgrading in Linux is very weak. I have found it to so in all distros I have tried.
 I always do a clean install between versions

---

### Post by trivialpackets on 2005-02-14
No worries, actually this is exactly what happened to me on my HP notebook, after trying a few times, I ended up with an error that said my xconf was not correct.  I thought about trying again, while making a backup for the xconf from warty that I could restore, but don't have time to mess this up again and have to go through complete reinstallation.  I have enough homework and work to deal with, so I'll wait for stable and hope for the best.  

[QUOTE=ubuntunewbie]Well, I am a recent Ubuntu user and like the OS VERY much ! I have recommended it to all my friends. The other day, I tried to upgrade my system from warty to hoary but it did not work. First of all, when I rebooted, it did not recognize my windows XP installation (it had done that when I installed Warty from a CD). I continued because I knew how to edit the grub menu list and so did not worry about it a lot. But after that, when I logged in, the whole desktop went blank and there was no panel for me to work with. I had to remove my power cord and reinstall the warty version all over again. Did anyone else face the same problem? if not, probably I did something wrong. Here is what I did.
I followed the instructions and changed the word "warty" to "hoary" in the sources.list file.
Then, I reloaded my synaptic package manager. Then I clicked on the "mark all upgrades" installation and then applied the upgrades. After an hour or so, the files were downloaded and installed. I said Y to all questions that were asked in the terminal screen which popped up after I had hit the "Apply" button (basically I said Y to use the package default files and not to use my existing ones). At the end it gave a message saying that the upgrades were successfully applied. So I rebooted but the upgrade did not work. 
Don't know if this is a problem just with me or if it is a known problem - but it's definitely a problem especially for a common user like me - I am not a very Hi tech programmer but am an average one at least. 
Please let me know if there is any website which details elaborately on how to upgrade from warty to hoary...

Long Live Linux ![/QUOTE]

---

### Post by cpinto on 2005-02-14
Next time try executing: sudo apt-get -t hoary dist-upgrade.
That's what I did and it's working almost flawlessly (aside from a few minor bugs like messed up menu entries and such)

---

### Post by trivialpackets on 2005-02-14
[QUOTE=cpinto]Next time try executing: sudo apt-get -t hoary dist-upgrade.
That's what I did and it's working almost flawlessly (aside from a few minor bugs like messed up menu entries and such)[/QUOTE]
 I'm actually thinking of wiping my windows portion of the hard drive and installing hoary there.  Things have gone fairly well, Can I use the same swap for both versions of Ubuntu, as obviously I'll only be using one @ a time?

---

