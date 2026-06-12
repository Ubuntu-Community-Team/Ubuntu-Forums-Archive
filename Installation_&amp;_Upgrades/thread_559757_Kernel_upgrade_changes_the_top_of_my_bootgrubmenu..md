---
title: "Kernel upgrade changes the top of my boot/grub/menu.lst from generic to 386"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Handssolow on 2007-09-25
Yet another kernel update and I'm faced with a black screen and only a command line on offer. My first thought is that's its my Nvidia restricted module that needs integrating with the new kernel. Instead the update puts the 386 version at the top of boot/grub/menu.lst whilst instead I've got an AMD with it's dual cpus and so I use the generic version but I've got a kernel update putting me back to 386 not generic.

After I # out the 386 entries in my menu.lst I'm back with generic and the delightful GUI experience that I'm used to this side of the new millennium.

Don't you just love it when you seen that you're due for a new kernel upgrade? 

No.

---

### Post by reckless2k2 on 2007-09-25
i had 386 issues related to nvidia drivers for older kernel. did you do the nv swap out you're supposed to do before kernel upgrades. if not, that's probably your problem. you have to remove more than just nvidia driver in synaptic or apt-get.

you understand?

---

### Post by buntunub on 2007-09-25
Strange. Ive never had any issues with Ubuntu kernel updates...ever. I run 4 comps, all with nvidia (different versions), and havent ever had my X broke yet. Maybe you might have some funky config setups that conflicted with the update scripts?

---

### Post by Handssolow on 2007-09-25
I'ts obvious I need some more information on this topic.

---

### Post by NJC on 2007-09-25
Handssolow;

Would setting the kopt line in menu.lst help? Maybe not ... but I was just trying to help user "dpar" with a similar problem [here.]("http://ubuntuforums.org/showpost.php?p=3425409&postcount=3")

---

### Post by Handssolow on 2007-09-25
No problem with kernel updates on my wife's PC but she's running a 386 with a  Radeon 9600 video chipset card.

---

