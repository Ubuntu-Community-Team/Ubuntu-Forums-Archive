---
title: "SSD installs for Lucid working?"
date: 2009-12-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2009-12-26
Hi,

I can't seem to get Kubuntu Lucid daily build live image (Dec 25) to install on my new Crucial M225 128 GB SSD with current 1819 firmware. I've got past other known issues like boot to login prompt (user perm issue), or nvidia card (nv) not working (select vesa) etc.

The installer progresses past installing grub then seems to get stuck at "running update-grub" for reeeaaallly loooong time...

(Win 7 RC and Fedora 12 are running smooth enough on this disk)

I know there is an existing bug for Karmic which may be related - [lpbug]445852[/lpbug]

What can I do to confirm and report this issue so that Alpha 2 may be good to go? Which logs etc to look into and what to search for in the bug DB for existing issues?

---

### Post by vishalrao on 2009-12-26
Doh. I tried again and it seemed to have worked (just needed to wait 7 min for update-grub to complete)...

Pasting output of "dmesg | grep ata1" anyway just for info...

[http://pastebin.ubuntu.com/347122/](http://pastebin.ubuntu.com/347122/)

Am running the Dec 25 daily live image of Kubuntu Lucid :)

---

### Post by andrewabc on 2009-12-26
I hope 7 minutes to update GRUB doesn't become the norm.

They havn't even fixed [Current grub-pc takes several minutes to show menu](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933) bug from Karmic. Is it fixed for Lucid? Takes longer for GRUB to show up than it does for my OS to load.

---

### Post by ranch hand on 2009-12-26
I am in Ubuntu and  I can say that I have no problem with Grub at all.  Comes up fast, a little more lag than I would like in going to black screen but not bad at all.

I do not have a long update time at all.  You need to keep in mind that my scripts quit running at 09_custom so that speeds things up a bit.  If your lag is in 30_os-prober remember that is not a grub program.

---

### Post by vishalrao on 2009-12-26
grub2 fine for me too but i just have the single disk :)

i hope the ssd ata errors are fixed soon, i want to enjoy super fast bootup and general sweetness!

---

### Post by Eclipse. on 2009-12-27
> **andrewabc said:**
> I hope 7 minutes to update GRUB doesn't become the norm.

They havn't even fixed [Current grub-pc takes several minutes to show menu](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933) bug from Karmic. Is it fixed for Lucid? Takes longer for GRUB to show up than it does for my OS to load.

Upstream bug report says its fixed.:)

[http://savannah.gnu.org/bugs/?27900](http://savannah.gnu.org/bugs/?27900)

---

### Post by andrewabc on 2009-12-27
> **Eclipse. said:**
> Upstream bug report says its fixed.:)

[http://savannah.gnu.org/bugs/?27900](http://savannah.gnu.org/bugs/?27900)

Thanks for the update!

It even says fix committed at the bug I posted that you quoted.
Better make it into 9.10!

---

### Post by Eclipse. on 2009-12-27
> **andrewabc said:**
> Thanks for the update!

It even says fix committed at the bug I posted that you quoted.
Better make it into 9.10!

I changed that. :)

Since its fixed upstream but not in ubuntu yet or a upstream release it gets that status.

---

### Post by vishalrao on 2010-01-01
I've filed [lpbug]502219[/lpbug] ...

Anyone with an SSD care to check your dmesg/logs for silent ATA errors (I get these errors during bootup which seems to slow the process) and add to or confirm the bug?

---

### Post by vishalrao on 2010-01-16
Update for bug [lpbug]502219[/lpbug] : Still have the same problems after installing Kubuntu Lucid Alpha 2 and also updating my firmware from 1819 to 1916 which includes active GC along with TRIM which works great (resolves perf issues) with Windows 7 RC.

Is there not anyone else on the forums using SSDs and do you not have any issues or is it just me? Note that I've been having the same/similar problems with other stable distros including Ubuntu 9.10, Fedora 12, OpenSUSE 11.2 and Arch.

---

### Post by farrell on 2010-01-16
I've just installed Ubuntu Lucid Alpha 2 on an Intel X25-M (Postville, 80GB) without any issues. Installation and Grub-setup were really fast. I don't know if this is still relevant, but here are my ata1-related messages (which seem to be the same for Ubuntu Karmic):

```

$ dmesg | grep ata1
[    0.752665] ata1: SATA max UDMA/133 abar m2048@0xf2926000 port 0xf2926100 irq 27
[    1.100069] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.100592] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.100597] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.100602] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.100880] ata1.00: ATA-7: INTEL SSDSA2M080G2GC, 2CV102HA, max UDMA/133
[    1.100884] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.101474] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.101479] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.101483] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.101789] ata1.00: configured for UDMA/133
[    1.120782] ata1.00: configured for UDMA/133
[    1.120791] ata1: EH complete

```

---

### Post by vishalrao on 2010-01-16
Thanks a lot farrell ! Looks like its a problem just with my disk (your logs look normal to my untrained eye at least) and I hope its just not my disk itself but all of the same models :D

I will update the bug and also post on the company forums, although I wonder why Win7 has appeared (cant seem to locate any error message or even notice any slowdowns/freezes) to be working smoothly since I got this SSD.

edit: Is there anything I can do to help diagnose/investigate the problem?

edit2: Anyone else with IndiLinx controller based SSDs around these parts? :)

---

### Post by andrewabc on 2010-01-16
I have 60gb ocz vertex firmware 1.3

Sorry but I won't be testing bug as I don't want to mess with my working OS (9.10) or fragment SSD since I havn't updated firmware to 1.41.

Does same thing happen under VM? I could test that.

---

### Post by vishalrao on 2010-01-16
No worries. Nope, it doesnt happen under a VM (but I've only run Vbox on Win7 so far)...
But I'm assuming it should be fine for you since 9.10 would give me errors too but you seem to be okay?

---

### Post by k64 on 2010-01-16
My Acer Aspire One has an 8GB SSD. When I upgraded from Karmic to Lucid, it ran just fine. I suggest, on an SSD, to install Karmic first, and then upgrade to Lucid.

---

### Post by vishalrao on 2010-01-19
OK I think I know what's happening and I've fixed my issue!

I should have figured this out sooner but the problem is/was NCQ not SMART.

I did a web search for "failed command READ FPDMA QUEUED" and saw some references to NCQ, SSDs and all that jazz.

So all I need to do is pass the linux kernel boot paramter along with the existing (unrelated) parameters "quiet splash" like:

```

quiet splash libata.force=noncq

```

Intel does NCQ support right for sure. And OCZ is apparently blacklisted already in the code it looks like that is why the above folks dont get this error.

The place to backlist in linux kernel (.32 series) libata source would be drivers/ata/libata-core.c around line 4252 with the existing OCZ ata_blacklist_entry item:

```

{ "CRUCIAL_CT128M225", NULL, ATA_HORKAGE_NONCQ },

```

This blacklist just the 128 GB model which I have, I'm guessing the 64 and 256 models also need blacklisting with their own ID strings. I guess you pass NULL for the firmware version string so it blacklists all of them.

I will post this info on the Crucial.com forums and also on the bug and see what happens from there.

Not sure if this should be fixed by blacklisting these Crucial M225 models in the libata linux kernel source or it should be fixed by Crucial in perhaps a new model and/or BIOS update.

I hope Ubuntu devs might get this into the .32 kernel released with Lucid to avoid headaches for other Crucial SSD users.

---

