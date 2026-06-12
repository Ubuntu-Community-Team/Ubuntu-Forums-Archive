---
title: "Keyboard Malfunction after Edubuntu Installation"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by StonePiano on 2006-12-12
I've just done a fresh installation of Edubuntu 6.10 on the kid's machine.  (It previously had an older version of Edubuntu running fine.)

Now the keyboard is malfunctioning in the graphical environment.  For example, I type a letter and nothing happens.  Then I type it again, and hundreds of that letter appear.  This makes it hard to log in!

If I switch to a non-graphical login (ctrl-alt-F2), then I can log in and the keyboard works fine.

Does anyone recognise this problem or know the fix?  (I have installed Linux a dozen times before, but am not a super-expert.)

Many thanks,
StonePiano

---

### Post by StonePiano on 2006-12-12
Ok, I found the answer here:

[http://ubuntuforums.org/showthread.php?t=293823&page=2]("http://ubuntuforums.org/showthread.php?t=293823&page=2")

Since mine was a ps2 keyboard and mouse, I did NOT need to change the BIOS.  
I only edited the file: /boot/grub/menu.lst

My thanks to Talbain for posting.

StonePiano

---

### Post by Simon G Best on 2006-12-13
I had (or maybe still have) the same problem.  First few times I started Xubuntu (6.10), the mouse was sometimes a bit stucky, but the keyboard was fine.  Then, the keyboard went bad - but only in X.  Single key-presses turning into multiple key-presses (sometimes filling up the keyboard buffer), and some long pauses, too.  Seems similar to the occasional mouse problems, which are to do with seemingly similarly scrambled mouse clicks.

I've 'solved' the keyboard problem by editing /etc/X11/xorg.conf.  In the 'Section "InputDevice"' for the keyboard, I changed the 'Driver' from '"kbd"' to '"keyboard"', and added the following line in that 'Section':-

```
        Option          "XkbDisable"    "true"
```

That extra line disables the XKEYBOARD extension (which is enabled by default).  As that option wasn't listed in the kbd man page, I also changed the 'Driver' to '"keyboard"', as already mentioned.

The result is that the keyboard now behaves properly - except that Caps Lock doesn't work.  I don't know if the Caps Lock problem is related, or something else.  I still have a bit of a stucky mouse, though, but as least I can type :) 

'man xorg.conf' for more information about xorg.conf(5x), 'man kbd' and 'man keyboard' for more about the kbd(4) and keyboard(4) drivers.

For completeness, my keyboard 'Section "InputDevice"' is now as follows:-

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
# Manually changed this:-
#       Driver          "kbd"
# to this:-
        Driver          "keyboard"
# so as to use the "XkbDisable" option below.
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"
# Manually added this:-
        Option          "XkbDisable"    "true"
# because otherwise there are keyboard problems.
EndSection
```

---

### Post by Simon G Best on 2006-12-13
Having read more about these problems, and having found that the Xlock thingy for unlocking the console has a weird timing problem, I'm sure my 'solution' isn't really a solution.  But it might help as a temporary 'fix' while sorting the real problem out :)

---

### Post by Simon G Best on 2006-12-13
Did the 'acpi' thing, as suggested by StonePiano, and my mouse, keyboard and Xlock thingy problems now seem to be solved :) 

Now I can get on with trying to solve a bunch of other problems :-P

---

