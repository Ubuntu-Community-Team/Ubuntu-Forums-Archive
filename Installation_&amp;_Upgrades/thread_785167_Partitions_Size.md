---
title: "Partitions Size"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Smart_Viral on 2008-05-07
I'm newbie and this is my first Ubuntu installation
& i will make partitions as
[LIST]
[*]4GB for swap (i have 2G RAM)
[*]11 for root
[*]10 for /home
[/LIST]

is this enough for high performance Ubuntu installation?
Thanks O:)

---

### Post by justifier on 2008-05-07
should be fine

---

### Post by Herman on 2008-05-07
4 GB is way more swap than you need, your computer will hardly ever need any swap area at all if you have 2 GB of RAM, or even over 1 GB of RAM.

The old rule of thumb about the recommended swap area being double the size of your RAM is out of date these days. That was a good rule when hard disks were about 8 GB and most people had between 32 mb and 256 mb of RAM.
I remember that was a nail biting decision when I dual booted Ubuntu Hoary Hedgehog with Windows 98 in a 6.0 GB hard disk in a PC with 128 mb of RAM. The little old computer I had really depended on all the swap area I could spare, but on the other hand, hard disc space was precious too. I had room for 3.0 GB for Windows 98 and 3.0 for Ubuntu, minus the swap area.
Nowadays most people have hard disks and RAM to waste, and swap area isn't such a big performance factor as it once was. I think you're better off saving some hard disk space there though. Nobody needs 4 GB of swap area.

---

### Post by Sef on 2008-05-07
>     * 4GB for swap (i have 2G RAM)
    * 11 for root
    * 10 for /home


Swap should be maximum of 1gb or even just do without it.  I have 2 gb ram and 1 gb swap, but swap is hardly even used.  If you do heavy gaming, video editing, or other graphic intensive operations, then swap will be necessary, otherwise it is optional.

I would make root 10 gb and 11 /home.

---

