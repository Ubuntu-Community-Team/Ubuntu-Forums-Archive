---
title: "Ubuntu 12.04 got corrupt after booting itself again in VirtualBox"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by Madeentje on 2012-05-06
Hi, I've just done something stupid..

I created a raw VMDK of the SSD I've put Ubuntu and Windows on. I've done this in the past with no problem, because I want to boot into my Windows quickly without having to shutdown Ubuntu.

So now I did it again in my new Ubuntu 12.04 installation (after 1.5 days of configuring it nicely!). When I boot it up first time I got this warning pop-up on VirtualBox (something usual, about capturing mouse/keyboard). While reading it, VirtualBox was booting my Ubuntu AGAIN virtually (inception), as it is first in GRUB2-menu. I knew the dangers of it.. (That stupid pop-up is to blame ><)

So now my Ubuntu got a bit corrupt... No sound, and graphics seem off while booting up/shutting down, and also in tty.

Please tell me there's a way to repair this? I don't look forward to installing my Ubuntu configuration perfectly again (takes ages with all my development programs).

Thanks for your time. Looking forward to some help.

EDIT1: Seems like sound is back after a reboot, although it takes a while to "load in". Also when shutting down it says "Stopping VirtualBox kernel modules...". I suppose that's not normal?
EDIT2: Now I booted into a previous Linux kernel and all seemed fine (correct graphics). I then booted back into the latest Linux kernel (which previously showed odd graphics), and now that seems fine too.

Seems like it's fine again... But maybe you guys still know of something that I should look out for or fix?
EDIT3: It still says "Stopping VirtualBox kernel modules" while shutting down. Not sure if this is normal behavior or not?

---

### Post by Paddy Landau on 2012-05-07
Sorry, I don't know what has happened there. Messing about with VB in that manner is easy to mess up, as you found!

But I'm glad it's working again.

Here is a lesson, though: before you do potentially dangerous things like this, back up your relevant partitions. You could use [CloneZilla]("http://www.clonezilla.org/").

---

### Post by Madeentje on 2012-05-07
Thanks :). I indeed hope everything is fine again, seems like it so far.

I'll give that CloneZilla a try soon, thanks :). I suppose it's similar to Acronis (which I used in dark times on Windows).

---

### Post by Paddy Landau on 2012-05-07
> **Madeentje said:**
> I suppose it's similar to Acronis
I don't know Acronis, but CloneZilla lets you back up partitions or entire disks and restore them.

Unfortunately, CloneZilla's interface is not user-friendly, but it is reliable, open source and free.

---

### Post by Madeentje on 2012-05-08
I see. Thanks for the advice. Will give it a shot when I've got some spare time.

---

