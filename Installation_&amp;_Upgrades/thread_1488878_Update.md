---
title: "Update"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by jet-san on 2010-05-20
Hi there!

I've just upgraded my Ubuntu from Karmic Koala to 10.04 and get some problems.
Just take a look at my screen shot.
[http://img20.imageshack.us/i/arghhh.png/](http://img20.imageshack.us/i/arghhh.png/)
When I tick "Broken packages" I see a lot of upgrades, shouldn't be only 3 there?

Second thing: Why my CLOSE/MINIMISE/MAXIMISE signs are on the left hand side?
How to change it?

Regards
Jet

---

### Post by uRock on 2010-05-20
That is where they are designed to be you can easily chose a different them with them on the right. Where are you ticking broken packages?

---

### Post by jet-san on 2010-05-23
I went to Synaptic Package Manager - > Settings -> Filters -> click on Broken.
Like I said nothing has changed.
I have same amount of... packages(?).

Oh Themes are working now, that's a good thing:)
I though something is wrong, cuz it was right theme.
I just clicked on it once again and appearance has changed, sweet thanks:)

Still got problem with Broken packages:/

---

### Post by dino99 on 2010-05-23
check your sources.list: only use genuine **[COLOR="Red"]lucid[/COLOR]** repo, no third party or ppa, then :

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get install -f

---

### Post by Soul-Sing on 2010-05-23
we do need the exact errormessage after:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by jet-san on 2010-05-24
After doing all what you guys said:
```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libopenal1 libfreebob0 fglrx-kernel-source libxml++2.6-2
  kdebase-runtime-data-common libqt4-phonon nspluginwrapper libxklavier15
  libdmraid1.0.0.rc15 libdmraid1.0.0.rc16 libicu40 latex-xft-fonts wine-gecko
  libpolkit-qt0 libsvga1 libknotificationitem1 libcompress-bzip2-perl
  libgupnp-1.0-2 xulrunner-1.9.1-gnome-support libboost-program-options1.38.0
  libdns53 libindicate-gtk1 gnome-blackjack libiso9660-5 libass3 libexiv2-5
  librasqal1 libisccc50 khelpcenter4 kpartx liblzma0 libpt2.6.4-plugins
  libindicate3 sdparm libx264-67 python-gtksourceview kde-icons-oxygen
  python-nautilusburn liblwres50 mplayer-skins libcelt0 raptor-utils
  python-sip4 xulrunner-1.9.1 libntfs-3g54 libbind9-50 liblzo2-2 libffado1
  libgdata5 libpt2.6.4 libisccfg50 redland-utils libpq5
  firefox-3.5-gnome-support dmraid libisc50 libopenjpeg2 fxload
  kdebase-runtime-bin-kde4 libgssdp-1.0-1 libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fglrx
The following NEW packages will be installed
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 29.2MB of archives.
After this operation, 100MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted fglrx 2:8.723.1-0ubuntu3 [29.2MB]
Fetched 29.2MB in 1min 22s (356kB/s)                                           
(Reading database ... 307279 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.723.1-0ubuntu3_amd64.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```What's next?:)

P.S.
I did leoquant's lines first, then all dino99.

---

### Post by Soul-Sing on 2010-05-24
Code:

```
gksudo nautilus
```

navigate via nautilus to /var/lib/dpkg/info

( search option on the the top right)
remove fglrx_2%3a8.723.1*

close nautilus

[COLOR="Red"]Important![/COLOR]

Code:

```
sudo apt-get update
```

Code:

```
sudo apt-get upgrade
```

this should re-install fglrx without problems.

---

### Post by jet-san on 2010-05-25
> **leoquant said:**
> 
navigate via nautilus to /var/lib/dpkg/info

( search option on the the top right)
remove fglrx_2%3a8.723.1*


Can u explain this part once again please?
I found few files starting with "fglrx-...", but not the one u told me to remove.
[http://img25.imageshack.us/i/infoee.png/](http://img25.imageshack.us/i/infoee.png/)

Regards
Jet

---

### Post by Soul-Sing on 2010-05-25
fglrx_2%3a8.723.1-0ubuntu3_amd64.deb

---

### Post by Drenriza on 2010-05-25
Off topic.

I see a tibia icon on your desktop. Good choice ;) Thumps up for playing a good game.

---

### Post by jet-san on 2010-05-25
Found it (I guess) in different direction.
[http://img227.imageshack.us/i/uhmm.png/](http://img227.imageshack.us/i/uhmm.png/)
Is that the file I'm looking for?
Should I remove it now?

P.S.
Yeah, Tibia is alright^^

---

### Post by Soul-Sing on 2010-05-25
cd /var/lib/dpkg/info/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb

that one

---

### Post by jet-san on 2010-05-25
I don't have this file in such a directory mate
[http://img3.imageshack.us/i/dammith.png/](http://img3.imageshack.us/i/dammith.png/)
or can't find it:(

---

### Post by Soul-Sing on 2010-05-25
I am very sorry, I can't help you with this one....
Maybe some else?

---

### Post by jet-san on 2010-05-26
Ok, thanks anyway mate!:)

---

### Post by jet-san on 2010-05-26
Maybe this can help?

[http://img401.imageshack.us/i/errorbs.png/](http://img401.imageshack.us/i/errorbs.png/)

Anyone?

Should I follow these instructions?

---

### Post by sveterv on 2010-05-26
I had the same problem with recent updates, but after message about having 3 broken packages, I simply have checked for updates again and installed all Update Manager have found, that solved problem, without going to Synaptic and looking for broken packages.

---

### Post by jet-san on 2010-05-26
Doesn't work for me:/

---

