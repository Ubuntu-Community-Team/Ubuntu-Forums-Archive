---
title: "How to slow down bootup?"
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2010-02-06
Well, lucid boots up so dang fast that I can barely (actually NOT) see the plymouth theme during startup, just for a brief while during shutdown :lolflag:

I tried adding an init script with a sleep 10 (up to 30) but it only seems to work during shutdown where I can see the entire space-sunrise shutdown theme.

I have a link from all the /etc/rcX.d folders where X is 2,3,4,5 and S called S85plymouthsleep pointing to a bash script at /etc/init.d/plymouthsleep which is just this:

```

#!/bin/sh

sleep 30

exit 0

```

But no joy...

I am searching online right now, found: [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

Anyone else tried something similar or knows how I should SLOW DOWN MY BOOT ? :)

---

### Post by wojox on 2010-02-06
That's a first. Usually it's the other way around.

---

### Post by phenest on 2010-02-06
You are having a laugh, right? Why do you want to do that? I'd rather a fast boot up time so as not to need plymouth. As I'm getting a boot up time of circa 17 seconds, a nice static Ubuntu logo (like Jaunty has) would suffice for me.

---

### Post by vishalrao on 2010-02-06
:lolflag: I just realised how funny the thread title sounds!

Eventually I'd revert to fast bootup with a very simple (or no) splash but just wanted to play around with the cool plymouth theming...

I'm using plymouth version "0.8.0~-10~nouveau" from the xorg-edgers nouveau PPA to answer the call for testing: [http://ubuntuforums.org/showthread.php?t=1400120](http://ubuntuforums.org/showthread.php?t=1400120)

This looks like a nice wiki: [http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts)

The link was printed as a warning by update-rc.d :D Lets see if I can figure out the plymouth starts-late-while-my-PC-boots-too-damn-fast issue :D

My boot (with an SSD) from grub to KDM is now UNDER TEN SECONDS... that is amazing... I am simply loving Lucid already...

---

### Post by Vanishing on 2010-02-06
> **vishalrao said:**
> Well, lucid boots up so dang fast that I can barely (actually NOT) see the plymouth theme during startup, just for a brief while during shutdown :lolflag:

I tried adding an init script with a sleep 10 (up to 30) but it only seems to work during shutdown where I can see the entire space-sunrise shutdown theme.

I have a link from all the /etc/rcX.d folders where X is 2,3,4,5 and S called S85plymouthsleep pointing to a bash script at /etc/init.d/plymouthsleep which is just this:

```

#!/bin/sh

sleep 30

exit 0

```

But no joy...

I am searching online right now, found: [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

Anyone else tried something similar or knows how I should SLOW DOWN MY BOOT ? :)

When I first saw the title, I loled.
and after I read this, I loled hard.

lol:lolflag:
its gotta be in /etc/rc*.d try some.

---

### Post by vishalrao on 2010-02-06
apparently rc*d is too late... because plymouth is an init/upstart script/job :D

so im now trying to get either an upstart job or initramfs script going...

---

