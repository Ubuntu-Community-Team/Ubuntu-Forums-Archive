---
title: "boot-repair gives no repair option"
date: 2019-05-02
forum: Installation &amp; Upgrades
---

### Post by dwater on 2019-05-02
I had a similar thing before, but that was after having a motherboard replaced[1]. This time, it is simply updating Windows that has done this.

I've tried both an ubuntu live flash drive, and installing boot repair on that, and also the boot-repair-disk, with the same result. Here's a photo of the screen from boot-repair on the latter - note this runs automatically after booting, so it isn't me mistakenly running 'boot-info' or anything like that:

[https://photos.app.goo.gl/igeJoQAKKExYsceB6](https://photos.app.goo.gl/igeJoQAKKExYsceB6)

Just as before, boot-repair has no 'Recommended repair' option, nor the '> Advanced options' toggle.

...and from a 'live usb drive':

[https://photos.app.goo.gl/CPSLe92oFxtehQqK8](https://photos.app.goo.gl/CPSLe92oFxtehQqK8)

Any ideas what might be going wrong, and how to fix it?

Max.[URL="https://ubuntuforums.org/showthread.php?t=2408539"]

[1] https://ubuntuforums.org/showthread.php?t=2408539[/URL]

---

### Post by oldfred on 2019-05-02
Are you running this?
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Not this?
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dwater on 2019-05-02
> **oldfred said:**
> Are you running this?
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Not this?
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

That's what you said last time :)
See screenshots. It's definitely boot *repair* I am running - actually, I don't manually run it when I use boot-repair-disk.
You can see that from the title of the windows in the screenshots, amongst other things.

One things that has come up since posting, is that the BIOS shows no drives. I can boot windows as normal (that's what I'm using now), so somehow Windows is working...Windows' device manager shows the drive - annoyingly, doesn't allow me to copy the text, so I have to photo the screen:

[https://photos.app.goo.gl/b6phCxdM14931QdY7](https://photos.app.goo.gl/b6phCxdM14931QdY7)

Any ideas?

---

### Post by dwater on 2019-05-02
Here's the info:

[http://paste.ubuntu.com/p/rTsBWPM23K/](http://paste.ubuntu.com/p/rTsBWPM23K/)

---

### Post by oldfred on 2019-05-02
Did you update UEFI and update NVMe firmware.
That often is a cause of NVMe drives not being correctly seen.

But Boot-Repair uses bootinfoscript for the first part of its report. And bootinfoscript has not been updated for NVMe drives.
See bug report.
Support NVMe and MMC devices bug oldfred request
[https://github.com/arvidjaar/bootinfoscript/issues](https://github.com/arvidjaar/bootinfoscript/issues)


One user did post in above issue thread, an updated bootinfoscript. Just as a test to see if it really works download that and post its output.
Please use code tags as it will be longer and just saves in in your /home.

---

### Post by dwater on 2019-05-03
ok, I'm back up and running now.

Like last time, I was scrambling a bit so I'm not 100% sure what I did that moved me forward. I did reinstall the drivers and bios that I had installed and which took me into the problem in the first place. I then rebooted and tried some Dell diagnotics and noticed that it seemed to 'see' the hard drive (I hadn't run that util before, so I don't know if it had changed)[1]. I then booted into BIOS config and it didn't seem to have changed, at least not in the 'drives' page, so I dug around a bit more - I've never been convinced I've been interpreting that page correctly. I found some mention of it in one of the pages at the top of the BIOS, and it did mention the drive[2]. So, I dug around a bit more and found the boot sequence page[3], which has a 'Windows Boot Manager' checkbox...so I unchecked that, saved and rebooted. The result was that it would no longer boot Windows...which I thought might be a step forward...so I booted in live ubuntu and run Disk Utility and it could see the SSD again - woo foo :) So, I did the boot-repair install stuff, and it looks normal again....and I did the 'Recommended repair', and it all worked....I'm now back in Ubuntu.

So, thanks for the tool :D

I'm not sure if it was reinstalling the BIOS (I did installed a different 'copy' of the download the 2nd time, so it could be that), or disabling that 'Windows Boot Manager' thing that helped. I suspect the latter (enabled by default, probably), but it's some clues for someone else anyway.

My next step will be to remove Windows altogether...I've been running out of disk space lately anyway.

[1] [https://photos.app.goo.gl/wZcZUDBoSvnvS3Kv6]("https://photos.google.com/photo/AF1QipPeE4jcixyJTXD7m0tcClSlvZQlXTpkoFFOnSCX")
[2] [https://photos.app.goo.gl/6oDtbQ6Ua7gM69Lf8]("https://photos.google.com/photo/AF1QipO-mFOKKLmw95U176NkTHPYRkrzKlOOihbD68UZ")
[3] [https://photos.app.goo.gl/JTKk4h1xbCWC7uGa8](https://photos.app.goo.gl/JTKk4h1xbCWC7uGa8)

---

