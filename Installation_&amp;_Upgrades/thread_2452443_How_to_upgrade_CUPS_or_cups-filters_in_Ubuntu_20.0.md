---
title: "How to upgrade CUPS or cups-filters in Ubuntu 20.04?"
date: 2020-10-22
forum: Installation &amp; Upgrades
---

### Post by alyana on 2020-10-22
Hi,

does anyone know how to upgrade the cups in Ubuntu 20.04?

I have several issues with printers (Brother MFC-L8900CDW, Brother MFC-L8650DW, HP OfficeJet 6950), that do not print multiple copies, only one copy comes out of the printer.

I did some research and found out, that this issue seems to be fixed now, in cups-filters 1.27.5 resp. 1.28, which is part of CUPS 2.3.3, and that is available for Ubuntu 20.10. [https://github.com/OpenPrinting/cups-filters/commit/6157b8f6178b89fa7a040c2057ff91eb9ac8885d](https://github.com/OpenPrinting/cups-filters/commit/6157b8f6178b89fa7a040c2057ff91eb9ac8885d)

Now since the machines are on production sites, we do not want to switch from an LTS release to a 9-month release.

All that is needed is to update CUPS, or at least the cups-filters. Switching to a different cups-filters version helped OpenSuse users too who face the same issues, as can be read here [URL="https://forums.linuxmint.com/viewtopic.php?t=326402"]https://forums.linuxmint.com/viewtopic.php?t=326402
[/URL]
I tried to install the updated cups-filters from the groovy repository, but it cannot be installed since there are too many unmet dependencies. I assume I have to upgrade the whole cups system to 2.3.3.

How to do that?

Or is there a chance that this fix is being applied through the regular updates? I somehow would not want to live with that bug for the lifetime of an LTS release!

Thanks for any help
Alyana

---

### Post by wolfzrat on 2020-10-29
Hi Alyana,

I found this for you in the Ubuntu forums, hope this helps, link is below:
LINK: [https://askubuntu.com/questions/1286047/how-to-upgrade-cups-and-cups-filters-in-ubuntu-20-04-to-the-latest-versions-that](https://askubuntu.com/questions/1286047/how-to-upgrade-cups-and-cups-filters-in-ubuntu-20-04-to-the-latest-versions-that)

---

