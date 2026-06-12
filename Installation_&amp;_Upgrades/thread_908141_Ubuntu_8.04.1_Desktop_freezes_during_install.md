---
title: "Ubuntu 8.04.1 Desktop freezes during install"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by widemeadows on 2008-09-02
I've downloaded Ubuntu 8.04.1 Desktop from mirror link supplied through the ubuntu.com website

I downloaded the image file ubuntu-8.04.1-desktop-i386.iso and burned it onto a CD-R using Nero Express - no problems so far.

I then tried to install it onto an "ordinary" desktop PC - Intel Pentium Dual Core E2180, 2GB RAM, Gigabyte Socket 775 mainboard, an empty 80GB SATA2 HDD (yes a compeletely fresh unused one), DVD-RW drive.

The PC will boot the .iso file and start to load it, then it says "Caldera DR-DOS", a few more messages and then stops and hangs. I've tried this several times and it never goes any further, even when I leave the system for a few minutes. I burned the CD as a bootable image using Nero Express, and it obviously appears to boot. If I do CTRL-C (I think), I get a DOS prompt with about a dozen files such as command.com, mscdex.exe, autoexec.bat listed on the A: drive (which isn't a 3.5 inch floppy as I don't have one hooked up to my PC) and when I do DIR on C: drive it just lists the ISO file.

I've also downloaded the Ubuntu 8.04.01 "Alternate install disc, 64 bit version, and this produces almost the same results - hanging in PC-DOS (as opposed to DR-DOS).

What have I done wrong? I haven't installed Linux for years (I last used RedHat about 3 years ago).

---

### Post by alanmilne on 2008-09-02
I had the same problem when I first tried to install Ubuntu, and discovered that I had a corrupt download of the .iso file.

Have you checked the .MD5 hash results with the published figures? This should verify that the .iso image is correct before you burn it to disk.

I suggest you follow this link for more information:-

[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

Alan L. Milne

---

### Post by Partyboi2 on 2008-09-02
Try burning the iso to disk using another program like [[COLOR=Blue]imgburn[/COLOR]]("http://www.imgburn.com/") and see if that fixes it.

---

### Post by Sef on 2008-09-02
> Try burning the iso to disk using another program....

Another good program is [isorecorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").

Good to read is [How to Write an ISO file]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm").

---

### Post by vishalrao on 2008-09-02
eh, how do you get "caldera dos" boot message? it might be what is present on the HDD? did you specify CDROM as first boot option in BIOS so that it boots before HDD?

---

### Post by abhishek.malhotra35 on 2008-09-02
Try using ultraiso. It is an iso image burner. You can download the trial version from its site. Trial for 30 days.

---

