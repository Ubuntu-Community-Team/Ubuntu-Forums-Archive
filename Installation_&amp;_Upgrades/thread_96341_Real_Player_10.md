---
title: "Real Player 10"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by mclen on 2005-11-28
Can anybody explain to me why I can't run Real Player? I have carefully followed the instructions on how to install player (found on [www.real.com/linux/)](www.real.com/linux/)).
First, I uploaded the RealPlayer10Gold.bin file to my root directory, then I followed the instructions:
- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.
- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.
- When you launch the player for the first time, a set-up assistant will take you through configuring your player.
- Enjoy your RealPlayer10 for Linux!
Everithing went ok with the first two, but the last two I wasn't able to finish.
The launcher was added automatically into the menu, but everytime I click on it the message appeares "Cannot lunch entry. Details: Failed to execute child process "realplay" (No such file or directory).

---

### Post by mclen on 2005-11-28
I I have visited [https://wiki.ubuntu.com/RealplayerInstallationMethods](https://wiki.ubuntu.com/RealplayerInstallationMethods),  and reinstalled the player, but still nothing happens as I click the menu item! The only change was that I do not get the alert. :(  What to do!?!

---

### Post by bored2k on 2005-11-28
Disable the sound server in 
System -- Preferences -- Sounds.

For an alternate and better version that does not require this, add
```
##PLF (tempo)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

```to your /etc/apt/sources.list, then ```
sudo apt-get update && sudo apt-get install realplay
```

---

### Post by SavageBeginner on 2005-11-28
You could try downloading the RPM and converting it to a .deb

```
sudo apt-get install alien
sudo alien RealPlayer10GOLD.rpm
sudo dpkg -i realplayer...i386.deb
```

---

### Post by bored2k on 2005-11-28
[QUOTE=SavageBeginner]You could try downloading the RPM and converting it to a .deb

```
sudo apt-get install alien
sudo alien RealPlayer10GOLD.rpm
sudo dpkg -i realplayer...i386.deb
```[/QUOTE]
That won't change a thing.

---

### Post by skeezer65134 on 2005-12-01
[QUOTE=bored2k]
For an alternate and better version that does not require this, add
```
##PLF (tempo)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

```to your /etc/apt/sources.list, then ```
sudo apt-get update && sudo apt-get install realplay
```[/QUOTE]
Installed just fine, but I have no video. Sound is fine, but I can't get a single .rm file to show video. Most of what I have uses RealVideo v8 for encoding, which should easily be supported in RealPlayer 10.

It might be a codec issue though, because Kaffiene crashes when I try to play the same .rm files through the w32codecs and the xine engine but ti works fine with some other .rm and .ram files. However, the stuff that DOES work in Kaffiene does not in RealPlayer. (Hope that isn't too confusing....)

Any ideas?

---

