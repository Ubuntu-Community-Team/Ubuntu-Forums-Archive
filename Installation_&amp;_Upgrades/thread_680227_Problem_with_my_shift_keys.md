---
title: "Problem with my shift keys"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by giftedwon on 2008-01-27
I just installed Ubuntu on a failry old Dell Lattitude that I got my hands on.  The processor is  1.8MHZ so its still fast enough.   THe shift keys were working fine yesterday and all of a sudden today they stoped working.   I rebooted,   Reinstalled  Ubuntu,  everything and it still does not work.  I can't  use  uppercase but it works with caps lock.


I did connect an external keyboard and it works fine there.   Maybe I did some key combination in the dell laptop that disabled it , I do not know.

I also ready in other post that  Gdesktops was causing this  I searched my system for it and was not able to find it.  Please help me with this problem.

Thanks

---

### Post by giftedwon on 2008-01-27
does anyone have an idea/

---

### Post by accatagon on 2008-01-28
Open the terminal and run "xev" (if you don't have it install it). When you press the shift keys while the window is  active, it should print out information about those keys. Take note of what the keycode it gives you is. Try doing the same thing with the external keyboard. Do the keycodes differ?

Next run "xmodmap". There should be a line that begins with "shift." If it doesn't have Shift_L and Shift_R following that, then that could be your problem. If this is the case run these commands (don't worry, the worst they can do is require you to reboot. They aren't permanent.)

```
xmodmap -e "add shift = Shift_L
xmodmap -e "add shift = Shift_R
```

Next run "xmodmap -pke". You will get a list of keycodes on the left and their corresponding keysyms on the right. Find the lines with the keycodes corresponding to your shift keys. Ideally, they should have Shift_L and Shift_R following the codes that correspond to left shift and right shift, respectively.  If they do not, then that is where your problem is. To fix this, you can run 

```
xmodmap -e "keycode (insert number here) = Shift_L"
xmodmap -e "keycode (insert number here) = Shift_R"
```

If either of those help you can put the stuff in quotes in a file and have it run on startup. If it doesn't work or you need help getting it to run on startup, tell me what went wrong.

---

### Post by giftedwon on 2008-01-30
that did not work.  are there any other alternatives?

---

### Post by giftedwon on 2008-01-30
As bad as this sounds I ended up reloading the laptop and it works now.   

Thanks again

---

