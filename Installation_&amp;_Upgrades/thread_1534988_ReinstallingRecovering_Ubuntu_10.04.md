---
title: "Reinstalling/Recovering Ubuntu 10.04"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by Trilby on 2010-07-20
I dual boot Ubuntu & Windows 7. Yesterday, for no appartent reason, Ubuntu suddenly became unuseable. It started when I was working on my laptop yesterday evening. Without warning, I started getting messages telling me that my file system was nearly full. Over the next minute I saw the disk useage in the partion rocket up to 100%. It had been about 20% when I started and I wasn't even using any file on that partition. 100GB does not just vanish on its own. Since my computer was functioning normally (except for the aforementioned problem), I desided the best course of action would be to restart my computer. I did this. Whilst Ubuntu was booting, I briefly saw a message about checking a hard disk partition for error and that it wasn't ready for mounting, but that disapeared before I had time to read it. I logged as normal, only to find that several things were amiss. The destop switcher on one of the panels crashed and disapeared, the sceenlets app was non-functional and I couldn't use the Ubuntu software centre. I turned my computer off again and left it until morning. When I came back to it, I found the login screen was non-fuctional -- it had no wallpaper, I couldn't login and there was a measage in the top left telling me a power manager was not installed.

I believe my Ubuntu system has become corupted in some way. How do I reinstall it to the same partition, without affecting my dual booting or my partition set up?

Thanks,
Trilby

---

### Post by AllenGG on 2010-07-20
Trilby: you may have discovered a bigger problem. First, I installed 10.04 on an old (10+yrs) system. I discovered , or the system did, that one of the drives was faulty.
This opens another problem,  that of "conflicts". Note, in Synaptic, when you check the "properties" of a potential app or subsystem, occasionally you will see: "conflicts with....."
There is no immediate way of determining : "what conflicts with what ".
This problem needs to be addressed, as well as the issue of things that are "suggested" as opposed to : "recommends".
Allen

---

### Post by Trilby on 2010-07-20
> **AllenGG said:**
> Trilby: you may have discovered a bigger problem...

Maybe, but I've been running Ubuntu since March with any such isues.

This may be because I changed the partitioning of my hard-drive the other day -- a system file may have become corupted. Why it would take serveral days for a problem to occur, I do not know.

---

### Post by varunendra on 2010-07-21
> **Trilby said:**
> I believe my Ubuntu system has become corupted in some way. How do I reinstall it to the same partition, without affecting my dual booting or my partition set up?

Simply reinstall as you might have done before, selecting the same partition as destination (select manual partition option when asked, and choose to format the destination partition).

Formatting will remove the current installation and grub installation (default option) in the last step should be automatically updated for your dual boot configuration.


If you need detailed support, please post the output of boot info script (courtesy of forum member meierfra) which you can download [here]("http://bootinfoscript.sourceforge.net/").

---

### Post by Trilby on 2010-07-21
> **varunendra said:**
> Simply reinstall as you might have done before, selecting the same partition as destination...

Thanks, I had feeling it would be something simple like that.
I'll let you know when I've done it.

Thanks,
Trilby

Update: Ubuntu is re-installed and working fine. Thanks :-)

---

