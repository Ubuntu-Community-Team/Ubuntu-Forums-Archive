---
title: "GRUB Error 15 - Can't get passed the Error message, can't boot from USB"
date: 2014-01-06
forum: Installation &amp; Upgrades
---

### Post by kruijer.tim on 2014-01-06
Hi Peops,

I have searched through a lot of forums but haven't find a solution for me yet...

I was messing around with my Asus eee PC 901 and installed android x86 4.2 on the netbook. Later I tried Android 4.3. For a little while it worked well, but later I couldn't start my netbook anymore. 

When I start the netbook, it shows the screen to tell you to press F2 to go into the bios settings, but whatever I try: it won't boot into bios settings... I'm desperate!

Anyone have a solution for me? 

Any help would be wonderfull! Thank you so much!

---

### Post by oldfred on 2014-01-06
Have not seen error 15 for ages. Grub2 does not have error codes.

That is from grub legacy which Ubuntu stopped using as standard with 9.10. Often seen soon after as many users had grub legacy but then may have installed grub2 and that is a conflict which error 15 usually is.

You have to get into BIOS to be able to chose another boot either USB if you system boots from that or Cd/DVD drive. Some have to fully power down, remove battery, and hold power switch for a few seconds to dissipate any residual energy.

---

### Post by kruijer.tim on 2014-01-06
Thank you very much, I somehow managed to get back into the bios and save the netbook ;)

---

