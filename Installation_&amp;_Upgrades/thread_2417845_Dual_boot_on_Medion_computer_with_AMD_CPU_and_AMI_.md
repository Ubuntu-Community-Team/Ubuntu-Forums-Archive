---
title: "Dual boot on Medion computer with AMD CPU and AMI BIOS not persistently achievable"
date: 2019-04-28
forum: Installation &amp; Upgrades
---

### Post by friebel on 2019-04-28
When trying to set up dual boot on medion akoya p32010 (Ryzen 5 2400G, 8GB RAM, 256-GB-SSD, BIOS AMI Aptio 350A4W0X.106 (27.12.2018), AGESA 1.0.0.5             ) I created additional UEFI partitions both on hard disk sda1 and on the nvme SSD and installed the required files there (as suggested by boot-repair). Any attempt to enter the boot information into the NVRAM under Ubuntu was unsuccessful. Trying to add the information under Windows10 using BCDEdit did also not succeed (maybe I did not enter the correct information?). However selecting the wanted boot device from the Windows recovery screen let me boot Ubuntu (once). Then I found out, that in the AMI BIOS in the Boot window there is an option to set the hard disk boot preferences (last entry on the page). There I could select the partition to start the boot process from. Then in the boot options the option to boot Ubuntu from the SSD could be selected and worked repeatedly.

The boot order and the Ubuntu entry remained as long as no change in the Ubuntu installation was done. Upgrading or installing packages led to the "repair" of  the grub installation (which according to the package manager was broken). Trying to fix the problem using boot repair (see log in [http://paste.ubuntu.com/p/jWgwDcMr3K/](http://paste.ubuntu.com/p/jWgwDcMr3K/)) did also not succeed. Both mechanisms reverted the BIOS entry for Ubuntu to the Windows boot manager and every time this happens, I had to manually change the boot order as described above again.

Is there any hope to fix this issue or can I cheat and let the package manager report the grub installation as successful?

---

