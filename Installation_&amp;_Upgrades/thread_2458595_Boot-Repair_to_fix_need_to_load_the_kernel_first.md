---
title: "Boot-Repair to fix need to load the kernel first"
date: 2021-02-28
forum: Installation &amp; Upgrades
---

### Post by Steph_Holmes on 2021-02-28
[LEFT][COLOR=#000000][FONT=Ubuntu]I'm having major problems booting my upgraded system. I was happily running 18.04 with a Gnome Flashback desktop, the upgraded to 20.04 with the MATE desktop (clean install). I started getting boot problems. The first thing I tried was reinstalling Ubuntu. Since then I have tried three times with Boot-Repair but get the same every time.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Dell Inspiron 3793[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]OS: Ubuntu Mate 20.04.2 LTS 64-bit
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Kernel: Linux 5.8.0-44-generic x86_64[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Desktop: MATE 1.24.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Memory: 15.4GiB
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Processor: Intel Core i5-1035G1 CPU @ 1.00GHz x 8[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu][http://paste.ubuntu.com/p/FNwGSfWY6x/](http://paste.ubuntu.com/p/FNwGSfWY6x/)[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]If you need any more information I am comfortable with the CLI.[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]When I try to boot into Linux (any Linux, normal or advanced, current or previous kernel) I get a few lines and then the system halts, generally but not always at the GRUB prompt, with 'you need to load the kernel first'.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]After several tries at rebooting (switch off, Ctrl-Alt-Del, even going in and out of BIOS setup) I happen to get lucky, but ten minutes to start Linux is a bit much.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]Can anyone help at all please, or do I have to reinstall my backup of 18.04 and ignore 20.04?
[/FONT][/COLOR][/LEFT]

---

### Post by cmcanulty on 2021-02-28
Can you boot into recovery mode by holding down shift while powering on and use arrows to get to command prompt and type 

```
sudo update-grub
```

---

### Post by oldfred on 2021-02-28
It says grub reinstalled correctly.
So you may have boot issue after grub.
What video card?
You show a lot of local network mounts. If system boots too fast network may not be available, or if issue with any mount you may have boot issues.
Do not know details but have seen autofs as better way for network type mounts.

 Autofs mount directories on an as-needed basis.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
Example autofs and _netdev
[https://ubuntuforums.org/showthread.php?t=2450936](https://ubuntuforums.org/showthread.php?t=2450936)
use autofs for any storage that isn't connected directly to the system with SAS, SATA, eSATA, or Infiniband connections

---

### Post by Steph_Holmes on 2021-02-28
Hi cmcanulty and oldfred and may I thank you for your speedy replies. (I was amused to see me described as 'first cup of Ubuntu' since I've been using Ubuntu since Breezy 5.10)
'update-grub' behaved as expected but didn't change the problem sadly. It would have been nice for the answer to be so simple. Oddly though, it got me thinking along the line that solved the issue.
I have a lot of network mounts in fstab. They have been extant since Precise but got a little broken by the change to Predictable-Network-Interface-Names which is why there is an additional 'mount -a' in /etc/network/if-up.d/fstab but it looks like it may be fixed in Focal.
The reason I use fstab mounts instead of autofs is that I need to authenticate before accessing the Samba shares, and as you know that stops automount.,
As I say though, I started thinking of timing and signing issues, and although I have secure boot turned off in BIOS, I wondered if it was being reactivated somehow. I ran boot-repair once again (I prefer it to the way you have to make changes in grub2...) and had a look at Advanced settings. Secure Boot was ticked. I unticked it, ran Boot-Repair to completion, and now have a fully functional system.
Once again, thank you both enormously for your time and help. It's users like you that make Ubuntu as brilliant as it is!

---

