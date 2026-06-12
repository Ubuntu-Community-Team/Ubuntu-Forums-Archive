---
title: "AMD64 with NVIDIA video card installation"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by bkline on 2006-03-11
I finally succeeded in getting Ubuntu 5.10-amd64 installed on a machine with an NVIDIA GeForce 4 video card.  It wasn't easy, and it took a **very** long time.  The installation process would finish the first pass, reboot, and then hang about 4/5 of the way through the rest of the installation/configuration.  This was very repeatable, though no problems with the 32-bit flavor of the OS.  I tried setting the DEBCONF_DEBUG=5 and BOOT_DEBUG=1 options, but there was no indication given of where to look for the diagnostics from these options, so no help there (it might be worthwhile considering adding a little more information to the help screens here).

So I tried server, which installed successfully.  Then I tried apt-get install ubuntu-desktop, and this hung just like the default installation had.  I looked in the logs, and found that one of the tt fonts had been partially installed when the hang occurred (this assumes that the logging is properly flushed after each entry, which I am guessing is true, since the last entry appeared not to have been truncated in the middle of the line).

Next I tried apt-get -s install ubuntu-desktop and captured the output in a file so I could install the individual packes separately.  This approach ran into another failure, with an error message which said "Process_queue: Assertion `dependtry <= 4' failed" (which I see has been reported once before, but as far as I could tell with no resolution, or even any followup from anyone else).

Next I found a tip for installing and enabling the nvidia-glx and nvidia-settings packages.  I repeated my server install, then inserted the nvidia steps (the nvidia-glx-config enable failed because X wasn't installed yet; no surprise), then proceeded with the installation of ubuntu-desktop, which succeeded.  The xorg.conf file had the vesa driver not the nvidia driver, presumably because the nvidia-glx-config step had failed.  So I ran nvidia-glx-config again, and it succeeded this time.  However, when I re-started X the machine hung with a monotonously repeated noise from the sound card.  So I rebooted into recovery mode and backed out the changes to xorg.conf, and was able to bring X back up again.  Finally, I went into the xorg.conf file and manually switched to the nv driver, which I had been able to do successfully with a 32-bit Debian on the same hardware.  That's where the machine is now, with the display at 1280x1024.

So in summary, a successful outcome, but a little puzzling.  For example, how was installing the nvidia-* packages able to suppress the failures when the nvidia-glx-config step wasn't able to work until after the ubuntu-desktop installation had made it successfully past the point where it had been failing before?  It's also a little odd that the nvidia driver, the installation of which presumably avoided the pothole which had been sabotaging the installation, hangs the machine when I try to plug it into X.  The truth is, although I managed to get the installation to succeed, I don't really understand why it worked.

If anyone on the other side of the wall is really interested in tracking down the cause of the failure, I could probably be persuaded to do some more testing and reporting, but without more guidance on how to generate useful logs on what the installer is doing at a much finer level of granularity I don't thing there's much point in continuing down this path on my own.

Hope these notes are helpful to someone else who finds himself in this boat.  :->}

Bob Kline

---

