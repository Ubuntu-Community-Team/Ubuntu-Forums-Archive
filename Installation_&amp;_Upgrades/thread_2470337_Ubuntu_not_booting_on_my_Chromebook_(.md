---
title: "Ubuntu not booting on my Chromebook :("
date: 2021-12-26
forum: Installation &amp; Upgrades
---

### Post by thatrius on 2021-12-26
Hi all,

I have a Samsung Chromebook that I've recently installed Ubuntu 20 on. It worked fine for a few days.

As I turned it on this morning though, I was met with a cold, 
"Chrome OS is missing or damaged.
Please insert a recovery USB stick or SD card."

CTRL-L doesn't work for some reason, all it does is beep at me (USB booting capability turned off somehow?). And if I go along with the "re-verifying the OS" thing, it wants a USB stick with ChromeOS on it, which I do not have, know how to get (no .isos anywhere online??), or frankly even want to reinstall in the first place.

Not sure what my computer specifications are... I can't exactly access any UI besides the few screens I mentioned... all I know is that it's a Samsung Chromebook, and it used to run ChromeOS (before running Ubuntu).

Not sure what to do here... is there a place I can get a ChromeOS .iso? Or better yet, just bypass that altogether and get back Ubuntu?

Thanks!

---

### Post by bobunderwood99 on 2021-12-27
Hello,

[https://support.google.com/chromebook/answer/1080595?hl=en](https://support.google.com/chromebook/answer/1080595?hl=en)

If you want to run Ubuntu without Chrome OS you'll need to modify or replace the firmware. See

[https://mrchromebox.tech/](https://mrchromebox.tech/)

---

### Post by thatrius on 2021-12-27
Thanks for the reply!

I actually installed Ubuntu using the same  mrchromebox tool, and it worked quite flawlessly. Though apparently not  completely so, given that the new OS seems to have erased itself

Unfortunately  I can't reliably access my main computer at the moment, but I'll try  out the chrome recovery tool as soon as I can.

---

### Post by bobunderwood99 on 2021-12-27
Hello,

I suspect this is more of a firmware issue than an Ubuntu problem.

"Legacy Boot Mode requires a functional RW_LEGACY firmware component, as well as the dev_boot_legacy crossystem flag to be enabled. Otherwise, you will simply hear two beeps when pressing [CTRL+L]."
[https://mrchromebox.tech/#bootmodes](https://mrchromebox.tech/#bootmodes)

Did you open up the Chromebook and disable the firmware write-protect (this will tell which mode you're using)?

---

