---
title: "lenovo T500 cannot boot lucid?"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by laborg on 2010-03-08
Hi!

[update]: It looks like that there is no problem with booting when removing the notebook from the dockingstation. Can anyone confirm this?

Someone else around with a lenovo t500 which will not boot 10.04 (neither a3 nor daily build from today).
What I see:
-Bootscreen loads for a couple of seconds showing me the new splash. 
-Mouse cursor appears
-A couple of lines indicating something with ureadahead and that it cannot write to broken pipe.

Since the T500 is a quite a common hardware for linux users I wonder if someone else has problems to boot lucid?

thx in advance

---

### Post by Arla on 2010-03-08
What happens after the couple of lines?

My Y450 seems to "pause" in booting, with just a flashing cursor, if I press return, then it finishes booting just fine, does seem to have been a bit screwy overall since I started playing in 10.04

---

### Post by Jancsy on 2010-03-13
@laborg: I've got exactly the same problem.

---

### Post by jdandison on 2010-04-04
I have a T500 (2055-45U) that has switchable graphics. I'm currently using Windows 7 & Ubuntu 10.04 via Wubi.

I can boot fine. When I'm notified that restricted drivers are available, I tried installing them, but on the next reboot, ended up with the behavior you describe.

You may want to try setting the BIOS to use only one video card or the other. There's a setting for integrated\discrete\switchable.

---

