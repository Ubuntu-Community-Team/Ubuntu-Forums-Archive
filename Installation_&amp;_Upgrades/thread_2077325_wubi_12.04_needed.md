---
title: "wubi 12.04 needed"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by iourine on 2012-10-28
Need to reinstall some Linux on a 10-years old Toshiba R100. It is a perfect machine with the only drawback: its BIOS cannot boot from conventional CD-ROMs or USB. Thus wubi is the most handy option, and quite sufficient for my needs.

There was Lubuntu 12.04 working successfully, but I carelessly upgraded it to 12.10. (Once again, never repair what is running ok!) It does not work, the machine becomes totally irresponsive as soon as X starts. Obvious workarounds (e.g. setting video modes manually in GRUB) do not help. Probably there is a more serious problem in X; it does not display neither a "low resolution" warning nor the cursor. I have too lilttle time to play with it, so reinstalling Lubuntu 12.04 would be the best choice.

The problem is that the current wubi 12.04.1 cannot install plain 12.04 distros - that is, most of *buntu clones. It downloads the .iso twice (via torrent and http), then writes in the log that "12.04 != 12.04.1" and aborts. This is definitely a bug! (Where to report it?) And there appears to be no easy ways to make it use the existing 12.04 files.](*,)

Does anyone have the original wubi.exe of 12.04 build, dated April 2012? Or a link to it? The one included in the CD-ROMs is not functional, there was a separate file downloaded apart from the .iso`s. Thnx in advance.

---

### Post by jerrrys on 2012-10-28
Just a thought

Install 10o4 and immediately upgrade to 12o4

---

### Post by howefield on 2012-10-28
Try here...

[http://old-releases.ubuntu.com/releases/12.04/](http://old-releases.ubuntu.com/releases/12.04/)

Scroll down to bottom of page.

---

### Post by iourine on 2012-10-28
Thanks to everyone, especially **howefield** for the link.The issue is solved much easier: wubi.exe should be extracted from the [virtual] CD and run from a local disk. Then in takes the CD and makes the 1st stage of installation under Windows. (If run directly from the CD or .iso, it asks to reboot from the CD, what is impossible ion my case.)

---

