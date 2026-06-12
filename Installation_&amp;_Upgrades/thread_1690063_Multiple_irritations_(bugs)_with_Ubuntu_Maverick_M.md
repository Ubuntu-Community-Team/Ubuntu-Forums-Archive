---
title: "Multiple irritations (bugs) with Ubuntu Maverick Meercat (10.10)"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by achim_59 on 2011-02-17
To get this basic question out of the way: I am using an IBM T43 Thinkpad.

I recently did a fresh install of Maverick (upgrade from Lucid not an option. (see [here]("http://ubuntuforums.org/showthread.php?t=1672315")) and reinstalled my data from backups.

I have since had a number of problems.

1. My most serious issue is the one with Evolution described in the link above. No solution in sight, sadly. I suspect that this is, however, a problem with evolution and not Ubuntu.

2. I get a garbled screen when I try to attach an external monitor. There appears to be a solution. See [this Ubuntu forum thread]("http://ubuntuforums.org/showthread.php?p=9958943"). Whether it works or not will have to wait until I get the chance to try it at home on a weekend. I'll make an amendment to this post if it does.

3. When I attach the T43 to its docking station, the machine won't boot at all. Quite simply nothing happens. I have to detach it, boot the laptop and then attach it to the docking station. The docking station worked fine with Lucid and earlier versions.

4. Nautilus started acting up after a few days. This began after I used the Rhythm Box music player. Thereafter each time I attempted to use the quick link to my home folder (yes, the desktop launcher,too) the music player would start instead of nautilus. I checked the properties for the launcher and everything seemed correct. The simple work-around was to remove the launcher altogether and add a new one. (The command, if anyone doesn't know, is simply "nautilus". The home folder is the default URI.)

5. occasionally i get a blotchy screen on startup. This did not happen before (e.g. with 10.04). The only option then is to force a shutdown and restart. Oddly, I don't have to hold the button for 5 seconds, it does the shutdown immediately. The second restart has, touch wood, always worked up to this point. This is really weird and doesn't happen every time. It occurs every 5th to 10th time I try to start the laptop.

I wonder if anyone else has had similar problems.

Achim.

---

### Post by AlvitrValkyrie on 2011-02-17
I don't know if this will help, but try clearing Evolution through the Synaptic Package Manager after you clear the folder. Re-install it, and then drag data from your backup into the .evolution folder, and into the right folder within. You can also "Mark All Upgrades" in the Package Manager and see if any of those will help your computer's issues. You can go to the Updates tab in the Repositories section (under Settings) of the manager and check the other two boxes. That will let you see what's available but not fully recommended.

Ubuntu 10.10 doesn't seem to be at a stage where it works perfectly with everything. My Logitech headset is having a similar problem to your docking station--it works, but not well. [The max volume is horribly low compared to when connected to a computer running Windows.]

I have the exact same problem as 4.

It seems there are an insane amount of updates for 10.10, most of which don't make any physical difference. A lot of these issues. for me, normally come after updates, or if I install a premature application from the Ubuntu Software Center. While the forums are amazing, I think the team should do some more product testing.

I'll add a number 6.
Sometimes the drop down menus for applications in the top panel appears bright, but it switches between that and a dark gray.

Besides all that, I think Ubuntu 10.10 "Maverick Meercat" for the desktop is pretty amazing. May not be perfect, but it is very compatible with a lot of things. Kudos to all the developers and open-sourcers out there.

---

