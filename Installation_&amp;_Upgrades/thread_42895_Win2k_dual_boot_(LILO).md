---
title: "Win2k dual boot (LILO)"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by marthynn on 2005-06-19
Dear ubuntu people,

thank you very much for creating this excellent distribution. I just have a small problem with setting up LILO to allow it to boot into an existing Win2000 installation as well as Linux.

Currently I have a Win98 installation on /dev/hde1, Win2k on /dev/hde8 and the ubuntu root directory on /dev/hde5. Thus I gave lilo.conf the two appropriate other="/dev/hde*" entries and reinstalled lilo in the MBR. Both entries appear as expected in the boot menu, but when I choose either of them, nothing happens -- the system just stands still, there is not even an error message. ubuntu still boots fine.

Before installing ubuntu I had an old debian installation on /dev/hde5 which I loaded using the NT boot manager. I was a bit over-keen when setting up ubuntu though, and told lilo to use the MBR, which means I can no longer get into Win2k to reactivate its boot manager.

Attempts at manually copying the MBR about just got me very close to losing my partition table, so I'm a bit scared about doing that now...

Any hints as to what might be going wrong would be appreciated...

Thanks,
marthynn

---

### Post by flyboy_2003 on 2005-06-20
[QUOTE=marthynn]Dear ubuntu people,

thank you very much for creating this excellent distribution. I just have a small problem with setting up LILO to allow it to boot into an existing Win2000 installation as well as Linux.

Currently I have a Win98 installation on /dev/hde1, Win2k on /dev/hde8 and the ubuntu root directory on /dev/hde5. Thus I gave lilo.conf the two appropriate other="/dev/hde*" entries and reinstalled lilo in the MBR. Both entries appear as expected in the boot menu, but when I choose either of them, nothing happens -- the system just stands still, there is not even an error message. ubuntu still boots fine.

Before installing ubuntu I had an old debian installation on /dev/hde5 which I loaded using the NT boot manager. I was a bit over-keen when setting up ubuntu though, and told lilo to use the MBR, which means I can no longer get into Win2k to reactivate its boot manager.

Attempts at manually copying the MBR about just got me very close to losing my partition table, so I'm a bit scared about doing that now...

Any hints as to what might be going wrong would be appreciated...

Thanks,
marthynn[/QUOTE]


To get around these issues when running multiple OS's on your PC, you might want to consider a 3rd party boot loader. I use Acronis OS Selector. I currently run 4 different OS's (WinXP, Ubuntu, Fedora, Gentoo) on the same laptop without problems. All you have to do is tell a version of Linux during the install to put Grub or Lilo on the first sector of the boot partition, then Acronis OS selector does the rest. You will always be able to boot whatever you have installed.

Seems to be (based on your /dev/hde drive) that you're running multiple drives in your system. This can get very complicated. A 3rd party boot loader maybe just what the doctor ordered!

That's my best advice.

---

### Post by luca_linux on 2005-06-20
I'm using GRUB without any problem.
All you need in GRUB is "mapping" --> [http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q10](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q10)

---

### Post by marthynn on 2005-06-20
[QUOTE=flyboy_2003]To get around these issues when running multiple OS's on your PC, you might want to consider a 3rd party boot loader. I use Acronis OS Selector.[/QUOTE]

Well, I don't really want to have to use something commercial if I can avoid it. I gave it a try, but got rather put off by the fact it needed 6 floppy disks!

[QUOTE=flyboy_2003]Seems to be (based on your /dev/hde drive) that you're running multiple drives in your system.[/QUOTE]

No, it's a single drive, but a stupid disk controller. It worked fine with the previous Debian installation though.

After many hours of trying around, I've now simply put the NT boot loader on a floppy, thus I choose which OS to boot by inserting or ejecting the floppy. Not great, but at least it works, and I don't have the patience to try around any more.

Thanks for your replies anyway!

---

