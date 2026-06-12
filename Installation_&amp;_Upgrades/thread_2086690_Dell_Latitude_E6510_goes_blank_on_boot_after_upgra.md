---
title: "Dell Latitude E6510 goes blank on boot after upgrade to kernel 3.2.0.32 and to 12.10"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by tuuk on 2012-11-21
Same/similar symptoms have been reported many times and I have read through a lot of material (including the sticky post in this forum), tried a lot of suggestions to no avail. It is possible that I have missed some information, but I am frustrated and I have nothing left to do but post here.

I have a Dell Latitude E6510 (integrated Intel HD graphics). I had Ubuntu 12.04 64-bit running on it, more or less smoothly. When the kernel was upgraded to version 3.2.0.32 (from 3.2.0.31), it would not boot any more. After the grub menu, the screen would go blank eventually. You could even hear the sound effects for the login screen, but there is only a blank screen. No switching with Ctrl-Alt-F1. The only 'fix' was booting with the previous kernel (3.2.0.31). After a while, I decided to upgrade to Ubuntu 12.10 (through the Update Manager) with the hope that the new kernel (which is 3.5.0.18 at this point) will fix it. It did not.

In the last few days, I tried some suggestions. It looked like it could be a kernel mode switching issue with the Intel graphics. Kernel boot options such as "nomodeset", i915.modeset=0 (or =1), apic=off, acpi_osi="Linux", noapic, nolapic made no difference. Purging and reinstalling package xserver-xorg-video-intel for a fresh driver was also useless. I ran boot-repair from a live CD (grub was updated to 2.00). Moreover, Ubuntu 12.10 live DVD does not boot (12.04 does), hence, even a fresh 12.10 install is not possible. Apparently, something in the kernel changed permanently and it affects my system. I still have kernel 3.2.0.31 to fall back on to.

As you can see, I am not an expert user. I can try to provide more and detailed information if you can let me know what might help.

Any help is very much appreciated.

---

### Post by YannBuntu on 2012-11-21
> **tuuk said:**
> As you can see, I am not an expert user.

But you have done a very good job already. :KS

1) please can you indicate your Boot-Info URL? ( [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) )

2) try the last Mainline kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc6-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc6-raring/) If your Ubuntu is 64bit, you need to install 4 files: the *all.deb and the 3 *amd64.deb

3) Create a Launchpad account if you haven't yet, login to this account, then open a terminal (from your installed session), and type:
```
ubuntu-bug linux
```

This will gather data and open an internet page. Fill in the Summary ("[Regression] Dell Latitude E6510 goes blank on boot since kernel 3.2.0.32"), and the detailed bug description.
Indicate us the link to this bug report, so that we can follow-up please.

---

### Post by surfincrow on 2012-11-22
Same issue here.

To add:
External monitors are working:
[LIST]
[*]Single VGA
[*]Dual screen DVI using Docking station
[/LIST]

The laptop display is detected when I open the display configuration. The display will light up a little bit (black instead of off).

Also the new 3.2.0.33 driver doesn't work

---

### Post by tuuk on 2012-11-29
Thanks YannBuntu. And apologies for the delayed feedback, due to lack of time as well as to the newest kernel partially resolving the issue (more below). I wanted to observe the system to notice the new behaviour, for which I don't have a clear pattern any more .

> **YannBuntu said:**
> 
<snip>

1) please can you indicate your Boot-Info URL? ( [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) )

I don't know whether it is still useful, but here is the Boot-Info URL:
[http://paste.ubuntu.com/1375057/](http://paste.ubuntu.com/1375057/)

> 
2) try the last Mainline kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc6-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc6-raring/) If your Ubuntu is 64bit, you need to install 4 files: the *all.deb and the 3 *amd64.deb
The last Mainline kernel does actually boot and give me the login screen. And, most of the time, everything else also works. Occasionally (and this seemed to get less often over the last week!), the login screen is not displayed as before with the old kernels. The only option is turning off with Ctrl-Alt-Delete or with On/Off button. Furthermore, occasionally, there is some unstability even when I am able to login (this is new after the kernel upgrade). Unity crashes, software and UI hangs, etc. Also, when that happens, apport seem to report crashes for Xorg and some problems with a package related to gpu (sorry for not being precise here; didn't take notes).

At least, the situation has improved quite a bit, such that I can boot and use my machine with no major problems. But, of course, the occasional hiccups and the knowledge that there is still something wrong is annoying.

> 
3) Create a Launchpad account if you haven't yet, login to this account, then open a terminal (from your installed session), and type:
```
ubuntu-bug linux
```This will gather data and open an internet page. Fill in the Summary ("[Regression] Dell Latitude E6510 goes blank on boot since kernel 3.2.0.32"), and the detailed bug description.
Indicate us the link to this bug report, so that we can follow-up please.I have not done this, because, as I said, I do not have a clear pattern to describe any more. It is not clear to me why this would happen only some of the time (e.g., why the graphics driver does not work only then). If you have suggestions for me to help track down the problem, I will be happy to try.

Thanks again.

---

### Post by YannBuntu on 2012-11-29
> **tuuk said:**
> Occasionally (and this seemed to get less often over the last week!), the login screen is not displayed as before with the old kernels. The only option is turning off with Ctrl-Alt-Delete or with On/Off button. Furthermore, occasionally, there is some unstability even when I am able to login (this is new after the kernel upgrade). Unity crashes, software and UI hangs, etc. Also, when that happens, apport seem to report crashes for Xorg and some problems with a package related to gpu (sorry for not being precise here; didn't take notes).

I would bet on Unity bugs and/or RAM problem, but i can't help more.

I recommend you create a new thread with more specific title, so that relevant people come and help you.

---

