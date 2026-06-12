---
title: "Ubuntu 20.04 fails to power - off"
date: 2020-12-03
forum: Installation &amp; Upgrades
---

### Post by gin-cognac on 2020-12-03
Basic system - SSD with operating system and files +HDD for bulk storage.
Ubuntu 18.04 been working happily.
Ungraded from 18.04 to 20.04 went smoothly - no changes to hardware system.
**Power off > restart**  no problem.
**Power off > Power off ** hangs. 
System commands have no effect so I guess the processor has closed down. error messages vary but most common are: 
                        
 [COLOR=#b22222]usb 1-9: hub failed to enable device, error -108  [/COLOR]
[COLOR=#b22222]usb 1-9: hub failed to enable device, error -108  [/COLOR]
[COLOR=#b22222]usb 1-9: device not accepting address 5, error -108  [/COLOR]
[COLOR=#b22222]usb 1-9: device not accept ing address 5, error -108  [/COLOR]
[COLOR=#b22222]usb usbi-port9: couldn't allocate usb_device  [/COLOR]
[COLOR=#b22222]sr 2:0:0:0: tag#19 timing out command, waited 120s  [/COLOR]
[COLOR=#b22222]INFO: task systemd-shutdow:1 blocked for more than 120 seconds.  [/COLOR]
[COLOR=#b22222]         Not tainted 5.4.0-54-generic #60-Ubuntu  [/COLOR]
[COLOR=#b22222]&#8220;echo 0> /proc/sys/kernel/hung_task_timeout_secs" disables this message  [/COLOR]
[COLOR=#b22222]Call Trace:  [/COLOR]
[COLOR=#b22222]__schedule+0x2e3/0x740  [/COLOR]
[COLOR=#b22222]schedule+0x42/0xb0  [/COLOR]
[COLOR=#b22222]schedule_timeout+0x10e/0x160  [/COLOR]
[COLOR=#b22222]wait_for_completion+0xb1/0x120  [/COLOR]
[COLOR=#b22222]? wake_up_q+0x70/0x70  [/COLOR]
[COLOR=#b22222]f lush_workqueue+0x135/0x420  [/COLOR]
[COLOR=#b22222]acp1_os_wait_events_complete+0x31/0x40  [/COLOR]
[COLOR=#b22222]acpi_power _off _prepare+0x1d/0x20  [/COLOR]
[COLOR=#b22222]kerne1_power _off +0x46/0x70  [/COLOR]
[COLOR=#b22222]_.do_sys_reboot+0x121/0x210  [/COLOR]
[COLOR=#b22222]? vfs_writev+0xc3/0xf0  [/COLOR]
[COLOR=#b22222]? do_writev+0x71/0x120  [/COLOR]
[COLOR=#b22222]_--x64_sys_reboot+0x1e/0x20  [/COLOR]
[COLOR=#b22222]do_syscal1_64+0x57/0x190  [/COLOR]
[COLOR=#b22222]entry_SYSCALL_64_after _hwframe+0x44/0xa9  [/COLOR]
[COLOR=#b22222]RIP: 0033:0x7f 1b616e5467  [/COLOR]
[COLOR=#b22222]Code: Bad RIP value.  [/COLOR]
[COLOR=#b22222]RSP: 002b:00007ffc23820138 EFLAGS: 00000202 ORIG_RAX: RAX: fff FFF FFFFFff fda RBX: OO0DDDD00000000D RCX: 00007f1b816e5487 RDX: 000000004321fedc RSI: 0000000026121969 RDI: c0000000feeidead RBP: 0000000000000000 ROB: 0000000000000020 ROS: 00007ffc2381f540 R10: 00007 1b60830900 R11: 0000000000000202 R12: 0000000000000000 R13: 0000000000000000 R14: 0000001b00000004 R15: 0000000000000000  [/COLOR]
[COLOR=#b22222]sr 2:0:0:0: tag#9 timing out command, waited 120s  [/COLOR]
  [COLOR=#a52a2a]
[/COLOR][COLOR=#000000]Repeats 

Any suggestions Please
[/COLOR]

---

