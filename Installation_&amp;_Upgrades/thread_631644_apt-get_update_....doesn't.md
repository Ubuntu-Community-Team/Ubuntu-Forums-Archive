---
title: "apt-get update ....doesn't"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by TheGZeus on 2007-12-04
During an update run, my connection to the network failed, adept crashed, and then my COMPUTER crashed, which shocked me...
On restarting I ran dpkg --configure -a 
It updated networkmanager, and that's all

Now none of the packages that it said needed updates, and/or failed to download packages for, register as needing updates.
apt-get update doesn't even seem to actually download said updates, so I tried changing repositories (to UK, then to main) but that did nothing of consequence.
Some of these packages seemed rather important (something to do with cairo and various other libraries), and this is disturbing...

Please help.

---

### Post by Pumalite on 2007-12-04
Try:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
(post output of errors if any)

---

### Post by TheGZeus on 2007-12-04
> **Pumalite said:**
> Try:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
(post output of errors if any)

Done all of them, no errors, it just says there are no upgrades available, thought I know there are.

---

### Post by Pumalite on 2007-12-04
Post the output of:
sudo apt-get update

---

### Post by TheGZeus on 2007-12-04
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_GB
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Fetched 3B in 7s (0B/s)
Reading package lists... Done

---

### Post by Pumalite on 2007-12-04
Some repos are being ignored, but your apt-get seems to be working. Have you tried installing something? Do you want to upgrade?

---

### Post by TheGZeus on 2007-12-04
I've tried installing, I think some random game, it worked, I uninstalled openoffice( I use Koffice anyway) as I knew it was one that needed updates, and I don't like vunerabilities.(and don't know why it requested update)
The ones ignored are just the British English translations, and that wasn't one of the things that needed updates.

Yes I want to upgrade everything that needs upgrades.

---

### Post by Pumalite on 2007-12-04
Go to Synaptic, reload and push the button that says 'Mark all Upgrades'. If nothing is marked, nothing needs to be upgraded.

---

### Post by TheGZeus on 2007-12-04
> **Pumalite said:**
> Go to Synaptic, reload and push the button that says 'Mark all Upgrades'. If nothing is marked, nothing needs to be upgraded.

-_-

Ok, while I use Adept, I know what you mean applies to both. There is nothing to mark ACCORDING TO THE PROGRAM.
I was 50% finished downloading 20 updates when the crash occurred.
That leaves 10 packages not even downloaded, let alone updated.

I don't see how there's not a problem here...

---

### Post by Locutus_of_Borg on 2007-12-04
try removing all the .deb files from /var/cache/archives and then apt-get update again

---

### Post by Pumalite on 2007-12-04
You can also check /var/lib/dpkg/status

---

### Post by TheGZeus on 2007-12-05
> **Locutus_of_Borg said:**
> try removing all the .deb files from /var/cache/archives and then apt-get update again

hmmm.... The only thing in there is the gimp files from when I installed that as a test(it wasn't a game, I remember now), as I ran apt-get clean as a last resort move(I usually fo that in a Saturday).

---

### Post by TheGZeus on 2007-12-05
> **Pumalite said:**
> You can also check /var/lib/dpkg/status

WHOA.That's an intimidating file.
I don't know what to look for.

---

### Post by elite_angel on 2007-12-05
remove all the .deb files from /var/cache/archives
then apt-get update again.

---

### Post by TheGZeus on 2007-12-05
> **elite_angel said:**
> remove all the .deb files from /var/cache/archives
then apt-get update again.

Done a few times. That's what apt-get clean was for.

---

