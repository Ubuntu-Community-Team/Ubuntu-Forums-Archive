---
title: "Ubuntu cannot see my Hard Drive during Installation"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by jingaling on 2010-07-03
Hi Guys,

I have ubuntu running on my netbook, and it's great...I love it! So much so that I decided to migrate my PC over to it the problem is though ubuntu cannot seem to find my hard drive when it comes to ask about the Partition Table.

At the moment my hard drive is running Windows 7. When I boot into ubuntu from the Live CD I can see the drive in there and browse it so it doesn't look like a driver issue to me.

My next though was maybe the install CD was broken to I downloaded it again and wrote to a fresh CD...same thing. I also get an error during boot saying "An unrecoverable error has occurred" but it then continues to boot (this is when booting to the Live CD not windows).

So I then thought OK, I'll try and install Kubuntu then install Gnome over the top of it...same thing on Kubuntu. No error message this time but when it comes to asking me to setup the partitions I just get a blank screen.

What am I doing wrong guys?

Thanks for your help in advance!

Kev

---

### Post by darkod on 2010-07-03
If the disk has been used in raid before, meta data remains on it. Even formatting doesn't remove it. Windows ignores it but ubuntu doesn't.

If you are NOT running raid, boot into live mode and execute:

sudo dmraid -r -E /dev/sda (if the disk name is not /dev/sda, change this)

If it asks you to remove settings, do it and the installer should work fine after that.

If you ARE running raid, don't do the above because it will break your array. You should install in another way for raid.

---

### Post by dino99 on 2010-07-03
some hdd have fab protection, so better to format them with external tools before installation, try partedmagic

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by jingaling on 2010-07-03
Thanks for the quick replies guys.

darkod - no it's just a single disk and it has never been in a RAID (not my knowledge anyway). Thanks for the advice mate.

dino99 - Thanks man, I'll try that is darkod's suggestion doesn't work.

Thanks again.

---

### Post by jingaling on 2010-07-03
Darko 0 your my ubuntu here mate!

That command worked a treat. Thanks again for your help guys!

Jing

---

### Post by darkod on 2010-07-03
> **jingaling said:**
> Darko 0 your my ubuntu here mate!

That command worked a treat. Thanks again for your help guys!

Jing

No problem. Enjoy it now. :)

---

