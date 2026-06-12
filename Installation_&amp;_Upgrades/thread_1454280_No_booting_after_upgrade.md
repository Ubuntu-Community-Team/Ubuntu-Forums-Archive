---
title: "No booting after upgrade"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by Apocalypse_666 on 2010-04-14
Hi! Out of curiosity I upgraded my exisiting 9.10 installation to 10.04 last night, presuming that development had progressed far enough not to pose any serious problems. However, when I had finished installing and tried to reboot, nothing happened.
I see the grub menu (I have a dual boot with win7), but whenever I select Ubuntu (regardless of kernel version or safe-mode) the screen just goes black, and nothing happens. 
Now, I know this is a risk when using a beta, but if anybody has any suggestion it'd be appreciated. 
The pc we're talking about is a Dell Latitide D630 laptop with 2 gb ram, a pentium T7500 (2.2ghz), and a nVidia Quadro NVS 135M. 
Thanks in advance!

Apoc

---

### Post by tom4everitt on 2010-04-14
In the grub menu, mark an ubuntu entry. Instead of pressing 'enter', press 'e' for edit. 

Then you will see a bunch of lines (commands). Write them down on a piece of paper. 

Restart your computer. Press 'c' in the grub menu. Execute the commands you wrote down one by one. Tell us what error message you get.

---

### Post by norseman-has-a-laptop on 2010-04-14
not to troll or anything but 10.4 is out??? sorry i dont really pay attention to 9.10 and the 10.4 stuff wow
i wouldn't know anything about 10.4 sorry

---

### Post by Apocalypse_666 on 2010-04-14
Okay, here's the commands and the feedback I got after entering them:
```

recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 93af2963-fef4-43e0-970b-3b52c4a9b1a5
linux /boot/vmlinuz-2.6.32-20-generic root=UUID=93af2963-fef4-43e0-970b-3b52c4a9b1a5 ro vga=773 quiet splash

```
To which I got the response:
```

    [Linux-bzImage, setup=0x3400, size=0x3d4960]
vga=773 is deprecated. Use set gfxpayload=1024x768x8, 1024x768 before linux command instead.

```
Then continued:
```

initrd /boot/initrd.img-2.6.32.20-generic

```
which returned:
```

[Initrd, addr=0x37877000, size=0x778072]

```

Then, after imputting all this, nothing happened. I don't know whether nothing is supposed to happen, but I would suspect it to at least try and boot, right?

Thanks by the way! 

Apoc

---

### Post by tom4everitt on 2010-04-14
Sorry, try to run 

```

boot

```

after all those.

---

### Post by Lithium777 on 2010-04-14
<-- new to forums so bear with the N00b :D (been using Ubuntu for looong time tho...since 7.04 )

anyway ...to reply.

same issue happened to me, i figured since working beta releases were showing up all over youtube (lol @ myself) i would go ahead and upgrade my beautifully customized Linux OS to 10.04...and ooooooooooh disapointment when i find out that the upgrade didn't upgrade at all...so i restart the computer to see "the" damage and i gotta admit i went through the 5 stages of death lol denial, anger, bargaining, depression, and finally last but not least the "f*ck it" stage: acceptance :lolflag:

anyway i realized that both my Linux and Windows partitions were gone forever (after i did a long a through research on the matter on my bargain-depressed stages ). i couldnt find squat on the matter so i figured id do a fresh install but at this point i had to clean my Linux partition, reinstall Ubuntu and see if i could even try to get my Windows data bak. DIDNT WORK. 

******IF YOU DONT WANT DETAILS SKIP TO THIS PORTION *************

I pop'd in a live cd (usb in my case) and mounted my partitions and made a backup of all my important files (yes music, spreadsheets, videos, media etc) and formated my whole drive :-({|=  :cry:   and decided to RE-install Windows and w8 for the "bugless" Ubuntu 10.04 ....

concluison: BIG ADVICE back up your files kids :)

---

### Post by drs305 on 2010-04-14
Apocalypse_666,

The responses you received after running the "linux" and "initrd" commands mean that Grub recognized them and also found the kernel and initrd image. As tom4everett says, just type "boot" and your system should boot.

Run "sudo update-grub" after you successfully boot, which may make changes to the lines which were causing problems in the original grub.cfg file.

---

### Post by Apocalypse_666 on 2010-04-14
Thanks for all the help! However, when I enter all the commands and end with boot, the same thing happens as when I simply select something from the grub menu: nothing. The screen goes black, no errors, no sounds, my harddrive wizzes slightly but nothing happens.

---

### Post by drs305 on 2010-04-14
> **Apocalypse_666 said:**
> Thanks for all the help! However, when I enter all the commands and end with boot, the same thing happens as when I simply select something from the grub menu: nothing. The screen goes black, no errors, no sounds, my harddrive wizzes slightly but nothing happens.

From your description, there is a good chance that Grub is passing control to the kernel and that the problem is occurring later in the boot. You could try editing the Grub 2 menu entry and removing "quiet splash" from the *linux* line in order to see what is happening during boot. 

Open the menu entry by pressing "e" and using the cursor and DEL keys to move to and delete these items. Then CTRL-x to boot.

---

### Post by Apocalypse_666 on 2010-04-14
Same results I'm afraid, black screen and nothing happening.

---

### Post by tom4everitt on 2010-04-15
Okay, at least I am out of ideas than. If you can boot from a 10.04 live cd, the easiest is probably to just

Boot from live cd, fetch anything important on to an external drive.

Reinstall 10.04 from scratch. 

If you don't reformat the hard drive, your user files should still be there after reinstall. But do a backup anyway.

---

### Post by drs305 on 2010-04-15
I'll have to agree with tom, in that we don't really know what the problem is. An alternative to a complete reinstall would be to reinstall only Grub 2. This may or may not fix the issue but is faster and if not successful would rule out G2 as the problem.

If you want to reinstall G2 from the LiveCD, it would take about 5 minutes. Here is the link to a post I made a few days ago on how to accomplish it (post 12):
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12]("http://ubuntuforums.org/showpost.php?p=9107370&postcount=12")

---

### Post by Apocalypse_666 on 2010-04-15
Okay, thanks for the help anyways. I'd already reinstalled grub before posting to this forum, so I guess there's nothing left to save me now... Again, thanks for your help!

Apoc

---

### Post by jimbo99 on 2010-04-15
During the upgrade did you get error messages xorg?

Try when booting to get to the list of boot options in grub.  Then tell it to choose the first option regarding recovery that corresponds to the newest kernel.  When presented with the text based menu choose the option to repair broken packages.  See if it updates anything.  If it does upgrade xorg/video stuff then try rebooting and going in again.

Similar things happened to me.  I remembered the xorg errors and did the updates from the recovery.  That solved my problem.

---

### Post by Lithium777 on 2010-04-21
i hate to be the one but...

"told you so..."

:P sorry. like i said a couple posts earlier, same thing happened to me, just copy important files and do fresh install :(

---

