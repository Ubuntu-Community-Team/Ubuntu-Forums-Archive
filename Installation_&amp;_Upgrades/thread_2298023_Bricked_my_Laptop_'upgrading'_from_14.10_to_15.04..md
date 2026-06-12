---
title: "Bricked my Laptop 'upgrading' from 14.10 to 15.04... Please help"
date: 2015-10-08
forum: Installation &amp; Upgrades
---

### Post by Chris_Sol_Gully on 2015-10-08
[COLOR=#000000]Hi, I recently went ahead and clicked on the 'system update' option for Ubuntu 15.04, which has bricked by laptop. It is now completely unusable. It starts in GRUB like normal and I can go through the login screens, then the desktop background loads, but I get no GUI. When I type ctrl+alt+T to try and get a terminal, it just makes the screen go black and it crashes... It had run well with 14.10 for about 6 months and I had held off on 'upgrading'... until recently figured I might as well try 15.04 since I couldn't ever get the laptop to wake up if it went into sleep mode and/or had the lid closed with 14.10. This wouldnt' have been such an issue if my wife wouldn't habitually shut the laptop to save energy every time she walks by it, plus it really wasn't so portable having to shut down and reboot all the time... I think it was a graphics card issue with the Nvida drivers. I had tried three different available drivers to no avail. So I thought maybe it might work better with 15.04 but that was a huge mistake...

It is an older HP Pavilion DV9500 laptop that used to run Windows 32 bit Vista. It has a Turion 64 x2 1900MHz & upgraded to ~3.6MB RAM & [/COLOR][COLOR=#000000]w/ ~ 114 GiB harddrive[/COLOR][COLOR=#000000], which ran Ubuntu 64 bit 14.10 just fine, aside from the sleep mode glitch.  

After the botched system upgrade through the Ubuntu system tools, I created a new boot-from-USB to try either a fresh install of 15.04, or maybe go back to 14.10 or even 14.04 LTS. Have even considered trying another distro like OpenSUSE or Mint to see if that might work better on this laptop than Ubuntu. But, I'm not sure how to go about this now. When I originally converted the laptop to 14.10 from Windows Vista, I made a boot-from-USB and followed the instructions and it worked just fine, easy enough. But now it won't let me boot from the USB. When i hit F9 to change the boot order, I get a 'Boot error' message and it just freezes there. Do I have to go about this a different way now after already having stalled Ubuntu? Not sure if the boot-from-USB install was just for the initial switch from windows. I've booted into 'system recovery' via F11 at startup and have tried to udate GRUB, and played around with some other recovery tools that didn't get me anywhere and ended up with it just crashing again. 

At this point I'd be perfectly happy just to get back to where I was with Ubuntu 14.10 or maybe another distro. The laptop is worth saving, I had upgraded the memory and got a big new battery for it once I had 14.10 working well, it has decent speakers and screen and worked well as an extra multmedia machine with 14.10. So how do I save this puppy, any suggestions? Thanks[/COLOR]

---

### Post by ubfan1 on 2015-10-08
Could be a video problem.  When you get the grub menu, choose "Advanced..." and you should get a list of older kernels, try the one that last worked.  Can you get to a virtual terminal (Ctrl-Alt-F2  (F1 through F6 should work, F7 is the GUI)?  If you can, maybe you can check for what video driver is in use, and install the last one that works if necessary.  I found an old HP with Turion/Nvidia using the 304 drivers just couldn't run Unity after some update, but switching the desktop to something else like fce4,.... made it better.

---

### Post by grahammechanical on 2015-10-08
Ubuntu 14.10 has reached end of life. It will not receive any security updates. Also, Ubuntu 15.04 will come with newer Linux kernels and newer proprietary video drivers and it is possible that the latest proprietary video drivers do not support your video adapter. Support for older video adpaters is often dropped from the latest proprietary video cards.

Not only can we select an earlier kernel for the Grub menu Advances Options but we can also select recovery mode>Resume. See if that loads to a working desktop and then go to System Settings>Software & Updates>Additional drivers tab and either choose the open source video driver or an older version of the proprietary video driver.

If all we get is the background wallpaper, then right clicking the wallpaper will bring up a menu. One option would be to load a terminal. Another option would be to change desktop background. That should open System Settings at the Appearance tab and from there we can get to Software & Updates>Additional Drivers tab.

Regards.

---

### Post by Chris_Sol_Gully on 2015-10-08
Cool. Thanks for your technical suggestions. I will try to load an older kernal thru the Grub menu and see if I can get anywhere and will post up result after I've had a chance to try this. I love that there is so much customization tools available for various configurations, but now I just gotta learn how to use them. Thanks for putting me in the right direction.

---

### Post by suprleg on 2015-10-08
Great advise [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"). Another alternative might be if your older video card continues to have compatibility issues with 15.04 drivers, or lack of, you might consider installing the "pure" drivers from the manufacturer's support site and install them outside of Ubuntu's software updating environment from the CLI after "purging" the precompiled video support.

---

### Post by flocculant on 2015-10-08
> When i hit F9 to change the boot order, I get a 'Boot error' message and it just freezes there.Is this what you see once it starts the USB?

If so - there are bugs about that kicking about, try hitting tab and see if you get a list of options? 

In the past I've seen (with unetbootin) unetbootinlive, with the ubuntu tool I've seen live - try those to get the USB going.

---

### Post by Chris_Sol_Gully on 2015-10-08
Thanks to the above advice, you can consider this one SOLVED! 

I went into 'Advanced' mode from GRUB, and selected the lowest numbered kernal (presumably the oldest), and it booted into 15.04 perfectly. 
Then from the terminal typed in $ sudo apt-get install nvidia-current which updated the video driver and seemed to help stabilze it, since the seach function was still making the graphics freak out. Seems almost good now. I'll try the open sourse driver now too, to see if that further improves it. 

@flocculant: I haven't tried to boot from USB again yet since was able to solve it with the current install, but I'll go back and play around with that some other time soon. Yes, 'boot error' was the message I was getting. I will try hitting tab and using those tools to get the USB going as you suggest. Thanks!

---

