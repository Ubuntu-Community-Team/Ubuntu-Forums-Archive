---
title: "problem installing 9.10"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by m3xican on 2010-03-01
Hi,

I've been using Kubuntu 9.04 for many months and today I've tried to install the latest 9.10 on my Dell XPS M1530.
Unfortunately I've not been able to pass the "Disk Setup" phase because when I try to specify the partition manually the installer is not reading any of my partitions.
All I get in the partition table is the /dev/sda device, but left and right clicks on the entry give no result.

I never had problems with *Ubuntu installers in the past, so I really don't get what's wrong this time. Any idea how I could sort this out?

Thanks.

---

### Post by wrose51106 on 2010-03-01
I had this same model laptop, make sure you update to the latest BIOS if you have not already so the video card does not melt.

Other than that I do not know, good luck!

-Bill

---

### Post by zeroseven0183 on 2010-03-01
OK. This should be a wild guess on my part...

Are you using a SATA drive or an SSD? If you're using SATA, check if you can turn OFF the Native SATA mode in the BIOS.

Have you tried running Kubuntu 9.10 using the LiveCD?

---

### Post by m3xican on 2010-03-01
> **wrose51106 said:**
> I had this same model laptop, make sure you update to the latest BIOS if you have not already so the video card does not melt.

Other than that I do not know, good luck!



Thanks for the hint, I've updated to the latest version even if I never had problems with the graphic card and this hasn't solved my problem :sad:

> **zeroseven0183 said:**
> OK. This should be a wild guess on my part...

Are you using a SATA drive or an SSD? If you're using SATA, check if you can turn OFF the Native SATA mode in the BIOS.

Have you tried running Kubuntu 9.10 using the LiveCD?
I do, I have a SATA drive, but the BIOS doesn't allow me to turn anything off, I could choose between 2 mode options though, but I'd like to avoid to mess thing up in the BIOS, so I'm going to try the text installer as suggested in [this thread]("http://kubuntuforums.net/forums/index.php?topic=3109470.0") I've just found on the kubuntu forum.

Finger crossed...

P.S.
the live CD works fine, the live distro read the partition with no problems... weird

---

### Post by wrose51106 on 2010-03-02
In the BIOS is a setting to turn on / off turbo memory I believe it is called. Disable that and give it a go. It has something to do with Vista, prefetch etc.

-Bill

---

### Post by m3xican on 2010-03-04
> **wrose51106 said:**
> In the BIOS is a setting to turn on / off turbo memory I believe it is called. Disable that and give it a go. It has something to do with Vista, prefetch etc.

-Bill

I can't find anything like that in my BIOS :sad:

Well, for now I'm too busy to waste more time with this installation, so I'm gonna keep working with the 9.04.
Quite disappointing the latest release doesn't work when the previous one does, but... not a big deal, I hope the next one will fix the problem.

Thanks everybody

---

### Post by m3xican on 2010-05-16
I tried every possible setting in my BIOS and to mark "nodmraid" option as well, but I still have the same problem with Kubuntu 10.04 [IMG]http://kubuntuforums.net/forums/Smileys/classic/sad.gif[/IMG]

Any developer could help here?

---

