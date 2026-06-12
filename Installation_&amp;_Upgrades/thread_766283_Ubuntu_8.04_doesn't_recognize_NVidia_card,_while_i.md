---
title: "Ubuntu 8.04 doesn't recognize NVidia card, while it was fine in 7.10"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Malfet on 2008-04-25
Afte upgrade I've found that new Ubuntu does not recognize NVidia graphic card, while it was working perfectly in Ubuntu 7.10. Is there a possibility to downgrade back to Ubuntu 7.10???

---

### Post by gtdaqua on 2008-04-25
it wont work because, ubuntu 8.04 runs a different kernel. 

But NVIDIA will install without any probs. Here is a guide to install it:

[url="http://ubuntuforums.org/showthread.php?t=596875"]
This is the Guide. Ignore the Title. It works for Hardy too.
[/url]

---

### Post by gtdaqua on 2008-04-25
> 
Is there a possibility to downgrade back to Ubuntu 7.10???


Hardy is supposed to be more stable than Gutsy although I never had any probs with Gutsy. 

Everytime your kernel is updated, you have to run the NVIDIA installer with "sudo sh ./NVIDIA-file-name.run"

---

### Post by Malfet on 2008-04-25
> **gtdaqua said:**
> Hardy is supposed to be more stable than Gutsy although I never had any probs with Gutsy. 
Everytime your kernel is updated, you have to run the NVIDIA installer with "sudo sh ./NVIDIA-file-name.run"

In Ubuntu 7.10 I just run Driver Manager and it found my NVidia card and install driver properly. 8.04 doesn't recognize it - I don't see a point in OS stability without a proper work of a graphic card.
By the way, Ubuntu 8.04 recognize my USB web-cam, while 7.10 did not, but I do not want to exchange graphic card for web-cam and see no way except to go back for 7.10
I just afraid of reinstalling all the software and my settings again...

---

### Post by Malfet on 2008-04-25
> **gtdaqua said:**
> it wont work because, ubuntu 8.04 runs a different kernel. 

But NVIDIA will install without any probs. Here is a guide to install it:

[url="http://ubuntuforums.org/showthread.php?t=596875"]
This is the Guide. Ignore the Title. It works for Hardy too.
[/url]

Thanks I will try! Even I do not have a "latest", but pretty old NVidia...

---

### Post by gtdaqua on 2008-04-25
so, the restricted driver manager does not show NVIDIA automatically?? 
I dont know how to sort that out, but I like to do stuff myself. They are more reliable. You can download the latest NVIDIA - its just 17 MB!

But in any case, pl tell how the installation went or wat u did.

---

### Post by Malfet on 2008-04-25
> **gtdaqua said:**
> so, the restricted driver manager does not show NVIDIA automatically?? 

No. It did in Ubuntu 7.10, but not in 8.04. Actually, it show, but ask a restart and then inform me that system can not recognize a graphic card. Becides, it destroy proper keyboard layout, so I can not login and have to fix it from concole mode.

---

