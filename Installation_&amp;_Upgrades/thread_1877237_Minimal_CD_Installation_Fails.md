---
title: "Minimal CD Installation Fails"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by matt3839 on 2011-11-07
Hello, I'm currently having some issues installing Ubuntu 11.10 AMD64 from the minimal installation disc (mini.iso).

Now, I've used the minimal CD in the past, and have had nothing but success with setting up a comfortable computing environment, but this time, I've been having odd errors:

The installation goes perfectly well throughout from start to finish, and the installer automatically reboots when it's done as normal, but after that, nothing. If I pick no packages during tasksel, the computer simply turns on and the text install, where I usually pick up from, does not boot; I'm not sure how to describe it, but my monitor continues to go from "No Signal" to a black screen as if it were warming up to display a signal, no error messages, no GRUB rescue screen or anything I could work with, which is extremely aggravating.

After trying that a few times, I decided to install the Lubuntu minimal desktop instead so I would have something to work with, but that time, when I booted into my new install, the Lubuntu splash screen popped up for a split-second before displaying an error about a "Broken pipe" and stopping with the flashing cursor.

I strongly doubt it's my computer (a custom-built Athlon II X4 machine), because other Linux distributions like Debian and Fedora boot easily and run superbly, but if I knew any better, I wouldn't be asking here... does anybody have a possible solution to this predicament? I will gladly provide any additional information!

---

### Post by MAFoElffen on 2011-11-07
> **matt3839 said:**
> Hello, I'm currently having some issues installing Ubuntu 11.10 AMD64 from the minimal installation disc (mini.iso).

Now, I've used the minimal CD in the past, and have had nothing but success with setting up a comfortable computing environment, but this time, I've been having odd errors:

The installation goes perfectly well throughout from start to finish, and the installer automatically reboots when it's done as normal, but after that, nothing. If I pick no packages during tasksel, the computer simply turns on and the text install, where I usually pick up from, does not boot; I'm not sure how to describe it, but my monitor continues to go from "No Signal" to a black screen as if it were warming up to display a signal, no error messages, no GRUB rescue screen or anything I could work with, which is extremely aggravating.

After trying that a few times, I decided to install the Lubuntu minimal desktop instead so I would have something to work with, but that time, when I booted into my new install, the Lubuntu splash screen popped up for a split-second before displaying an error about a "Broken pipe" and stopping with the flashing cursor.

I strongly doubt it's my computer (a custom-built Athlon II X4 machine), because other Linux distributions like Debian and Fedora boot easily and run superbly, but if I knew any better, I wouldn't be asking here... does anybody have a possible solution to this predicament? I will gladly provide any additional information!
I need to ask some questions--

1. When you installed from mini.iso, when it got to the TASKEL screen, what screen manager did you install?

2. When it booted after the minimal install, did that black screen have a purplish hue to it?  Thinking it went from a total text to Graphical screen, where X started and hung.
   a. Did you try to press <cntrl><alt><F2> to see if you could get to a TTY text session?
  b. While that was installed, did you try to press shift on boot to see if the grub menu came up? 

3. What is the Video is this box?  

4. What is your goal?  I'm asking you where want to get to, with an offer of help to get you there....

5. Does this PC boot and run the Live Image from the LiveCD?

I have some ideas on what is happening but need info to narrow that down. I am wondering why an AMD64 box would need a minimal install instead of the LiveCD or Alternate Install > thinking that there must be some reason that maybe you might expand on...

---

### Post by matt3839 on 2011-11-07
> **MAFoElffen said:**
> I need to ask some questions--

1. When you installed from mini.iso, when it got to the TASKEL screen, what screen manager did you install?

2. When it booted after the minimal install, did that black screen have a purplish hue to it?  Thinking it went from a total text to Graphical screen, where X started and hung.
   a. Did you try to press <cntrl><alt><F2> to see if you could get to a TTY text session?
  b. While that was installed, did you try to press shift on boot to see if the grub menu came up? 

3. What is the Video is this box?  

4. What is your goal?  I'm asking you where want to get to, with an offer of help to get you there....

5. Does this PC boot and run the Live Image from the LiveCD?

I have some ideas on what is happening but need info to narrow that down. I am wondering why an AMD64 box would need a minimal install instead of the LiveCD or Alternate Install > thinking that there must be some reason that maybe you might expand on...

1. I did not select a screen manager, I was going to proceed with my setup from a text console after I booted into my new installation, though during the final attempt, I did select a single option, the Lubuntu minimal desktop.

2. I did not explicitly attempt those, I'm afraid, but I *did* attempt to press just about every key on the keyboard to see if I could get it to respond, including some Ctrl/Alt key combinations, but to no avail. If I might have missed one, I don't mind giving it another shot.

3. A Radeon HD 4650. When booting from a text install in other distributions, I have no issues, and I also get smooth, fluid performance when using graphical applications.

4. My goal here is to have a minimal installation going: I generally dislike Unity, KDE, etc. but feel that at the core, Ubuntu is a superior solution for a Linux desktop. I usually use the minimal CD because it's easier and faster to build up rather than tear down, and most of the packages I planned to install, like awesome, are in the repositories anyway.

5. Yes, live installation media works as normal.

---

### Post by MAFoElffen on 2011-11-07
> **matt3839 said:**
> 1. I did not select a screen manager, I was going to proceed with my setup from a text console after I booted into my new installation, though during the final attempt, I did select a single option, the Lubuntu minimal desktop.

2. I did not explicitly attempt those, I'm afraid, but I *did* attempt to press just about every key on the keyboard to see if I could get it to respond, including some Ctrl/Alt key combinations, but to no avail. If I might have missed one, I don't mind giving it another shot.

