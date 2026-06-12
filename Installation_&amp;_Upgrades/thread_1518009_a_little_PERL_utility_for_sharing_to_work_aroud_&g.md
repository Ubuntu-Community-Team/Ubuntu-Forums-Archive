---
title: "a little PERL utility for sharing to work aroud &gt;1 argument to play command in grub2"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by joephi on 2010-06-25
The GRUB I have, 1.98-1ubuntu6, will indeed function with either a single argument (file to get MIDI-like data from) or an odd number of arguments greater than 3, but it always throws an error about the tempo argument in the latter case being a nonexistent file.  So what the heck, I pulled up the info page on play to discover the file format (hmmmm....wasn't text, it was binary :-) ), and sort of said to myself "I could use pack() for that...and a little glue code..."  So about 3 hours of programming fun later, I have the attached program for anyone who would like to write out a GRUB2 file compatible with the one argument play command.

example usage:```
mkgrubtune 480 440 1 >/boot/grub/boottune.bin
```
...and for my system, a fragment of grub.cfg:```
play (hd0,2)/grub/boottune.bin
```

---

