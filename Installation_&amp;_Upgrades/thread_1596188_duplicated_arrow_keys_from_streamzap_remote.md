---
title: "duplicated arrow keys from streamzap remote"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by diamaunt on 2010-10-14
after upgrading from 10.04 to 10.10, I'm getting arrow key outputs from my streamzap remote, plus tons of output in /var/log/messages, like:       Oct 13 23:37:30 freyr kernel: [  164.323245] streamzap 7-1:1.0: streamzap_callback: received urb, len 2   Oct 13 23:37:30 freyr kernel: [  164.323255] streamzap 7-1:1.0: sz idx 0: 3f   Oct 13 23:37:30 freyr kernel: [  164.323263] streamzap 7-1:1.0: sz idx 1: ff  Oct 13 23:37:31 freyr kernel: [  164.427414] streamzap 7-1:1.0: streamzap_callback: received urb, len 2  Oct 13 23:37:31 freyr kernel: [  164.427424] streamzap 7-1:1.0: sz idx 0: f  Oct 13 23:37:31 freyr kernel: [  164.427434] streamzap 7-1:1.0: sz idx 1: ff    this duplicates the up down left right that lirc is feeding into mythtv, making it impossible to navigate menus.  I keep getting the directional keypresses from the remote even if I apt-get remove lirc.      maybe there's supposed to be some way to configure things with this new ir-core 'feature' but an eveing of googling hasn't brought me even the tinyest hint of how.

---

### Post by jabjoe on 2010-10-17
The double input is due to the streamzap being registered with both xinput and lirc. Both are adding their events to anything listening, so a steamzap event equal two events.

So far, the only way I've found to ensure it's only registed with lirc is add the line:

ATTRS{name}=="Streamzap*", GOTO="persistent_input_end"

to the top of /lib/udev/rules.d/60-persistent-input.rules

There may well be a better way, and this doesn't help with the flood of streamzap messages in dmesg, but it at least means you can use the remote ok.

There is another thread on this:

[http://ubuntuforums.org/showthread.php?p=9987811#post9987811](http://ubuntuforums.org/showthread.php?p=9987811#post9987811)

Hope some of this helps. :-)

---

### Post by jabjoe on 2011-01-09
I finally got annoyed by the dmesg messages swamping everything to look.

I think the problem is in the driver:

/drivers/media/IR/streamzap.c

in the function streamzap_callback

The lines:

dev_info(sz->dev, "%s: received urb, len %d\n", __func__, len);

and

dev_info(sz->dev, "sz idx %d: %x\n",
			i, (unsigned char)sz->buf_in[i]);

which, as you can see are the messages swamping dmesg.

I think what is meant to happen is that these lines are only done if "debug" is true. Then you can control this logging with the "/sys/module/streamzap/parameters/debug" file. But the debug variable isn't acturally used and these lines are always executed if there is data.

Hope this helps someone!

---

