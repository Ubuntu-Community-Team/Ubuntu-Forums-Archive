---
title: "zsnes currently won't run on intrepid 32-bit"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by &#12465;&#12452;&#12488; on 2008-09-22
ZSNES currently dies upon launch here in intrepid. Anyone else experiencing this, or is it just my system? I really wanted a round of Donkey Kong Country right now. :(:(

> *** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7c01388]
/lib/tls/i686/cmov/libc.so.6[0xb7bff4b0]
zsnes[0x8056c1b]

I guess it's a libc bug

---

### Post by amano on 2008-09-22
I can confirm that. Please file a bug!

In the meantime you can use the snes9x .deb from this page: [http://www.snes9x.com/phpbb2/viewtopic.php?t=3703&postdays=0&postorder=asc&start=0](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703&postdays=0&postorder=asc&start=0) It works great for me and even offers the NTSC filter (for the ultimate retro feeling), just like zsnes.

Maybe it would be a good time to consider switching from zsnes as well because with their next version they switch to QT widgets and the snes9x .deb is pure GNOME.

---

### Post by hellibombelli on 2008-09-22
The bug is already reported here:
[https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/250425]("https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/250425")

---

### Post by ubulette on 2008-09-22
This is caused by the hardened toolchain.
See [https://wiki.ubuntu.com/CompilerFlags](https://wiki.ubuntu.com/CompilerFlags)

I know it could be annoying for users but it is a good thing in general as it leads to better quality and security. I've found and fixed a few myself. It's just unfortunate that more of these issues are found so late in the cycle. But better now than after release.

---

### Post by mikedep333 on 2008-09-23
How would I go about running zsnes on 64-bit intrepid? Wine?

Update: Yes, wine appears to run it well. One and a half layers of emulation is awkward in theory, but oh well.

---

### Post by dfreer on 2008-10-09
ZSNES binary from Hardy *should* work fine as well. Also, as long as you have the proper 32-bit libs you should be able to run the 32-bit version of ZSNES in 64-bit Intrepid.

---

