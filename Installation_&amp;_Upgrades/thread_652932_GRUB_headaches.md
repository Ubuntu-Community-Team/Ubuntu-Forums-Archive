---
title: "GRUB headaches"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by alvarez1900 on 2007-12-29
I have Linux tweaked almost to perfection... Still working on a few things but I cannot crack this one major annoyance... Ever since I began with Feisty(now on gutsy 64bit) on my Qosmio laptop when I do a fresh boot the QOSMIO boot screen locks on screen and the GRUB never shows... You can select the OS you want and hit enter and it will boot from there but it never displays... After the initial boot if you reboot the GRUB will in fact show.. however on the initial boot you are left in the dark.

 My best guess is its some resolution thing and after boot the resolution is recognized and it shows from then on however on fresh boot the resolution isn't allowing it to show? Does that make sense? Or has someone faced something like this previously?

 Thanks for any help I would love to fix this annoyance and have searched the forums endlessly to no avail and couldn't crack it myself *sigh*

---

### Post by alvarez1900 on 2007-12-29
wow... nobody?

---

### Post by alvarez1900 on 2007-12-30
please? :(

 everything I post here noone can answer :( I end up figuring it out but noone is able to help me :( frustrating.

---

### Post by TrapMakeR on 2007-12-30
alvarez1900,

I think some time ago I had the same problem with "Linux from scratch 6.1".
I scripted system installation for myself and after selection in GRUB screen
was black for some time and only then console output appeared. It was
very annoying. Later on I moved to LFS 6.2 and the problem disappeared.
I was using HP Compaq nc6000 notebook. Unfortunately I do not know
what was the cause.

---

### Post by skillllllz on 2007-12-30
> **alvarez1900 said:**
> I have Linux tweaked almost to perfection... Still working on a few things but I cannot crack this one major annoyance... Ever since I began with Feisty(now on gutsy 64bit) on my Qosmio laptop when I do a fresh boot the QOSMIO boot screen locks on screen and the GRUB never shows... You can select the OS you want and hit enter and it will boot from there but it never displays... After the initial boot if you reboot the GRUB will in fact show.. however on the initial boot you are left in the dark.

 My best guess is its some resolution thing and after boot the resolution is recognized and it shows from then on however on fresh boot the resolution isn't allowing it to show? Does that make sense? Or has someone faced something like this previously?

 Thanks for any help I would love to fix this annoyance and have searched the forums endlessly to no avail and couldn't crack it myself *sigh*

First, is the BIOS updated to the latest version? If not, please be sure to do that before going any further, as the BIOS is in total control of video display at that stage in boot up.

If the BIOS is up to date, then the next thing to check is the amount of RAM memory being shared with video. This is assuming the video card actually does use shared RAM memory. If it in fact does, try setting the shared amount in the BIOS to a greater value.

If the video card does not use any shared memory, or the value is not adjustable, please post here the available BIOS options found under "Video Configuration" and I will try to assist you further.

---

### Post by alvarez1900 on 2008-01-02
Solved. 

 I disabled the boot animation and the sound logo. It now shows the Qosmio logo REAL FAST then goes to the GRUB... I figured they were fighting for time on the initial boot.. 

 Now to get my external eSATA HD to show in ubuntu lol.

---

