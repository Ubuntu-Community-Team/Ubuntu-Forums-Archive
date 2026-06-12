---
title: "initramfs BusyBox 'Could not load' USB Live bootup error"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by robyholmes on 2010-02-13
Hi,

I have downloaded the latest Ubuntu 9.10 and used 'U904p' a program I had for creating 9.04 live USB I had before. I had 9.04 on the USB pen but thought that 9.10 would be better to install right away rather than upgrading it. So I run through the CLI and make it bootable and all that. I come to put in my pretty old (Spare parts mashed together) Linux box. I get this about 1 minute after the Ubuntu logo and loading bar:

Top of page: WARNING: Couldn't open directory /lib/modules/2.6.31-14-generic: No such file or directory

Then lots of 'FATAL: Could not load /lib/modules/2.6.31-14generic/modules.dep No Such file or directory'

Then I am dumped in to Busybox in initramfs command line.

I have been googling and look around the forums all last night and this morning. I find loads of stuff from 9.04 but not 9.10? I tried the old 'Pull USB pen when Ubuntu log shows' and 'Changed SATA settings' turned them off in end, using IDE.

Could it be that I created it using the old U904p program. I will look in to the newer one. Seen it about on forums. Otherwise any ideas? I am wanting to build a FOG box for imaging all my PC's and trailing it for work.

Thanks a lot
Rob Holmes

---

### Post by robyholmes on 2010-02-13
Just tried with UNetBootin and it did the same errors as above. So the pen drive must be ok. Its the kernel right? Could I install say a older version 8.04 (I know people have said this works) and upgrade? Or would it just show this error on the reboot?

Its only for FOG so it might be worth dropping back to 8.04 and leaving it at that. I will wait for a reply before trying it.

---

### Post by robyholmes on 2010-02-13
Had to install 8.04 in end. But all is now working and FOG is up and running! Great bit of kit FOG, loving it!

---

