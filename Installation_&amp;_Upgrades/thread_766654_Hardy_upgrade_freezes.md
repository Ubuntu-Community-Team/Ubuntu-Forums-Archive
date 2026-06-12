---
title: "Hardy upgrade freezes"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by sphilli8 on 2008-04-25
Hi,
sorry to add yet another upgrade problem, but I couldn't see it anywhere else.

I'm attempting to upgrade (on a different computer to the one I'm on now) from Kubuntu Gutsy to Hardy using the Alt CD. It was working fine most of the way (tells me it's 99% done) UNTIL:

it's just frozen. It's at the "Installing the Upgrades" section, and the terminal has said "* stopping Firestarter firewall..." for about one hour now. I can't even abort. I've tried Ctrl+C to quit, I've tried opening up ksysguard to kill Firestarter myself, neither works.

Can somebody please tell me 
a) how to make it bypass that step and just complete the upgrade!
b) failing that, how to abort the bloody thing.

hope you can help

---

### Post by sphilli8 on 2008-04-25
Well, I wound up just turning the computer off at the switch in frustration.

On rebooting, Hardy appears to be installed and running...but I'm waiting for something to go wrong (Firefox appears to have lost it's icon, but I can live with/fix that).

If anyone can suggest anything I should do to avoid running into problems because the last 1% of "installing the upgrades" was not completed, and because "cleaning up" remains 100% undone, then please let me know.

cheerio

---

### Post by jahvascriptmaniac on 2008-04-25
To finish the install :

sudo apt-get update (update packages lists)
sudo apt-get dist-upgrade (upgrade all packages)

To cleanup :
# remove dependencies that are not needed any more
sudo apt-get autoremove
# remove .deb files that are useless now everything's install :
sudo apt-get clean

To get your repositories back to life :
sudo software-properties-gtk
And see in third-party repositories that you've got every repos you used to have.

For the firefox Icon, I got the same issue on one of the 3 computers I upgraded... Dunno why, but I'd be happy to know the fix :-)

---

### Post by sphilli8 on 2008-04-26
thanks for that. I think it's alright now. The repositories list was still mostly Gutsy, so they're all changed to Hardy now.

The only problem I can see now is that Hardy doesn't recognise my wireless card. That may be unrelated to the upgrade freeze though.

thanks again

---

