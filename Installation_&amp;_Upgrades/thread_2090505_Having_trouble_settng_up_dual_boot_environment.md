---
title: "Having trouble settng up dual boot environment"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by JOZeldenrust on 2012-12-02
Hey everybody,

I recently got a new PC, after my ancient one finally gave out. It came with Windows 8 preinstalled, and after five years of using Linux exclusively, I kind of want to keep Windows around so I can play some games without endless fiddling in Wine. I still want Ubuntu as my every day OS, though, so I wanted to set up a dual boot system.

So I downloaded a LiveCD image, burned it onto a DVD, and tried to run it. My PC wouldn't boot from the DVD, and I couldn't get into the BIOS (I can now), so I took the LiveCD up on its offer to help me boot from DVD.

I was presented with a nice menu offering the choice between Windows 8 and Ubuntu. I chose Ubuntu, and was greeted with an error message. Turns out I needed the 64 bit version. So I downloaded that, and installing Ubuntu onto the partition I had created for it was a breeze.

There's just one little problem: it's not dual boot. I have two possible boot partitions, one for Win 8, one for Ubuntu. If I set the BIOS to boot from the Win 8 partition, I get the nice menu from earlier, and selecting Win 8 works, but selecting Ubuntu makes the PC try to boot from CD again, which isn't what I want. If I set the BIOS to boot from the Ubuntu partition, it straight up boots into Ubuntu.

So, how do I fix it so I have a boot sequence that gives me two working options, one for Win 8 and one for Ubuntu?

Any advise will be greatly appreciated.

---

### Post by darkod on 2012-12-02
Most new computers come with the new type of UEFI boot, and not with the older legacy bios boot.

I don't use uefi, but here is more info about successful uefi dual boot, since things are not exactly the same as with bios boot:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The most important seems to be to boot the cd in uefi mode, not legacy mode. The installer will then install ubuntu in uefi mode. And only the 64bit version has uefi support but you already mentioned you downloaded the 64bit ISO as a second attempt.

PS. Of course, all of this applies only if your computer really uses uefi boot. I think there is a procedure to test that in that link.

---

