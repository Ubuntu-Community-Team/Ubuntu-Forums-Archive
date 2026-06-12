---
title: "Xerus upgrade, cannot update: failed to download repository"
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by Rrory on 2016-05-10
I upgraded to Xerus no problem, no with updates I get a red triangle with an exclamation ! telling me the update information is outdated due to network problems or repository is no longer available. Then when I do try to update I get this message: failed to download repository information (check your connection).

My connection is fine, sometimes I'll check and it says my system is up to date. I do get the gray screen a lot since I upgraded. Trusty Tahr LTS was so great I never had problems.ugh

Not very technically inclined so please help!
Rory

---

### Post by Impavidus on 2016-05-11
What do these terminal commands tell you?```
sudo apt update
sudo apt upgrade
```They should give us more meaningful error messages.

---

### Post by grahammechanical on 2016-05-11
> I do get the gray screen a lot since I upgraded.

Does this happen with Libreoffice 5? It does on my system. I do not put the blame on the OS. Have you installed any PPAs? You may have installed a PPA that does not exist for 16.04. That will cause this problem. And we will know for sure from the output of those 2 commands.

Regards.

---

### Post by Rrory on 2016-05-11
okay after *sudo apt update* I got this:
```
E: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release)  No Hash entry in Release file /var/lib/apt/lists/partial/dl.google.com_linux_talkplugin_deb_dists_stable_Release which is considered strong enough for security purposes
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

after *sudo apt upgrade* no error message got lots of xenial-updates files and they were sucessfully installed.
thanks both of you for you help!

Never had gray screen with LibreOffice 5.

---

### Post by QDR06VV9 on 2016-05-11
> **Rrory said:**
> okay after *sudo apt update* I got this:
```
E: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release)  No Hash entry in Release file /var/lib/apt/lists/partial/dl.google.com_linux_talkplugin_deb_dists_stable_Release which is considered strong enough for security purposes
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

after *sudo apt upgrade* no error message got lots of xenial-updates files and they were sucessfully installed.
thanks both of you for you help!

Never had gray screen with LibreOffice 5.
See this for the Error shown: [http://askubuntu.com/questions/760305/how-to-install-google-talkplugin-deb-in-ubuntu-16-04](http://askubuntu.com/questions/760305/how-to-install-google-talkplugin-deb-in-ubuntu-16-04)

---

### Post by Rrory on 2016-05-11
Okay, thanks I unchecked the plugin repository and then tried the Software Updater. It downloaded and checked but in the middle it greyed out? Does this have to do with that plug-in or as said since I do have ppa packages?

---

