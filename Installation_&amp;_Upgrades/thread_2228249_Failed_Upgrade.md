---
title: "Failed Upgrade"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2014-06-06
Today in the AM I received a notification from the Sotware Manager (SM) on a 32bit 12.04 system (for a kernel upgrade), and after saying yes and inputting the password, a message appeared saying that the updates were not trustworthy and thus SM could not continue. After repeating the excercise 3 times and receiving the same negative I ask for advice on how to proceed. 

Thanks for your support.

---

### Post by grahammechanical on 2014-06-06
My guess is that you have installed some software through PPAs. These are Personal Package Archives and although they are registered with Ubuntu Launchpad they are considered as untrusted. I always disable any PPAs once the software I desire is installed. It avoids these kind of messages. System Settings>Software and Updates>Other Software and then reload.

Regards.

---

### Post by mayagrafix on 2014-06-06
So basically uncheck all that says "ppa/launchpad.net/**...

[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/OtherSoftware_zpscb7e6ed0.png[/IMG]
NOTE: this image is from another PC. For show purposes only.

Thanks for your help :KS

---

### Post by mayagrafix on 2014-06-07
No luck with finding "System Settings>Software and Updates>Other Software" panel. I tried typing "Software Sources" in Dash but only "Ubuntu Software Center" and "Software Updater" shows. What's up with this? is there no way to choose which PPA are enabled in 12.04 LTS? or is this panel MIA in my system?

---

### Post by monkeybrain20122 on 2014-06-07
It is probably just a gpg error for the ppa. If you have installed synaptic you can update manually and it would still go through with a warning (and terminal would work too, "sudo apt-get update && sudo apt-get upgrade") Update-manager is not very flexible in that if one software source is problematic (say gpg error or server down) then even unrelated upgrades got held up, I don't use it.

You can choose the ppa with the Software & Updates GUI (software-properties-gtk) which is also accessible from sysnaptic (Settings > Repositories > Software Sources > Other Software) or the Software Centre (Preferences > Other Software or something like that) 

If it turns out to be a gpg error it can be easily fixed (just google "gpg error Ubuntu"), I can never remember that long cryptic command. :)

---

### Post by mayagrafix on 2014-06-18
Thaanks. Got rid of the ofending PPA and upgrade proceded smoothly.

---

