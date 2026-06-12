---
title: "'panic occurred, switching back to text console'"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by CCoder on 2011-04-30
hello dear Ubuntu fans,

Before all of this I was running Fedora. & all was fine. but sometime after some improper shutdowns (battery was not enough & the computer shutdown itself), Fedora showed some pop-ups about "An hard disk may be failing."

Some time after that I got those errors at boot-up as a BIOS-function. (Sony VAIO VPCEB2Z1E)
So it had nothing to do with Fedora.

Fedora had become EXTREMELY slow.

But now when I try to install Ubuntu 11.04. There is kernel error.
[INDENT]Kernel panic-not syncing attempted to kill init
...
panic occurred, switching back to text console[/INDENT]

This is like this after selecting Direct Install & also after selecting 'Try Ubuntu without installing.'

This thing is driving me nuts.!!

Any help would be really appreciated... :(

[IMG]http://i52.tinypic.com/2jfvcx.jpg[/IMG]

---

### Post by CCoder on 2011-04-30
I am now dowloading the Alternate installer & trying it that way.
The version I USED was DesktopAMD64.

---

### Post by dino99 on 2011-04-30
its often happening with some chipsets, try an other cold boot

or run : sudo initramfs -u -k

---

### Post by CCoder on 2011-04-30
I do not understand I'm sorry. Another cold boot?

---

### Post by dino99 on 2011-04-30
> **CCoder said:**
> I do not understand I'm sorry. Another cold boot?

cold boot = you switch power off from psu, then power on again (wait a few seconds) and boot again

---

### Post by CCoder on 2011-04-30
So, considering, I'm doing this on a laptop... I remove the power cord & that's it. Or is there some sort of switch inside the computer?

---

### Post by dino99 on 2011-04-30
only use the "power" button

---

### Post by CCoder on 2011-04-30
Already done that.
No change.

---

### Post by dino99 on 2011-04-30
try to boot in recovery mode ("shift" key down at bios end process to get grub menu) then select "repair packages"

---

### Post by CCoder on 2011-04-30
no change :(

---

### Post by CCoder on 2011-04-30
i am going to install ubuntu this evening via the alternate installer & via RJ45 network (not via wifi)... just need to get some cables. no rj45's lying around in the house

---

### Post by Soulflare3 on 2011-05-12
Hey

I am actually having a similar error but it produces the same result.

```
[  937.850009]  [<ffffffff8106b42a>] ? alarm_setitimer+0x3a/0x60
[  937.850009]  [<ffffffff81076d2e>] ? sys_alarm+0xe/0x20
[  937.850009]  [<ffffffff8100c002>] ? system_call_fastpath+0x16/+0x1b
[  937.850009] Code:  Bad RIP value.
[  937.850009] RIP  [<          (null)>]            (null)
[  937.850009]  RSP <ffff8800750a9c08> 
[  937.850009] CR2: 0000000000000000
[  937.850009] ---[ end trace 21b49d485c324d37 ]---
[  937.850009] Kernel panic - not syncing: Fatal exception in interrupt
[  937.850009] Pid: 9948, comm: rs:main Q:Reg Tainted: G       D     2.6.38-8-generic #42-Ubuntu
[  937.850009] Call Trace:
[  937.850009]  [<ffffffff815bfece>] ? panic+0x91/0x19c
[  937.850009]  [<ffffffff815c41ca>] ? oops_end+0xea/0xf0
[  937.850009]  [<ffffffff810404ad>] ? no_context+0xfd/0x190
[  937.850009]  [<ffffffff81040665>] ? __bad_area_nosemaphore+0x125/0x1e0
[  937.850009]  [<ffffffff81127a95>] ? __inc_zone_page_state+0x35/0x40
[  937.850009]  [<ffffffff81040733>] ? bad_area_nosemaphore+0x13/0x20
[  937.850009]  [<ffffffff815c6ced>] ? do_page_fault+0x44d/0x540
[  937.850009]  [<ffffffff811230f7>] ? shmem_getpage+0x2d7/0x920
[  937.850009]  [<ffffffff81117c6d>] ? update_page_reclaim_stat+0x2d/0x70
[  937.850009]  [<ffffffff8110c18a>] ? unlock_page+0x2a/0x40
[  937.850009]  [<ffffffff815c34d5>] ? page_fault+0x25/0x30
[  937.850009]  [<ffffffff8104dde6>] ? enqueue_task+0x66/0x80
[  937.850009]  [<ffffffff8104de2e>] ? activate_task+0x2e/0x40
[  937.850009]  [<ffffffff8105f438>] ? try_to_wake_up+0x1d8/0x3e0
[  937.850009]  [<ffffffff8105750e>] ? entity_tick+0x6e/0x150
[  937.850009]  [<ffffffff81074e00>] ? process_timeout+0x0/0x10
[  937.850009]  [<ffffffff8105f675>] ? wake_up_process+0x15/0x20
[  937.850009]  [<ffffffff81074e0e>] ? process_timeout+0xe/0x10
[  937.850009]  [<ffffffff81074964>] ? call_timer+0x44/0x130
[  937.850009]  [<ffffffff81074e00>] ? process_timeout+0x0/0x10
[  937.850009]  [<ffffffff81075fb4>] ? run_timer_softirq+0x134/0x280
[  937.850009]  [<ffffffff8102c85d>] ? lapic_next_event+0x1d/0x30
[  937.850009]  [<ffffffff8106d538>] ? __do_softirq+0xa8/0x1c0
[  937.850009]  [<ffffffff810983ef>] ? tick_program_event+0x1f/0x30
[  937.850009]  [<ffffffff8100cf1c>] ? call_softirq+0x1c/0x30
[  937.850009]  [<ffffffff8100ea45>] ? do_softirq+0x65/0xa0
[  937.850009]  [<ffffffff8106d755>] ? irq_exit+0x85/0x90
[  937.850009]  [<ffffffff815cafb0>] ? smp_apic_timer_interrupt+0x70/0x9b
[  937.850009]  [<ffffffff8100c9d3>] ? apic_timer_interrupt+0x13/0x20
[  937.850009]  [<ffffffff8106ac97>] ? spin_unlock_irq+0x17/0x20
[  937.850009]  [<ffffffff8106ac8e>] ? spin_unlock_irq+0x1b4/0x210
[  937.850009]  [<ffffffff8106b394>] ? do_setitimer+0x1b4/0x210
[  937.850009]  [<ffffffff8106b42a>] ? alarm_setitimer+0x3a/0x60
[  937.850009]  [<ffffffff81076d2e>] ? sys_alarm+0xe/0x20
[  937.850009]  [<ffffffff8100c002>] ? system_call_fastpath+0x16/+0x1b
[  937.850009] panic occurred, switching back to text console
```

Once this error is displayed, different things happen. One time my WiFi control button's LED flashed, another my caps lock key's LED started blinking. Usually the computer will freeze, and the only thing you can do is kill the power. [pc: Compaq Presario CQ62-219WM, 64-bit Intel Celeron 900 processor]

I have downloaded the iso twice (ubuntu-11.04-desktop-amd64.iso) and the same thing happens every time I boot. I can get the install to start, but about 35ish minutes into the install,  (about 65-70%) this happens. Every time. I have tried like 5 or 6 times.

I am going to try the Ubuntu-10.04.1-desktop-amd64.iso and see if that works... 

Have you yet tried the alternate for 11.04? I am trying the older one just to be sure (skipping alternate).

I am wondering if this is a problem with the amd64 version of 11.04?

---

### Post by Soulflare3 on 2011-05-17
Ok, so I finally got Ubuntu 11.04 64-bit installed. This should help you as well.

First, I installed Ubuntu 10.04 LTS 64-bit. I installed a few apps (Opera, Filezilla, etc) then decided to update. After the update, it lets you upgrade to Ubuntu 10.10. I did this, and when I logged back in, I got a message saying that I could now upgrade to 11.04. I just finished that upgrade, and it is running great. I am guessing there is a problem with the ISO file on the main Ubuntu website...

Note: while upgrading from 10.04 to 10.10, my screen went black, and all I could see was the pointer. There was NO disk activity whatsoever. If you encounter this problem, turn off your computer. Turn it back on, and when you get to the GRUB screen, choose the most recent linux, but instead of the normal, hit the recovery one. When the menu comes up, select the option dpkg, and let it run. The install will pick up as if it never stopped. Simple restart and it was good to go.

Good luck!

---

### Post by callmechakri on 2011-07-06
Hey People.. Any Solution for **Ccoder** issue apart from trying to get the upgrades from one version to another.??(Upgrade from one version to another is really another pain in the neck)
I am trying to install Ubuntu 11.04 directly by booting with a CD. I have rebooted the machine like 5 times still same error. 

I am stuck with same error as Ccoder.

[I][  342.604509] Kernel Panic - not syncing: Attempted to kill init!
[  342.604531] Pid: 1, comm:run-init Not tainted 2.6.38-8-generic #42-Ubuntu
[  342.604541] Call Trace:
[  342.604561]  [<ffffffff815bfece>] ? panic+0x19c
[  342.604573] [<ffffffff81069ac3>] ? forget_original_parent+0x263/0x270
[  342.604584] [<ffffffff81069aeb>] ? exit_notify+0x1b/0x180
[  342.604596] [<ffffffff810133af>] ? flush_ptrace_hw_breakpoint+0x1f/0x40
[  342.604607] [<ffffffff8106a4b3>] ? do_exit+0x1d3/0x410
[  342.604619] [<ffffffff81165111>] ? sys_write+0x51/0x90
[  342.604628] [<ffffffff8106a847>] ? sys_exit+0x17/0x20
[  342.604637] [<ffffffff8100c002>] ? system_call_fastpath+0x16/0x1b
[  342.604659] panic occured, switching back to text console[/I]


I am kind of not interested in upgrading from one version to another since my current version is Ubuntu 9.10.

Any help is highly appreciated....

---

### Post by Soulflare3 on 2011-07-06
I think there is something wrong with the 64-bit iso file. The only way I was able to get ubuntu to update was to install the old one and update through the update manager. I do have to say though, a few hours after upgrading to 11.04, I downgraded back to 10.10. There were a lot of compatibility issues (especially with compiz) and everything was focused on app icons like for an ipod. I didn't like it.


I have downloaded the amd64.iso 2 or 3 times, and gotten the same results every time. It will run from the cd (live) but will not install. It always gets an error, and then just sits there.


I'm sticking with 10.10 :/

---

### Post by CCoder on 2011-07-07
i'm sticking with the 10.10 version as well. 11.04 doesn't play well with my computer, imo.

---

### Post by pro_mvb on 2011-11-26
hi.
I have dwa525 wireless card,
I installed driver rt3562.
my wireless card found any network (with wcid) but when i want to connect my access point,show me the full black page(like dos) and then computer freez.
in black page i see this error:
```

kernel panic not syncing fatal exception

```
and end of lines i see :
```

panic occurred, switching back to text console

```

:(:(
how solve this problem?
(sry i cant speak english well:lolflag:)

---

### Post by thanigaivelan19 on 2012-03-30
Hi,

I am getting this error 

Kernel Panic - not syncing: fatal exception in interupt

panic occurred, switching back to text console


Please help me

Thanks

Thanigaivelan

---

### Post by MissRudaKropka on 2013-02-03
Hi, I just had the same error message plus additional faults with the graphics. I hope it is only the 12.04 64bit version. I'm going to try the 12.10 32 bit and see if it helps. fingers crossed!

---

### Post by oldos2er on 2013-02-03
If you have further questions please start a new thread, this one's fairly old.

---

