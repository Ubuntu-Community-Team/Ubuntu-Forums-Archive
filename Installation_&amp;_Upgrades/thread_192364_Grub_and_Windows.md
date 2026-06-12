---
title: "Grub and Windows"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by elbryan on 2006-06-08
Good evening ^^.
I'm looking for a solution that i wish someone could tell me ..

I've a parition with Windows XP(sda1) and another one with Linux (Kubuntu) (sdb6).
During a first linux's installation i prompted "no" to install grub and I opted for lilo bootloader (installing it in sdb6 partition).
When the installation finished I booted in linux (with a 3rd part bootloader [System Commander]) but it gived me a lot of error breaking the startup at bashbox (bluhbox maybe i can't remember the name).

I reinstalled linux and i overwrote the MBR with the grub and kubuntu worked well...

Now I had had some problem with Windows so I have overwritten the MBR with Windows's one..

So I still have 2 choises:
- Reinstalling grub in MBR
- Reinstalling grub/lilo on /dev/sdb6 and reable my Bootloader.

From the highness of your experience, hint me the right way to avoid another reformat / reinstall :)

Thank you so much!

---

### Post by elbryan on 2006-06-08
Another info.. when I try to start with Linux from my bootloader, appears a console:
"grub> "
I think it's a minimal console..

I've already tried to do a "setup (hd0,1)" but nothing worked well .. apparentely no modify occoured.

Would be wonderfull now installing grub into Linux partition to let it starting with System Commander. No one has a solution?

---

### Post by elbryan on 2006-06-08
Ok I've solved with simple commands...

I booted with Knoppix and I opened a root shell and I typed "grub".

grub >

ok let's find where grub lies

grub > find /boot/grub/stage1
(hd1,5) --> this in my case.. you, obviously, put in the following lines what you received

grub > root (hd1,5)
grub > setup (hd1,5)

In this way you'll install grub on your partition untouching MBR! 
If you want to overwrite the MBR, don't care about the ",5" simply do

grub > root (hd1)
grub > setup (hd1)

Now I have Windows and Linux working togheter .. Lindows!

---

