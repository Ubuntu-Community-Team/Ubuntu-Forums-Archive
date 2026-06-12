---
title: "PC won't boot after upgrading from Ubuntu 9.04 to 9.10"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by MegaShark on 2010-03-25
Hi guys,

I wanted to use Ubuntu on one of my old laptops (a great, speedy modern OS on a modest hardware PC). Unfortunately this PC can not at the time read all CD-ROM's (can't figure out why it does read some) and I've installed Ubuntu 7.10 - the only CD it did read at the time.

I've used it for two years but I never got my wireless card to work (OK, most of the time it was collecting dust) :)

A couple of days ago I finally realized how to use ndiswrapper (lol...) and I was able to get a working Wi-Fi connection on this laptop. I then proceeded to upgrade it over the internet, to Ubuntu 8.04, then 8.10, then 9.04 and, last night, to 9.10.

It has worked through each and every of these updates, but after 9.10 the PC won't even boot (after "GRUB loading...).

Any clues on what can I check right now?

I'm still quite new to Linux so sorry for being a major noob.

Thanks in advance.

---

### Post by wkulecz on 2010-03-25
I believe you are another victim of the switch to grub2 introduced in 9.10.  On my test system 10.04Beta has the same error I had in 9.10 -- ignoring the BIOS's boot order setting.

Google:  grub2 update-grub

Good luck!  IMHO Grub2 and its documentation are a long way from ready for prime time.  I think Ubuntu is making a big mistake here and will break a lot of dual boot systems causing a lot of ill will.

If you haven't reformated to ext4, I suspect you can reinstall grub and edit /boot/grub/menu.lst to boot the new 9.10 system (this is gone in grub2), but if you can't boot from a live CD I'm not sure what you can do to fix it.

I cloned my 9.10 test system with rsync to a new drive formated ext3 and boot it with grub (grub legacy as the 9.10 can do no wrong crowd likes to call it) and have had no more boot issues.

--wally.

---

### Post by MegaShark on 2010-03-25
Thanks for the quick answer.

I knew I recalled having a particular brand of CD-RW that this 2003 (!) laptop could read... I found one of those CDs and burnt 9.10 to it.

Having that said I guess I'll just reformat the whole system with a fresh 9.10 installation.

If that doesn't work (or if I can't figure out ndiswrapper on 9.10... lol) I guess I'll just revert back to 7.10 and upgrade it all the way to 8.10 but not more - I was never a big fan of cleartype (in fact I hate it, even in Windows...)

What do you guys think about this?

---

