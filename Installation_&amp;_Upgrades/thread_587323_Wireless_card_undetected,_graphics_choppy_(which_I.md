---
title: "Wireless card undetected, graphics choppy (which I somehow broke trying to fix)"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2007-10-22
Worst. Upgrade. Ever.

Last night I upgraded my Inspiron 8600 running Feisty to Gutsy. 
- ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
- Netgear WG511T wireless card

I didn't get any errors during the upgrade process, the only time I actually did anything was when deciding whether or not to replace certain files or keep the originals.
After rebooting, though, I had problems:
- Wireless card (Netgear WG511T) no longer detected, even though it was detected right away by Edgy and Feisty (and even the Gutsy live cd, though I never successfully connected with it while using the live cd)
- Graphics were choppy, and effects weren't enabled (that's because my card is blacklisted, and I already know there's a way to get around that). 
I could enable effects, but for some reason it would change to some ugly theme rather than keep my normal one.

Being unable to access the internet, I decided to try fixing things myself. I didn't know what to do about my wireless card, so I set to work on the graphics instead. 
This is what I did:

In the "Screens and Graphics Preferences" window, I decided to change my screen model from the default "Plug 'n' Play" to "1280x1024 laptop display panel". I know this isn't right, but for some reason I went with it even though that's not my resolution.
Next, I change my graphics card driver from "ati - ATI Mach8, Mach32, Mach64, and Rage..." (I don't know what it says after that) to "ATI - Radeon (vesa)" because I thought I remembered choosing the "vesa" driver back on Feisty.

Then, unable to resist my constant urge to tinker with things, I decided to enable desktop effects. First I tried Normal, which worked, then I tried Extra...which killed my system.
I was logged out and presented with what was supposed to be my login screen, but instead it was just a jumbled mix of colored lines. Freaking out, I restarted my computer only to find that the same thing happened again. 

Unable to use any GUI, I don't know how to revert back to the original settings, nor how to fix the problems I was having in the first place. Please, if you actually took the time to read through all of this, ANY ideas would be absolutely great.
I love Ubuntu, but for all the praise this release has gotten, I'm really disappointed with how the upgrade worked out.

---

### Post by rainwalker on 2007-10-22
I think it's also worth noting that I'm currently on my computer, but I'm doing this all from the Gutsy live cd via wired network.
Thank you Ubuntu!

---

### Post by wirechief on 2007-10-22
you got yourself in a real pickle! but you might get out of it with dpkg-reconfigure-xserver.xorg -phigh
I am on the irc channel for ubuntu if you want to chat live and we can open a pm screen 
to chat.

---

### Post by rainwalker on 2007-10-22
Doesn't that require a GUI? Because I literally cannot use any GUI...

---

### Post by wirechief on 2007-10-22
dpkg-reconfigure-xserver-xorg -phigh  sorry i think the other had a dot in it.

---

### Post by rainwalker on 2007-10-22
Still, won't taht require a GUI? 

I PMed you, FYI

---

### Post by rainwalker on 2007-10-22
I checked some backups I made a while back of my xorg.conf, and the driver listed for my card says "ati"
Is that the same one that I listed was used originally?

---

### Post by superyounan1 on 2007-10-22
hello friend, sorry to hear about all your problems, I'm sure you'd feel better though if i told you all the problems I had upgrading. But don't worry, there are many things you can do to get going.

> 

Unable to use any GUI, I don't know how to revert back to the original settings, nor how to fix the problems I was having in the first place. Please, if you actually took the time to read through all of this, ANY ideas would be absolutely great.



start your computer in "recovery mode", when you boot there should be a 3 second opportunity to load your Grub boot menu options, I don't remember what key you have to hit, maybe DELETE or F12, something like that.

Once you get the GRUB menu, you'll see a list of options including the Recovery mode, choose that one.

It will boot into the command line, log in with your usual username and password. When you get your command prompt ready, type
```
sudo dpkg-reconfig xserver-xorg
```

(actually i think you will log in as root, so you won't need sudo, but if you are logged into your typical account, keep sudo in)

This should prompt you through many options including screen setup and video driver. For your card, the default opensource video driver should be called "ati". I think that should answer this question:

> I checked some backups I made a while back of my xorg.conf, and the driver listed for my card says "ati"
Is that the same one that I listed was used originally?

after you're done with the reconfiguring, type the following to restart your computer
```
sudo shutdown -r now
```
(again, if you're root then forgo sudo, just type shutdown -r now)

Post your results.


If you can successfully log into ubuntu like before with the gui, the first thing I recommend you do is to do a clean install. I can't tell you what a world of difference it did for me, NIGHT AND DAY

good luck

---

### Post by rainwalker on 2007-10-22
Um...how much memory should I set to be used by the video card?
EDIT: Nevermind


Use kernel framebuffer device interface?

---

### Post by superyounan1 on 2007-10-22
> **rainwalker said:**
> 
Use kernel framebuffer device interface?


it won't matter, the default option is 'No' i believe, just stick with that.

---

### Post by rainwalker on 2007-10-22
What should I identify my monitor as? Generic monitor?

---

### Post by superyounan1 on 2007-10-22
> **rainwalker said:**
> What should I identify my monitor as? Generic monitor?

thats fine

---

### Post by rainwalker on 2007-10-22
Okay, done.
Yay! It created a backup. Gotta love backups...

I'll restart and post the results

---

### Post by rainwalker on 2007-10-22
Looking good so far, resolution is right
YES! Okay, GUI is working
Logging in...
Black desktop first, then the panel loads, then my background

Okay, I'm back to where I started

---

### Post by rainwalker on 2007-10-22
Now my problem is with the actual video.
It's choppy, and if I move a window, I can literally see my screen refresh the window as I move it
What do I do?

---

### Post by superyounan1 on 2007-10-22
> **rainwalker said:**
> Now my problem is with the actual video.
It's choppy, and if I move a window, I can literally see my screen refresh the window as I move it
What do I do?

- can you post a link to specs for your laptop? When i look it up it all i find are nvidia graphics
- are you using desktop effects / compiz / compiz fusion / beryl?
- can you describe your experience some more, add more details

---

### Post by -Zeus- on 2007-10-24
I have the same problem.  No wireless, choppy graphics.  This is the second time it happened (first time they fixed it whth an update)

---

### Post by rainwalker on 2007-10-24
Installing the restricted drivers manager (which for some reason was removed during the upgrade) fixed my card, but my refresh rate is stil WAAYYY too low

---

