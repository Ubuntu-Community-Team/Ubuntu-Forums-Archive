---
title: "Can't boot after &quot;upgrade&quot; from 9.04 -&gt; 9.10 Server [images attached]."
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by coheed on 2009-12-21
Ok, so I'm a semi-Ubuntu newbie here. This post is about an error upgrading from 9.04 server to 9.10 server through GNOME's package manager where it tells you that there is a "new distribution available".

I had a problem in the past where an upgrade went corrupt (or something) and wiping the hard-disk and reinstalling with the newest CD solved the problems. This time, however, I have data on my hard-drive I'd like to retain (as well as all my user setups and network configuration, etc.)

So here's what happened: 
Package manager has been telling me for a while that there was a new distribution available, so I waited until I was caught up with work, and today decided to upgrade. All the steps went through fine. I checked on it periodically and everything was downloaded, and from what I remember seeing installed. Eventually, somewhere in the upgrade my screen went black and the mouse cursor froze on the screen. I waited for about another hour (even though when I had last looked at it, it said I had 21 minutes left), and figured that it was a lost cause at this point... Everything was frozen and nothing was making it respond (the HDD light wasn't blinking anymore either). So... not knowing what else to do, I hit the "reset" button on the computer box.

I'm assuming at this point that my upgrade/installation did not finish, and there's something seriously wrong here...

Here's what I'm seeing now. 

After reboot, I see the normal bootup text, it says it's loading grub (See pic_1.jpg below)

Then it goes to pic_2.jpg, where it says it's "Booting from (hd0,0) ext 3" and "Starting up"

All of this seems normal, if I can recall (I hardly ever had to restart!)

Then, pic_3.jpg is where the new stuff starts. I have never seen this loading image, but it goes to the screen, shows the white "ubuntu" logo or whatever it is for about 30 seconds, and THEN...

pic_4.jpg is where my computer freezes, and the cursor just blinks and nothing ever happens.


If I boot into recovery mode by pressing ESC when it asks for the GRUB boot menu, and select Recovery Mode (I choose option "Ubuntu 9.04 kernel 2.6.28-17-server [recovery mode]), I get a bunch of spit-out text, and then it stops on pic_6.jpg (the same as above except I can see all the other stuff that looks like greek to me...) There is no option to boot into a 9.10 kernel, and I'm not sure if there should be.

Any suggestions on how to get this up and running?

---

