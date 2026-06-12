---
title: "LiveCD Installation problem"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Jademalo on 2010-05-15
So ive been trying to install 10.4 as a fresh install from a LiveCD. I downloaded the 64 bit ISO (I use Win7x64 normally, my processer is a core2 duo 2.2ghz or something along those lines), booted it up, and it starts loading. after a while, the screen chantges to a massive amount of coloured static. I tried reburning the disc, but it made no difference.

Im now redownloading the file and the 32bit version too.

Is this a problem anyone else has had, and if it is, is there any way to solve it? I would really like to use the 64 bit version.

Thanks

---

### Post by kansasnoob on 2010-05-15
Be sure and check the md5sum of the .iso:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also when you first boot the CD as soon as the first screen shows up with two small logos at the bottom (human = keyboard) press any key to display the languages option and after selecting language you'll see several options. Choose "Check CD for defects". It takes a few minutes to run so be patient.

If that passes next choose to "Try without changes" and if you still get the garbled screen reboot again and look here:

[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

Those are older screenshots but try F6 and select "nomodeset".

---

### Post by Jademalo on 2010-05-15
> **kansasnoob said:**
> Be sure and check the md5sum of the .iso:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also when you first boot the CD as soon as the first screen shows up with two small logos at the bottom (human = keyboard) press any key to display the languages option and after selecting language you'll see several options. Choose "Check CD for defects". It takes a few minutes to run so be patient.

If that passes next choose to "Try without changes" and if you still get the garbled screen reboot again and look here:

[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

Those are older screenshots but try F6 and select "nomodeset".


nomodeset worked! thank you so much =]

---

### Post by Jademalo on 2010-05-15
Alas, ive got another problem.
After a seemingly faultless install, I restart my computer. It goes straight into windows 7 which i installed just before ubuntu.

I cannoy boot into the live disk, however i can boot subbesfully into the installer interface.

My drive is partitioned 10gb Ubuntu, 1gig swap, the rest windows 7, bar a 30gb partition at the end for world of warcraft. 

Is there anything I can do?

EDIT: In my stupidity grub installed on the random empty hard drive i had in my computer at the time. Whoops :E

Edit 2: Ok, now ive gotten into my installation exactly the same fuzziness happens. Even in recovery mode. I cant get into my ubuntu installation without this graphical.. coloured static thing

---

### Post by darkod on 2010-05-15
Boot the live mode (Try Ubuntu) and you can reinstall grub2 to the correct disk. Use the nomodeset again if it doesn't want to load the live mode.
Or did you manage to add grub2 already?

PS. You dodn't even need live mode. Make the other hdd as first option which will show you grub2 menu. Boot ubuntu, and once in there in terminal just add grub2 to the MBR of the correct disk.
For example, if the correct disk is /dev/sda, and grub2 now is only on /dev/sdb, just execute:

sudo grub-install /dev/sda

But that has to be from the hdd ubuntu. From live mode the commands are different.

---

### Post by Jademalo on 2010-05-15
> **darkod said:**
> Boot the live mode (Try Ubuntu) and you can reinstall grub2 to the correct disk. Use the nomodeset again if it doesn't want to load the live mode.
Or did you manage to add grub2 already?

I have grub installed, albeit to the wrong drive. My ubuntu is in the right place, and i can start booting it. I know how to fix grub now thankfully.

My problem is the same problem with booting the livecd. When booting into the hdd ubuntu installation through grub, Very early on, the screen just displays coloured static.

I have an nVidia GeForce 9500 GT if that makes any difference

EDIT: no matter what i do, I cant get into linux. It either hangs or displays this coloured static.
=[

---

### Post by Jademalo on 2010-05-15
Im starting to get stressed now. No matter what im doing in getting this same graphical glitch, be it booting from the live CD or the installation on my hard drive.

---

### Post by darkod on 2010-05-16
You can try updating the video driver. Do you get a grub menu at start? Select the recovery mode entry for ubuntu, not the normal.

If the process hasn't changed, in the next step select something like "root with networking" which should give you internet.
Once it loads the command prompt, try adding the EnvyNG package:

sudo apt-get install envyng-core envyng-qt

Run it in text mode with:

envyng -t

Select Install Nvidia driver from the menu. It will show two or three, so try googling a bit which is the correct driver for your card, so you know before you start. Sorry I use ATI and have no clue.

After you select the driver it downloads it automatically and installs it. When it finishes it will ask to restart and with some luck the normal grub entry will work this time. :)

---

### Post by Jademalo on 2010-05-16
I cant boot into recovery mode. The graphics load, but it just hangs.
EDIT: never mind, I see what youre getting at. Im struggling to get it to recognise the network now however :E

Edit2: Its coming back with "Couldnt find package envy-core"

---

### Post by Jademalo on 2010-05-16
Right, I cant do anything at all. I have internet access, I can successfully ping google, but I cant get envyNG to work at all. It just comes up as nonexistant.

EDIT: Ive been poking around, and apparently its been deleted from the lucid sources. Is there any way I can add karmic?

---

### Post by darkod on 2010-05-16
> **Jademalo said:**
> I cant boot into recovery mode. The graphics load, but it just hangs.
EDIT: never mind, I see what youre getting at. Im struggling to get it to recognise the network now however :E

Edit2: Its coming back with "Couldnt find package [COLOR=Red]envy-core[/COLOR]"

envyng-core
envyng-qt

Did you try with the above?

---

### Post by Jademalo on 2010-05-16
Ive tried pretty much everything that i can, and its not recognising anything to do with envyng at all. -core, -qt, anything. It just comes up as "couldnt find".
Apparently this is because its been deleted from the lucid repo. apparently.

Ive scoured all over the place however and found the .tar.gz. Is there any simple way to install it from this?

---

### Post by darkod on 2010-05-16
Not sure. But it just occurred to me that there is something else you can try. If you needed to set 'nomodeset' to install it, you might need it permanently, or at least for a while.

When you get the grub menu, highlight the ubuntu normal mode entry but don't hit Enter. Hit 'e' instead. It will show you the booting commands.

Move the cursor with the arrows to get to the line starting with linux, hit End to move it to the end and add nomodeset there. Press Ctrl + X to boot.

If that worked, once you are in your ubuntu installation, you can make it permanent with:

sudo gedit /etc/default/grub

in the line GRUB_CMDLINE_LINUX="" add it between the "". Save and close. Run:

sudo update-grub

to update the grub.cfg.

If that doesn't work I'm out of ideas. :(

---

### Post by Jademalo on 2010-05-16
> **darkod said:**
> Not sure. But it just occurred to me that there is something else you can try. If you needed to set 'nomodeset' to install it, you might need it permanently, or at least for a while.

When you get the grub menu, highlight the ubuntu normal mode entry but don't hit Enter. Hit 'e' instead. It will show you the booting commands.

Move the cursor with the arrows to get to the line starting with linux, hit End to move it to the end and add nomodeset there. Press Ctrl + X to boot.

If that worked, once you are in your ubuntu installation, you can make it permanent with:

sudo gedit /etc/default/grub

in the line GRUB_CMDLINE_LINUX="" add it between the "". Save and close. Run:

sudo update-grub

to update the grub.cfg.

If that doesn't work I'm out of ideas. :(

You are FANTASTIC!
INSTANTLY i got into it :D

On another note, I did manage to get envyng installed, but it came back with a lot of errors.

When i got in, i got a thing telling me to install some nvidia drivers. So im going to try them and see if they work.

---

### Post by milanbarossa on 2010-08-11
darkod, thanks a zillion.;) i have installed lucid netbook remix to my compaq mini and all I have seen was a blank screen with the cursor blinking. i spent the last ~3 hours to fix this problem.:x i removed quiet splash as you said, and then added "nomodeset" over there and it works!

---

