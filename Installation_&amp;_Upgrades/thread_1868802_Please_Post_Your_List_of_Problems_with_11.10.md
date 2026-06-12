---
title: "Please Post Your List of Problems with 11.10"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by pukster on 2011-10-24
I accidentally upgraded to 11.4 (I thought it was a security update) and it was a nightmare to get that working. In a classic case of fool-me-once... I upgraded to 11.10 and I am having less serious problems, but they are still there. NOTE: if there is a more official channel to talk about these problems, I have no problem merging this topic, or moving it.

Please share your problems.

1)Alt+Tab is annoying. If I have three terminals, it groups them all as one terminal (Apple does this too). I have to either stay alt+tabbed on the terminal for a second before it shows each terminal, or manually click on the desired terminal (however, this does not work for maximized terminals).
2)Mouse wheel can no longer be used to navigate different tabbed windows of, for example, gedit.

---

### Post by df747jet on 2011-10-25
You can install the Compiz Config manager to help fix your alt-tab problem.
```
sudo apt-get install compiz-config-settings-manager
```

The application should show up under System > Preferences

Try using the Static Application Switcher, or the Shift Switcher, to see if they work better for you. 

As for #2, use Vim or E-macs. ;)

---

### Post by flitbee on 2011-10-25
I upgraded to 11.1 and I got a screen asking me to login. I've not got this before, but anyway I entered by root password but it doesn't seem to recognize it. I cannot access any files! Anybody experience the same? This upgrade is a TOTAL SHOWSTOPPER for me. I cannot login to my own system!!

[IMG]http://desmond.imageshack.us/Himg534/scaled.php?server=534&filename=img2579is.jpg&res=medium[/IMG]

---

### Post by paskari on 2011-10-25
> **df747jet said:**
> You can install the Compiz Config manager to help fix your alt-tab problem.
```
sudo apt-get install compiz-config-settings-manager
```

The application should show up under System > Preferences

Try using the Static Application Switcher, or the Shift Switcher, to see if they work better for you. 


I did that it led to the THIRD problem associated with 11.4/11.10, workspaces having seizures. Does this happen to anyone else? You have 5 windows in each of 6 workspaces spread across 3 monitors, then you try to switch to another workspace, and the screen goes all epileptic and when it stops twitching, everything is randomized. This has to be the most irritating problem because reorganizing everything is a helluva chore

The icing on the cake is that the only real solution to this, a simple script to generate all necessary windows and assign them to desired target windows/workspaces which is called on login, is impossible. There is no way to launch a window and specify where it should open up. $DISPLAY does not work, neither does wmctrl

---

### Post by paskari on 2011-10-25
They shouldn't advertise beta upgrades, then idiots like me foolishly click upgrade thinking everything is going to be OK, then the sky starts falling.

They should set up an old school ftp site so only the hard core coders dare download it.

---

### Post by flitbee on 2011-10-25
> **paskari said:**
> They shouldn't advertise beta upgrades, then idiots like me foolishly click upgrade thinking everything is going to be OK, then the sky starts falling.

They should set up an old school ftp site so only the hard core coders dare download it.

It's a beta upgrade? But i got the alert via Update Manager asking me to update to 11.1 :(

---

### Post by pukster on 2011-10-25
> **flitbee said:**
> It's a beta upgrade? But i got the alert via Update Manager asking me to update to 11.1 :(

11.4 was a beta, 11.10 is a [beta2]("http://fridge.ubuntu.com/2011/09/22/ubuntu-11-10-beta-2-oneiric-ocelot-released/"). I'm assuming that's not quite good enough to be a stable build.

---

### Post by flitbee on 2011-10-25
> **pukster said:**
> 11.4 was a beta, 11.10 is a [beta2]("http://fridge.ubuntu.com/2011/09/22/ubuntu-11-10-beta-2-oneiric-ocelot-released/"). I'm assuming that's not quite good enough to be a stable build.

