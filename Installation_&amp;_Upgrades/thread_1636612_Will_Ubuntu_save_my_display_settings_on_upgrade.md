---
title: "Will Ubuntu save my display settings on upgrade?"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by dogmom on 2010-12-03
I have a Dell Latitude C600 that's running Jaunty / 9.04.  It works great, but I'd like some of the added bling of 10.04, including the extra workspaces.  However, the reason I went with Jaunty in the first place is because that version still has (and uses) the xorg.conf file, which had to be extensively modified so that the display would work properly.  Resolution of the Latitude is 1024x768, but xrandr insists that it's 800x600.
I have seen the "fixes" for 10.04 that tell the user to "change" their xorg.conf file, but a fresh install of 10.04 doesn't *have* an xorg.conf file.  That's why I went with Jaunty in the first place - because it had the file I needed to modify. Therefore, I am not sure how far I can trust those "fixes" to be accurate. 

Since I use the computer for several things, and I have a lot of items already saved on there, including extra programs I need for my job, I want to make sure that if I upgrade, I won't have to scrub it and start over.  So here's my question: can I safely upgrade my Latitude to 10.04, and will it still display correctly, or will the display be hijacked by xrandr and fail to work in the future?  And, are there any other "gotchas" that I can / should expect if I do upgrade?  Thanks very much for any help or advice you may have.

---

### Post by cmcanulty on 2010-12-03
You should also consider creating a separate home partition. I backed up all my files then did that with a live CD. Didn't mess up anything and all my files were still there but definitely backup first in case of an error. Now when I upgrade almost everything stays the same. The downside is of course any build up of errors will remain also.

---

### Post by dogmom on 2010-12-03
I'm not sure what you're recommending.  Creating a new home partition with a live CD?  Upgrading using a live CD?  In any case, I can't use a live CD, due to the display issues.  I've tried using a live CD now that I got the display issue resolved, but the live CD apparently uses xrandr - which caused the problem in the first place.  I get a split screen - the display is a bit scrambled, and I can't actually select anything easily.  I was hoping to just upgrade either using Update Manager or via apt-get in command line, but I don't want to risk losing all my stuff or having to rebuild if it jacks everything around.

Thanks for the reminder to back up my stuff before I start, though - that WILL be invaluable.

---

### Post by cmcanulty on 2010-12-03
The reason I said use live CD is you need to repartition when drive is unmounted which means using a live CD but you can use another live CD Knoppix and Puppy live Cds work well and you just burn a CD then run as a live session and set like 10 or 1`5 GB as / partion (boot and system) and rest as /Home with all your settings and documents.There are several detailed tutorials on doing that.By doing it on a lighter distro you may get around the screen issue. It doesn't mean you are installing those systems just use it for the repartitioning. Then when your/Home is on a separate partition you can upgrade without messing up all your configs as only the / partition is redone on an upgrade. Read a little from the web sites and if still confused ask something else.

---

### Post by dogmom on 2010-12-03
Ah, I see now.  Thanks.  

If I do that, will my xorg.conf file setting override 10.04's desire to use xrandr instead?  That's really the whole question - if I have an xorg.conf file, will 10.04 use it?  If not then I've still gone through all that partitioning for essentially no purpose.

---

### Post by cmcanulty on 2010-12-03
First do a search and find exactly where the file is. If it is in /Home it will stay the same if it is in / then it wouldn't help. I think I was doing a tweak recently and looked for that file and didn't find it anywhere but you also could copy your file and paste it somewhere in your home folder then put it back in the correct place after partitioning but I hope someone else will confirm this first as I don't want to screw up your system. I did a search and on my system it is in the
 Home/cmcanulty/build/target/generic/target_xenclient_skeleton/etc/x11/xorg.conf
I hope yours is there too as it took forever to type! I couldn't find a way to copy paste it.

---

