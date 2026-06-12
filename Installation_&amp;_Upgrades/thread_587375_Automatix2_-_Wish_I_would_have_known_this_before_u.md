---
title: "Automatix2 - Wish I would have known this before upgrading!!!"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by spamking2000 on 2007-10-22
FYI/AA

Automatix2 for Ubuntu 7.10 (Gutsy AMD64, i386) has been released. Read through this post for information regarding this version of Automatix before using it! Remember, Automatix for Gutsy will NOT be backwards compatible with the previous versions. This will require the user to do a clean install for Gutsy or to run Automatix on Feisty and uninstall everything that Automatix has installed before the upgrade. Links to the .debs can be found at the bottom of this post.

From: [http://www.getautomatix.com/forum/index.php?showtopic=1558](http://www.getautomatix.com/forum/index.php?showtopic=1558)

Wish I would have known this before I upgraded my main system! I've REALLY enjoyed using Automatix, but I'm not sure that I'll use it in the future due to this. Now that I'm on Gutsy, opening Automatix resulted in a message that the version I had only worked on 7.04 and that I would have to upgrade. Then Automatix's website says a clean install is required for Automatix to work on Gutsy.

That's cheap. Sounds like if I do get the new version of Automatix installed, it still won't recognize what I've installed with Automatix in 7.04.

---

### Post by jtbl on 2007-10-23
The reason for doing this was to fix the bugs Matthew Garrett found in the Feisty version of Automatix, and in the process compatibility was broken.  Everything is still ok if you didn't uninstall the software before upgrading; its just easier to uninstall the software before the upgrade.  Most of the software was installed through apt and can still be uninstalled using synaptic.  The important thing is to uninstall the Feisty version of Automatix and remove the log files in the home directory. This can be done by entering the following two commands in terminal:

sudo apt-get --assume-yes remove automatix2

rm -rf ~/.automatix

This can still be done after upgrading to Gutsy.  The last things that need to be done are to install the Gutsy version of Automatix,  [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation),  and to clear old entries out of your sources.list.  Two ways to do this are to run the Gutsy version of Automatix and goto 
File->Remove Automatix Repos.  Exit and reload Automatix and everything should work fine.  The second way is to get a clean sources.list, instructions can be found here:  [http://www.getautomatix.com/wiki/index.php?title=Sources.list#Ubuntu_Installation](http://www.getautomatix.com/wiki/index.php?title=Sources.list#Ubuntu_Installation) .  Also, if you find anything in Automatix to be uninstalled uninstall it.

---

### Post by wieman01 on 2007-10-23
Actually I recommend staying away from Automatix in general as there isn't a case for it any longer and since it constitutes a risk for your system's integrity.

---

### Post by orange2k on 2007-10-23
> **wieman01 said:**
> Actually I recommend staying away from Automatix in general as there isn't a case for it any longer and since it constitutes a risk for your system's integrity.

That may be true, but it is still the easiest way to install audio/video codecs and other stuff...
And since I did a clean install of 7.10 64-bit, I couldn`t install EasyUbuntu because I couldn`t import the PGP keys for the medibuntu repository, and besides EasyUbuntu doesn`t do 64-bit stuff...
I know there are other possibilities to do this right, but with Automatix I can do that in a snap...

---

### Post by wieman01 on 2007-10-23
> **orange2k said:**
> That may be true, but it is still the easiest way to install audio/video codecs and other stuff...
And since I did a clean install of 7.10 64-bit, I couldn`t install EasyUbuntu because I couldn`t import the PGP keys for the medibuntu repository, and besides EasyUbuntu doesn`t do 64-bit stuff...
I know there are other possibilities to do this right, but with Automatix I can do that in a snap...
Are codex still an issue? I run Kubuntu, but Koffeine offers me to install restricted drivers once it recognizes a particular format. So in my opinion Ubuntu is convenient enough, at least in that respect. Anyway, if one likes it, there is nothing I can say against it. Just be aware of the risk.

---

### Post by compiledkernel on 2007-10-26
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

They contain the packages that are desired in this capacity. And adding them to synaptic is as easy or easier than installing Automaitx2 to get it done. This includes the packages for  xmms-wma, w32codecs, acroread, google-earth, skype, and non-free-codecs.

---

### Post by Pumalite on 2007-10-26
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by louieb on 2007-10-26
Don't know if this is typical but all I did before upgrading my laptop was use Synaptic to uninstall Automatix2 before upgrading to Gutsy. Upgrade appears to have been successful.

---

