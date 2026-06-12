---
title: "Fresh install of 9.10 gui is all weird and not working"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by sdmike on 2009-12-09
So I just installed Ubuntu 9.10 amd64

I go to launch the OS and the whole screen is a cream color with white lines dropping down.

I know the obvious assumption is it's a driver problem.

So my question is who do I get into the terminal on boot or switching from gui to terminal?

I have on board intel graphics and windows 7 runs perfectly so I know my onboard video card is fine.

I've been looking around the forum but I can't find a problem quite like this.

What should I do?

---

### Post by darkod on 2009-12-09
I can help you only partly. In the grub boot menu don't select the normal mode, instead select the recovery mode entry. In the next menu something like "root with networking". That will give you command prompt with internet access. But I have no clue where/how to get Intel drivers.
Maybe googling your chipset might help.

---

### Post by sdmike on 2009-12-09
I selected recovery mode and I see all the text coming down and then the gui just starts up automatically.

I never see a screen that says root with networking.

I just need to get to the command line from boot :(

---

### Post by phillw on 2009-12-09
Hi,
Not sure if this applies to 64 bit, but it may be worth a try ...

[http://ubuntuforums.org/showthread.php?t=1325771](http://ubuntuforums.org/showthread.php?t=1325771)

typing 

```
intel +video +64 bit +ubuntu +9.10
```

Into Google comes up with a lot of hits.

Hope that helps,

Phill.

---

### Post by sdmike on 2009-12-11
```
As soon as you get the grub screen at boot (yours may have a very short countdown before it proceeds in to boot) press ESC *immediately*. Use the arrow key to scroll down to the boot line - should look similar to this:

Ubuntu 9.10, kernel 2.6.31-14-generic
press the "e" key to edit the line - you should see something like the following:

kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=dc3cf399-6b13-4704-80c5-0e02fe6cd364 ro quiet splash

using the arrow keys, go to the end of the line and add:

i915.modeset=0 <press enter>

so that the kernel line now looks similar to:

kernel /boot/vmlinuz-2.6.31-14-generic root=UUID=dc3cf399-6b13-4704-80c5-0e02fe6cd364 ro quiet splash i915.modeset=0

press the "b" key to boot

If you get the GUI screen, you can make the change permanent by:

* booting up and logging in to the GUI
* click applications/accessories/terminal
* type:



sudo cp /boot/menu.lst menu.lst_save <press enter>

sudo gedit /boot/menu.lst <press enter>

```

Ok so I get to the part where I have to copy "cp /boot/menu.lst menu.lst_save"

I don't see that file in /boot/

What should I do now?

I was able to update everything but everytime I have to boot I have to edit that boot section.

---

### Post by sdmike on 2009-12-14
bump!

---

### Post by sdmike on 2009-12-17
Bump!

---

### Post by efflandt on 2009-12-18
9.10 uses grub2 which does not use menu.lst

From a terminal **sudo nano -w /etc/default/grub** and append to quoted strings in following lines [DEFAULT is for regular kernels and without that is for (recovery) entries]:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

After saving that, **sudo update-grub**

---

