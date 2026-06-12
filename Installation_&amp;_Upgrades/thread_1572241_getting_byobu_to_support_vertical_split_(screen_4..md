---
title: "getting byobu to support vertical split (screen 4.0.3)"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by HyperFlexed on 2010-09-10
Hi all,

I patched the latest screen source (4.0.3) with the patch here:
[http://fungi.yuggoth.org/vsp4s/](http://fungi.yuggoth.org/vsp4s/)

it adds vertical split functionality to screen (surprised this isn't in the official screen source yet).

when I run screen, I can go "ctrl+a, V" and get my vertical split going. However, if I run byobu, I don't get the vertical split. (the vert_split command doesn't show up in the help screen for byobu "ctrl+a, ?")

Is byobu a full-on fork of screen? I thought it was simply a wrapper of some kind. I would assume that upgrading screen would upgrade byobu. In fact when I check the version in byobu, it reports the version of screen instead.

Screen is handy, but byobu is prettier, so if I could get vertical split in byobu I'd be laughing. Anyone accomplish this yet?

---

### Post by masque7 on 2010-11-19
For byobu you can do a horizontal split with C-a S 
(that's CTRL + a [together] key then press S)

You then move to the split with C-a <tab>, but it's the same as the current window!

For vertical splitting, use the same but C-a | instead of C-a S.

I find this quite tedious; and it doesn't work. Does anybody know how to use it? It seems to mirror whatever is in the current window.. I'm on Ubuntu 10.04 with (byobo -v) 
[I]byobu version 2.68
Screen version 4.00.03jw4 (FAU) 2-May-06[/I]. 

You could try a terminal emulator called *terminator* which handles splitting with ease, but then that takes away the whole point.

---

