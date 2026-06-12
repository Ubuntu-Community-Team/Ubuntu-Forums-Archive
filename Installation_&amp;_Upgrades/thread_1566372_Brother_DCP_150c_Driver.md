---
title: "Brother DCP 150c Driver"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by Geunor on 2010-09-02
I have got Ubuntu 10.04 on a IBM Think Pad T43 laptop which has been partitioned between Ubuntu and Windows. I have installed the driver for my Brother DCP 150c printer on the Windows partition and it works fine but I am struggling with the Ubuntu side for installing the Driver. I am new to this so I may need a step-by-step on how to go around doing this. I have been on the Brother website and have come across two downloads for the printer. These are LPR and CUPS. I don't have a clue what these mean or which one I should install. I have downloaded the LPR driver but there is no installer included in the folder so I'm guessing that I will have to drag and drop the folder into another folder somewhere but I am not sure which folder to put it in. Does anyone have any suggestions? thank you for your time and help.

---

### Post by plucky on 2010-09-03
> **Geunor said:**
> I have got Ubuntu 10.04 on a IBM Think Pad T43 laptop which has been partitioned between Ubuntu and Windows. I have installed the driver for my Brother DCP 150c printer on the Windows partition and it works fine but I am struggling with the Ubuntu side for installing the Driver. I am new to this so I may need a step-by-step on how to go around doing this. I have been on the Brother website and have come across two downloads for the printer. These are LPR and CUPS. I don't have a clue what these mean or which one I should install. I have downloaded the LPR driver but there is no installer included in the folder so I'm guessing that I will have to drag and drop the folder into another folder somewhere but I am not sure which folder to put it in. Does anyone have any suggestions? thank you for your time and help.

Open Synaptic Package Manager (**System > Administration > Synaptic Manager**) and search for **dcp-150c** and you should find ```
brother-cups-wrapper-extra
brother-lpr-drivers-extra
```

Mark both for installation and apply.This will install the drivers for the printer.

Then connect and power on your printer and open **System > Administration > Printing**.You should now be able to install your printer and select the correct driver.

If your printer has a scanner,you have to go to the brother website and download the .deb file for your scanner.Once it is downloaded you can then double click on the file and it will install.


Good Luck

---

