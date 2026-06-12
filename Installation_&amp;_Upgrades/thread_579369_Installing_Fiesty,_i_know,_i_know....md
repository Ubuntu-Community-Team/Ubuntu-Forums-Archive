---
title: "Installing Fiesty, i know, i know..."
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by DrCuddles on 2007-10-18
Hi all, im a fresh new Ubuntu user and i need some help...

I have ben testing the Beta of Gutsy on a Virtual Machine for some time and made a decision to do a switch!

I installed Ubuntu Fiesty on my HDD all fine last night and was going to just let it update to Gutsy on its own as i cant be bothered waiing for the download mirors to die down and after a few tries it installs, woo!:)

BUT, now i have a serious problem, i think i know what it is but i need conformation before i start messing with anything.

The X Server starts up in a resolution my monitor cannot support, i think its because i installed ubuntu with both my monitors plugged in... correct me if im wrong but i believe this si the cas, so im goind to manually reconfigure the config file for th Xserver so that it doesnt try and display the mad 2048x768 resolution on just the one monitor.

If anyone has any other information they could give me on how to fix the problem i would be happy to take help.

A bbit more info is im running an:
AMDx64
NVidia gfx card
(i think thats all the info thats needed really)

Ubuntu loads fine with the nice Orange Bar loader and then when its about to go onto the logon screen it displays only in my right monitor but its the craziest resolution ever displaying two loaders that have stopped loading with what i think is 24bit colour (i had to change the colour when i used this in a Virtual Machine)

Thanks in advance

---

### Post by aJayRoo on 2007-10-18
Well, I know that when I try to uinstall Ubuntu with both my monitors plugged in the results are not good! I think you have a good grasp of your problem, entering the correct resolution (or removing the incorrect one) on the 24 bit depth line of the xorg.conf file should do the trick. If you are using the proprietry Nvidia driver I would suggest using the nvidia-settings program to setup dual displays after you have a working system, if that is something you want to do.

---

### Post by DrCuddles on 2007-10-18
Do you think i should Set up one monitor, then use the NVidia setup program to set my second one up and plug it back in when setting it up through that? or choose a correct resolution with both of them plugged in?

Thank you by the way :)

---

### Post by DrCuddles on 2007-10-18
Ok, i unplugged one of my monitors and added an extra resolution which i **know** worked, that didnt work so i went back and turned the bit depth down to 16 and it still didnt work, so when i get back from work im going to try swapping the monitors and see if its not just reading the wrong one off first setup, how do i find out what make monitor im using?

Thanks

---

### Post by aJayRoo on 2007-10-18
Well, I usually can't get Ubuntu to install properly if both my monitors are plugged in (because I can't see anything properly on either display) so I would recommend unplugging one monitor and getting the other up and running first. I guess you will want to reconfigure the xserver-xorg package using
```
sudo dpkg-reconfigure xserver-xorg
```
to get your primary monitor setup. Chances are the xorg.conf is a little messed up due to having both monitors plugged in when the package was configured. Then once you are all setup with that one and it works fine, you can plug in the other monitor and use the nvidia tool to detect and setup the second display correctly.

---

### Post by DrCuddles on 2007-10-19
Well i have it all installed and up and running now with my loverly Restricted NVidia drivers chugging merrily along but i think i can't get both my monitors working together with Ubuntu as they are seperate monitor sizes, one is 19" and the other is 17" and every time i try and set up my resolutions it messes up on me, so im going to stick with one monitor until a fix has crept up or i get a new monitor(the latter is probably what will happen in the end :P)

---

### Post by aJayRoo on 2007-10-19
Ah ok, I seem to remember getting two monitors of different sizes to work in the past, but i don't remember having that setup for long so I suppose there must have been issues with it! Anyway, as long as you are happy with what you have then I guess its ok!

---

