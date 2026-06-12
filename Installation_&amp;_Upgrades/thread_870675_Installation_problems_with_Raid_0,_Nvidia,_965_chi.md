---
title: "Installation problems with Raid 0, Nvidia, 965 chipset"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by garfield81 on 2008-07-26
Hi I have a DG965WH Intel motherboard (Core 2 Duo 6600) with two hard drives setup as RAID0 and a Nvidia 7600GT. I downloaded the 64Bit 8.04 Ubuntu CD and tried to boot from it. I get the screen asking for a language and upon choosing English and I choose Install Ubuntu. Then I see the Ubuntu logo with the non-definitive progress bar. Then the progress bar changes to being definitive and suddenly vertical lines appear on my screen and they start dancing (some lines start switching colors).

Then I tried rebooting and choosing Try Ubuntu without installing and I get the same dancing vertical lines after the ubuntu progress bar.

Does this have to do something with the Raid 0 or the Nvidia graphics card.

FYI: You'll hate me for this but Vista works fine. (*Ducks*)

Thanks

**UPDATE:** I got Ubuntu to boot by unplugging one of the monitors. But Ubuntu does not recognize the RAID0 array. Do I follow the same procedure as a fakeraid?

---

### Post by garfield81 on 2008-07-28
Update Bump

---

### Post by DemaSRV on 2008-07-29
You will have to install it like you would on a fakeraid.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

that may be of some help. Best of luck!  I have a computer in a very similar setup but I was never able to get the fakeraid working correctly (this was a long time ago though).  Oh and after you get ubuntu installed you should be able to go back to your dual monitor setup.

---

