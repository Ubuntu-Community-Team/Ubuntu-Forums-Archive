---
title: "Upgraded to 10.10, won't load"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by joeyfixit on 2012-04-04
My 2 year old asus k50 laptop has ubuntu and windows 7. I used lucid lynx until yesterday, when I upgraded to 10.10. Upgrade went smooth until I tried to restart. Now ubuntu won't load; I get the blinking cursor. Windows still works fine (as well as it ever did).

The menu still offers 5 different options for 9.10, as set up by my friend back in 2009. Didn't think anything of it since 10.04 worked with these prompts (2 generic, 2 generic recovery mode, 1 memtest).

I can edit from this boot menu or get into grub command lines, but I don't know what to do with this stuff. I admit I'm not code-savvy and perhaps I was over my head upgrading, but transitioning from 9.04 to 10.04 didn't have these problems, iirc.

Seems like a simple problem, but i dont have the solution. Help?

---

### Post by Karlchen on 2012-04-04
Hello, joeyfixit.
> My 2 year old asus k50 laptop has ubuntu and windows 7. The important thing to know here would be: Are Windows 7 and Ubuntu each installed on separate disk partitions? Or are we talking about a Wubi installation, i.e. a Ubuntu installation the filesystem of which is located inside a huge file named root.disk which can be found in a folder \ubuntu\disks?

[SIZE=1]**<personal comment>**[/SIZE]
> I used lucid lynx until yesterday, when I upgraded to 10.10.[SIZE=1]What a weird idea. Lucid is an LTS edition which is going to live until April 2013. Maverick will die before Lucid. So what might be the kick of updating to a dying edition? OK, just my 2.5 cents.
You did update and it should have worked correctly.[/SIZE]
[SIZE=1]**</personal comment>**[/SIZE]


> Upgrade went smooth until I tried to restart. Now ubuntu won't load; I get the blinking cursor. Have you tried switching to a console monitor my pressing <Ctrl><Alt><F1> e.g. As a matter of fact, there should be 5 console monitors, <Ctrl><Alt><F1>, <Ctrl><Alt><F2> ... <Ctrl><Alt><F5>. And the GUI should be on <Ctrl><Alt><F7>.

> The menu still offers 5 different options for 9.10, as set up by my friend back in 2009. Didn't think anything of it since 10.04 worked with these prompts (2 generic, 2 generic recovery mode, 1 memtest).This will be the Windows boot manager menu. And the strings inside the menu may never have been updated to reflect the change from Karmic to Lucid and now to Maverick.

> Seems like a simple problem Might be, might be not. Without knowing the details why Ubuntu refuses to boot to the GUI it is hard to tell whether simple problem or complex problem.

What you might try to do is this:
During the boot process, where you can choose between the 5 Ubuntu options, press the letter "e" for edit. Then suffix the string " nomodeset" to the line which launches "vmlinuz". Then press <F10> I think in order to really boot. 
If you are lucky this will make Ubuntu boot fully and the GUI will be displayed.

If not, please, try whether you can activate the console monitor #1 and let us know whether you see any error message there.

Kind regards,
Karl
--

P.S.:
If my suspicion should be correct that your boot menu is not the grub menu, but an outdated Windows boot manager menu, then the boot problem might simply be that the kernel which it tries to boot does no longer exist on the disk.

---

### Post by mörgæs on 2012-04-04
If your Ubuntu installation is separate from Windows (that is, not Wubi) I recommend that you backup your data and delete all Ubuntu partitions. After that go for a fresh install of 11.10.

---

### Post by joeyfixit on 2012-04-04
I wanted to update to the latest version of ubuntu and I needed to go through 10.10 to do it, according to the update manager.

Control alt f1 does indeed get me to a login screen. First thing it says is 

chroot: cannot execute /etc/apparmor/initramfs: No such file or directory exists

Followed by

Starting up...
Ubuntu 10.10 Gremmie tty1

Gremmie login:

The boot command doesn't work, what now?

---

### Post by darkod on 2012-04-04
Yes, the upgrade path is version by version UNLESS you upgrade from LTS to LTS. You can do that directly, and since you had 10.04 LTS if you waited two more weeks for 12.04 LTS to be released, you could have jumped straight to the latest one.

As for your boot problem, there is a sticky above all the threads for video issues and I believe the blinking cursor on blank screen is one of them. There are procedures and fixes in that sticky so I would start there.

---

