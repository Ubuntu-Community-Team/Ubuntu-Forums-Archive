---
title: "Fresh Install Crashes. Driver Issue? What Do I Do Next?"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by Mar Komus on 2013-03-27
I installed Linux Ubuntu 12.10 as a dual boot to my HP Pavilion Slimline s7700n running Windows Vista. I started by shrinking the Vista partition natively. I then restarted with the disc and installed. But when I tried to boot into the new Linux partition, I got this following error...

[ATTACH=CONFIG]240622[/ATTACH]

I'm told this is a video driver error. Does anyone know what I might do to correct it? I haven't tried simply reinstalling, but if that's what it takes...:popcorn:

---

### Post by Bashing-om on 2013-03-27
Mar Komus     ; Hi !

Looks probable to be graphics related.
When you boot up, you get a grub boot menu for which operating system you want to boot. In this menu is an option "recovery mode"; Arrow down to the entry and press enter -> recovery console, in this recovery console choose "resume normal boot:. Can you now boot to the desk top (perhaps degraded, ok) ?
If you have got to this point, you will now install a graphics driver.
On the left side of the screen is the "launcher" -> System Settings -> Software Sources(from top task bar menu options) -> Additional Drivers (tab in Software Sources) ..... install the recommended driver.
[INDENT=2]
hope this works for you

[/INDENT]

---

### Post by Mar Komus on 2013-04-03
Thanks! That worked!

---

