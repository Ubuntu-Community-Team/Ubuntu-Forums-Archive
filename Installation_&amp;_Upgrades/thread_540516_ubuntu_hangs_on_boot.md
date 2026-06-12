---
title: "ubuntu hangs on boot"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by heliocentric on 2007-09-01
hi 

after installing with the alternate cd (because the the live cd wont work) i try and boot ubuntu and it hangs on the load screen then says '/bin/sh: can't access tty; job control turned off' then wont go any further. can someone help me fix this?

thanks

---

### Post by merlinus on 2007-09-01
Do you get to the grub menu?  If so, can you boot into Recovery Mode?

-merlin

---

### Post by heliocentric on 2007-09-01
it goes to grub yeah. when i choose recovery it starts going through lots lists but then just stops and and nothing happens

---

### Post by merlinus on 2007-09-01
When it stops, try this:

Ctrl-Alt-F1 to get to prompt

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

-merlin

---

### Post by heliocentric on 2007-09-01
did u mean wait till it stops in recovery mood?

if so i followed your instructions and it said

          check root= bootrag cat /proc/cmdline
          or missing modules, devices: cat /proc/modules 1s /dev
ALERT! /dev/sda2 does not exist. Dropping to a shell!


then it loads to busy box again and gives the same error as my original one and then says sudo was not found

what does this mean? 

thanks

---

### Post by heliocentric on 2007-09-02
bump

---

### Post by Compguru on 2007-09-02
Hello, well i am pretty sure it means your bios  bootup configuration is set up wrong, i suggest you ...1.) have someone  with experience in that area of the bios help you, or 2.) attempt having at your bios settings yourself,If you know what your doing in the bios settings,Till you get it to boot properly.

Let us know how it went for you.

---

### Post by heliocentric on 2007-09-02
what kind of thing should i look for in the bios? 

thanks

---

### Post by vadania on 2007-09-02
> **heliocentric said:**
> what kind of thing should i look for in the bios? 

thanks

Well since you said it complains about missing /dev/sda2, I belive you should check the hard disk  number. Maybe you have moved a hard disk, or such...

---

### Post by heliocentric on 2007-09-02
well i tried changing around things in the bios but it made no difference :(

i think im gonna have to give up on ubuntu, which is a shame

its a pitty they cant make it easier to install

---

