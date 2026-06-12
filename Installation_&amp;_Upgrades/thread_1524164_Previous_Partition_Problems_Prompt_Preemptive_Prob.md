---
title: "Previous Partition Problems Prompt Preemptive Probe"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by CommieTechie on 2010-07-04
So I've done this once before... I have a hard drive that is half Ubuntu 8.04, and half Ubuntu 10.04. I want to knock out the 8.04 partition and make it all 10.04. 

The problem is that last time I did this (same situation, 7.10 -> 8.04) GRUB couldn't find the 7.10 partition anymore, prompting me to reinstall GRUB. It worked, but it seemed to latch on to my (then) current kernel version, and didn't boot into the newer kernel anytime it updated. It was, needless to say, quite annoying.

Now, 10.04 slapped GRUB2 onto my system. I'm wondering, will GRUB2 have the same type of problem? Is there a better way to go about knocking off my 8.04 partition then I've been doing? Any help is appreciated here.

---

### Post by darkod on 2010-07-04
If you are using grub2 from 10.04, you could simply delete the 8.04 partitions, it has no relation to them. If the swap partition is shared with 10.04, make sure not to delete it.

After that if you run:

sudo update-grub

it will remove the 8.04 from the boot menu. After that expanding the 10.04 partitions is up to you, if that's what you plan to do.

---

### Post by CommieTechie on 2010-07-04
Awesome thanks. I'll go try that now. I guess I neglected to update grub after deleting the 7.10 partition last time I attempted this. And then I couldn't get back into the 8.04 partition and it was just a mess...

---

### Post by CommieTechie on 2010-07-04
Yup! That did it. Thanks for the help, it worked perfectly :)

---

