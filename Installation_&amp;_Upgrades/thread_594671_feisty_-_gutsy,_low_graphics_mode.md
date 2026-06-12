---
title: "feisty - gutsy, low graphics mode"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by ndefron on 2007-10-28
I'm currently running in low graphics mode following upgrade from feisty - gutsy. 

I have tried to fix through screens and graphics GUI (as per other posts) however my monitor is not listed. 

Please go easy on me, I'm a total newbie, but thought I'd better ask before I do something I don't understand.

i've got:

amd64x2, nvidia 8600 gt, and my monitor is ag neovo f-17c

Kind regards
ndefron

---

### Post by jenhsun on 2007-10-28
Try this for your graphic card
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
You can do it in without X Windows

Or
You better do a research and get your monitor vertical and horizontal range.

in terminal, try

dpkg-reconfigure xserver-xorg

and follow the screen message

---

### Post by hlmuller on 2007-10-28
You might also try installing in the "Safe graphics mode", the second option.  You probably won't get usplash while it boots and starts X, but it may start X at a normal resolution.

I had usplash / virtual terminal issues to work out afterwards, But the above is what got me over the hurdle.

---

### Post by ndefron on 2007-10-28
Thanks for the advice, seems to work ok once I disabled the restricted nvidia driver.

---

