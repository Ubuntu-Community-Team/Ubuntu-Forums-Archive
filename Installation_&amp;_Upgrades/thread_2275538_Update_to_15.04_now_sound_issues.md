---
title: "Update to 15.04 now sound issues"
date: 2015-04-26
forum: Installation &amp; Upgrades
---

### Post by amrabdi on 2015-04-26
So, I was able to upgrade to 15.04 via software update, but I now sound ins't working and keyboard & mouse aren't fully working. When I try to go the mouse setting and keyboard settings, control panel closes. Certain keyboard short do not work, like ctrl+alt+t does nothing. 

As for sound I have my 5th gen Intel NUC connecetd to my tv via HDMI and had sound playing through HDMI. It was working normally this morning, butonce I upgrade to 15.04 sound went away. In sound panel no audio output devices come up. I plugged in some headphones and those were not reconginzed. I reinstalled pulseaudio and nothing. I tried ALSA audio, the same thing. 

I tried software update and even re-enabled whichever repository is compatible with 15.04 and then did another update, but not dice in getting sound or the mouse and keyboard settings to work. Any ideas?  

Side note, bluetooth ins't working correctly. It keeps like disabling and enabling itself for no reason.

Edit:  I did a dist-update fixes the keyboard issues, but the bigger sound issue is still not fixed.

---

### Post by amrabdi on 2015-04-27
Update I just did a sudo apt-get dist-upgrade and I was able to get the keyboard and mouse setting to work again(I had the gnone repository added), along with getting upgrade to the latest version of gnome(I like how it looks btw). I still can't figure out how to get sound to work, or get bluetooth to turn or properly. Thank you.

Edit: so i made a live usb of 15.04 and tried it under live mode at sound was working(bt had the same issue). I then tried to see if I can do a reinstall, but that option was greyed out. Is it possible to do a reinstall to get sound to work, while keeping apps and files intact? Or use whatever files/data from the live mode to get sound back?

---

### Post by amrabdi on 2015-04-28
Anyone here with a suggestion on what do to do? I uninstalled and reinstalled all the sound drivers(at least I think I did, as I uninstall & reinstalled both pulseaudio and alsa), but no dice. Thank you.

---

### Post by amrabdi on 2015-04-28
Any tips or tricks on doing a reinstall or repair install if possible?

---

