---
title: "Screen Resolution Problem After OS Update to 16.04"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by stephen67 on 2016-10-15
The update seemed to complete properly.

There are no more updates available.

When I booted, I get a resolution of 1024*768.

System settings says my monitor is not recognized.

I should get 1920*1080 and did so properly before the update.

System also seems a little sluggish.

Any and all assistance appreciated!

Thanks

---

### Post by stephen67 on 2016-10-15
I upgraded to 16.10 hoping that that would fix the screen resolution problem.

It did not. :(

I ran xrandr and it only reports up to 1024*768

---

### Post by stephen67 on 2016-10-16
I tried further with xrandr 

[https://wiki.archlinux.org/index.php/xrandr](https://wiki.archlinux.org/index.php/xrandr)

I used

cvt

I got: Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode 1920x1080_60.00

After the last commend, my screen resolution was reduced to something like 640x480 and an error window popped up. I could not read the full error message because it was off the screen. It started with "Could not set"

I had to do a reset.

---

### Post by stephen67 on 2016-10-16
I was given this in another forum:

[https://gist.github.com/mvollrath/9aa0198264e6b4890914](https://gist.github.com/mvollrath/9aa0198264e6b4890914)

It worked! Joy!

---

### Post by RobGoss on 2016-10-16
Glad you resolved your issue if you no longer need assistants would you mind marking this thread as solved, you can do this by using the** Thread Tool** at the top of this post

Thank you

---

