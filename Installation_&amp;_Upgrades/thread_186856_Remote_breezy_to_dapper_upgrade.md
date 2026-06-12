---
title: "Remote breezy to dapper upgrade"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by kingmonkey on 2006-06-02
Has anyone done a remote breezy to dapper upgrade through ssh? and did you run into any problems?

---

### Post by simms on 2006-06-02
Yep, you can do it over ssh without any problem.  Same as Debian. 

I recommend using 'screen' as a wrapper, just in case you lose the connection during the upgrade. This way you can connect again and get back to your session with a 'screen -D -r'. 
Of course, any reboot required will nix the screen session, but in any case the reboot won't be necessary until the upgrades are complete.

---

### Post by kingmonkey on 2006-06-02
Thanks, 

Never heard of screen before and sounds good.

Here is a short intro website if anyone is interested.
[http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

