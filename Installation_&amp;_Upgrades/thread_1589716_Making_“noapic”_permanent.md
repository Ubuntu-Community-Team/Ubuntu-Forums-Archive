---
title: "Making “noapic” permanent"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2010-10-06
Making “noapic” permanent

This is a 10.04 new installation from a usb drive, and I’m getting kernel panic on boots.  [I’ve figured out how to get around that on boot]("http://www.linuxquestions.org/questions/linux-newbie-8/how-to-add-noapic-to-grub-599143/"), but I want to make the “noapic” permanent.  
I’ve run into kernel panic before with this machine (emachine t3516a), but it looks like the old commands to make “noapic” persist through reboots are no longer valid with this new distro.  I tried both of the commands listed [here:]("http://ubuntuforums.org/showthread.php?t=704873") but no files are produced, so there’s nothing to append the suggested entries to.

I’m a beginner with all this, but it’s fine if you just give me a link to the post where the solution is presented.  If I can’t figure it out, I’ll ask further questions. 

Thanks in advance, 
Scott

---

### Post by nevius on 2010-10-06
```
sudo gedit /etc/default/grub
```
add "noapic" in between the quotes on the line that says GRUB_CMDLINE_LINUX=""

Then ```
sudo update-grub
```

---

### Post by sks24 on 2010-10-06
worked like a charm nevius.  Thank you very much.

---

### Post by Aitaix on 2010-10-24
Works like a hot damn. thanks!

---

