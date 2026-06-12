---
title: "Aptitude dead, because of a shutdown while updateing !"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by emshains on 2008-08-26
So the story sounds like this:
I was updating my system, because it had the new kernel packages, I started it around 11:40(ish). I though this wouldn't take more than 10 minutes, but then, when it started the kernel download, the speed went down from 200kb/s to 25kb/s so it wasn't ready till 11:55. Then it started to install and I went away for a half hour to do other things around the house. Then I came back and the PC wasn't on. "Oh well, maybe later", I thought and went shopping for the school. So I came back and after an half hour I tried to turn on the PC and it didn't even boot the bios, although the all the coolers worked. I've had this problem before so I took the battery out of the motherboard and stuck it right back (that reloads bios) and then it worked. So I booted it into ubuntu and the update-manager said it was "broken". It said that running "aptitude --configure -a" could fix this, but that didn't do the trick. It was a dependency problem with elisa-plugins-bad, which needed libpy-pigment (or something like that, generally a pyhton library for pigment) and that couldn't be installed because of it hasn't configured yet libpigment (or something like that). I couldn't delete or install or update anything with apt-get, because it repeated the that I have a broken package.  I deleted both pigment and python library files for pigment with manually and then I opened up Synaptic package manager, and viola, I could remove the elisa-plugins-bad. 

I think this shows the vulnerability of aptitude itself, because I couldn't imagine that the whole system would be brought down to its knees if I'd pull the plug while I'm installing a .rpm on SuSe. 


P.S. I'm starting to think about a new os.

---

### Post by Pumalite on 2008-08-26
After sudo dpkg --configure -a; try:
sudo apt-get -f install
It would help if you post the output here.

---

### Post by emshains on 2008-08-27
Those two commands didn't put out anything other than the usual "sudo apt-get remove". As I said above I already fixed the problem by deleting manually the problematic  dependanceies and then removing the problematic app with synaptic.

---

