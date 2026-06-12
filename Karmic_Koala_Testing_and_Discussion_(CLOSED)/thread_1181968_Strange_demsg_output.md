---
title: "Strange demsg output"
date: 2009-06-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cariboo on 2009-06-08
When I run dmesg, I get the following output at the very end:

```
21.591534] IRQ 18/nvidia: IRQF_DISABLED is not guaranteed on shared IRQs
[   26.720926] Too big adjustment 32
[   26.834021] Too big adjustment 32
[   26.849893] Too big adjustment 32
[   26.876237] Too big adjustment 32
[   26.890959] Too big adjustment 32
[   26.905797] Too big adjustment 32
[   26.932403] Too big adjustment 32
[   26.993970] Too big adjustment 32
[   27.009791] Too big adjustment 32
[   27.036153] Too big adjustment 32
[   27.097976] Too big adjustment 32
[   27.113791] Too big adjustment 32
[   27.140216] Too big adjustment 32
[   27.202330] Too big adjustment 32
[   27.218027] Too big adjustment 32
[   27.245345] Too big adjustment 32
[   27.310066] Too big adjustment 32
[   27.325800] Too big adjustment 32
[   27.352008] Too big adjustment 32
[   27.413967] Too big adjustment 32
[   27.429797] Too big adjustment 32
[   27.457278] Too big adjustment 32
[   27.473825] Too big adjustment 32
```

The only problem I seem to have is every once in a while the monitor will go into sleep mode while I'm using the computer, it goes all the way to where the monitor displays:

```
Power Saving Mode
```

by moving the mouse everything comes back the way it should.

I'm using the 180.44 driver.

Has anyone else run into this problem?

---

### Post by super.rad on 2009-06-08
Yeah started getting this problem recently, using ATI HD3200 card with radeon drivers so obviously not an issue with the drivers.
EDIT: Forgot to say I'm also getting the asme dmesg output

---

### Post by Didius Falco on 2009-06-08
I'm not getting it in dmesg, but I am getting it in kern.log
```
Jun  7 23:08:56 John kernel: [   77.612793] Too big adjustment 32
Jun  7 23:08:56 John kernel: [   77.630434] Too big adjustment 32
Jun  7 23:08:56 John kernel: [   77.645050] Too big adjustment 32
Jun  7 23:08:56 John kernel: [   77.671517] Too big adjustment 32

```

I'm using the stock xorg ATI driver.

I'm also getting a never-ending stream of

```
Jun  9 03:42:23 John kernel: [ 3121.669564] end_request: I/O error, dev fd0, sector 0
Jun  9 03:42:35 John kernel: [ 3133.844793] end_request: I/O error, dev fd0, sector 0
Jun  9 03:42:47 John kernel: [ 3146.016360] end_request: I/O error, dev fd0, sector 0
Jun  9 03:42:59 John kernel: [ 3158.184677] end_request: I/O error, dev fd0, sector 0
Jun  9 03:43:11 John kernel: [ 3170.357364] end_request: I/O error, dev fd0, sector 0
Jun  9 03:43:24 John kernel: [ 3182.541373] end_request: I/O error, dev fd0, sector 0
Jun  9 03:43:36 John kernel: [ 3194.728997] end_request: I/O error, dev fd0, sector 0
Jun  9 03:43:48 John kernel: [ 3206.913036] end_request: I/O error, dev fd0, sector 0
Jun  9 03:44:00 John kernel: [ 3219.081635] end_request: I/O error, dev fd0, sector 0
Jun  9 03:44:12 John kernel: [ 3231.257117] end_request: I/O error, dev fd0, sector 0
Jun  9 03:44:24 John kernel: [ 3243.424874] end_request: I/O error, dev fd0, sector 0
Jun  9 03:44:37 John kernel: [ 3255.613316] end_request: I/O error, dev fd0, sector 0
Jun  9 03:44:49 John kernel: [ 3267.780693] end_request: I/O error, dev fd0, sector 0
Jun  9 03:45:01 John kernel: [ 3279.956523] end_request: I/O error, dev fd0, sector 0
Jun  9 03:45:13 John kernel: [ 3292.125255] end_request: I/O error, dev fd0, sector 0
Jun  9 03:45:25 John kernel: [ 3304.317193] end_request: I/O error, dev fd0, sector 0
```
in kern.log

It's also taking a very long time to boot. The splash screen loading bar moves about 25% of the way, then just hangs there, with no detectable disk activity. If I wait 30-40 seconds, it then continues loading to the log in screen and lets me log in normally, but the fd0 errors continue the whole session.

I'm not getting a kernel oops, and I have apport set to load automatically, but no errors bad enough to trigger a report are happening for either.

Regards,

Didius

---

### Post by jerrylamos on 2009-06-08
At the end of kern.log I get:

