---
title: "[noob] Installing Ubuntu onto an empty partition. Help."
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by cjschris on 2010-12-28
Hi everybody.
I recently got a new HDD, and partitioned it as such:
Windows - 157GB
My Files - 524GB
Empty Space - 68GB

I want to install Ubuntu onto that empty space, but feel a bit confused during installation.

I'm up to Step 4 in the Install of 10.04.
And below are some pictures of what's happening.
[IMG]http://storage.cjs.au.com/rsz_screenshot.jpg[/IMG]
I press Forward
[IMG]http://storage.cjs.au.com/rsz_1screenshot-1.jpg[/IMG]
Then I select /dev/sda4 and press forward.
And this is where I need help.
I want to keep all my partitions, except for this one. But when I select this one and then press forward it says:
No root system is defined.
Please correct this from the partitioning menu.

Please help.:p

---

### Post by ezsit on 2010-12-28
First problem, you partitioned the 68GB as an NTFS partition, Ubuntu can't use that space. At this point in the installation you need to delete that partition and actually free up some space for Ubuntu.

After you delete that 68GB NTFS partition, create a root / partition of about 15GB, a SWAP partition of about 1GB and the remaining space as a /home partition. Once you have created all these partitions for Ubuntu, then you can proceed.

You could also just go with a root / and a swap partition, in which case 67GB for root / and 1GB for swap should be fine.

---

### Post by cjschris on 2010-12-31
So, do i need a swap partition?
And if so, what happens if I dont make one.
Also, if I do the above:
> You could also just go with a root / and a swap partition, in which case 67GB for root / and 1GB for swap should be fine.
Will I get a dual-boot menu so I can get windows?
Thanks.

---

### Post by kansasnoob on 2010-12-31
I'd suggest having a look here:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

or here:

[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

Since you already have 3 primary partitions you should now create an extended partition which can contain several logical partitions.

---

### Post by lithopsian on 2010-12-31
You don't have to have a swap partition, but you can create one while you are partitioning.  If you don't create one you'll either have to live without swap (possible if you have lots of RAM and no need to hibernate) or go with swap files.  There is no real downside to swap files, in fact they are more flexible because they are easier to change.

---

### Post by mick222 on 2010-12-31
No need to reformat select sda4 for click change select mount as / and reformat to ext 4 Ubuntu should create a swap for you.You dont say how much ram you have swap is ussually twice ram but noyt really needed if you have more than 2gb.yes you will be able to select windows at boot

---

