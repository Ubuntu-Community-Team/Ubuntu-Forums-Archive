---
title: "Upgraded to 11.04 - can't boot new kernel"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by pissedoffdude on 2011-04-29
I updated the 64-bit version of 10.10 to 11.04 and I am having trouble booting the new kernel, 2.6.38.  The old 2.6.35 kernel under the previous linux versions works fine.  All went well with the update except grub, it installed to the wrong drive, but that was a quick fix  When I try to boot the new kernel in verbose mode, it stops after
```
init: unreadahead-other main process (844) with status 4
init: unreadahead-other main process (849) with status 4
init: unreadahead-other main process (854) with status 4
app armor: skipping firefox

```

Booting the old kernel in verbose reports the same messages, but it doesn't freeze there.  I noticed the config, system-map, vmcoreinfo, and vmlinuz files in /boot had incorrect permissions and I tried setting the same ones the working kernel has but I had no luck.  Also, I've tried purging the new kernel and reinstalling it, but I get the same problem.  Anyone have any ideas on what I could do?

Problem Solved!!
Apparently this was a graphics issue. Before upgrading, I didn't uninstall the nvidia driver from the .run file.  Booting into recovery mode and reinstalling the driver fixed the problem.

---

### Post by ben2talk on 2011-05-05
Not in my case (I think)

I cannot boot the default option: **[COLOR="DarkRed"]2.6.38-8-generic-pae[/COLOR] **
I lose graphics very quickly.

However, going to 'older versions' and selecting the **[COLOR="Green"]2.6.38-8-generic[/COLOR]** option works fine.

What's the crack here?

---

### Post by cis202 on 2011-05-06
do you have two graphics cards (one onboard and one separate)?
I too cannot boot the new kernel and try to find out what causes this.
Some msgs on the fora suggest it has to do with having double graphic-cards. That's why I ask.

---

### Post by MOraleSs on 2011-05-08
Same problem here. I upgraded two servers today. One of them booted with no problems, the other one just refuses to boot with the new kernel. The 2.6.35 version of the previous version works fine. I tryed everything the last 3 hours and still no luck.
I don't think it's a graphic card issue, since I use the server version.
Please, can someone help with this issue?

---