Jun  8 13:54:22 linux kernel: [   42.957195] gvfs-gdu-volume[3014]: segfault at c ip b7fc3fda sp bfc0d340 error 4 in libgdu.so.0.0.0[b7fbb000+22000]
Jun  8 13:57:28 linux kernel: [  228.948943] gvfs-gdu-volume[3128]: segfault at c ip b7f5efda sp bfe3df70 error 4 in libgdu.so.0.0.0[b7f56000+22000]

I don't seem to see the other errors people are reporting.

I am running a different kernel

Linux version 2.6.30-999-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1244192415 SMP Fri Jun 5 09:45:34 UTC 2009

because on this i845 I get invisible cursor with KMS, a known bug fixed in 2.6.30-999

Jerry

---

### Post by xebian on 2009-06-08
@Didius

Looks like it's trying to read/write the floppy drive.

---

### Post by Didius Falco on 2009-06-08
> **xebian said:**
> @Didius

Looks like it's trying to read/write the floppy drive.

Yes, it is - the strange thing about that is there has never been a floppy disk drive in this PC. This leads me to believe the search will remain fruitless.

However, I'm not averse to waking up one morning and finding a brand-new one installed with a little Koala logo on the front.
  
I should dig around and see what's causing it, but I'm having some health issues right now that requires fairly heavy doses of painkillers, and I'd rather not tinker too deeply while under the influence of prescription narcotics. Don't (floppy) drive drugged, you know. <G>

Hmm, I'd also better take that under consideration if I think I do see a Koala brand floppy drive installed... :wink:

Regards,

Didius

---

### Post by Didius Falco on 2009-06-08
BTW, I forgot to mention that I'm running the 2.6.30-8 kernel.

I'd also be interested to know if  Cariboo, or anyone else, is seeing the same errors in kern.log...

Regards,

Didius

---

### Post by Naddiseo on 2009-06-08
> **Didius Falco said:**
> BTW, I forgot to mention that I'm running the 2.6.30-8 kernel.

I'd also be interested to know if  Cariboo, or anyone else, is seeing the same errors in kern.log...

Regards,

Didius


I get them too. The floppy errors have stopped though, an update yesterday must have fixed them. I thought it was my HDD was dying 'cause I could hear a ticking sound. Then I rmmod floppy and it fixed.

---

### Post by tghe-retford on 2009-06-08
I too have been getting the "Too big adjustment 32" message in kern.log. It happens when I log in. I restarted the computer and got this:
```
Jun  8 19:26:17 TGHE kernel: [   25.839498] Too big adjustment 32
Jun  8 19:26:17 TGHE kernel: [   25.901385] Too big adjustment 32
Jun  8 19:26:17 TGHE kernel: [   25.916575] Too big adjustment 32
Jun  8 19:26:17 TGHE kernel: [   25.940489] Too big adjustment 32
Jun  8 19:26:17 TGHE kernel: [   25.957383] Too big adjustment 32
Jun  8 19:26:17 TGHE kernel: [   25.972507] Too big adjustment 32
Jun  8 19:26:17 TGHE kernel: [   26.005167] Too big adjustment 32
Jun  8 19:26:18 TGHE kernel: [   26.020511] Too big adjustment 32
```
I then logged out and logged back in (to diagnose a problem with screen tearing and Wine) and then to confirm it happened during login, again just now.
```
Jun  8 20:05:47 TGHE kernel: [ 2395.844231] Too big adjustment 32
Jun  8 20:05:47 TGHE kernel: [ 2395.912847] Too big adjustment 32
Jun  8 20:07:23 TGHE kernel: [ 2491.408064] Too big adjustment 32
Jun  8 20:07:23 TGHE kernel: [ 2491.473382] Too big adjustment 32
Jun  8 20:07:23 TGHE kernel: [ 2491.488574] Too big adjustment 32
Jun  8 20:07:23 TGHE kernel: [ 2491.512451] Too big adjustment 32
Jun  8 20:07:23 TGHE kernel: [ 2491.529373] Too big adjustment 32
Jun  8 20:07:23 TGHE kernel: [ 2491.544505] Too big adjustment 32
Jun  8 20:07:23 TGHE kernel: [ 2491.577103] Too big adjustment 32
Jun  8 20:07:23 TGHE kernel: [ 2491.592511] Too big adjustment 32
Jun  8 20:07:58 TGHE kernel: [ 2526.928235] Too big adjustment 32
Jun  8 20:07:58 TGHE kernel: [ 2526.992785] Too big adjustment 32
Jun  8 20:08:21 TGHE kernel: [ 2549.836241] Too big adjustment 32
Jun  8 20:08:21 TGHE kernel: [ 2549.900898] Too big adjustment 32
Jun  8 20:10:24 TGHE kernel: [ 2672.148238] Too big adjustment 32
Jun  8 20:10:24 TGHE kernel: [ 2672.212767] Too big adjustment 32
Jun  8 20:30:35 TGHE kernel: [ 3883.603624] Too big adjustment 32
Jun  8 20:30:35 TGHE kernel: [ 3883.665361] Too big adjustment 32
Jun  8 20:30:35 TGHE kernel: [ 3883.681563] Too big adjustment 32
Jun  8 20:30:35 TGHE kernel: [ 3883.705391] Too big adjustment 32
Jun  8 20:30:35 TGHE kernel: [ 3883.722353] Too big adjustment 32
Jun  8 20:30:35 TGHE kernel: [ 3883.737498] Too big adjustment 32
Jun  8 20:30:35 TGHE kernel: [ 3883.769947] Too big adjustment 32
Jun  8 20:30:35 TGHE kernel: [ 3883.785501] Too big adjustment 32
```
I'm using the 2.6.30-8-generic kernel and NVidia 185.18.14 drivers from Michael Marley's PPA. No floppy disk drive in this system either.

