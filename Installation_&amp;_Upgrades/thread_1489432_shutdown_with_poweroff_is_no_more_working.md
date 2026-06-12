---
title: "shutdown with poweroff is no more working"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by alterpinguin on 2010-05-21
shutdown with poweroff is no more working
with ubuntu 10.04 
(i did only check the 64bit version)
kernel 2.6.32-22-generic
and with the 64bit-install-live-system 10.04LST
The same hardware can poweroff with ubuntu 9.04
and did it with the first few update versions for 9.10
(i did not check 9.10 to the latest updates).
I still have 9.04 installed, but the easiest way to check
is to use the install-CD.
All those suggestions to use
apic=force
or use no splash
or do a commandline shutdown dont work.
Booting into rescue-mode and using only the console
(thats without x11) does not work too.
The "poweroff" shuts down the harddrives (one can hear
the spin-down) but freezes with the last line
saying "poweroff" after stopping logging, poweroff harddisks,
and so on.
It looks like poweroff is the same like "system halt"
except poweroff of the harddisk.
Doing a "reboot" works.
So for now i do a "system halt" instead of poweroff
and press the power-off-button at the computer.
-
Can anyone please tell working examples? Including which
kernel-version and whether the live-system bootet from
the install-CD 10.04 did work too?
Btw. i used the 10.04 install-CD booting from usb-stick
(made with usb-creator from the iso).

---

### Post by alterpinguin on 2010-05-24
added the output of the poweroff-fail ubuntu 10.04 from
dmesg, lspci, uname
to the bugs launchpad:
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/98790](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/98790)
together with the same outputs
of the working ubuntu 9.04 version(older kernel) on the same computer.
-
If anyone knows a better place, pls. drop a message.

---

### Post by dino99 on 2010-05-24
> **alterpinguin said:**
> added the output of the poweroff-fail ubuntu 10.04 from
dmesg, lspci, uname
to the bugs launchpad:
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/98790](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/98790)
together with the same outputs
of the working ubuntu 9.04 version(older kernel) on the same computer.
-
If anyone knows a better place, pls. drop a message.

this report was opened 3 years ago, no activity and no suscriber, so ...

might use the errors logged and update the kernel to 33, 32 have many issues

---

### Post by alterpinguin on 2010-05-24
> **dino99 said:**
> this report was opened 3 years ago, no activity and no suscriber, so ...

might use the errors logged and update the kernel to 33, 32 have many issues

sorry to ask again,
do you suggest i should open a new bug? I tried to find some already posted bugs about shutdown failing and found this. Here in the forum are some older entries, but no hints about what changed or if there were solutions about it (for ubuntu 10.04).
At the moment i shutdown for reboot and when rebooting press the power-off-button at the computer-case or switch of the power of the power-supply.

---

### Post by dino99 on 2010-05-24
only about the latest 30 days:

[http://www.google.com/search?as_q=shutdown+lucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=shutdown+lucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by alterpinguin on 2010-05-24
> **dino99 said:**
> only about the latest 30 days:

[http://www.google.com/search?as_q=shutdown+lucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=shutdown+lucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

thanks a lot for your help.
i added my logs to the bug
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580867](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580867)

---

### Post by alterpinguin on 2010-06-03
solved the issue for me, like that:
-
there was a new kernel update, so i thought again about trying to shutdown with poweroff, but sadly it did not work too.
```

uname -a
Linux rf-desktop 2.6.32-22-generic #35-Ubuntu SMP Tue Jun 1 14:18:25 UTC 2010 x86_64 GNU/Linux

```

so i looked again for those "funny" acpi settings and kernel-boot-options,
found this site:
> [http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php](http://www.cyberciti.biz/howto/question/static/linux-kernel-parameters.php)
and gave a try to:
```

acpi=oldboot

```
as ONLY option for the boot-kernel - no other things like "quiet" or "splash", only this.
And ? the computer did poweroff like with the old ubuntu 9.04 version.
The last line to see for me was the line with " halted" .. and then everything went off (not only the harddisks-spindown like before ...)
-
this may be "solved" for me, with this kernel-boot-option.
Needless to say, the cpu-throttling is still working ...
and if i will see any other bad results, i will update this posting
and tell whats going wrong.
-

---

