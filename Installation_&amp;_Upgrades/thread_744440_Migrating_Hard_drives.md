---
title: "Migrating Hard drives"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by jpw27 on 2008-04-03
I just got a hard drive to replace my current small one.  What I would like to know is what is the easiest way to migrate all my data over to the new one.  Is there a way to make a bootable copy of it?  Or would a clean install on my new drive and then copying my /home and /usr directories work?

Thanks,
Jason

---

### Post by VMan on 2008-04-03
You can make a backup of your current HD and then restore it to the new one.  That sounded like the best (but not easiest) path.  I happened to have an external HD that was big enough.  I copied my /home directory to the external HD, performed a new install to the new HD, and then copied my /home files from the external HD to the new HD.  I picked this path since I had made several mistakes with my old installation and wanted to start fresh.  The only problem I ran into was that I couldn't find a .deb package of the emerald theme I was using.  I put my old HD back in, copied the theme to a USB stick, swapped HDs again, and then installed the theme I wanted.  I'm using a theme called "Lime Green Refresh" and had my desktop heavily customized to look really good with it (colors, icons, wallpaper, splash screen, background color).  I didn't copy the /user directory as i was performing a new install and didn't want any of the errors I had created with the old one to carry over.  

If this doesn't sound like fun to you, there are some instructions and some backup programs out there that are supposed to back up your entire HD partition and then restore it to a new HD.  If I remember, you had to use a live CD to boot and restore.  If you still need help, post here and send me a PM (I don't always check the forums like I should).  I'll try to dig up the info I found back then.

By the way, I found it very useful to keep my old HD.  I constantly swap them out.  That way I can test new stuff on the old HD without the possibility of screwing up an install that I really like.  This is on a laptop so swapping the HDs is as easy as two screws, remove a plastic cover, unplug the current HD and pug in the other HD.  It was a real lifesaver a few months ago when I was trouble shooting network problems (the school's security system doesn't like linux or macs).  I was able to figure out a solution (took several installs and configurations) and then apply the solution that worked to the installation that I intended to use.

---

