---
title: "Can (and shall I) upgrade from a Lucid Lynx?"
date: 2019-06-16
forum: Installation &amp; Upgrades
---

### Post by kromak on 2019-06-16
I have been wondering if I cab and if shall upgrade from a Lucid Lynx system. I am not sure if it can be done. Even if it can,  there quite a few limitations ahead. 
1)The currently free space in the ubuntu partiton is 1.3GB.I can improve deleting temporary information (web browser stuff, thumbnails of photos) and also uninstalling programs that I will need in the future, but are not currently needed (like wine). However, it will not be much bigger than that. If I can open 2GB would be a small miracle I guess.
2)Graphics user interface has to be EXACTLY the same
3)Gimp has to remain a 2.6.

Neither of the above requirements are negotiable, besides the precise amount of space.

If all the above requirements can be satisfied, then I would appreciate links with information on how to proceed wit the upgrade.

---

### Post by kurt18947 on 2019-06-16
If no need EXACT on those  items, I don't see how. Lucid used Gnome 2 which no one currently supports that I'm aware of. You might come pretty close like Ubuntu Mate but exactly? I doubt it. I presume you could download an old version of Gimp but I don't know how it would work with current OSs. You'd probably need 10+ GB. for a fresh install to have any space. Lucid has been out of support for 4 + years so you've gotten no security updates in that time.

---

### Post by ubfan1 on 2019-06-16
I squeezed a 14.04 to 16.04 upgrade with less than  1.5G free by making links for /usr/share , /usr/src ,  and  /var/cache/apt/archives to external storage (after cleaning up the /var/log dir).  The upgrade is possible, but keeping old versions of some things may be harder -- maybe not if they still run with the new libraries (you might have to add some links pretending to be the old libs).

---

### Post by kromak on 2019-06-16
> **kurt18947 said:**
> If no need EXACT on those  items, I don't see how. Lucid used Gnome 2 which no one currently supports that I'm aware of. You might come pretty close like Ubuntu Mate but exactly?

Perhaps some small differences are acceptable, I would need to know them to be sure. Unfortunately cannot afford to upgrade and then discover it's not good enough, since I would not be able to go back.

> I doubt it. I presume you could download an old version of Gimp but I don't know how it would work with current OSs.[quote] You'd probably need 10+ GB. for a fresh install to have any space. Lucid has been out of support for 4 + years so you've gotten no security updates in that time.

If there is support for gtk 2.x then might work.

> I squeezed a 14.04 to 16.04 upgrade with less than  1.5G free by making  links for /usr/share , /usr/src ,  and  /var/cache/apt/archives to  external storage (after cleaning up the /var/log dir).  The upgrade is  possible, but keeping old versions of some things may be harder -- maybe  not if they still run with the new libraries (you might have to add  some links pretending to be the old libs).

Hmmm, not that encouraging, I suppose A upgrade from a 10.04 to the minimum newer version that I need would use more than that.

---

### Post by Artim on 2019-06-16
You can use the unsupported version indefinitely but not online.  As long as it's not connected to the Internet, do your thing on any old unsupported Ubuntu.  Save any work you wish to share to a thumb drive, and take it to your internet-connected machine (should should be a supported version) and share it.

Gnome 2 is unsupported, but MATE is a fork of Gnome 2, so the interface is likely to be very much like what you are accustomed to on Gnome 2.

---

### Post by kromak on 2019-06-17
> **artimboy said:**
> You can use the unsupported version indefinitely but not online.  As long as it's not connected to the Internet, do your thing on any old unsupported Ubuntu.  Save any work you wish to share to a thumb drive, and take it to your internet-connected machine (should should be a supported version) and share it.

Gnome 2 is unsupported, but MATE is a fork of Gnome 2, so the interface is likely to be very much like what you are accustomed to on Gnome 2.

That would be due to security reasons? Honestly I don't care. Anyway I was thinking that doing a fresh install on another partition would be better. I have 3.2GB of free space there, plus can throw at least 1GB to the Lucid Lynx partition. Plus I can possible do online backup to my dropbox account or similar, increasing the free space even more, while the Ubuntu partition I cannot reduce the current occupied by much.

But then comes a problem: I would need to do the Ubuntu (or any Linux that does not take too much space) install without the help of: cd/dvd, flash drive or pxe booting. Can it be done?

---

### Post by QIII on 2019-06-17
Hello!

As stated, Lucid is hopelessly out of date.  It cannot be updated.  You will not be able to install software from its repos without some specific changes to config files.  It should not be used to connect to the web -- period.

You may not care about security, but it would be extremely negligent of us to help you use Lucid in the face of its security risks.

I don't know what makes you demand "exactly the same" interface and Gimp 2.6, but we aren't in the business of remembering details of a 10-year old, unsupported release.  Your proposed partitions, while they might work, are far to small for any practical use.

Upgrading an EOL release through several other EOL releases to try to get to a supported release is a recipe for disaster.

Please install a supported release of Ubuntu.

Closed.

---

