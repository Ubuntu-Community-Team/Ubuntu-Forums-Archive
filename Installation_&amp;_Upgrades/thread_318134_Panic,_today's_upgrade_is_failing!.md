---
title: "Panic, today's upgrade is failing!"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by ildella on 2006-12-13
During the upgrade of today's security updates, the update manager hanged up. So I went to terminal:

della@della-desktop:~$ sudo apt-get upgrade 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

as you like:

--- output begins here ---

della@della-desktop:~$ sudo dpkg --configure -a
Setting up linux-libc-dev (2.6.17.1-10.34) ...
Setting up linux-image-2.6.17-10-386 (2.6.17.1-10.34) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-386

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000] Oops: 0002 [#2]

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000] CPU:    0

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000] EIP is at ext3_readpage+0x1/0x10 [ext3]

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000] eax: d9e67180   ebx: 00000000   ecx: f8963620   edx: c1100b80

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000] esi: c1100b80   edi: d862178c   ebp: 00000efa   esp: c49a9dfc

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000] Process amarokapp (pid: 13465, threadinfo=c49a8000 task=d2b93030)

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000] Stack: c013c80e 000000d0 00000001 00000efa 00000000 d9e67180 d9e671c4 d86216f0 

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000]        00000f7f 00000800 00000efb 00000efb 00000f04 00f80000 00000000 00000000 

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000]        00000f04 00000800 00000000 00000000 00000001 00000000 00000efa 00000000 

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000] Call Trace:

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000]  <c013c80e> do_generic_mapping_read+0x4ae/0x540  <c013d21d> __generic_file_aio_read+0xfd/0x230

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000]  <c013bb30> file_read_actor+0x0/0xf0  <c013d395> generic_file_aio_read+0x45/0x60

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000]  <c01581e4> do_sync_read+0xc4/0x100  <c012a640> autoremove_wake_function+0x0/0x50

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000]  <c02c6228> mutex_lock+0x8/0x20  <c0158db5> generic_file_llseek+0x55/0xd0

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000]  <c0158c9c> vfs_read+0xbc/0x180  <c0158120> do_sync_read+0x0/0x100

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000]  <c0159101> sys_read+0x41/0x70  <c0102dbb> sysenter_past_esp+0x54/0x79

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000] Code: 00 02 eb b5 8d b6 00 00 00 00 89 d0 89 ca 8b 4c 24 04 c7 44 24 04 80 71 94 f8 e9 0b 4e 83 c7 8d 74 26 00 8d bc 27 00 00 00 00 89 <d0> ba 80 71 94 f8 e9 d4 48 83 c7 8d 74 26 00 83 ec 14 89 5c 24 

Message from syslogd@localhost at Wed Dec 13 21:00:36 2006 ...
localhost kernel: [17183889.528000] EIP: [pg0+944583377/1069069312] ext3_readpage+0x1/0x10 [ext3] SS:ESP 0068:c49a9dfc
dpkg: error processing linux-image-2.6.17-10-386 (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Setting up mdadm (2.4.1-6ubuntu5.2) ...
update-initramfs: Generating /boot/initrd.img-2.6.17-10-386

--- output ends here ---

Well, as you can see after some minutes I give a stop signal (CTRL-C), the update process try to continue but it stops at that point. 

So, I fear to reboot! 

I have a ubuntu edgy, up to date till yesterday with beryl up and running with no problems. System is an AMD 64, kernel is i386, latest nvidia driver on a 6600GT... something else?

What can I try to do? 

Thanks.

---

