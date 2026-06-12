---
title: "Maverick Upgrade Nightmare"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by irrdev on 2010-10-12
I've operated Ubuntu/Kubuntu for 4 years, and have never yet encountered the upgrade nightmares I've experienced so far...

So yesterday I decided to upgrade my Ubuntu installation (which has Kubuntu-desktop installed, I should add). Anyways, having learned from past experience that it's better disable 3rd-party repositories before upgrading, I did just that. The upgrade seemed to go fine, except that a few packages, inexplicably, have unmet dependencies. My first reaction was that my respository mirror must not be up-to-date, so I switched over to us.ubuntu.com. This didn't fix the issue at all. I then tried to use the -f swich to install the missing dependencies, and that hasn't done any good either. The interesting thing is that these broken packages include plasma-workspace and ubuntu-desktop. These aren't 3rd-party dependencies or dependencies that might have been dropped as part of the upgrade. The computer boots just fine, the login manager works perfectly and I can even run applications just fine using Alt+F2 from the (absent) plasma workspace. The Gnome desktop, meanwhile, didn't install at all. 

I've attached a list of my software repositories as well as a screenshot of the command "sudo apt-get upgrade". Performing the command "sudo apt-get dist-upgrade" results in exactly the same output. As I mentioned, I've already changed mirrors to us.ubuntu.com, so the problem can't be that the package is missing from the server. Any help would be extremely appreciated!

P.S. I REALLY don't want to do a fresh install since I have MANY programs on my computer, including several licensed Windows programs running under Wine.
P.S.S. I tried installing Gnome-desktop in order to at least get a working DE and got similar missing package dependencies that would result in a completely broken installation. This is obviously not a DE-related issue, although the DE packages just happen to be among those affected. The base Linux installation, kernel, GDM and KDM are just fine though, as well as the GTK+ and QT libraries which still allow me to run applications.

---

### Post by fatbotgw on 2010-10-13
Have you tried removing/purging the desktop packages?  I seem to remember having a similar problem that was fixed by "apt-get purge xxx" where "xxx" was the package and then re-installing.

Also, it's my understanding that everything installed under Wine is in the .wine directory in your Home directory.  I believe that as long as you back up that folder you could do a fresh install, restore the directory, and still have your Wine installed programs.

---

