---
title: "Unable to shutdown properly"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by junxuan on 2010-04-02
I'm having some issues with the shutdown of lucid lynx. It never seems to complete. It always gets stuck at the part where the 5 dots change colour. It didn't work on a clean install at first. I updated everything and it still couldn't shut down. Even when I shutdown straight from the login(before I even use it) it still fails to shut down. Anyone having the same issues?

btw my bootup time is also horrible, i see the cursor blink for quite some times, far from 10 sec :/

---

### Post by ZeroLinux on 2010-04-02
In grub press "E" 
Go to kernel options 
Try to add after "quiet splash" smth like  "acpi=off" - it may speed up booting. "Press Ctrl-x" Enjoy speed booting. Just try.
But it will not help you to shutdown your computer. 
To solve this issue you should pick up what really helps from [here]("https://help.ubuntu.com/community/BootOptions")
It seems the problem is in ACPI system. Try different options from the 1s table "Kernel Options"
 
Let us know after what problem happens. Delete words "quiet splash" and watch the process of booting

And the you can find problematic place in /var/log/dmesg.log

After finding right parameters you can easy add them permanently

---

### Post by junxuan on 2010-04-02
Thanks bro, I'll test it and see how it goes :)

---

### Post by zika on 2010-04-02
I'm complaining on that problem, for months, now... If You find anything useful, please share with us...

---

### Post by junxuan on 2010-04-02
adding the acpi=off still doesn't work, boot up still takes quiet long. FYI Windows 7 boots almost as fast >.<, as far shutting down, I still have not had a successful one :/

---

### Post by bvanaerde on 2010-04-03
Same problem here, on my laptop (Acer Travelmate 4001WLMi).
I have to shutdown "the hard way". It seems everything gets shut down properly, I even notice that the hard disk stops spinning, and after that it remains in an infinite loop at the shutdown page.

I've had shutdown problems on my laptop for each beta release, and they always got fixed with the stable release. So I'm quite confident it will be solved in no time.

---

### Post by louieb on 2010-04-04
T30 laptop - just stared hanging on shutdown with the update of a couple of days ago. - Lucid  Alpha  installed back January - and up to date as of last night. Oh well...

---

### Post by bvanaerde on 2010-04-21
I noticed that, when pressing ALT+F1 right after shutting down (before the shutdown screen with the blinking lights), my laptop does shut down.
This will bring you to a console screen, and then it immediately shuts down correctly.

---

### Post by LowSky on 2010-04-21
Same issue with it failing to shutdown. This happened with the last 9.10 beta too, so I'm not too worried.

---

### Post by BrokeMahPC on 2010-04-28
Just installed kernel 2.6.34-020634rc5-generic and it started this problem - never had it before.
The system reboots ok but does not completely shutdown.
Everything seems to poweroff and you can hear things spinning down but the Plymouth splash with the animated dots is still on the screen.

---

### Post by bvanaerde on 2010-04-28
After the latest updates (to the Release Candidate), it's still there.
Maybe a little late, but I filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/571488").

---

