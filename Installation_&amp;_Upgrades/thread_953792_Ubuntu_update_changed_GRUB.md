---
title: "Ubuntu update changed GRUB"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by wanstronian on 2008-10-20
Hi all,

Last night Ubuntu 8.04 downloaded some updates, and the updates have changed the contents of my GRUB bootloader list such that my previous default (item 4) is now item 6 and as a result the wrong thing boots.

It's a simple matter to update menu.lst, but I don't really want to have to do this when I get an update - it's especially a pain if my wife is the first person to use the computer post-update, as she doesn't understand what's happened!

How do I ensure that the default item, stays default? The new items seem to be added at the top of the list, so I can't see how it will ever work?

Thanks
!

---

### Post by 22flames on 2008-10-20
no the right thing boots or edit the menu.list to fix it it was a kernal update which is a good thing it fixes errors etc. 

22FLAMES

---

### Post by paulb42 on 2008-10-20
I'd recommend using StartUp-manager ( get it via Synaptic ) .... makes updating the menu.lst even easier, and in the advanced section you can limit the number of kernels displayed in Grub, that way your XP or whatever system will always be item number 6 ....

Paul
(Linux convert since July)

---

### Post by wanstronian on 2008-10-20
Sorry - not sure what you're saying. I understand that the kernel updates are a good thing, but I need a way to stop it effectively changing the default boot item in GRUB when such updates happen.

I want to be able to turn the pc on then come back to it in a minute or so when it's booted into my default OS ([SIZE="1"]which is Vista - sorry[/SIZE] :redface:)

---

### Post by caljohnsmith on 2008-10-20
What you could do is put your default Ubuntu entry before the lines in the menu.lst that say:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
And then set the "default X" line (X is some number) in the menu.lst to "default 0", assuming there are no other OS entries before the Ubuntu entry that you add above. That way whichever Ubuntu entry you put before those above lines will always be the default entry, and having Grub update will not change it. 

To modify your menu.lst you can do:
```
gksudo gedit /boot/grub/menu.lst
```
If you want more specifics, please post your menu.lst, otherwise let me know how it goes. :)

---

### Post by wanstronian on 2008-10-21
That sounds like what I want - probably would have discovered it myself if I'd bothered to examine the menu.lst file or read up on GRUB! Pah - bloody Windows user... :rolleyes:

I won't know if it's worked until the next time I get a kernel update, but I reckon it's a winner - thanks for your help!

W

---