Why did it appear in the Ubuntu Update Centre (or whatever it's called)?? I thought that was only for Stable releases. Like Windows Update. I assumed it was safe and went ahead updated. And now I can't login! I was beginning to like Ubuntu

---

### Post by pukster on 2011-10-25
> **flitbee said:**
> Why did it appear in the Ubuntu Update Centre (or whatever it's called)?? I thought that was only for Stable releases. Like Windows Update. I assumed it was safe and went ahead updated. And now I can't login! I was beginning to like Ubuntu

The exact same thing happened to me wrt 11.4 and now it is happening again with 11.10 (although it's my own damn fault for making the same mistake twice). Now my Unity thingy is gone. Basically I can't open any programs, and my workspaces are gone. I had to hit 50 permutations of Ctrl, Alt, shift, Option and T to get the terminal to open up so I could type google-chrome so I could get here to find a solution

---

### Post by flitbee on 2011-10-25
> **pukster said:**
> The exact same thing happened to me wrt 11.4 and now it is happening again with 11.10 (although it's my own damn fault for making the same mistake twice). Now my Unity thingy is gone. Basically I can't open any programs, and my workspaces are gone. I had to hit 50 permutations of Ctrl, Alt, shift, Option and T to get the terminal to open up so I could type google-chrome so I could get here to find a solution

And did you? Were you able to recover anything? I can't login too..

---

### Post by pukster on 2011-10-25
> **flitbee said:**
> And did you? Were you able to recover anything? I can't login too..

Maybe I should not have said 'exact'. My system kept halting before going to the login screen. I had to delete my xConfig file and then it worked. In your case, I don't know. The only thing I can suggest is to either try logging in as root, or login command line to see if that works.

---

### Post by pukster on 2011-10-25
> **flitbee said:**
> And did you? Were you able to recover anything? I can't login too..

yours sounds like your password got corrupted, or your account was deleted.

---

### Post by ratcheer on 2011-10-25
I had a very difficult time upgrading from 11.04 to 11.10. My system kept freezing during the upgrade process and, after I finally got the upgrades finished, it froze every time I tried to login. I finally gave up and did a fresh install.

Unfortunately, the fresh installation was freezing at the login screen, too. I eventually solved the problem. I run Arch Linux in another partition on the disk. Apparently, coincident with running the Ubuntu upgrade (I think the upgrade process caused it, but I will never be able to prove that), shutting down Arch started leaving my external USB drive in a bumfuzzled state that caused system freezes for 65 seconds after every reboot. Once I learned that, it became a simple matter to remember to umount the external drive before rebooting from Arch.

Note that Arch and Ubuntu had peacefully coexisted on my system for weeks prior to running the Ubuntu upgrade. Both Linuxes had shared the external drive with no problems at all. And now that the freezes started occurring, they continue. The freezes occur whether I am booting to Ubuntu or Arch. Or even to the Parted Magic CD, although that freeze is much shorter.

So, even though I am working around the problem, I wish I had never done the Ubuntu upgrade. It seems to have affected something about my PC, itself.

Tim

---

### Post by runeh76 on 2011-10-25
Only way to enter graphical-mode is to hit Ctrl+Alt+F1 and type startx...every boot.

Second problem is that i dont have working internet anymore :)

Im clad that i took image backup!!

I made thread 10 minutes ago here (installation&upgrades), pls give me solutions!

Thank you!

---

### Post by coffeecat on 2011-10-25
> **pukster said:**
> 11.4 was a beta, 11.10 is a [beta2]("http://fridge.ubuntu.com/2011/09/22/ubuntu-11-10-beta-2-oneiric-ocelot-released/"). I'm assuming that's not quite good enough to be a stable build.

This is not so.

11.04 was released on 28th April 2011 after having gone through the beta phase in March and early April. The link you posted was the announcement on 22nd September for the beta2 ISO of 11.10. 11.10 went final on 13th October 2011, which is mentioned near the end of the link.

Since there is already a sticky thread about 11.10 bugs and their workarounds here:

[http://ubuntuforums.org/showthread.php?t=1859528](http://ubuntuforums.org/showthread.php?t=1859528)

I am closing this thread.

---

