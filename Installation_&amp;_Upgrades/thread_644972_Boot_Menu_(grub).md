---
title: "Boot Menu (grub)"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by james_bandido on 2007-12-19
i'm a noob but i was successful enough to install windows xp and ubuntu on an ibm thinkpad r50e after a lot of trial and errors specially on the partioning part ... 

my main question is how do i change the selection time ?

it only allows me several seconds to make a selection and boots up automatically ubuntu ... 

can i change this default time setting ?

is there a way that i can point it by default to windows xp (as this is the last option in the selection list) ?

my wife and i share this laptop and she still insists on using windows rather than ubuntu ... 

any help that would point me in the right direction is highly appreciated ...

thanks in advance ...

---

### Post by rsambuca on 2007-12-19
> **james_bandido said:**
> i'm a noob but i was successful enough to install windows xp and ubuntu on an ibm thinkpad r50e after a lot of trial and errors specially on the partioning part ... 

my main question is how do i change the selection time ?

it only allows me several seconds to make a selection and boots up automatically ubuntu ... 

can i change this default time setting ?

is there a way that i can point it by default to windows xp (as this is the last option in the selection list) ?

my wife and i share this laptop and she still insists on using windows rather than ubuntu ... 

any help that would point me in the right direction is highly appreciated ...

thanks in advance ...

You can edit a file called menu.lst to make all of these settings.  To change the selection time, you want to change the line that says> timeout 10 and change the number (in seconds) to whatever you want.

To change the default to Windows, you want to change the line that says > default 0to match your Windows entry.  The numbering starts at zero, not one, though, and includes all of the title/root lines (Therefore the line that says title  Other operating systems: is counted).

On a side note, once the grub menu comes on, all you have to do is press an arrow key to stop the clock.  You don't have to get it to the right entry and press enter in the time.  I have my default set to 2 seconds, and that gives you plenty of time to press an arrow key and stop the timer.

To edit the menu.lst, you need to use a text editor with root permissions.  The code to do this is ```
gksudo gedit /boot/grub/menu.lst
```

If you need further assistance, let us know.

---

### Post by LaRoza on 2007-12-19
> **rsambuca said:**
> 
To edit the menu.lst, you need to use a text editor with root permissions.  The code to do this is ```
gksudo gedit /boot/grub/menu.lst
```

If you need further assistance, let us know.

Make a backup copy first. If something goes wrong, you can change it back easily.

---

### Post by james_bandido on 2007-12-19
it worked !!!

thank you thank you very much !!!

---

### Post by rsambuca on 2007-12-19
Good stuff!

I just wanted to give you a heads up that if a new kernel is ever added by the developers, then it will be automatically added to your menu.lst.  After these types of updates, then your default # will likely not be correct anymore, so you will have to change the number again, or delete the old kernels.

If you want to avoid this in the future, you can set the default # to zero, and move the > title Windows
root ...
chainloader +1section above the line that says > ### BEGIN AUTOMAGIC KERNELS LIST
Then any kernel changes won't affect your default.

---

