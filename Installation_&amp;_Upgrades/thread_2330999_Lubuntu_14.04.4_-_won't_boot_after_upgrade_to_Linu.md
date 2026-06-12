---
title: "Lubuntu 14.04.4 - won't boot after upgrade to Linux kernel 3.16.0-77"
date: 2016-07-17
forum: Installation &amp; Upgrades
---

### Post by Tucker_Cahooter on 2016-07-17
Hi. I just let my computer (Toshiba Satellite laptop based on AMD A6-5200 APU) install the latest security fixes. When I rebooted a whole swag of error messages appeared and then the system failed to boot (I couldnt catch the error messages). I did a hard reboot and selected the previous kernel (3.16.0-76) and it booted fine. So it appears that something in Linux kernel 3.16.0-77 (which I gather was released a few days ago) breaks with my system. I looked in /var/log but since I was able to boot ok all the log files looked ok (I am just a general user so let me know if there is somewhere else I should be looking for details). Anyone able to shed some insight into this or also having this problem?

---

### Post by Bashing-om on 2016-07-17
Tucker_Cahooter; Hello;

Many times we see this condition as the result of a broken proprietary graphic's driver; the driver built on the old kernel.
Can you boot to terminal (ctl+alt+F1 at the login screen) ?
If so we can prosecute this as a driver issue, perhaps all that is required is to re-install the driver in the current kernel.


maybe yes,
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by Tucker_Cahooter on 2016-07-19
Thanks for that. Yes I am able to boot to terminal using the newer kernel version. If there is anything you would like me to try to assist in identifying the cause of the problem, please let me know.

---

### Post by Bashing-om on 2016-07-19
Tucker_Cahooter; Yeah ;

> **Tucker_Cahooter said:**
> Thanks for that. Yes I am able to boot to terminal using the newer kernel version. If there is anything you would like me to try to assist in identifying the cause of the problem, please let me know.

Now we can get somewhere.

What does X's log file relate :
As you are in a minalistic terminal and can not copy paste, let's post that file to a pastebin
```

cat /var/log/Xorg.0.log | nc termbin.com 9999

```
Where the result is a URL back in terminal.
Pass that complete link back here and we access that file and see what the story is.
We see what the hardware is and if a driver for the hardware got built .

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by jeremy31 on 2016-07-19
Is secure boot enabled on the computer?  It seems that Canonical is enforcing secure boot rules in the latest kernels and that will cause issues with unsigned modules

---

### Post by Tucker_Cahooter on 2016-07-24
Sorry for the delay in replying, been busy with other things. Yes secure boot is enabled on the computer. 

What I have found so far is that when I removed fglrx-updates et al and reverted to fglrx that the system wouldn't boot to the older kernel version either. So I purged fglrx entirely and I am able to boot successfully using the latest kernel. 

I can access the Xorg.0.log file now but it is huge so if there is any particular part that is of interest let me know.

---

