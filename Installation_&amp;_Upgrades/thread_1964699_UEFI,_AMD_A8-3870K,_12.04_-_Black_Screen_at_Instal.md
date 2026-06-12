---
title: "UEFI, AMD A8-3870K, 12.04 - Black Screen at Install"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by pneumatic on 2012-04-24
I've followed probably 50 of the 100 or so suggestions as to installing under a UEFI environment and nothing seems to work.  I can't even get the minimal install to see the SATA3 drive.

Should I just try to find a motherboard with the old school BIOS or is there something that will make this work?

---

### Post by oldfred on 2012-04-24
I think you have 3 different issues and am not sure of the order you need to try to fix them

Some BIOS and Linux drivers do not work with SATA3, others report no issues. Have you tried your SATA2 ports?

Almost all successful UEFI installs are those with the partitioning done in advance and it still depends on whether you boot liveCD or USB in UEFI mode or BIOS mode. Almost all UEFI systems will still boot in BIOS/MBR mode. Some have settings and others just seem to look for efi partition and if not found default back to looking for MBR to boot.

Black screen is usually after grub2 & Ubuntu have booted but video drivers are not correct or correctly loaded. Often just adding a nomodeset boot parameter to grub2 boot menu solves the issue, but some UEFI systems were not using shift key to show grub menu correctly. Not sure if that bug is fixed.

So have you partitioned correctly with gpt and both efi & bios_grub partitions?

---

### Post by darkod on 2012-04-24
On top of oldfred suggestions, I believe most boards that have UEFI have the option to disable the UEFI boot in the BIOS. If you do that it would boot in standard bios mode so you will have one issue less to worry about.

---

### Post by MonkeyPaw on 2012-04-24
Not sure what options you've tried, but I successfully installed 12.04 on a UEFI board with a A8-3850. I, too, had a blank screen issue. What I did:

1. Installed a dedicated graphics card and plugged monitor into it.
2. Went into BIOS and made sure the integrated graphics remained enabled, even with an PCIe card installed
3. Installed 12.04, rebooted
4. Downloaded the 12.3 Catalysts from AMD.com, installed them, shut down.
5. Pulled dedicated graphics card, plugged monitor into motherboard. Started up and made it to Ubuntu.

If you don't have a spare card to try, try running the install while plugged into an HDMI display. You should get a picture. Once installed, get the 12.3 Catalysts installed, and then you should get a picture from the other display ports on the motherboard.

---

### Post by MonkeyPaw on 2012-04-24
I should also add that you should check that your BIOS is set to AHCI, not IDE. Mine defaulted to IDE. I did NOT need to disable UEFI boot.

---

### Post by pneumatic on 2012-05-02
MonkeyPaw,

Thanks for the suggestion for a dedicated graphics card - that worked.  Then I installed the Catalyst driver in order to make the onboard one work.

Everything is good now.

---

### Post by vishnumrao on 2012-05-14
I too had the black screen problem. Tried booting up a few times with the live usb, and it booted in once properly. Seized the opportunity and installed. No problems after installing!

BTW, all you with AMD Fusion chips, have you had this problem? [http://ubuntuforums.org/showthread.php?t=1980287](http://ubuntuforums.org/showthread.php?t=1980287)

Please post replies to that thread. I don't want to hijack this thread.

---

