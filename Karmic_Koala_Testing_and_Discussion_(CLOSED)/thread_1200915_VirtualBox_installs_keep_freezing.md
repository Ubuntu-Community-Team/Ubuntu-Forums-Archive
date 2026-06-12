---
title: "VirtualBox installs keep freezing"
date: 2009-06-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ace214 on 2009-06-30
I have Ubuntu and Kubuntu Karmic installed from the 06-29-2009 alternate cds and they keep freezing in VirtualBox after a few seconds. Kubuntu sometimes doesn't even start completely.

I realize that this may be a bug with that day's CD, but are there any suggestions to try and solve this problem without downloading new CDs and such?

I'm using the proprietary version of VirtualBox in Ubuntu Jaunty.

---

### Post by zekopeko on 2009-06-30
try this:

[https://help.ubuntu.com/community/RsyncCdImage](https://help.ubuntu.com/community/RsyncCdImage)

it should only fetch the bytes that changed so you will download a few MB at most.

---

### Post by martalli on 2009-07-05
I have found that virtualbox works well for a while with my 9.10 install, but will freeze up suddenly, especially when doing updates or installs.  Even the progress bar animation quits working.  I can 'unfreeze' this by closing the virtual machine, saving the machine state, and then restarting the machine.  When the machine restarts, it briefly loses its network connection, then reestablishes the connection and the starts up again.

I wondered if this might be a driver issue.  It occurs with or without the vbox additions, but is there a kernel just for virtual machines or something along those lines?

Bryan

---

### Post by timfidler on 2009-07-06
I get the freezing problem in VirtualBox when trying to run 9.04 as a guest. Thanks for the tip on saving the state - this gets it going again but as there are 150 updates to do and it pauses after each one I could be here for a while!

In fact just thinking about it, I've had 9.04 do the same thing on me on a new native install, only once though. Very odd, never had any probs with previous releases.

---

### Post by timfidler on 2009-07-06
OK - I've solved my problem. It may well apply to Karmic too, so I'll share... Basically if you edit your VM settings and change the network adapter from PCInet_FAST to the Intel Pro Desktop one and boot back up, the problem disappears.

Hope this helps for you too.

---

### Post by ace214 on 2009-07-06
> **timfidler said:**
> OK - I've solved my problem. It may well apply to Karmic too, so I'll share... Basically if you edit your VM settings and change the network adapter from PCInet_FAST to the Intel Pro Desktop one and boot back up, the problem disappears.

Hope this helps for you too.

Thanks for the tip. I will try this later.

---

### Post by erdalronahi on 2009-07-06
Thanks a lot, this tip was really helpful

---

