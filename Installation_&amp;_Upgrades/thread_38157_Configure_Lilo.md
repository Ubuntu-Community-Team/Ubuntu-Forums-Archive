---
title: "Configure Lilo?"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by Mierkat on 2005-05-30
OK of course being my first post, and in following the going trend, I'm a Linux newbie ;)

Now with that out of the way I have a question. I'm pretty much starting to get the hang of this but I got click happy tonight and when I installed lilo I accidentally skipped right past what it told me to do to configure/install it.

Anyone know what it said and how I configure Lilo so I can leave GRUB behind?

---

### Post by grim42 on 2005-05-30
Hi Mierkat,

You can configure LILO with the */etc/lilo.conf* file and then install it with *sudo lilo*.

I think *man lilo.conf* or *man lilo* should give you some information.

Any particular reason you don't like GRUB?

---

### Post by Mierkat on 2005-05-30
Thank you for the reply, I will have to try that.

It's not that I don't like GRUB, if I remeber correctly from when I tested SuSe out a couple years ago Lilo let me set the default OS, in which I want to set my default selected OS to WinXP (if I could get rid of it I would :wink:) so that way if I turn on my computer and walk away, or forget to select WinXP before the timer runs out, I don't end up in Linux.

If there's a way to do this in GRUB then I would have no problem keeping it, but I didn't see any way to do this.

---

### Post by grim42 on 2005-05-30
In your GRUB config file (*/boot/grub/menu.lst*) there should be a line with something like *default 0*. This means it will boot the 1st entry in the file (zero based, ie. 0 is 1st, 1 is 2nd, etc.)

Try changing this to the number of the Windows entry.

I'm not 100% sure of this, but I think it's correct.

If you have trouble with this, then use LILO instead -- it's usually pretty good at booting a Windows partition.

---

### Post by mingus on 2005-05-31
If you skipped past lilo during install and used grub instead (I'm assuming you are booting with the latter), you will need to install lilo with Synaptic.  The control file is lilo.conf and the man page will give you the options.

Both grub and lilo easily handle specifying a default, and booting from Windows.  For that matter, if its Windows you want as the default, you can also configure the Windows boot loader to give you the option to boot Ubuntu.  Instructions can be found googling.

Note that with Debian, you have the update-grub command which auto generates the menu.lst control file.  It is heavily commented to understand how this works.  You can manually bypass it of course, but if you later do update-grub you may lose your changes.  I don't know if the lilo control file is managed similarly.

Under the hood, each boot loader does have its advantages.  Until recently at least, grub had issues if the boot sector was beyond cylinder 1024, while lilo has the LBA option which gets around this.  Conversely, grub is more flexible with splash aesthetics.  Etc.

--mingus

---

### Post by Mierkat on 2005-05-31
Thanks for the input! I haven't had time to mess with it (weekend got busy) so tonight I will try fiddling with GRUB and see if I can get it to work the way I want before I try try switching to LILO.

---