---

### Post by xebian on 2009-06-08
> **Didius Falco said:**
> BTW, I forgot to mention that I'm running the 2.6.30-8 kernel.

I'd also be interested to know if  Cariboo, or anyone else, is seeing the same errors in kern.log...

Regards,

Didius

No problem here.  Using karmic 30-8-generic 64-bit kernel, NV 185.18.14, KDE 4.3 B1/2

---

### Post by cariboo on 2009-06-08
I just tried grub2 and it failed, but I can still read the logs, I get the same output in /var/log/kern.log as I do with dmesg.

```
Jun  8 16:23:42 alexis-karmic kernel: [   21.580999] IRQ 18/nvidia: IRQF_DISABLED is not guaranteed on shared IRQs
Jun  8 16:23:47 alexis-karmic kernel: [   26.624945] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   26.734030] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   26.749894] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   26.776298] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   26.790968] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   26.805820] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   26.832547] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   26.893986] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   26.909797] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   26.936298] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   26.997979] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   27.013816] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   27.040256] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   27.101992] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   27.117793] Too big adjustment 32
Jun  8 16:23:47 alexis-karmic kernel: [   27.144132] Too big adjustment 32
Jun  8 16:23:48 alexis-karmic kernel: [   27.210674] Too big adjustment 32
Jun  8 16:23:48 alexis-karmic kernel: [   27.225925] Too big adjustment 32
Jun  8 16:23:48 alexis-karmic kernel: [   27.252423] Too big adjustment 32
Jun  8 16:23:48 alexis-karmic kernel: [   27.315168] Too big adjustment 32
Jun  8 16:23:48 alexis-karmic kernel: [   27.329947] Too big adjustment 32
Jun  8 16:23:48 alexis-karmic kernel: [   27.357539] Too big adjustment 32
Jun  8 16:23:48 alexis-karmic kernel: [   27.373900] Too big adjustment 32
Jun  8 16:23:55 alexis-karmic kernel: [   35.508022] eth0: no IPv6 routers present
```

I'm running kernel 2.6.30-8

@Didius Falco

Try disabling the floppy in the BIOS, that stopped the fd0 errors on my system.

---

### Post by alphacrucis2 on 2009-06-08
> **cariboo907 said:**
> 

I'm running kernel 2.6.30-8

@Didius Falco

Try disabling the floppy in the BIOS, that stopped the fd0 errors on my system.

I found the floppy disk errors stop if I actually put a floppy in the drive. The problem started with the 2.6.30-8 kernel.

---

### Post by cariboo on 2009-06-09
Of the 8 computers I have on my network, only 2 have floppy drives, so getting rid of the fd0 error was a priority for me. I found that disabling them in the BIOS was the easiest way to get rid of the error.

---

### Post by Didius Falco on 2009-06-09
> **cariboo907 said:**
> I just tried grub2 and it failed, but I can still read the logs, I get the same output in /var/log/kern.log as I do with dmesg.

@Didius Falco

Try disabling the floppy in the BIOS, that stopped the fd0 errors on my system.

Thanks, cariboo907, that did the trick!

I had recently flashed the BIOS with the latest update trying to solve the "ata3 soft reset" error, but it reintroduced a problem I'd had with earlier versions of the BIOS. At boot, my ATI 4870 would run the fan really fast then subside, repeating this 3-4 times before it would boot - it was like "the little engine that could" or something. Since it also didn't solve the "soft reset" error, I reverted back to the older one, and I neglected to turn off the floppy.

Now it is booting into the log in screen with no problem.

I am still getting the "Too big adjustment 32" error in kern.log, but it still isn't showing up in dmesg.

Regards,

Didius

---

### Post by taavikko on 2009-06-10
Having the same output "too big adjustement" on my laptop running with r620 chipset ati/gpu.
Does anyone have any details what it means?

---

### Post by johnnyis42 on 2009-09-28
So I did a grep -r on the linux kernel source, low and behold:

```
grep -r "Too big adjustment" linux-source-2.6.28
linux-source-2.6.28/sound/pci/hda/hda_intel.c:			snd_printk(KERN_WARNING "Too big adjustment %d\n"
```

Verdict: the problem is somewhat sound related.

---

### Post by cariboo on 2009-09-28
I never noticed when, but the message has gone away.

---

