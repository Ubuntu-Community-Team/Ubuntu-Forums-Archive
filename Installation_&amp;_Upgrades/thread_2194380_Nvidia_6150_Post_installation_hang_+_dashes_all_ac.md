---
title: "Nvidia 6150: Post installation hang + dashes all across black screen at startup"
date: 2013-12-18
forum: Installation &amp; Upgrades
---

### Post by rickhamilton6202 on 2013-12-18
Hi all, If this is in the wrong forum or something, my apologies.

I'm trying to install Ubuntu 13.10 on a EMachines EL1300G-02W desktop with the following specs:

[LIST]
[*]AMD Athlon 2650e processor
[*]nvidia GeForce 6150 SE integrated graphics
[*]1 GB RAM/160 GB HDD
[*]DVD Burner with LabelFlash technology
[/LIST]

I am running into issues at the end of setup/at first boot.

I am able to get through setup ok, and can click on and see everything on screen without a problem. I'll click the restart button at the end of setup and the disk ejects from the drive..everything's fine up to this point. After this the screen goes blank and stays blank This particular computer doesn't have a HDD activity light so I have no idea what the computer's doing while this is happening but the power light on the computer stays green along with the monitor. The first time this happened I gave it a minute or two to see if it'd complete the restart then I held down the power button and rebooted cold. 

I got the Ubuntu splash screen and dots moving across..they went away and I was greeted to a all black screenfor a few seconds. I got a notification describing a new shortcut key as well as being disconnected from the network appear in the upper right of the screen (despite this, the typical gray menu bar was not present during this...the screen remained all black) then the screen turned to this:

[IMG]http://i.imgur.com/6JeUWtp.jpg[/IMG]

Thinking I screwed up and manually shut down too early, I powered off the computer...and reinstalled Ubuntu again. I clicked finish and the computer screen went black again like before. I then waited 15 to 20 minutes before checking back..still blank. Moved the mouse, etc. but nothing. Held down power and rebooted like before and I got the same thing as before...passes boot screen, goes to blank screen before switching to what you see above. I checked to make sure I could run Ubuntu off the Live DVD i made (choosing the "Try" option vs. the "install" option) and I can just fine. Proceeding to run the installation from the live environment results in the same behavior.

In each case, I made sure I only had the minimum number of devices required to install Ubuntu plugged in: I have a Belkin USB wi-fi adapter but I unplugged it prior to the first installation attempt. I also chose during setup to erase Windows and install only Ubuntu to the computer's HDD. Finally, I don't know if this matters but I'll mention it anyway, this computer simply refused to boot from a USB key at all: I tried every USB port + verified that I could boot from the USB key I made on my laptop. That's why I burned a DVD of Ubuntu..the DVD was burned from within Ubuntu on the laptop + was burned with the slowest setting per the installation page instructions. The computer shipped with Windows XP but was upgraded to Windows 7 by my brother's GF's mother (this is her old computer..she gave it to my brother's GF).

Any suggestions would be great, and thanks for the long read.

---

### Post by rickhamilton6202 on 2013-12-18
Update: I did some more poking around with the computer today at the suggestion of a friend. I noticed that once the computer lands on that final screen with the dashes across it, the keyboard is not responsive: I found this out attempting to enter the Ctrl + Alt + F (insert F# key here) key combo suggested by a linux using friend. I hit the caps and num lock keys respectively and the corresponding lights did not come on.

Out of curiousity, I booted the computer with only the monitor plugged in, just to see if it'd boot to the desktop. I got the splash screen like before..the red dots going across, then got a black screen, saw the "disconnected" notification come and go, and the black screen remained. I left the system for 15 minutes or so and it was still the same.

EDIT 2: I hit CTRL + Alt + F1 (i believe it was F1..could have been F2) and got dumped into a command line. I was able to log into the command line and it's there. Now, to google how to restart the GUI to see what happens...

Edit 3: hit Ctrl + Alt + F7 to switch to the GUI...i first got the black screen but hit it again and got the ubuntu wallpaper for a moment before it switched to a corrupted mess. At this point the keyboard is locked up again.

---

### Post by mörgæs on 2013-12-19
Hi, welcome to the fora.

Nvidia screen cards often need the **nomodeset** boot option. Have you tried that?

---

### Post by rickhamilton6202 on 2013-12-19
> **mörgæs said:**
> Hi, welcome to the fora.

Nvidia screen cards often need the **nomodeset** boot option. Have you tried that?

I have not tried that yet. I'll Google it, give it a shot and report back.

Edit: I added the flag and was able to boot to a low resolution desktop. I guess my next step would be to get the wifi adapter setup then run system updates to pull the nvidia driver?

Thanks again for helping out! Much appreciated.

Edit two! I got the wi-fi adapter set up and working. I then installed the latest Nvidia driver from Ubuntu Software Center, rebooted, and everything is just perfect! 

Thanks again for the help!

---

### Post by mörgæs on 2013-12-20
You are welcome. Please mark the thread 'solved'.

---

