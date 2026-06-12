---
title: "New Ubuntu 16.04 install with issues."
date: 2016-06-15
forum: Installation &amp; Upgrades
---

### Post by George_Ross on 2016-06-15
I used Ubuntu a few years ago & now I'm back. I setup Ubuntu 16.04 LTS 64bit to install & boot from a 16Gb USB drive. If the drive isn't plugged in the computer boots to Windows 10 64bit.

During install I "skip" the language package install & this may be associated with my issue, but there's more. I have tried Libre Office in the past & don't like it. I tried to install Apache Open Office from a DEB file but couldn't. I guess the presence of Libre Office blocked this. After restarting Ubuntu I began getting Libre install errors. I tried uninstalling Libre Office a few more times but still couldn't install Apache Open Office. After another reboot I found help at a website & was able to uninstall Libre & finally got Apache OO to install. 

But I still get the Libre Office productivity suite - arch-independent files error. The updater says 23Mb of date is ready to install but it fails, maybe because Apache OO in installed now ??? Bu, apparently parts of Libre are still in the system somewhere. 

How can this be fix? I don't want Libre Office but don't like the error either.

[ATTACH=CONFIG]269596[/ATTACH]

---

### Post by Fire_Chief on 2016-06-15
Hi George,

Can you detail exactly how you went about the uninstall of Libre Office? This would normally be done by
```
sudo apt-get remove libreoffice
```

Cheers!

---

### Post by GARoss on 2016-06-15
> **Fire_Chief said:**
> Hi George,

Can you detail exactly how you went about the uninstall of Libre Office? This would normally be done by
```
sudo apt-get remove libreoffice
```

Cheers!

Hi, thanks. I'll give that a try. I tried several different uninstalls but this did allow Apache OO 4.1.1 to install after the uninstall of Libre. The website is found [here]("https://itsfoss.com/install-openoffice-ubuntu-linux/").

sudo apt-get remove --purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove

I then followed the install for Apache OO 64bit.

I'm tempted to just reinstall 16.04 & forget Apache OO.

BTW - George_Ross & GARoss are the same person. I wound with 2 IDs somehow????

---

### Post by George_Ross on 2016-06-15
Here is the results-

george@george-P67A-UD3-B3:~$ sudo apt-get remove libreoffice
[sudo] password for george: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libreoffice' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:5.1.3) but it is not going to be installed
 libreoffice-help-en-us : Depends: libreoffice-l10n-en-us
 libreoffice-l10n-en-gb : Depends: libreoffice-common but it is not going to be installed
 libreoffice-l10n-en-za : Depends: libreoffice-common but it is not going to be installed
 libreoffice-style-elementary : Depends: libreoffice-common (= 1:5.1.3-0ubuntu1) but it is not going to be installed
 libreoffice-style-galaxy : Depends: libreoffice-common (= 1:5.1.3-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by GARoss on 2016-06-16
Fire_Chief, I appreciate your offer to help me but I've decided to reinstall Ubuntu & allow all updates to install as the OS installs. This is different than how I installed the 1st time. After the install completed there was a 215Mb update waiting to be installed. This was different. I'll try the Libre uninstall you suggested now.

---

### Post by DuckHook on 2016-06-16
> **Fire_Chief said:**
> This would normally be done by
```
sudo apt-get remove libreoffice
```This will only remove the metapackage but will leave all of the component packages behind.

@OP

The metapackage is just a wrapper around the real meat of the matter. Removing only the metapackage it is like throwing away a wrapper. The meat is still left behind. To remove all components completely including config files, you must do:```
sudo apt purge libreoffice-writer libreoffice-calc libreoffice-impress libreoffice-draw libreoffice-base libreoffice-math
```If you have installed dictionaries, etc, these must be removed separately.

---

