---
title: "Able to get graphics with startx but no other login manager"
date: 2019-09-11
forum: Installation &amp; Upgrades
---

### Post by jviereck on 2019-09-11
This is installing Ubuntu 16.04 on a Dell Precision 5820 with the latest Bios revision 1.11.1.

After installing Ubuntu 16.04 (needed to use acpi=off as boot option to get the graphical screen for the installation to work), the screen after booting shows the message "/dev/sda2: clean, ....". The graphical login screen does not show up. After some investigation I figured out it's possible to go to some other terminal (e.g. CTRL + ALT + 1) and start some basic X environment by executing `startx`. This brings up a graphical user interface.

Looking at the output of /var/log/syslog shows a stack trace that seems xorg related.

Does anyone has an idea how to debug or fix this further?

Best,
Juilan

[1]: [https://photos.google.com/share/AF1QipNe9_S4pfF_BBzoDyNYOL0w3ScNdO2Bjj9CVbOMmDwdOAljIlnxAOCEvqihRK5NXw/photo/AF1QipMUOvq9DZQQUw_hH1njLPyiNRDikiiNffx8an82?key=Rk9hR1ExUWpyaXhoR1RFUkJuWmxrcUxIWE1BOW9n](https://photos.google.com/share/AF1QipNe9_S4pfF_BBzoDyNYOL0w3ScNdO2Bjj9CVbOMmDwdOAljIlnxAOCEvqihRK5NXw/photo/AF1QipMUOvq9DZQQUw_hH1njLPyiNRDikiiNffx8an82?key=Rk9hR1ExUWpyaXhoR1RFUkJuWmxrcUxIWE1BOW9n)

---

