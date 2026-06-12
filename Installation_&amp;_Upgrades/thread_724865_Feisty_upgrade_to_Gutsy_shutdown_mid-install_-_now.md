---
title: "Feisty upgrade to Gutsy shutdown mid-install - now I get kernel panics on startup"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by mattp52 on 2008-03-15
OK, so I've had a Feisty install running nicely and decided to upgrade to Gutsy so I could install the backports of MythTV 0.21 which I use my Ubuntu install for.

I followed the install instructions published here:

[http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy/](http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy/)

Everything was running smoothly. All packages downloaded and I was working through the actual install when about mid-way through my machine decided to shutdown. This in itself is a total mystery but as I've set my Myth box to shutdown when it's finished recording, I think the ACPI settings for the recording I *would* have been recording had I not shutdown all MythTV processes kicked in and initiated a shutdown.

End result is that I now cannot boot the system - presumably because it is some mutated offspring of Feisty and Gutsy. On restart I get these errors once Grub has done it's stuff:

```

[ 27.466347] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0.0)

Kernel alive
kernel direct mapping tables up to 10000000 @ 8000-4000 

```

An additional annoyance is that my BIOS now doesn't seem to recognise the serial keyboard I have plugged into it so I cannot enter the BIOS set-up to force a start-up off my Feisty install/rescue disk  (Motherboard is an MSI K9N Neo). I see some USB driver log messages pop-up on a restart so is it likely/possible the BIOS only supports USB keyboards?

What's the best way forward? Do I get hold of another disk, partition it and install a fresh latest-and-greatest Ubuntu system on that and configure all-over again the nuances of my imon-soundgraph remote, smb shares etc., write-off my old MythTV recordings files and database but attempt to salvage the videos, music and pictures off the original disk?

Or if I can get the rescue disk to run do I have any chance of either a) patching the system back to it's running state or b) running a system upgrade tool off the CD and point it at my existing HD.

Seems to me that not many OSes can weather a shutdown mid-install - what's the bestway forward?

---

