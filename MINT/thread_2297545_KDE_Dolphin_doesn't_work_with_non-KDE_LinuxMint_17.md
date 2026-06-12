---
title: "KDE Dolphin doesn't work with non-KDE LinuxMint 17.2"
date: 2015-10-04
forum: MINT
---

### Post by Kevin McCready on 2015-10-04
All I get is a blank screen with no files displayed. And some menu icons don't display.

I seem to remember something about needing a KDE launcher when running some KDE apps in non-KDE environments, but can't track the soln.

here's the error messages from the terminal
```
dolphin(4234)/kdeui (KIconLoader): Error: standard icon theme "oxygen" not found! 

dolphin(4234) KXMLGUIClient::loadStandardsXmlFile: ui/ui_standards.rc not found in ("/home/k/.kde/share/config/", "/etc/kde4/", "/usr/share/kde4/config/") 
dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234)/kdecore (trader): KMimeTypeTrader: couldn't find service type "Application" 
Please ensure that the .desktop file for it is installed; then run kbuildsycoca4. 
Object::connect: No such signal org::freedesktop::UPower::DeviceAdded(QDBusObjectPath)
Object::connect: No such signal org::freedesktop::UPower::DeviceRemoved(QDBusObjectPath)
dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234)/kdecore (trader): KMimeTypeTrader: couldn't find service type "Application" 
Please ensure that the .desktop file for it is installed; then run kbuildsycoca4. 
dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234)/kdecore (K*TimeZone*): KSystemTimeZones: ktimezoned initialize() D-Bus call failed:  "The name org.kde.kded was not provided by any .service files" 

dolphin(4234)/kdecore (K*TimeZone*): No time zone information obtained from ktimezoned 
dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234)/kdecore (trader): KMimeTypeTrader: couldn't find service type "Application" 
Please ensure that the .desktop file for it is installed; then run kbuildsycoca4. 
dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234): No ksycoca4 database available! 

dolphin(4234)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4234)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4234)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4234)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4234)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4234)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4234)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4234)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4234)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
dolphin(4234)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
```

---

### Post by Bucky Ball on 2015-10-04
*Thread moved to **MINT**.*

Please use [code] tags. See the last link in my signature. Thanks.

---

### Post by Kevin McCready on 2015-10-05
I couldn't find a code tag for terminal output.

---

### Post by Bucky Ball on 2015-10-05
As I said, last link in my signature explains two ways of adding them, manually and by using 'Go Advanced' or 'Adv Reply'. Look for the '#' hash symbol. Put your output between the tags.

* I've added them to your first post. Edit that and you will see how it's done manually.

---

### Post by Kevin McCready on 2015-10-05
My apologies. I thought the code was for terminal input, not output. BTW any help on the substance of my post?

---

### Post by Bucky Ball on 2015-10-05
Any code. Use code tags. Thanks.

... and no, sorry. I don't use Mint. You might improve your chances of getting support by posting on [their forums here]("http://forums.linuxmint.com/") as well. The Ubuntu Forums are primarily for the support of the official Ubuntu flavours: Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu and Ubuntu Mate.

Good luck. :)

---

### Post by Kevin McCready on 2015-10-05
Thanks again
Unfortunately the linux mint forums are rubbish. Is there an ubuntu using xfce?

---

### Post by Bucky Ball on 2015-10-05
Xubuntu, but you can install xfce4 in any Ubuntu (and some other distros). 

```
sudo apt-get install xfce4
```

Log out, choose the xfce4 session from 'Sessions' and login.

Anything you attempt to jam in from KDE may or may not work. I wouldn't try and cram Dolphin into Xubuntu. You will drag in a whole lot of dependencies and Xubuntu is intended to be a light OS.

If you want to use KDE Dolphin, why not install an OS that runs it natively, Kubuntu?

---

### Post by Kevin McCready on 2015-10-05
I run an old slow machine and have found Linux Mint with xfce to work quite well. Is Kubuntu lightweight?

---

### Post by Bucky Ball on 2015-10-05
No. Xubuntu or Lubuntu it is. I imagine you would install xfce4 in Ubuntu Mate exactly as I have described above, but don't know if it's any lighter than Mate. You could go for Xubuntu-core, Lubuntu-core or a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD"), add xfce4 and whatever other apps you need/want. That would be the lightest approach.

---

### Post by Kevin McCready on 2015-10-05
So it seems a lightweight install with Dolphin is out of the question?

---

### Post by Bucky Ball on 2015-10-05
Why not [this]("http://www.linuxmint.com/edition.php?id=196")? Click the torrent link if you use torrents and get it that way. Create a USB and see if you can run a live session from that ok. If so, install.

[Here]("http://www.linuxmint.com/download.php") are some other options.

The other option is to try installing Xubuntu or Lubuntu or a mini.iso and then add dolphin. See what happens. Xfce4 is pretty tied up with its file manager Thunar, so there may be a conflict. I generally use pcmanfm but leave thunar installed. No issue.

---

### Post by Kevin McCready on 2015-10-05
eeek! I've just spent an hour or two on a new install. Would hate to have to start again, but will do so if needed. But do you or anyone recall the fix for kdelauncher or klauncher or whatever it was to help kde apps run in non-kde systems?

---

### Post by buzzingrobot on 2015-10-05
Like most major KDE components, Dolphin assumes it's running on KDE and has a large number of dependencies that need to be installed, including kderuntime and the KDE search framework.  Here is the list for Trusty, which Mint 17.2 is based on: [http://packages.ubuntu.com/trusty/dolphin](http://packages.ubuntu.com/trusty/dolphin).

---

### Post by Kevin McCready on 2015-10-05
thanks so much.
that partially worked. To get the find function working properly I had to follow these instructions:
[http://www.ryananddebi.com/2015/07/13/linux-getting-find-working-in-dolphin-on-kde-linux-mint-and-kubuntu/](http://www.ryananddebi.com/2015/07/13/linux-getting-find-working-in-dolphin-on-kde-linux-mint-and-kubuntu/)

---

