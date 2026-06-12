---
title: "Compiz crashes with SIGSEGV after upgrade to 12.04"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by peterdm on 2012-04-26
I just upgraded to 12.04. After reboot, I can't login because compiz crashes with a SIGSEGV (nvidia, x86_64). No workaround. Apparently there are several bug reports about this, some of which a couple of weeks old.

And again, I'm stuck with a broken upgrade. For several releases, Ubuntu stability is in free-fall... If Ubuntu wants to keep their rapidly shrinking user base, they'd better act fast.

With a such a huge bug on release date, at least have the decency to *postpone the release until fixed*!

Peter

---

### Post by sheldonl on 2012-04-26
Same thing happened to me, but both on upgrade and on a fresh install. What video card do you have? I have an nvidia card and I think the crashing started when I installed the nvidia binary drivers.

---

### Post by Cripton on 2012-04-26
I have a nvidia 6100 onboard video card with a nvidia 410 motherboard chipset, and i have the same issue, fresh install in amd64 environment
Final release ubuntu 12.04

---

### Post by Cripton on 2012-04-26
> **sheldonl said:**
> Same thing happened to me, but both on upgrade and on a fresh install. What video card do you have? I have an nvidia card and I think the crashing started when I installed the nvidia binary drivers.

i didnt install the nvidia propietary drivers and crash anyway

---

### Post by Cripton on 2012-04-26
```
cripton@FileServerNew:/etc/X11$ dmesg | grep nvidia
[    8.969690] nvidia: module license 'NVIDIA' taints kernel.
[    9.214824] nvidia 0000:00:05.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[    9.214835] nvidia 0000:00:05.0: setting latency timer to 64
cripton@FileServerNew:/etc/X11$ dmesg | grep NVIDIA
[    0.000000] ACPI: DSDT 000000006fff3180 06274 (v01 NVIDIA AWRDACPI 00001000 MSFT 0100000E)
[    8.969690] nvidia: module license 'NVIDIA' taints kernel.
[    9.216749] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012
cripton@FileServerNew:/etc/X11$ dmesg | grep compiz
[  149.614620] compiz[1620]: segfault at 7ff37c728c00 ip 00007ff3acaa67e5 sp 00007fff06d7bf18 error 4 in libc-2.15.so[7ff3aca15000+1b3000]
[  154.507295] compiz[1970]: segfault at 7f53aaaa1400 ip 00007f53cc6df7e5 sp 00007fff7bb964b8 error 4 in libc-2.15.so[7f53cc64e000+1b3000]

```
hope it helps

---

### Post by SevenThunders on 2012-04-27
I've got the same problem here.  64 bit ubuntu 12.04 and I own an Nvidia gtx 280.  Compiz crashed and I have no unity and no cairo-dock.  I now seriously regret this upgrade.  I hope it can be fixed soon.

---

### Post by kiriath-arba on 2012-04-27
Same issue here, after upgrading from 11.10 to 12.04 with 64-bit Ubuntu.

```
dmesg | egrep 'nvidia|NVIDIA|compiz'
[   17.007844] nvidia: module license 'NVIDIA' taints kernel.
[   17.157793] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 22 (level, low) -> IRQ 22
[   17.157800] nvidia 0000:00:0d.0: setting latency timer to 64
[   17.158060] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012
[   62.706009] compiz[2721]: segfault at 7f3d890bc000 ip 00007f3da7d797e5 sp 00007fff08e65288 error 4 in libc-2.15.so[7f3da7ce8000+1b3000]
[   88.671842] compiz[2860]: segfault at 7f0d48070000 ip 00007f0d66dc27e5 sp 00007fff4256c7f8 error 4 in libc-2.15.so[7f0d66d31000+1b3000]

sudo lshw -class display
[sudo] password: 
  *-display
       description: VGA compatible controller
       product: C61 [GeForce 7025 / nForce 630a]
       vendor: NVIDIA Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:22 memory:de000000-deffffff memory:c0000000-cfffffff memory:dd000000-ddffffff memory:dffc0000-dffdffff
```

Currently, I can still use 12.04 by selecting the "Ubuntu 2D" log-in option.

---

### Post by kiriath-arba on 2012-04-27
Ok, have emailed (all 4,694 lines of) the nvidia-bug-report.log file from my desktop machine to [email]linux-bugs@nvidia.com[/email] as suggested here:
[http://nvidia.custhelp.com/app/answers/detail/a_id/44]("http://nvidia.custhelp.com/app/answers/detail/a_id/44")

Although, the actual shell command in this case is just:

```
sudo nvidia-bug-report.sh
```

---

### Post by LordMikey on 2012-04-27
Same here with C61 [GeForce 6150SE nForce 430]
It worked fine after upgrading until I allowed it to install the proprietary driver.  Now it will only work with 2D.

Another shocker for Ubuntu.  Pretty much every one of their last 4-5 releases has taken me out of action one way or another.  Given the ubiquity of Nvidia graphics cards, how did this whopper make it through to release?

---

### Post by deculpep on 2012-04-27
Same exact problem here. Any tips on disabling autologin so I can change the session to unity 2D?

Found the answer I needed:
From a terminal (ctl+alt+F1 or from SSH)
```
sudo nano /etc/lightdm/lightdm.conf
```
and make your changes, comment autologin out

---

### Post by kiriath-arba on 2012-04-28
Was looking at this question:
[https://answers.launchpad.net/ubuntu/+question/194996]("https://answers.launchpad.net/ubuntu/+question/194996")

Have removed the proprietary nvidia driver for the time being and can now use 12.04 with the standard "Ubuntu" log-in option.

System Settings --> Additional Drivers --> select driver to remove --> Remove

---

### Post by jody.palmer on 2012-04-29
> **kiriath-arba said:**
> Was looking at this question:
[https://answers.launchpad.net/ubuntu/+question/194996]("https://answers.launchpad.net/ubuntu/+question/194996")

Have removed the proprietary nvidia driver for the time being and can now use 12.04 with the standard "Ubuntu" log-in option.

System Settings --> Additional Drivers --> select driver to remove --> Remove

Thanks!  The workaround worked for me.

(I had the same problem... upgrade from 11.10 to 12.04 failed due to compiz dying on a seg fault in libnvidia-glcore.so)

---

### Post by Jvdy on 2012-06-03
press ctrl-alt-F1 and then type: display=:0 compiz --replace then Ctrl-alt-F7  reboot your computer thats work fine for me

---

