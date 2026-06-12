---
title: "garbled display post initrd boot"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by xcasex on 2009-12-17
I have an issue that's preventing me from using my hp probook.
the probook 4510s comes w. a intel gma x4500hd card and various other hw.
the laptop has two os's installed karmic koala & win7 and i've stumbled upon a problem i just dont know how to solve.. 

i've taken the following steps while trying to boot:
1) normal boot, results in blank screen and if i ctrl+alt+f7 it pops to a garbled black display with white grungy lines.

2) booting into rescuemode, same thing

3) defaulting back to previous kernel and pursuing the normal boot, same result as 1.

4) previous kernel, same procedure as step 2, same result as step 2.

no matter the combination to try to access the VTs i cant do jack or ****.

any ideas?

---

### Post by zexarious on 2009-12-17
I have the same issue that you're describing, except I'm on a dell c640 with a radeon card.

All I can do is SSH in.

Get one of these errors if I do startx
```
[    0.242280] (EE) PreInit returned NULL for ""PC Speaker""
```

Starting gdm by itself gives this:

```
gdm-binary[8768]: WARNING: Unable to find users: no seat-id found

```

---

