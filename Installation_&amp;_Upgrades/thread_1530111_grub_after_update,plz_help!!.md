---
title: "grub after update,plz help!!"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by parth.s on 2010-07-13
Hey i have ubuntu 10.04 on a dual boot with win XP.And lucid has definately made me forget XP...

I regularly update ubuntu. Each time i update ubuntu and restart the machine there is a new entry added in the grub 2.Now its showing three entries of ubuntu!

for eg..now i have the grub showing

Ubuntu, with Linux 2.6.32-23-generic
Ubuntu, with Linux 2.6.32-23-generic (recovery mode)
Ubuntu, with Linux 2.6.32-22-generic
Ubuntu, with Linux 2.6.32-22-generic (recovery mode)
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Microsoft Windows XP Professional (on /dev/sda1)


so each time i upgrade a new entry will be made and list larger..now how do i cope with this.Are those entries kept in case i want a roll back.

---

### Post by robert shearer on 2010-07-13
> so each time i upgrade a new entry will be made and list larger..now how do i cope with this.Are those entries kept in case i want a roll back.

Correct.

Though usually all you need is the current kernel and one spare to boot into if needed.

So, open synaptic package manager and in the search box type linux-image.

Scroll through and look for the ones that match those shown in grub.In your case...

2.6.32-23-generic
2.6.32-22-generic
2.6.32-21-generic

These should have a green box next to them showing they are installed.
Right click on the oldest (2.6.32-21-generic) and select remove.
Apply and all should be well (two left thats good ;) )

Now when you reboot there should be only two shown.

---

### Post by parth.s on 2010-07-13
And should i choose complete removal or just normal removal.
thanks robert.

---

