---
title: "Black Screen, blinking cursor after updating"
date: 2014-05-04
forum: Installation &amp; Upgrades
---

### Post by 10011010010 on 2014-05-04
I attempted to update from 13.04 to 13.10 yesterday. When I restarted the computer at the end of the update process and selected ubuntu, a bunch of white text came up. I don't remember the details, but I think it said [OK] after each line. The last line said "Starting". I waited for 20 to 30 minutes with no change, and then I turned off the computer and tried to reboot. Since then, after I select Ubuntu, I get a black screen with a flashing cursor.

I searched for the issue on Google and ran boot-repair. The details are here: [http://paste.ubuntu.com/7388479/](http://paste.ubuntu.com/7388479/)
Note that after I ran boot-repair and rebooted the computer, before going back to the all-too-familiar blank screen with blinking cursor, it displayed some text on the screen breifly. I didn't have time to get a picture or anything, but the last line was something to the effect of "[computer name] login>". Since then there has been no text on that screen.

Any help would be greatly appreciated. I haven't exactly been thrilled with having to use windows.

---

### Post by 10011010010 on 2014-05-04
Could this have something to do with this: "/usr/sbin/grub-bios-setup: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track."?

---

### Post by ajgreeny on 2014-05-04
See this thread which suggests a good answer, but I have never even heard of flexnet before and don't use windows, so this is all foreign to me. However, there is a great deal of info on your problem at [https://www.google.co.uk/#q=site:+ubuntuforums.org+flexnet&safe=off](https://www.google.co.uk/#q=site:+ubuntuforums.org+flexnet&safe=off) which I will have to leave you to try to figure out.  Boot repair is supposed to be able to fix the problem but it appears yours did not do so.

The only other thing I can do is wish you good luck; I hope you manage to fix this.  Keep us all informed if and when you figure out the solution.

---

### Post by 10011010010 on 2014-05-04
I used the procedure described [here]("http://ubuntuforums.org/showthread.php?t=1661254") to clear sectors 1 through 62 and then reinstalled GRUB. the problem remains. I ran boot repair again and it was unable to fix whatever the issue is. It shows that FlexNet is gone, so apparently that wasn't it. The information is [here]("http://paste.ubuntu.com/7394361"). I don't know if this is relevant, but here is the message that gets displayed when I shutdown the computer from the black screen.
[IMG]http://i564.photobucket.com/albums/ss90/Titanium_Crusher/Screenshot_2014-05-04-15-59-28.png[/IMG]

---

### Post by 10011010010 on 2014-05-07
Any ideas? Help would be greatly appreciated. I have made no progress in the last couple of days.

---

