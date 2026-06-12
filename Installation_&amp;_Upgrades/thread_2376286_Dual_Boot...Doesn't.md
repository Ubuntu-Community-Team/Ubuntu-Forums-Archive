---
title: "Dual Boot...Doesn't"
date: 2017-11-01
forum: Installation &amp; Upgrades
---

### Post by sccjono on 2017-11-01
Hello all,

Up until now I have had Ubuntu installed on a laptop as the only OS, but I have just bought a new laptop that came with Windows 10 and I wanted to set it up to allow the choice of which OS to boot via Grub. It was perhaps complicated slightly by the fact the Windows system has a separate recovery partition, but I followed the instructions that I found online. The problem I have is that unless I interrupt the boot and select the Ubuntu boot manager manually (which displays Grub with both boot options as expected) it boots in to Windows with no Grub menu being displayed.

I have tried looking in BIOS but whilst I see both boot managers being listed I don't see an option to change the order. Can anyone please help? I can't always be interrupting the boot, it defeats the object.

Can I please ask you assume a complete novice when you answer as I am no Linux expert. Thanks.

jono

---

### Post by yancek on 2017-11-01
Boot Ubuntu and open a terminal and run the following command to verify that you are using UEFI (or not) and post the results here.

```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
```

If it displays the message "EFI boot on HDD", then run the following command and post the  output here again:

```
sudo efibootmgr
```

Someone should then be able to give you the command to set the Ubuntu entry with both windows/Ubuntu entries first priority.

---

### Post by oldfred on 2017-11-01
What brand/model system.

Some violate UEFI standard that says NOT to use description as part of UEFI boot.
And of course they made the only valid description "Windows Boot Manager".
Multiple work arounds depending on how you boot.

This should work if UEFI standards followed.
Check current order & hex number of each entry:
sudo efibootmgr -v
       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok. An example making 0002 first:
sudo efibootmgr -o 2,1
see also 
man efibootmgr

You should also be able to boot into UEFI and change boot order there.

---

### Post by sccjono on 2017-11-01
Thank you yancek. This is the output I get from your commands.

```

jono@htl1:~$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
EFI boot on HDD
jono@htl1:~$ sudo efibootmgr
[sudo] password for jono: 
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,3001,0002,2001,2002,2004
Boot0001* Windows Boot Manager
Boot0002* ubuntu
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot3001* Internal Hard Disk or Solid State Disk

```

---

### Post by sccjono on 2017-11-01
> **oldfred said:**
> What brand/model system.

Sorry, I should have said. This is a vanilla install of Ubuntu 17.10 on a HP 17 N3710.

> This should work if UEFI standards followed.
Check current order & hex number of each entry:
sudo efibootmgr -v
       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok. An example making 0002 first:
sudo efibootmgr -o 2,1
see also 
man efibootmgr

You should also be able to boot into UEFI and change boot order there.

OK, I'm a little bit lost here sorry. your first command give me
```
jono@htl1:~$ sudo efibootmgr -vBootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,3001,0002,2001,2002,2004
Boot0001* Windows Boot Manager	HD(1,GPT,4da41e38-f576-4113-b8a2-3797c28b298a,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...}................
Boot0002* ubuntu	HD(1,GPT,4da41e38-f576-4113-b8a2-3797c28b298a,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot3001* Internal Hard Disk or Solid State Disk	RC
```

What would you suggest for the next command?

Thanks
jono

---

### Post by sccjono on 2017-11-01
Ah no sorry ignore me. I re-read your advice and understood it better. It worked! Thank you both so much, I really appreciate it.

jono

---

