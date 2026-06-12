---
title: "Blank Monitor after fresh LAMP Server installation"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by CaptainCalvin1987 on 2013-03-07
I have worked with Ubuntu in the past, this time i am working with the Server Distro and i went through the installation and selected the LAMP server. After it was completed, it booted back up and it just went to a blank screen. I was able to see the GRUB screen and select option if necessary. I know the server is online because i can view the test PHP page when browsing to the IP address. Any ideas on how to bring the terminal up on the monitor. I am not able to get to it with SSH because the connection is refused.

Thanks!

---

### Post by MAFoElffen on 2013-03-07
AlthougH Server Edition is text base, it still uses a VGA graphics layer... So if it has nvidia or radeon GPU, it will come up with tweaked graphics. Simple fix.

First question would be to ask- What kind of graphics GPU does that PC have?

Second would be... On server, with the Grub2 menu, you have only 2 seconds to hit a <down-arrow> key before that menu disappears to keep it there. Then arrow to the first menu item. Press <e>, Go down to the line that starts with "linux", arrow over to where it say "RO" and after if add "-Single --verbose nomodeset"... Press <cntrl><x> to boot. It will boot with verbose messaging on, with kms off.

Since there is no splash screen, just blank until the login... there is a lot going on during that boot process. One of my servers stays blank for 1 -1.2 minutes before it actually gets to the login... Needs to make sure it's not just "working"... or hanging on something else.

Another thing th=o help this is to see if you can get to a root prompt from the rescue menu. 

Will followup from there after you've answerd and tried those things...

---

### Post by CaptainCalvin1987 on 2013-03-07
Thanks for the Reply, I didn't even think about the GPU. What i actually did is just took out the GPU card that was in there and used the native VGA from the Motherboard which works fine.
Thanks!

---

