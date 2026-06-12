---
title: "Messy Boot Record??"
date: 2019-04-29
forum: Installation &amp; Upgrades
---

### Post by voyto on 2019-04-29
A while back, I had an issue with my Ubuntu Server 16.04 install. I did a clean re-install on the same drive, with a full format during setup.

Since then, I've been unable to remotely reboot as it always selects the wrong boot device, resulting in a blank screen. I can do it locally by going into BIOS and selecting from the boot list. Trying to set the default boot order only works after 1 reboot, then reverts back to the entry that won't load.

My boot list includes....

- UEFI OS (Ubuntu) - This is what it keeps trying to use and doesn't work
- Ubuntu - This works perfectly

Below is a result from my "efibootmgr -v" output in case that helps. Does anyone know how to fix this? Thank you!

```

BootOrder: 0000,0007,0004,0006
Boot0000* ubuntu        HD(1,GPT,1822ea29-de35-4e88-8c0a-1176858326e6,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004  UEFI OS       HD(1,GPT,1822ea29-de35-4e88-8c0a-1176858326e6,0x800,0x100000)/File(\EFI\BOOT\BOOTX64.EFI)
Boot0006  Hard Drive    BBS(HD,,0x0)..GO..NO........O.H.i.t.a.c.h.i. .H.D.P.7.2.5.0.5.0.G.L.A.3.6.0................>..Gd-.;.A..MQ..L. . . . . . .E.G.5.A.4.3.F.R.4.2.Y.5.A.D.......BO..NO........O.T.O.S.H.I.B.A. .D.T.0.1.A.C.A.3.0.0................>..Gd-.;.A..MQ..L. . . . . . . . . . .4. .K.3.B.N.L.E.S.G.......BO..NO........O.S.T.8.0.0.0.D.M.0.0.4.-.2.C.X.1.8.8................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .C.Z.0.T.C.7.C.C.......BO..NO........O.W.D.C. .W.D.3.0.E.Z.R.Z.-.0.0.Z.5.H.B.0................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.4.C.1.N.C.R.K.Z.K.C.......BO..NO........O.S.A.M.S.U.N.G. .H.D.1.0.3.S.J................>..Gd-.;.A..MQ..L.2.S.6.4.9.J.Z.C.1.B.5.4.7.0. . . . . . .......BO..NO........O.W.D.C. .W.D.3.0.E.Z.R.Z.-.0.0.Z.5.H.B.0................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.4.C.2.N.X.L.2.J.N.L.......BO
Boot0007* ubuntu        HD(1,GPT,1822ea29-de35-4e88-8c0a-1176858326e6,0x800,0x100000)/File(\EFI\Ubuntu\grubx64.efi)

```

---

### Post by oldfred on 2019-04-29
You show ubuntu as first boot entry.
Is your UEFI then changing boot order?
What brand/mode system?
Some only want to boot fallback/hard drive entry at /EFI/Boot/bootx64.efi.
Some with HP have found UEFI update then allows system to work.

Have you tried copying /EFI/ubuntu/shimx64.efi to /EFI/Boot and rename to bootx64.efi. (backup current bootx64.efi, but if from Windows it will not be useful).

---

### Post by voyto on 2019-04-30
> **oldfred said:**
> You show ubuntu as first boot entry.
Is your UEFI then changing boot order?
What brand/mode system?
Some only want to boot fallback/hard drive entry at /EFI/Boot/bootx64.efi.
Some with HP have found UEFI update then allows system to work.

Have you tried copying /EFI/ubuntu/shimx64.efi to /EFI/Boot and rename to bootx64.efi. (backup current bootx64.efi, but if from Windows it will not be useful).

I set and save the boot order, also disabling all other drives. After reboot, the BIOS reverts back to UEFI being to of the list and it fails to boot.
It's an ASUS B85M-G board.
I'll try that suggestion later on - would that mean I can leave UEFI at the top of the list and it will boot correctly?

---

### Post by oldfred on 2019-04-30
Have you updated UEFI from Asus?
It should not be changing boot order.
I have an Asus Z97 and it does not change order. Probably similar UEFI.

Yes if you make the fallback or hard drive default boot entry bootx64.efi really be a copy of shimx64.efi, then that entry will also boot Ubuntu.
The /EFI/Boot/bootx64.efi is the standard boot entry for all external devices regardless of vendor. But UEFI added that as a fallback entry to boot internal devices.

---

