---
title: "Mint 15 and Genius Pensketch Tablet"
date: 2014-06-23
forum: MINT
---

### Post by Yugata on 2014-06-23
I hope I've submitted this to the right place... A bit of a heads up, I'm new both to the forums and to Linux in general.

I recently bought the Genius Pensketch M912A tablet and have been trying to find ways to get it to work correctly under Linux Mint 15. I've tried doing the same thing as someone else with the same tablet and similar distro even though the thread is outdated, ([http://ubuntuforums.org/showthread.php?t=1710068](http://ubuntuforums.org/showthread.php?t=1710068)) and it didn't work.

This tablet comes with both a pen and a mouse. When I try to use the pen, it works like a tablet pen should by moving the computer mouse to the corrisponding area on my screen, but it doesn't click or highlight when I touch it to the tablet surface or click one of the buttons. The light flashes, so the tablet itself recognizes that I'm trying to click, but it doesn't follow through to my computer. The mouse, on the other hand, will click but not move. Sometimes the two will flip-flop between each other, and I found out upon rebooting just a moment ago that these problems are not present during the entirety of the boot-up process including a few seconds after I've logged in as a user.

I had a Wacom Bamboo tablet before this, and it works just fine. I don't know if the software for that is messing with the Genius compatability or not...

When I type lsusb into the terminal I get:```
Bus 005 Device 002: ID 0458:5015 KYE Systems Corp. (Mouse Systems)
```

And xinput list get me:```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Genius PenSketch M912                       id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; C-Media USB Audio Device                    id=10    [slave  keyboard (3)]
    &#8627; CNF7017                                     id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
```

---

