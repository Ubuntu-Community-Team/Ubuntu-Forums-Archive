---
title: "Samsung 193P monitor has black stripe down one edge"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by Torben Lund on 2006-06-20
I'm a complete newb to Ubuntu but I have worked as a Windoze admin for 12 yrs so I can follow most instructions (even without a wizard :wink: ) I also have a Samsung 193p monitor, which has a 3/4" strip down the RHS of the display once Ubuntu has loaded - I just can't get rid of it 

If I reduce the resolution to a klunky-looking 1024x768, the screen is correctly filled - so it looks as though the refresh rate is the key. With my screen set at a resolution of 1280x1024, the stripe comes back as though the whole display is shifted to the left by about 3/4" (I note that the screen works fine at this resolution in Windows).  I have have tried to set the refresh to 60KHz in the Gnome preferences but the only option was 75KHz.

Drilling a bit deeper into the forums, I found a post suggesting changed to my xorg.conf. However, after setting my xorg.conf file so that it looked the one in @rosslaird's post ([http://ubuntuforums.org/showthread.php?t=19366)]("http://ubuntuforums.org/showthread.php?t=19366%29"), I rebooted and found that was still unable to reduce the refresh rate below 75Khz because the drop-down list only has one entry: 75Khz :confused: 

Can somebody please help out at hapless newb and tell me what I have to do to make 60MHz an option for 1280x1024 in the screen resolution dialogue? Perhaps I have edited the wrong conf file or I'm missing something else...?

Just for added interest, is there a standard screen-rotation utility that might work with my display?

_[COLOR=Red]** Edit - Fixed it!**[/COLOR]_

Many thanks to Ross Laird for his help with this. I won't replicate the detail here, but everything I needed can be found here: [http://ubuntuforums.org/showthread.php?p=1164353#post1164353]("http://ubuntuforums.org/showthread.php?p=1164353#post1164353")

Still looking for screen rotation sofware though...

Torben

---

