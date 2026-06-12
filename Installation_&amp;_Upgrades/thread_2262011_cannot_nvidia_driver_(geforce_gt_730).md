---
title: "cannot nvidia driver (geforce gt 730)"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by extraordinary on 2015-01-22
./NVIDIA-Linux-x86_64-346.35.run: 10: ./NVIDIA-Linux-x86_64-346.35.run: RcFileLocale: not found
./NVIDIA-Linux-x86_64-346.35.run: 11: ./NVIDIA-Linux-x86_64-346.35.run: ToolTips: not found
./NVIDIA-Linux-x86_64-346.35.run: 12: ./NVIDIA-Linux-x86_64-346.35.run: DisplayStatusBar: not found
./NVIDIA-Linux-x86_64-346.35.run: 13: ./NVIDIA-Linux-x86_64-346.35.run: SliderTextEntries: not found
./NVIDIA-Linux-x86_64-346.35.run: 14: ./NVIDIA-Linux-x86_64-346.35.run: IncludeDisplayNameInConfigFile: not found
./NVIDIA-Linux-x86_64-346.35.run: 15: ./NVIDIA-Linux-x86_64-346.35.run: ShowQuitDialog: not found
./NVIDIA-Linux-x86_64-346.35.run: 16: ./NVIDIA-Linux-x86_64-346.35.run: UpdateRulesOnProfileNameChange: not found

---

### Post by Tom_Dalton on 2015-01-22
You'll probably need to provide a little more context before anybody can help you with this. What are you trying to do? What version of Ubuntu are you running?

---

### Post by mörgæs on 2015-01-22
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by efflandt on 2015-01-24
Why are you trying to use a .run script? If you want to have everything compatible and update automatically use Ubuntu packages.

I doubt if you need anything newer than one of the mainstream nvidia packages (**nvidia-331-updates** for newest of those). Although, if you messed things up trying to run the .run script and following do not work, not sure how to fix that short of reinstalling Ubuntu (enable **nomodeset** kernel boot parameter while booting live/install iso or if not done during install, in /etc/default/grub insert nomodeset between the quotes for "quiet splash" and run: sudo update-grub).```
sudo apt-get update
sudo apt-get install nvidia-331-updates
```That worked even for my newer GTX 750 Ti with Maxwell chip. The only reason I wanted a newer version was to play around with video overclocking. If you want the 346.35 driver, add the xorg-edgers ppa to your repos and install nvidia-346: [http://www.ubuntuupdates.org/ppa/xorg-edgers](http://www.ubuntuupdates.org/ppa/xorg-edgers) ```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-346
```

---

