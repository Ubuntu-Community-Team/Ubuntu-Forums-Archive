---
title: "[HOWTO] Convert (any) ext3 partitions to ext4"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by c0ldfusi0n on 2009-04-03
Hey everyone!

I noticed there's a lot of talk about converting ext3 partitions to ext4, especially your boot partition on this forum. I managed to do it a few days ago, so I figured I'd share with you all, as I got a fair amount of information from all of you's :)

For the sake of maintaining, I posted it on my personal blog, but there's no ad or any kind of spam/annoyances, I hope that's ok.

Here's the URL: [http://blog.fusi0n.org/linux/converting-ext3-partitions-to-ext4-on-ubuntu-904-jaunty](http://blog.fusi0n.org/linux/converting-ext3-partitions-to-ext4-on-ubuntu-904-jaunty)

Let me know if you have anything to add!

---

### Post by FuturePilot on 2009-04-03
There's no need to patch Grub or anything. It was already patched in Jaunty.

Also it's not really necessary to add the rootfstype=ext4 parameter if you already changed ext3 to ext4 in fstab.

---

### Post by c0ldfusi0n on 2009-04-03
> **FuturePilot said:**
> There's no need to patch Grub or anything. It was already patched in Jaunty.

Also it's not really necessary to add the rootfstype=ext4 parameter if you already changed ext3 to ext4 in fstab.

It's interesting that you mention that there's no need to patch GRUB, because that's what I believed based on the information I found online. However, when I had an unpatched GRUB running, my system wasn't booting. First, GRUB gave me an error saying that it attempted to access a block outside partition (without mentioning error 24) then it gave me a simple Error 24, which is basically the same thing. As soon as I patched and updated grub, it worked just fine. Weird?

---

### Post by FuturePilot on 2009-04-03
> **c0ldfusi0n said:**
> It's interesting that you mention that there's no need to patch GRUB, because that's what I believed based on the information I found online. However, when I had an unpatched GRUB running, my system wasn't booting. First, GRUB gave me an error saying that it attempted to access a block outside partition (without mentioning error 24) then it gave me a simple Error 24, which is basically the same thing. As soon as I patched and updated grub, it worked just fine. Weird?

Probably this
[https://bugs.launchpad.net/ubuntu/+bug/353071]("https://bugs.launchpad.net/ubuntu/+bug/353071")

I ran into the same thing on 2 computers. Something doesn't go right with Grub when converting from Ext3 to Ext4. It probably worked after you patched it because the workaround is to just reinstall Grub to the MBR.

---

### Post by c0ldfusi0n on 2009-04-03
Thanks FuturePilot. Updated the article accordingly.

---

### Post by FuturePilot on 2009-04-03
> **c0ldfusi0n said:**
> Thanks FuturePilot. Updated the article accordingly.

No problem :)

---

