---
title: "Hibernate on Dell XPS M1330 - it works, but dmesg has errors?"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cfogelberg on 2009-04-09
Dear all,

I have just installed the Jaunty beta on my Dell XPS M1330, which I am also triple booting into Windows Vista and Dell Media Direct.

Initially, hibernate and resume didn't work in Ubuntu. After installing all of the updates (I also force-installed the latest versions of ekiga, indicator-applet, indicator-messages through the Synaptic Package Manager) it now seems to work. However it generates some output when it's doing that which makes me think it's only just working. See output from dmesg, including some stuff before and after which I don't think is relevant. There were no messages on hiberate, the messages I saw on restore start at about 3717.102296:

```
[ 3716.820161] ata3: SATA link down (SStatus 0 SControl 300)
[ 3716.822661] ata1.00: configured for UDMA/133
[ 3716.836108] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[ 3716.836124] sd 0:0:0:0: [sda] Write Protect is off
[ 3716.836125] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3716.836145] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3717.013586] iwlagn: Radio Frequency Kill Switch is On:
[ 3717.013589] Kill switch must be turned off for wireless networking to work.
[ 3717.013631] tg3 0000:09:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfd3f0000)
[ 3717.081883] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f1aff800-f1afffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[ 3717.101277] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[ 3717.102296] ricoh-mmc: Resuming.
[ 3717.102304] ricoh-mmc: Controller is now disabled.
[ 3717.102476] sd 0:0:0:0: [sda] Starting disk
[ 3717.276724] pm_op(): usb_dev_restore+0x0/0x10 returns -19
[ 3717.276727] PM: Device 2-1 failed to restore: error -19
[ 3717.276898] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -71 (exp. 26).
[ 3717.276901] uvcvideo 2-6:1.1: resume error -5
[ 3717.277157] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -71 (exp. 26).
[ 3717.277160] uvcvideo 2-6:1.1: resume error -5
[ 3717.277877] PM: Image restored successfully.
[ 3717.319976] Restarting tasks ... <6>usb 2-1: USB disconnect, address 2
[ 3717.321992] done.
[ 3717.322022] PM: Basic memory bitmaps freed
[ 3717.326130] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[ 3737.617426] tg3 0000:09:00.0: irq 2296 for MSI/MSI-X
[ 3737.672529] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3737.677068] iwlagn: Radio disabled by HW RF Kill switch
[ 3737.695993] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3739.260672] tg3: eth0: Link is up at 100 Mbps, full duplex.

```

I'm posting this here for two reasons:
1) To check that it is actually working properly, despite the messages.
2) To flag it in case someone needs to do something about it.

I'm not sure what the synaptics_resume_reset is, I have found one bug report which might be relevant and suggests that it isn't a problem here though: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330606]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330606")

Thanks for your help and support :)
Christo

---

