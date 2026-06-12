---
title: "&quot;atkbd serio0:&quot; Error filling logs"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by gibbylinks on 2010-11-02
[B]I posted this in the DELL forums with no response !
[/B]             
                                                                Hi All

I have this error

```
Oct 16 09:58:14 gibbylinks-laptop kernel: [ 3159.348419] atkbd  serio0: Use 'setkeycodes e00d <keycode>' to make it known.
Oct 16 09:58:14 gibbylinks-laptop kernel: [ 3159.358468] atkbd serio0:  Unknown key released (translated set 2, code 0x8d on isa0060/serio0).
Oct 16 09:58:14 gibbylinks-laptop kernel: [ 3159.358481] atkbd serio0: Use 'setkeycodes e00d <keycode>' to make it known.
Oct 16 09:58:15 gibbylinks-laptop kernel: [ 3160.400807] atkbd serio0:  Unknown key pressed (translated set 2, code 0x8d on isa0060/serio0).
Oct 16 09:58:15 gibbylinks-laptop kernel: [ 3160.400818] atkbd serio0: Use 'setkeycodes e00d <keycode>' to make it known.
```Filling my error logs. I have tried this [COLOR=Blue][http://ubuntuforums.org/showthread.php?t=1282027](http://ubuntuforums.org/showthread.php?t=1282027)[/COLOR] and it's also been put on launchpad as a bug [COLOR=Blue][https://bugs.launchpad.net/ubuntu/+s...ux/+bug/549741]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549741")[/COLOR] although I'm not convinced it's keyboard related.

Has anyone else come across this and if so did you solve it ?

 I'm running 2.6.3 BIOS on my 1501 with replacement battery.

This is the only thing spoiling my Ubuntu experience. Everything works fine despite this, it's just irritating :confused: And from browsing through the forums this has been around for a while !!

---

### Post by gibbylinks on 2010-11-07
FYI 

I recently replaced my hard drive with an SSD and this bug has gone !!

---

### Post by P4man on 2010-11-07
Very wild guess. The harddrive had a G sensor (to park heads in case of a drop). And that g sensor is providing the "unknown keypresses" the kernel is detecting?

---

