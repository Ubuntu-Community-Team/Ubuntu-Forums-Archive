---
title: "Resolution problem revisited"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Larikun on 2007-10-20
Ok, so I installed Feisty a little while back on my laptop, and like a few others I had a problem with my resolution getting stuck at 800x600, after some reading through these forums and whatnot I found a solution to it, no real big problem to it.

(Fixed with the sudo dpkg-reconfigure xserver-xorg command mainly)

Now with the upgrade to Gusty, when I boot up, I can visually make out the logon screen, so I know X is starting, but after some fooling around and getting really frustrated with a flashing screen with an external monitor, I figured out what was going on.

The upgrade somehow set X to use a default resolution of 1600x1200, so considering it's basically the same problem with being stuck at 800x600, I figured I'd follow the same steps to try and correct it.

After booting into safe mode (or whatever you want to call it) I ran the xserver configure program again, went through the steps I was used to and set up my monitor resolution/refresh rates.

Boom, problem persists, so I remembered there was another way around this problem and it involved modifying the xorg.conf file and just removing or adding resolutions/refresh rates in it.

However when I got into the file, all the resolutions I had set up in the reconfiguring of xserver were still there... so I decided to try and start X back up and see if everything was fine.

Nope it defaulted back up to 1600x1200.

So in short for those who aren't interested in reading all that mess I have done these steps to try and fix the problem:

1. Reconfiguring xserver.
2. Editing the xorg.conf file.
3. And manually setting the resolution once X started all the way up and I was on the desktop (just a flickering screen which resulted in a headache) down to 1280x1024.

Once I was able to set the resolution back down to 1280x1024, it actually didn't stick and the graphics didn't kick back in, so I did a ctrl-alt-backspace and it just handed me back into the terminal.

So in really big shortness, I can't get my resolution to go down to 1280x1024 (or anything else I tried), X seems intent on sticking at 1600x1200.

---

