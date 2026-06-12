---
title: "Old kernels in Grub2 don't exist"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by dndrich on 2010-05-10
Ubuntupals:

I just installed 10.04 over my previous dual boot with Windows7 and 9.10. Went well. Now, in the Grub2 menu, there are like 14 kernels. I tried to find them in Synaptic to delete them, but they are not there! So, I went to grub.cfg and deleted the entries, updated grub, and they were back! How do I get rid of these entries?

---

### Post by igf1 on 2010-05-10
sudo update-grub

Have you tried that?

---

### Post by dndrich on 2010-05-10
Yes. For some reason it is finding images that don't seem to exist. At least, I can't find them in Synaptic. And, other than grub, this is a clean install. I deleted the partition that had 9.10 when I installed 10.04. So, I have 10.04, Windows7, swap, etc. Can't figure out how to get rid of these!

---

### Post by garvinrick4 on 2010-05-10
> **dndrich said:**
> Ubuntupals:

I just installed 10.04 over my previous dual boot with Windows7 and 9.10. Went well. Now, in the Grub2 menu, there are like 14 kernels. I tried to find them in Synaptic to delete them, but they are not there! So, I went to grub.cfg and deleted the entries, updated grub, and they were back! How do I get rid of these entries? There is a file in grub somewhere where you can set how many kernels to hold before it throws them away.
 Going to look for it in a while, memory stinks sometimes when looking for paths.
Usually for users with one OS and you do not see the grub menu at boot and kernels can
stack up. Me I keep 2 kernels active for each install. I believe default was about 10 kernels or so, a lot anyway. Wish I could remember the path but I will sooner or later. Only a few places it could be. Now with computer janitor even GUI will tell you when there are multiples.
 You should try CODE:

sudo aptitude update && sudo aptitude upgrade

In terminal and it will tell you what should be tossed and how to do it.

---

### Post by dndrich on 2010-05-10
> **garvinrick4 said:**
> There is a file in grub somewhere where you can set how many kernels to hold before it throws them away.
 Going to look for it in a while, memory stinks sometimes when looking for paths.
Usually for users with one OS and you do not see the grub menu at boot and kernels can
stack up. Me I keep 2 kernels active for each install. I believe default was about 10 kernels or so, a lot anyway. Wish I could remember the path but I will sooner or later. Only a few places it could be. Now with computer janitor even GUI will tell you when there are multiples.
 You should try CODE:

sudo aptitude update && sudo aptitude upgrade

In terminal and it will tell you what should be tossed and how to do it.

What is so weird is that I ran the code above, and it says 0 for upgrade or remove. I have searched in Synaptic, and these kernels are not there. Yet they appear in the grub list on boot. Would love to get rid of them.

---

### Post by igf1 on 2010-05-10
hmm, I havnt done this on ubuntu (or Grub2 for that matter) 

Here's a link [https://help.ubuntu.com/community/Grub2#/etc/default/grub](https://help.ubuntu.com/community/Grub2#/etc/default/grub)

That should help.

---

### Post by dndrich on 2010-05-10
OK, I found the kernels in /boot. I gksudo nautilus, and deleted them. I then ran update-grub, and that did it. Don't know what those were doing there, but there you have it.

---

