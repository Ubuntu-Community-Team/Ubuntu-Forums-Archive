---
title: "Shutdown during synaptic uninstall. Ubuntu Won't Boot!"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by insertnewsn on 2007-09-04
I was trying to fix a problem with my ALSA sound driver, and so I went into the Synaptic Manager to remove everything dealing with ALSA. I made a mistake and chose to uninstall a ton of things (compiz, beryl, etc), and once I realized the mistake I made, I shutdown my computer in order to stop the uninstall process.

Now my computer won't boot into Ubuntu!
It only boots into a terminal prompt, and i'm not sure what I can do to repair the damage that I've done. 

I know there are certain repair features on the Alternate Installer disc, but I was just wondering if there was a simpler way to repair my Ubuntu Installation using the terminal?
Any help would be greatly appreciated!!

Thank you!

---

### Post by frank95com on 2007-09-04
You can try to put this command in the terminal as root:
```
dpkg reconfigure -a
```
I think that it will restart uninstalling the programs (I'm quite sure) so I don't think there's a solution but wait for others better experienced than me.:)

---

### Post by insertnewsn on 2007-09-04
Thanks for your quick reply!

I just tried doing that, and after the 25-30 minute process completes, I still cannot boot into Ubuntu. It stops at a terminal screen and asks me to login. After logging in, it just sits at the terminal screen like before. Any ideas?

Again, thank you so much for your quick reply.

---

