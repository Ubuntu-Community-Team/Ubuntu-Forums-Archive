---
title: "Gnome fallback Ubuntu 12.04 LTS"
date: 2014-02-21
forum: Installation &amp; Upgrades
---

### Post by geoffrey-unwin on 2014-02-21
After a serious mishap I needed to reinstall the O/S on a new Hard Drive, so I took the opportunity of downloading the latest offering and installed that. I am an old luddite and much prefer the old Gnome and so I also down loaded *** gnome-session-fallback***, as I did a couple of years ago when 12.04 first emerged.
My problem is that I can not get the old classic look back. The usual familiar log in "cluster" half way up the left side of the screen does not appear, and the wretched machine seems hell bent on keeping me on what we luddites see as the garish mess that is now the new Ubuntu.
Any advice would be more that welcome.

---

### Post by ibjsb4 on 2014-02-21
Like you, I have ran Classic 12.04 for a couple of years and now on 12.04.4.  I am not seeing this change your talking about.  I do only run Metacity, do not have Compiz installed.  Could that be the difference?  Or are you seeing the Unity interface and can't go to Classic?

I had to google "luddite" :)

---

### Post by sudodus on 2014-02-22
Try kansasnoob's Precise Gnome Classic Tweaks, either according to his description

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

...
I also want to use the Zukitwo-Dust gtk theme and change the cursor and icon themes as described [here]("http://ubuntuforums.org/showpost.php?p=11993655&postcount=70") (three commands):  
```
sudo add-apt-repository ppa:caffeine-developers/ppa -y && sudo add-apt-repository ppa:alexmurray/indicator-sensors -y && sudo add-apt-repository ppa:webupd8team/themes -y && sudo apt-get update && sudo apt-get install gnome-panel indicator-applet indicator-applet-session shiki-colors-metacity-theme caffeine indicator-sensors zukitwo-theme-all zukitwo-colors-theme -y && gconftool-2 --set "/apps/metacity/global_keybindings/panel_run_dialog" --type string "<Alt>F2" && gsettings set org.gnome.desktop.screensaver lock-enabled false && gsettings set com.ubuntu.update-notifier auto-launch false && gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close" && gconftool-2 -s --type string /apps/metacity/general/theme Shiki-Colors-Metacity && echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile && gsettings set org.gnome.desktop.interface menus-have-icons true && gsettings set org.gnome.desktop.interface buttons-have-icons true && gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.nautilus.desktop volumes-visible true && gsettings set org.gnome.desktop.interface gtk-theme Zukitwo-Dust && gsettings set org.gnome.desktop.interface icon-theme ubuntu-mono-dark && gsettings set org.gnome.desktop.interface cursor-theme DMZ-White

```

The results:
...

or with a One Button Installer tarball

```
GnomeClassic1204-oem.tar.xz            # in OEM mode, password: changeme
GnomeClassic1204.tar.xz 
```

according to this link

[http://help.ubuntu.com/community/OBI](http://help.ubuntu.com/community/OBI)

---

