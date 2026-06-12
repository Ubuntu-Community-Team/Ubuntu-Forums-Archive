---
title: "Can't change &quot;warning&quot; system sound"
date: 2009-02-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eqisow on 2009-02-26
All of my other system sounds are easily changable, however the "warning" sound will not change. It stays default, even though it says it's changed, no matter what sound I select. It's not a problem with the sound file either, because files that work as other sounds don't work as the warning sound.

'dmesg | tail' gives nothing useful

This is such a peculiar problem I don't even know where to start debugging it. Any ideas?

---

### Post by eqisow on 2009-02-28
I fixed it by replacing /usr/share/sounds/ubuntu/stereo/dialog-warning.ogg with the sound I wanted. Obviously this falls under "work around" rather than "solution," but perhaps it will help somebody with the same issue.

Oh, and if it happens to be a wav file, like mine was, you can call it warning-sound.ogg and it will still be recognised and played. Linux doesn't really use file extensions in the way that Windows does. They are mostly for the users benefit in Linux land. :)

---

