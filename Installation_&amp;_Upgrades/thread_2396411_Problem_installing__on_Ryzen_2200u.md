---
title: "Problem installing  on Ryzen 2200u"
date: 2018-07-15
forum: Installation &amp; Upgrades
---

### Post by anoxable on 2018-07-15
Hello,  ive tried to install latest version of ubuntu,  but when i press install,  i am greeted with this error, not sure what seems to be the problem.

---

### Post by dinkidonk on 2018-07-15
If possible, try to update your BIOS.

---

### Post by pqwoerituytrueiwoq on 2018-07-15
Typically i see this issue if a CPU OC is unstable, try disabling any overclocks setting you have in your bios
make sure your bios is up to date and you have a 18.04 boot image
it may be necessary to disable the turbo or automatic OC ryzen uses until you can upgrade the kernel to something from the mainline ppa
the latest stable is 4.17.5, on the unstable side you have 4.18-rc4 as of 2018-07-15 07:30 EST

---

### Post by oldfred on 2018-07-15
You may need newer kernel than the one standard in 18.04. You then have to use a ppa.

        Ryzen 2400G UEFI issue on 4K at 60Hz
[https://ubuntuforums.org/showthread.php?t=2387396](https://ubuntuforums.org/showthread.php?t=2387396)
Raven Ridge With The Ryzen 5 2400G On Mesa 18.2 + Linux 4.17 Is Finally Stable MSI B350M GAMING PRO
[URL="https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1"]https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1
      [/URL]
 MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux) 
    [URL="https://www.phoronix.com/scan.php?page=article&item=ryzen-2400g-may&num=1"]
[/URL]

---

