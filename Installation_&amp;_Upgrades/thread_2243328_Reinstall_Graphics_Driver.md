---
title: "Reinstall Graphics Driver"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by Devanil_Choudhury on 2014-09-08
Hi..
    I have recently installed a 3d visualization software named VAPOR in Ubuntu-14.04 LTS. My graphics details are Intel sandybridge hd graphics. But during running this vapor there is always a error like -

 [B]Code: 4006
[/B]
[B]Message: GL Vendor String is MESA.
[/B]
[B]Graphics drivers may need to be reinstalled


[/B]Though I have Mesa and for Ubuntu there is default graphics driver Radeon. So please suggest me how to solve this problem.

Thanks in advance.

---

### Post by JMB74 on 2014-09-08
May or may not help, but have you read this? [https://www.vapor.ucar.edu/forums/code-4017-message-no-efc-files-found-directory](https://www.vapor.ucar.edu/forums/code-4017-message-no-efc-files-found-directory)

---

### Post by grahammechanical on 2014-09-08
Mesa and Radeon are words used in connection with the open source video driver for AMD/ATI graphic adapters. The error message is telling you that the software needs a proprietary video driver. Go to System Settings>Software and Updates>Additional Drivers tab and allow the utility to find video drivers for you. The machine needs to be connected to the internet. Then you can select a proprietary video driver. See if that makes any difference.

Regards.

---

