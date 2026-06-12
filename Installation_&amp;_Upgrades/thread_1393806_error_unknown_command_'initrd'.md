---
title: "error: unknown command 'initrd'"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by slugicide on 2010-01-29
I'm trying to install Ubuntu on my Dell Mini 9 with a brand new SSD, but when I try and boot it up I get the message  "error: unknown command 'initrd'." I'm completely stuck. Any help?

---

### Post by lisati on 2010-01-29
What are you installing from? If it's a CD, it could be a bad burn....

---

### Post by wojox on 2010-01-29
[unkown command 'initrd']("https://wiki.ubuntu.com/Grub2#unkown%20command%20%27initrd%27")

---

### Post by lisati on 2010-01-29
> **wojox said:**
> [unkown command 'initrd']("https://wiki.ubuntu.com/Grub2#unkown%20command%20%27initrd%27")

Hmmm interesting.......

@slugicide: check out the link wojox provided.

---

### Post by slugicide on 2010-01-29
I did as your link suggested. Once in Ubuntu I tried the command "sudo grub-install /dev/sda" as suggested, but all I got was: "cp: cannot stat '/boot/grub/video_fb.mod': Input/output error"
Now when I reboot instead of getting the wonky grub entries I get a cursor after the lines "rescue:grub> unaligned pointer 0x97fe Aborted. Press any key to exit." Doing so reboots me into the exact same rescue:grub message.

---

### Post by slugicide on 2010-01-30
Anyone have any ideas for where I should go from here?

---

