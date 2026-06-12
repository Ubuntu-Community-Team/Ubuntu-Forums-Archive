---
title: "oh oh. I upgraded."
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by Spyd on 2006-02-19
Ok, so I was walking past my ubuntu laptop as i do every day when i go to school, and it dawns on me, I have not rebooted this laptop in over 4 months. I mean I use it, but it ALWAYS works ( I love linux ) so I thought, I should pay some attention to it and give it some TLC and maybe update the packages etc. 

so I hit the updater and it goes to town. I leave it till the next day

so then its ready for a reboot, and I do it. when it comes back up, it now has 4 kernel booting options for my ubuntu enjoyment:
2.6.12-10-386
2.6.12-10-386 (recovery)
2.6.10-5-386
2.6.10-5-386 (recovery)

So I hit the new 6.12 kernel and wait in anticipation, I watch as the stuff flies by, I see no errors other than my typical alsa restore error, but then it begins to fire x and thats where things get ugly. 

When the complete boot is complete I sit at a brown desktop with a mouse pointer. nothing else. If I touch a key, any key or combination of keys, the mouse cursor swells to a very large size, pressing it again makes it normal, if I keep pressing it keeps swelling until it cycles around to small again, thats it, thats what the 6.12 kernel does for me. there appears to be 3 levels of swell inculding normal size.

i press the power button and it will do an orderly shutdown.

if I boot to the older kernel, 6.10 it behaves differently, it will boot to black screen (everything goes normal up till x fires and it gives me a black screen, keys do nothing, power button shuts down but not in an orderly fashion. 

I can boot to recovery mode, no problem, and my xorg.conf looks normal. can anyone suggest something? Hold my hand to get it working again? 

Thanks in advance for any help here...
Franco

---

### Post by aysiu on 2006-02-19
I don't know what you mean when you say your xorg "looks normal." It may have to be adjusted (for some strange reason). When you get to the brown screen or black screen, press Control-Alt-F1, log in, and then type these commands: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Jedeye on 2006-02-19
if you can boot to the promp and just log in without launching X or perhaps even in the recovery mode you could try this
```
sudo dpkg-reconfigure xserver-xorg
```
It will set up X for ya.

Hope this helps... I have not had much experience with this.

---

### Post by Jedeye on 2006-02-19
well it seems that im getting beaten to the post quite often aysiu's details are a little better ;) so try that.

---

### Post by Spyd on 2006-02-19
Thank you Aysiu and Jedeye
ok, as I mentioned before, when in this state the keys do nothing so ctrl-alt-f1 does not work, however I did boot to recovery and run the config, choosing the defaults. rebooting resulted in a text screen error that X failed to start. So i ran reconfigure again, and enabled the frame buffer. Now when I reboot i get my brown desktop and mouse cursor, but it does not swell. and does nothing else. keys do nothing now. power button on the machine performs an orderly shutdown.

Any other suggestions?
F

---

### Post by Jedeye on 2006-02-19
can we get some specifics on your hardware... videocard processor etc..

---

### Post by Spyd on 2006-02-19
HP Compaq nx 9110 laptop
1 gig of ram
mobility radeon 9000 IGP video
2.80-GHz Intel Pentium 4 Processor with 533-MHz Processor Side Bus and 512-KB L2 cache
Dualbooting XP and Ubuntu

---

### Post by renzokuken on 2006-02-19
do you not have to reinstall the ATI drivers (fglrx) for the new kernel? or was that just for nvidia?

---

### Post by Jedeye on 2006-02-19
[QUOTE=renzokuken]do you not have to reinstall the ATI drivers (fglrx) for the new kernel? or was that just for nvidia?[/QUOTE]
not sure... but it would probably be a good idea to... here is a link to updating to the newest drivers [http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")

---

### Post by Spyd on 2006-02-19
Umm. are you suggesting that I HAVE to run FGLRX? I didnt have to use it before to use ubuntu and i do now?

---

### Post by renzokuken on 2006-02-19
you dont have to, but i would recommend it if you have a radeon card, its easy and u do notice a video performance increase

[http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ati+fglrx](http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ati+fglrx)

---

### Post by Spyd on 2006-02-19
I appraciate that thanks, but before I make things more difficult, I really need to get it to work first. then I can move on to improving.
Franco

---

