---
title: "Huge initrd.img size"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by predato on 2013-01-17
I have Zorin OS based on natty, I have slow boot time and huge  initrd.img size, it's 230 mb after I upgraded kernel to version 3.0.0 I searched the net for a solution but I didn't find an answer.
Would you please tell me how can I reduce size of initrd.img. I tried to change in sudo gedit /etc/initramfs-tools/initramfs.conf "most" to "deb" as advised in a forum, it only reduced 3mb.
People have around 15 mb at most. Why do I have such a huge initrd.img size?

---

### Post by ibjsb4 on 2013-01-17
Don't know about Zorin, but do know Natty has reached EOL and no longer supported in Ubuntu.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by predato on 2013-01-17
> **ibjsb4 said:**
> Don't know about Zorin, but do know Natty has reached EOL and no longer supported in Ubuntu.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Thank you for the post.  
I tried the solution in this post, [http://unix.stackexchange.com/questions/30345/why-is-my-initial-ramdisk-so-big](http://unix.stackexchange.com/questions/30345/why-is-my-initial-ramdisk-so-big)
 it reduced the size to 97mb is the same size as my previous kernel's  initrd.img. It's still too big

---

