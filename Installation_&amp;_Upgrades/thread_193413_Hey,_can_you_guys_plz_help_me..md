---
title: "Hey, can you guys plz help me."
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by BuckVincent on 2006-06-10
Ok, well I just decided to use Ubuntu since my computer is having problecations with XP and Ive been wanting to try Linux for a while. Anyway.

I put in the install disk and everything was fine, it loaded up great and everything, then it said that is was finished and it ejected the cd and it said for me to reboot, so I did. It then went to a screen where it said it was unpacking the files. I let it sit there and went and watched tv, came back 30 min later and it was still on zero. So I was like ok. Well I rebooted again and it happened the exact same way. Then I decided to just try and reformat it. Well when I did this it came up as a Grub 15 error. Now it wont do anything...any ideas?

---

### Post by zxee on 2006-06-10
How did you and what did you use to create a filesystem for the install?
Error 15, grub, is file not found so it seems something went wrong, perhaps with creating the filesystem, or grub was installed to the wrong place? Although I think that's less likely. Provide a little more specifics about your install i.e, partitioning and what selection you made for grub, and someone will probably be able to figure this out.

---

### Post by BuckVincent on 2006-06-10
I used the Ubuntu cd that I have, I dont remember which partition I selected...I remember it said that for some reason it couldnt make back-ups and said I could skip. Think that is the problem?

---

### Post by zxee on 2006-06-10
Do you have the live cd? If you can run from a live cd you could try looking at your hard drive with cfdisk. Open the terminal app and type sudo cfdisk /dev/hda. If you are not using your master or sole "A" drive you will have to change /hda to the actual drive designation. Assuming you get that far cfdisk should show you partitions and hopefully linux usable partitions on your drive. Copy and paste the results of cfdisk and then we will know more how to help you.

---

### Post by BuckVincent on 2006-06-10
it wont even let me run from the live cd.

---

### Post by BuckVincent on 2006-06-12
can someone please help? i dont know waht to do...

---

