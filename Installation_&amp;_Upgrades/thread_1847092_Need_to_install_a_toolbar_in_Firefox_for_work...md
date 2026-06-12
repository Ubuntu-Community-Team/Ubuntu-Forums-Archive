---
title: "Need to install a toolbar in Firefox for work.."
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by jrschrock on 2011-09-20
Hello, I'm having trouble installing a sidebar that I use for link building. It's basically a Google PR, backlink checker-type thing designed by the company I work for. The name of the file is lbgurus.xpi so I've been trying to use Wine to install it. I have to go into the tmp directory to permit it to run as executable, which I'm able to do fine, but when I go to open it (and subsequently add it to Firefox, ideally ) I'll choose to open it with Wine application launcher (exact name ?) and then nothing happens= no error messages, no evidence of it being included in my Firefox extensions..etc..

Does anyone have suggestions? Preferably command line operation? As an incentive, I'll add that once I have this installed and get my VGA issues resolved, I'll be 100% free from my girlfriend's Windows 7 OS laptop. Until then, they've still got a claw or two left in me :)

---

### Post by jrschrock on 2011-09-20
jrschrock@Jeremy:~$ sudo apt-get install /tmp/lbgurus.xpi
[sudo] password for jrschrock: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package /tmp
jrschrock@Jeremy:~$ 


Just tried that in Terminal to no avail

---

### Post by Elfy on 2011-09-20
Do it from within Firefox. Install addon from file in the addon manager

---

### Post by jrschrock on 2011-09-20
I guess I never knew about the add-on manager for as long as I've been using Firefox. Took all of 30 seconds. Thank you very much!

---

