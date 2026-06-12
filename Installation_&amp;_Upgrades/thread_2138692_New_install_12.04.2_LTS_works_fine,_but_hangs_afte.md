---
title: "New install 12.04.2 LTS works fine, but hangs after upgrade"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by mark2013 on 2013-04-25
Hi I have a recently (brand new) installed Ubuntu 12.04.2 LTS 64 bit PC.  I can browse web, open documents, etc, UNTIL I run updates.

I run the update manager and apply the updates, then the system needs a reboot.

The system still boots OK.  However it will hang after about 5 mins after logging in.

If I don't login, it will happily wait at the login screen indefinitely; it's only after login that the system hangs.

Observations:
- Mouse pointer still moves around, everything else hangs, screen is totally unresponsive except for mouse pointer.
- Nothing else has been installed, simply off the CD (and USB) and then applied updates.
- Tried installing both from USB and CD, no difference
- Confirmed md5 sums on the downloaded ISO are A-OK (also tested the CD for defects before installing).
- No fancy partitioning, just straight defaults 
- Motherboard is an Asustek P8P67
- CPU is Intel G550 at 2.60GHz
- Graphics card appears to be the Intel on board H61 thing (no additional separate graphics card).
- 4 GB RAM
- I also tried Xubuntu, I get exactly the same symptoms: Install all is well, then run updates, updates all work fine, reboot system, login, then hangs.
- I tried turning off all updates except required security updates, still get this behaviour.
- Tried turning off desktop compositing, no difference to the behaviour, it still hangs after updates.

- Installed Ubuntu Server (is a non GUI of course!) 12.04.2 LTS 64 bit, all fine, updates all fine, everything works OK.  So most likely the issue is GUI related!

My research points to similar behaviour being related to buggy nvidea video drivers, but as I have no fancy cards, just using vanilla Intel H61 on board video, I don't think that applies in this case (I can't change the 3rd party drivers as none are in use).

Please help with any advice, or how I might track/debug what is causing this.

Thank you
Mark

---

### Post by Bucky Ball on 2013-04-25
Please run these, one after the other, in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

The second command will not upgrade the distribution to the next release, but will upgrade any software in the current release that needs upgrading. Reboot and see what happens.

PS: Never run the second command by itself. Always update before 'sudo apt-get upgrade'.

---

### Post by FenrirXIII on 2013-04-25
have you tried sudo apt-get install mesa-utils?
then find out what kind of graphics chip you got like "ironclad", "sandy bridge", etc.
if it is sandy bridge your best bet is not to install a certain update, that is the linuxkernel35, i had this problem before with my brothers computer and it took me weeks to realize that maybe sandybridge has an gpu problem with the kernel. so far my brothers computer is not freezing. so that must be the key.

---

### Post by mark2013 on 2013-04-25
> **Bucky Ball said:**
> Please run these, one after the other, in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

The second command will not upgrade the distribution to the next release, but will upgrade any software in the current release that needs upgrading. Reboot and see what happens.

PS: Never run the second command by itself. Always update before 'sudo apt-get upgrade'.

Hi yes that works.... ran the command line update and it's all happy so far.  I didn't realise the GUI Update program and the command line were so different...  I know the command line tool to upgrade to a new kernal is different.  In fact on my server I've only been running the two commands above so maybe server will still break if I tried to upgrade the kernal (or is the correct term "distro"?).

Is there a way to stop the GUI tool from automatically offering to upgrade the kernal?  Also it appears that some of the kernal upgrades have a problem with the embedded Intel graphics chip, has this been logged as a bug?  I found a discussion on it here:
[URL="http://askubuntu.com/search?q=12.04+freezes+after+upgrade"]
http://askubuntu.com/search?q=12.04+freezes+after+upgrade[/URL]

Thanks for your help!
Mark

---

### Post by mark2013 on 2013-04-25
PS I can't seem to mark thread as solved, under thread tools I just see three entries: Show Printable, Email This Page, Subscribe to this thread.  How do I set thread to solved please?  Thanks!

---

### Post by Bucky Ball on 2013-04-25
> **mark2013 said:**
> PS I can't seem to mark thread as solved, under thread tools I just see three entries: Show Printable, Email This Page, Subscribe to this thread.  How do I set thread to solved please?  Thanks!

Forums had an upgrade recently and the 'Solved' method is broken. Try this:

Edit first post, click 'Go Advanced', change the prefix [ubuntu] in the title of the thread to [solved]. It's there as a default selection.

Kernel updates (more recent kernels) should be installed as part of your regular updates. As long as you are with the kernel used on 12.04 LTS you should be fine. Do you know the number of the kernels that are supposed to interfere with Intel? 13.04 kernel by any chance? Neither of the two commands in my previous post could upgrade to that. You would need to manually add the 13.04 kernel ppa or something along those lines.

---

### Post by mark2013 on 2013-04-26
> **Bucky Ball said:**
> Do you know the number of the kernels that are supposed to interfere with Intel?

No but according to the link I posted, one poster mentions versions:
[http://askubuntu.com/questions/269883/ubuntu-12-04-freezes-after-update](http://askubuntu.com/questions/269883/ubuntu-12-04-freezes-after-update)
> It started with kernel 3.2.0-39, and also  happens in kernel 3.2.0-40 and 3.2.0-41. I avoid it by booting to  3.2.0-38 (at boot time, I select "previous kernels" option, or whatever  it's called, and select 3.2.0-38-pae from the list)

and it's confirmed as a bug which has more information:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1157252](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1157252)

Thanks for your help :)
Mark

PS Might be an idea to update your signature instructions for marking threads SOLVED for us newbies; I've marked as SOLVED so should show up now.

---

