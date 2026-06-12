---
title: "Are my booting files ok?"
date: 2018-08-30
forum: Installation &amp; Upgrades
---

### Post by drpeppercan on 2018-08-30
I have the impression that my booting files are not where they should be.
There're a few things that are right:
[FONT=verdana]1. Ubuntu takes a notorious amount of time to boot. More than it should, that's for sure. Even when booting from the Live USB drive it's way way faster.[/FONT][FONT=Arial][FONT=verdana]2. I see 2 shimx64.efi files. Is this normal? (see results below for efibootmgr -v[/FONT][FONT=monospace][FONT=verdana]).
3. Windows Boot Manager won't show as a choice in BIOS. However, it does show in GRUB.
4. I don't know if it's related but a couple apps won't work as expected: [/FONT]
  a) rEFInd - as you can see below, it is installed. I have not attempted to configure it though, but it may not be needed. 
  b) Also, both [Ktube]("https://keshavbhatt.github.io/Ktube-media-downloader/") and Ultimate [Media Downloader 2]("https://snapcraft.io/ultimate-media-downloader2") - They show reassuring messages saying the file downloaded successfully, yet it's not where it says it would. The developer says this has never happened before.

[FONT=verdana]I understand that all this is not necessarily related, but if there's something wrong with the booting files, couldn't that explain why rEFInd is not working?, for instance.[/FONT]
[/FONT][/FONT]
[FONT=Arial][FONT=monospace]sudo efibootmgr -v[/FONT]
[FONT=monospace]BootCurrent: 0001[/FONT]
[FONT=monospace]Timeout: 1 seconds[/FONT]
[FONT=monospace]BootOrder: 0001,0002,0000[/FONT]
[FONT=monospace]Boot0000* ubuntu    HD(1,GPT,6513d43f-d266-435e-a2df-915943d89816,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)[/FONT]
[FONT=monospace]Boot0001* Ubuntu    HD(1,GPT,6513d43f-d266-435e-a2df-915943d89816,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}..._................[/FONT]
[FONT=monospace]Boot0002* rEFInd Boot Manager    HD(1,GPT,6513d43f-d266-435e-a2df-915943d89816,0x800,0x100000)/File(\EFI\refind\refind_x64.efi)

[/FONT][FONT=monospace]------------------------------[/FONT][FONT=monospace]------------------------------[/FONT][FONT=monospace]------------------------[/FONT]
[/FONT]

[Boot Repair Disk report]("http://paste.ubuntu.com/p/jC6jWhFGmD/")
[FONT=Arial]
[FONT=monospace]------------------------------[/FONT][FONT=monospace]------------------------------[/FONT][FONT=monospace]------------------------
[/FONT]
[FONT=monospace]apt-cache policy refind[/FONT][FONT=monospace]refind:[/FONT]
[FONT=monospace]  Installed: 0.11.3-0ppa1[/FONT]
[FONT=monospace]  Candidate: 0.11.3-0ppa1[/FONT]
[FONT=monospace]  Version table:[/FONT]
[FONT=monospace] *** 0.11.3-0ppa1 500[/FONT]
[FONT=monospace]        500 [http://ppa.launchpad.net/rodsmith/refind/ubuntu](http://ppa.launchpad.net/rodsmith/refind/ubuntu) bionic/main amd64 Packages[/FONT]
[FONT=monospace]        100 /var/lib/dpkg/status[/FONT]
[FONT=monospace]     0.11.2-1 500[/FONT]
[FONT=monospace]        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) bionic/universe amd64 Packages[/FONT]
[/FONT]
[FONT=monospace]------------------------------[/FONT][FONT=monospace]------------------------------[/FONT][FONT=monospace]------------------------

[FONT=verdana]Thank you guy! :)[/FONT][/FONT]

---

