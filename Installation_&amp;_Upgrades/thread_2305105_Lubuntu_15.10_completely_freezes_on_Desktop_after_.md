---
title: "Lubuntu 15.10 completely freezes on Desktop after installing updates"
date: 2015-12-02
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2015-12-02
Well. . .that was a mistake. 

I decided to do a fresh install of Lubuntu 15.10. I had trouble at the beginning, and with your awesome help, was able to resolve that specific issue.

Now I have installed all the updates for Lubuntu 15.10, I get a complete freeze on Desktop. Can't reboot normally unless I do a cold reboot, which I have done three times. Recovery Mode shows no errors and everything seems to be normal, that is, until I get to the Desktop. And then nothing works. Well I do start with a keyboard and a mouse, both which work, well at least I can move the mouse and the keyboard light is on. However I cannot click on anything. Desktop completely frozen. Oh, when I do Ctrl-Alt-Delete or Ctrl-Alt-F1, then both the Mouse and the Keyboard stop working and freeze.

Is there any way to figure out what the new issue is and what is causing the complete freeze?

Thank you for any assistance you may be able to provide. If there is no fix I will wait until 16.04. However, I feel if 15.10 isn't working, then 16.04 might not work either.

---

### Post by roler2 on 2015-12-08
Well. . .hopefully one of the brilliant and talented Forum Members can provide me with their opinion(s).

I reinstalled 14.04. Working great, that is, with the original default kernel. No freezes. No cold reboots. Fonts aren't blurry. Firefox is a little sluggish, especially with Yahell Email. Oh I do have to utilize the default 14.04 kernel. If I upgrade the kernel or do the Hardware Enablement upgrade, I do get the exact same problem as described above with 15.10, including very blurry fonts and desktop freezes.

Since 15.10 completely failed, and the HWE completely failed with 14.04, especially with the upgraded kernel, does that mean 16.04 LTS when it is released will also fail? Will my old P4 be too old to work correctly with the kernel that will be released with Lubuntu 16.04?

Please advise if possible. Thank you!

---

### Post by scoutchorton on 2015-12-08
I had a similar problem a few days ago on Ubuntu 15.10. I just turned off my computer, turned it back on and booted like normal. If this is the case, then should be just a freeze of the desktop, but if not, then it could be a corrupted file or something. I believe I had something with Ubuntu 12.04 where it did something like that and I re-installed because I wasn't as talented as I am now.

I would wait for some people more talented than me, but if I could give any advice, I would say that I am pretty sure there is a command in terminal (if you can get there by Ctrl+Alt+f1), where you can delete the desktop and reinstall. Because you are on Lubuntu, I am pretty sure that commmand would be something like:

```

sudo apt-get purge lxde
sude apt-get install lxde

```

I wouldn't try that so you don't make anythin worse than it is, but that would be my best guess.

Good luck! :D

---

### Post by sudodus on 2015-12-08
> I reinstalled 14.04. Working great, that is, with the original default kernel. 

I think your problem is not the Pentium 4 processor, but maybe the graphics chip or some other hardware component.

Lubuntu 14.04 LTS and 14.04.1 LTS with the trusty kernel, the 3.13.0-xx series, will be supported until  April 2017. The corresponding standard Ubuntu flavour will be supported until April 2019. So if you need a trusty kernel, you might be able to tweak the desktop environment of Ubuntu to get something, that will work for you for two more years (after Lubuntu 14.04 end of life April 2017 to April 2019).

Usually more effort is invested in the LTS versions, so we can hope that 16.04 LTS, xenial, will work with your P4 computer. It works in my old Dell Dimension 4600 with a P4.

A one or two days old [xenial daily iso file](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/108308/downloads) uses the following kernel

```
$ uname -a
Linux lubuntu 4.3.0-1-generic #10-Ubuntu SMP Wed Dec 2 21:09:16 UTC 2015 i686 i686 i686 GNU/Linux

```

---

### Post by roler2 on 2015-12-11
Thank you very much! I have a P4 Dell Dimension 2400 with the very old i915 Card. Works OK with 14.04 (Graphics aren't the best). However, the fonts are rendered much more clearer, distinct and brighter than installing the HWE or even when trying to get 15.10 to work.

I notice a few Forum Members are having difficulty with 15.10 so I feel better now.

I think it is a combination of the old Graphics Card and the updated Kernel. I had a lot of problems upgrading the HWE on 14.04 with the same exact problems. However, I have had success with the default 3.13 Kernel.

Also I don't notice any difference in 'upgrades' between 14.04 and 15.10. Also what happened to the TTY in 15.10? They were missing in the etc/init Folder.

---

### Post by sudodus on 2015-12-11
I can run text screens with the hotkey combinations

[I]ctrl + alt + F1
ctrl + alt + F2
...
ctrl + alt + F6[/I]
and return to the graphical desktop environment with
*ctrl + alt + F7*
also in Ubuntu 15.10.

What is your problem with TTY?

---

