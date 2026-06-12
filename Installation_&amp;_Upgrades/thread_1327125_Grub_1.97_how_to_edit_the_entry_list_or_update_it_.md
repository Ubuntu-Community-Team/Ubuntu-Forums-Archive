---
title: "Grub 1.97: how to edit the entry list or update it to full release/latest version?"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Pott on 2009-11-15
Well I got grub 1.97 beta 4 with my Karmic for some reason, I thought it'd come with Grub 2... 

Anyway, I couldn't find the file to edit the menu list, it's not the same as on grub 1.5. How do I access it?

Also since I have a beta version, how do I upgrade to the full grub 2.0 hassle free? I read a thread about it with some instructions but they're out of my league :( Mostly as long as 1.97 works and I can edit the list to change the default and remove useless entries, I'll be fine.

Thanks!

---

### Post by darkod on 2009-11-15
I might be wrong but out of whatever reason, 1.97 is grub2. :)
The previous also called legacy now, seems to be 0.97 or grub(1). :)

Here are some basics:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It depends what exactly you want to edit. The best way to know that you have grub2 is that you don't have /boot/grub/menu.lst to edit any more.

---

### Post by Pott on 2009-11-15
Great thread, had most of what I needed, thanks. I still can't delete entries but at least it's a bit clearer now!

---

### Post by darkod on 2009-11-15
No problem, glad I could help. :)

Depending what you need to delete, menu entries I guess?
It really does take time understanding how grub2 works, I am also confused still. Luckily mine worked fine from install and I had no need to change anything, just removed the memtest entries from menu.
The 10_linux file is taking care of linux distributions but it seems only stops at your ubuntu. Other distros need to be detected by the OS prober feature, but this is my assumption, not sure.
Windows installations definitely need to be detected by the OS prober.
So if you want to remove some windows entry, one solution might be to disable the OS prober (so it doesn't put the entry back in the menu every time) but then you need to make manual entries for windows installations that you want in the menu in the 40_custom file.
Generally it seems to go:
10_linux
20_memtest
30_os-prober
40_custom

---

### Post by coelho10_lk on 2009-11-21
Hi, I'm facing another problem, but very similar.
I have 3 sistems on my notebook, windows, linux ubuntu and redhat 4 AS. And after migrate to 9.10, the RedHat boot was improperly set by the grub. Another words, I can't boot RedHat.
On onder Ubuntu version I could edit menu.lst and change the boot strings.
How could I perform the same process on this version?
Thanks.

---

### Post by sajidalideshmukh on 2010-02-03
> **darkod said:**
> I might be wrong but out of whatever reason, 1.97 is grub2. :)
The previous also called legacy now, seems to be 0.97 or grub(1). :)

Here are some basics:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It depends what exactly you want to edit. The best way to know that you have grub2 is that you don't have /boot/grub/menu.lst to edit any more.

That link is really helpful. Fixed my all issues of Grub 1.97 aka 2.0

---

