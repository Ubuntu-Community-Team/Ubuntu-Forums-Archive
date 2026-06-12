---
title: "Uninstall is broken"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by mizar001 on 2006-12-17
Some days ago i realized that my system was overloaded by useless applications, due to my curiosity to try the powerful ubuntu programs.

I wanted to uninstall some packages, like some games and similar stuff. But when i go to apt-get,aptitude or adept , these packages are marked as NOT INSTALLED, and even when i click to install it shows me that will be an error in installing these packages (Broken(install)).

I must say that 1 months ago i found my sources.list file completely deleted (don't know why), and i was never able to restore it like before, so  maybe actually i've different repositories.

I have my packages correctly placed in /var/cache/apt/archives.
If i try to uninstall them , i've an error message that say:
this package is not installed.

What i have to do ? And the lack of repository should be considered a threat to uninstalling packages ?

---

### Post by maxamillion on 2006-12-17
I assume it possible that tools like apt-get and aptitude would cross reference their files with your sources.list and generate strange behavior because one does not exist (which is strange in itself).

You should be able to use "sudo dpkg --purge application_name" to remove the packages and if that returns that they aren't installed then you have a very unique situation and I might recommend a backup of personal files in the home directory, a download of a new image, double check the md5sum and re-install.

/me

---

### Post by mizar001 on 2007-01-19
Really i thought that aptitude/apt-get/synaptic and adept all refer to the same /etc/apt/sources.list .

---

