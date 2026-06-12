---
title: "Feisty and 3CN3AC556"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by jcsewell on 2007-04-27
Machine: Dell latitude C600
NIC: MiniPCI 3Com 3CN3AC556 (I think ubuntu uses the 3c59x driver)
Problem: No network connectivity

The NIC works, because I installed Feisty using the netboot method.  A few months ago I had Edgy on this machine and the NIC worked there.

On first boot, I noticed no network connectivity.  I right clicked the network icon beside the clock and looked at "Connection Information".  It defaulted to DHCP and showed all zeros.

I then went into System-Administration-Network and set up the machine as static IP with appropriate parameters.  Still no go.

Set it back to DHCP.  Still no go.  The DHCP server (D-Link DI-524) does not seem to see any requests from the client.

Now my "Connection Information" under the network icon is greyed out.  I suspect my NIC is not detected/supported.  This is strange as I installed this machine OVER the network last night.  How can I tell if the NIC is there?  Pointer to docs would be appreciated.


-James

---

### Post by jeepGuy on 2008-02-03
I had a similar problem with a Dell Latitude C600. Using the alternate installation CD for Feisty, Ubuntu did not detect the 3Com 3CN3AC556. This was puzzling because an installation on another C600 had gone flawlessly a couple weeks earlier.

THE FIX - The C600 that wouldn't recognize the NIC had BIOS version A09. The other had version A20. From information I found at [http://gentoo-wiki.com/HARDWARE_Dell_Latitude_C600](http://gentoo-wiki.com/HARDWARE_Dell_Latitude_C600), I updated the BIOS to the latest version, which  is A23. Get it from Dell  [here]("ftp://ftp.us.dell.com/bios/C600_A23.exe"). If you don't have Windows on your system, use this [.iso]("http://www.bay-wolf.com/bios/latc600/C600_A23.zip") file instead.

After the BIOS upgrade, Ubuntu install had no problem identifying the 3Com NIC.

While Ubuntu recognized the NIC, the operation was erratic and displayed TX errors and RX overruns. I removed two screws from the bottom of the case to access the mini card, then removed and reinstalled the card. After securing the screws, the card has worked without a problem.

---

