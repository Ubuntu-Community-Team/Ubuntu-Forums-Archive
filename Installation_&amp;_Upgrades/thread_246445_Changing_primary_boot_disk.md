---
title: "Changing primary boot disk"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by vinrouge on 2006-08-29
I'm a relative newbie and have done my best to scour the forum for the answer to my query. The problem goes like this:
1) Dapper Ubuntu X server got broken because of infamous update.
2) I reinstalled Ubuntu (Breezy Badger) on my slave HDD (hdb) so that I could get back online to figure out what went wrong. Fixed X server problem.
3) Now, however, Grub booter wants to select the Breezy version on hdb as default to boot, rather than the Dapper version on master HDD (hda). Dapper (and its several incarnations) is listed further down as "Other Systems." I don't mind keeping the Breezy version on hdb for future emergencies, but I would rather have default be the latest Dapper on hda so that I don't have to force the selection each time the computer boots up.
4) I've read about changing menu.lst under /boot/grub on hda, and have fiddled with it considerably. However, none of the changes I make are recognized when I reboot (including changing the default number, etc). This leads me to suspect another /boot/grub exists on the hdb partition which is being accessed at boot time. Yet try as I might, I cannot find a trace of it. 

So...aside from reinstalling everything, is there a quick way to fix this little annoyance?

Thanks!
Doug

---

### Post by Iowan on 2006-08-29
Can you boot into Dapper from the existing menu?
What kind of "fiddling" have you done (physically move the Dapper line, or just change the default number)?
What do you mean by:> none of the changes I make are recognized when I reboot  - menu.lst changes back?

---

### Post by vinrouge on 2006-08-29
Can you boot into Dapper from the existing menu?

At bootup, the Grub menu presents me with the Breezy kernel as default. Scrolling down, the Dapper kernel (along with several previous Dapper kernels) is listed under "Other systems" which I can then select, and everything boots fine. 

What kind of "fiddling" have you done (physically move the Dapper line, or just change the default number)?

I haven't moved any of the Dapper lines, just changed the default number (also tried 'saved'). I also gave  GrubEd a shot, but it did not change the default kernel highlighted (now Breezy) when I rebooted. What is curious is that the Breezy kernel is nowhere to be found among the kernels listed in the Automagic Kernels List.

What do you mean by:
Quote:
none of the changes I make are recognized when I reboot
- menu.lst changes back?

No, the changes I make in menu.lst are still there after rebooting, so it's not getting overwritten somehow. Rather, at boot up, no matter what I put in menu.lst, the highlighted default kernel is always Breezy, with the Dapper versions listed further down.

---

### Post by confused57 on 2006-08-29
You can reinstall grub to the master hd, using the Dapper live cd:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

In fact, the live cd would be a good way to get back online, if your xserver breaks again.

---

### Post by vinrouge on 2006-08-30
Thanks a million, that did the trick. 

As an aside, I first tried just running grub in a terminal from my normal Dapper session instead of the live disk. At the grub command prompt, the 'find' command worked okay, but when I tried the 'root' and 'setup' commands, I got this:

grub> root(hd0,0)

Error 27: Unrecognized command

grub> setup(hd0)

Error 27: Unrecognized command

grub>

Everything works fine, however, under the live disk. Why that?

Doug

---

