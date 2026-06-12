---
title: "Ubuntu Loading Crach  After Install."
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by mohajerx on 2007-08-17
Hello ,
My PC INFO :
AMD Athlon 64 , +3200 , 512 MB RAM

Ubuntu Info :
Downloaded From Internet , ubuntu-7.04-alternate-amd64.iso

I write it to cd ( 16 x speed ) then install it and i set Automatic partition for create partitions in free space  on Drive E ( 15gig ). also i have windows xp in drive C.

**Problem :**
Now When i select Ubuntu to Start, First i see Loading Bar page but after that , i see only a "Orange-Colored page with a small Circle in center" ( then crashed , Circle dont have any progress ).

and i wait more time for scape this page there is no ant action totally.

whats problem ?

tnx.

---

### Post by merlinus on 2007-08-17
Can you boot into Recovery Mode from the opening menu?

-merlin

---

### Post by mohajerx on 2007-08-17
Yes ,
I Can boot Into Recovery Mode From Opening Menu.
( also all cheching sections is [ OK ] )
Then I can use command line.
**root@ubuntu:~#**

---

### Post by merlinus on 2007-08-17
Try this at the CLI:

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

Hopefully this will get you to a gui and you can search for the driver for your video card.

-merlin

---

### Post by mohajerx on 2007-08-20
Tnx merlinus , But not solved ,
after this changes and after loading bar i see black page and then restart.

its possible to install Ubuntu 32bit in Amd Athlon 64Bit system ?

---

### Post by merlinus on 2007-08-20
Yes, and maybe it will work better.  You still may hae video problems, so try what I wrote above with the new install.

-merlin

---

