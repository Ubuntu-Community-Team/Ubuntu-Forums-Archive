---
title: "Huge problem- comp froze during upgrade, nothing works"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by LuciaZephyr on 2008-07-06
I was upgrading my laptop from 7.04 to 8.04 and while it was installing the packages, my laptop froze and crashed completely.

When I turned it back on, it's.... well, it starts off in low-graphics mode. I get to the log-in fine, but once I enter my username and password, instead of giving me my desktop, it hangs on a completely orange screen.

Any help would be greatly appreciated. I'm very scared for my laptop's sake. I hope I haven't lost everything.

---

### Post by Midwest-Linux on 2008-07-06
> **LuciaZephyr said:**
> I was upgrading my laptop from 7.04 to 8.04 and while it was installing the packages, my laptop froze and crashed completely.

When I turned it back on, it's.... well, it starts off in low-graphics mode. I get to the log-in fine, but once I enter my username and password, instead of giving me my desktop, it hangs on a completely orange screen.

Any help would be greatly appreciated. I'm very scared for my laptop's sake. I hope I haven't lost everything.

 I'm guessing here that it sounds like a issue with xorg.org/ video driver. What is the laptop make and model number? Ram? Speed?

---

### Post by LuciaZephyr on 2008-07-06
It's a Dell Inspiron 6000. I'm not certain on the speed or RAM, but I know the video card was a Radeon Mobility.

---

### Post by LuciaZephyr on 2008-07-06
Okay, it's 3 AM, my computer is fixed after I followed about seven different troubleshooting guides. I'm going yo go crash now.

Oi vey.

---

### Post by bsmith1051 on 2008-07-06
Any idea which guide was the key?

---

### Post by LuciaZephyr on 2008-07-06
Now that I'm awake, yep. :D

So first I futz with grub, but that did nothing. I went back to the login and remembered I could access the terminal by changing the session before logging in. I did so, then followed this: [http://ubuntuforums.org/showthread.php?t=189520](http://ubuntuforums.org/showthread.php?t=189520)

Not exactly, mind you, because certain commands refused to finish, but eventually I followed those steps to finish the upgrade, then rebooted.

Then I had to fix my screen resolution. It is not fun having a widescreen laptop with 640x420 (or wotever). I had to fix a few smaller issues, but I think that's a Your Milage May Vary sort of thing.

And ta dah! Fixed and 8.04!

---

### Post by Tintazul on 2008-07-30
> **LuciaZephyr said:**
> So first I futz with grub, but that did nothing. I went back to the login and remembered I could access the terminal by changing the session before logging in. I did so, then followed this: [http://ubuntuforums.org/showthread.php?t=189520](http://ubuntuforums.org/showthread.php?t=189520)

And ta dah! Fixed and 8.04!
Thanks for posting that link... and ta dah! is the feeling here, too! Overall, the upgrade took me... 7 hours 30 minutes (too long.)

---