3. A Radeon HD 4650. When booting from a text install in other distributions, I have no issues, and I also get smooth, fluid performance when using graphical applications.

4. My goal here is to have a minimal installation going: I generally dislike Unity, KDE, etc. but feel that at the core, Ubuntu is a superior solution for a Linux desktop. I usually use the minimal CD because it's easier and faster to build up rather than tear down, and most of the packages I planned to install, like awesome, are in the repositories anyway.

5. Yes, live installation media works as normal.
I know when I tested dev-Onieric iso's in the last test cycle, on the mini.iso, the text console install worked great... If I did the default install, if I "didn't " select a desktop at the TASKEL screen, when it finsihed and rebooted, if would hand oon a purplish screen... 

What would happen was that it included a "vt.handoff=7" kernel boot option, which is fine for a graphics session, but not for text.  (remove if need for text.)

Ubuntu base is very solid = I agree.  Unity overhead is high.  Good plan.

On recent changes to that base, even Grub2 and the kernel is doing more with graphics. It is doing all that through KMS technologies. Your more familiar with your model of Radeon card.  Isn't the HD4650 one of those cards where the drivers are on the cusp, where you can use the opensource xorg.xserver-video-radeon, the fglrx or Catalyst drivers?  

Some HD 4650's have problems booting with KMS without the drivers configured yet. You can turn it off temporarily from the Grub boot menu:
Hold the shift key down while booting up.  At the Boot menu, press "e" to get into an edit mode.  Arrow down to the line that starts with "linux." Arrow right over to after where it says "quiet splash" and before where it says "vt.handoff=7" and insert the text "radeon.modeset=0".  That will turn of KMS for your card to boot.

On "Broken Pipe" issues: Reinstall and see if it reoccurs.  That one is a plymouth issue that seems to keep popping up since 10.04.  Please report it so they can come up with "another" patch

---

### Post by matt3839 on 2011-11-07
> I know when I tested dev-Onieric iso's in the last test cycle, on the mini.iso, the text console install worked great... If I did the default install, if I "didn't " select a desktop at the TASKEL screen, when it finsihed and rebooted, if would hand oon a purplish screen... 

What would happen was that it included a "vt.handoff=7" kernel boot option, which is fine for a graphics session, but not for text.  (remove if need for text.)Interesting, I'll give it a shot as soon as possible, many thanks.

> Ubuntu base is very solid = I agree.  Unity overhead is high.  Good plan.Why, thank you. :)

> On recent changes to that base, even Grub2 and the kernel is doing more with graphics. It is doing all that through KMS technologies. Your more familiar with your model of Radeon card.  Isn't the HD4650 one of those cards where the drivers are on the cusp, where you can use the opensource xorg.xserver-video-radeon, the fglrx or Catalyst drivers?

Some HD 4650's have problems booting with KMS without the drivers configured yet. You can turn it off temporarily from the Grub boot menu:
Hold the shift key down while booting up.  At the Boot menu, press "e" to get into an edit mode.  Arrow down to the line that starts with "linux." Arrow right over to after where it says "quiet splash" and before where it says "vt.handoff=7" and insert the text "radeon.modeset=0".  That will turn of KMS for your card to boot.Makes sense, thanks.
However, does this have any impact on the configuration of the installed system, i.e. will I need to reactivate KMS once I've booted into my new system? Forgive my ignorance, I'm not used to taking special steps during installation, especially since my card works perfectly outside of this issue.

> On "Broken Pipe" issues: Reinstall and see if it reoccurs.  That one is a plymouth issue that seems to keep popping up since 10.04.  Please report it so they can come up with "another" patchI would be more than happy to.

---

### Post by MAFoElffen on 2011-11-07
> **matt3839 said:**
> 
However, does this have any impact on the configuration of the installed system, i.e. will I need to reactivate KMS once I've booted into my new system? Forgive my ignorance, I'm not used to taking special steps during installation, especially since my card works perfectly outside of this issue.
What I described on turning off KMS is a temporary fix to get you passed the the black/purple screen--> So you install your graphics driver.  Once your graphics driver is installed it would not be needed anymore.  Do it as I described is just in temporary memory, on the fly.

One other tip:  
If you do fglrx... once you get booted, edit your /etc/apt/sources.list and uncomment the 2 lines for the Conical Partners Repo. If you don't do that, the flgrx drivers won't show in the additional drivers applet.  Don't know why this wasn't a default, but it's something that affects you and you need to know about.

---

### Post by matt3839 on 2011-11-07
Oh, goodness, I feel so silly. This entire time, I kept forgetting to select "command-line install" from the boot menu.

I sincerely apologize for using up any valuable time, and greatly appreciate your assistance.

---

### Post by papibe on 2011-11-08
Just consider that you may still boot into a black screen because of a bug. Check this thread [here]("http://ubuntuforums.org/showthread.php?t=1836985") to both bypass it and fix it.

Regards.

---

### Post by MAFoElffen on 2011-11-08
> **matt3839 said:**
> Oh, goodness, I feel so silly. This entire time, I kept forgetting to select "command-line install" from the boot menu.

I sincerely apologize for using up any valuable time, and greatly appreciate your assistance.
No problems.  I'm here to help / as others helped me early on when I needed it.  Believe me, I still need help on some things.

Please use the "Thread Tools" link and mark this thread Solved, right?

---

### Post by matt3839 on 2011-11-08
Ah, the issue was that for some reason, a tty session only opens when manually switched to. I'm guessing it has to do with Ubuntu's traditional suppression of startup messages, but  no matter.

Thank you all for your help. I'll mark the thread as solved as soon as I can--I can barely send this, since I'm on my phone...

---

