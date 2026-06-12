---
title: "Ubuntu and Intel DG33BU chipset a problem?"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by TedBonel on 2007-07-13
Hi,

       I installed Ubuntu 7.04 (32bits) on a new windows xp box.
       My network card is not recorgnized (ifconfig only lists the localhost). I have a DG33BU chipset with bios version number DPP 35105.86A.0216.2007.0502.1916.
       Do I need to download drivers for this chipset? Intel does not seem to have available for download at their website ([http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2780](http://downloadcenter.intel.com/Product_Filter.aspx?ProductID=2780)) such drivers for unix based OS!
       Any help is welcome.
       T.

---

### Post by TedBonel on 2007-07-14
Hi,

     I've been doing some research on the web. Others have had the similar problems. It seems that the chipset is too new for the current (stable) ubuntu release (7.04). 

      For example, 
     [http://listas.fi.uba.ar/pipermail/lug/2007-June/025514.html](http://listas.fi.uba.ar/pipermail/lug/2007-June/025514.html)
      seems to have recompiled the kernel. It refers to "mm-2.6.22" and "intel module for the chipset". Unfortunately, I do not know how to recompile the kernel (nor should I have to in order to install ubuntu!).

      Other examples of problems with this chipset may be found by searching for "dg33bu" in this forum.

      I would really appreciate some help. For now it seems I have to uninstall ubuntu 7.04 and wait for gutsy.

      T.

---

### Post by TedBonel on 2007-07-24
Hi,

     I noticed that two new upgrades of the BIOS have been issued (mine is 216, latest is 249). 
     Would any of the experts on this forum encourage such an enterprise? 
     Thanks,
     T.

---

### Post by rbmorse on 2007-07-24
I think the best advice is to go to the page for your motherboard on Intel's web site ([http://downloadcenter.intel.com/Filter_Results.aspx?strTypes=all&ProductID=2780&OSFullName=OS+Independent&lang=eng&strOSs=38&submit=Go%21](http://downloadcenter.intel.com/Filter_Results.aspx?strTypes=all&ProductID=2780&OSFullName=OS+Independent&lang=eng&strOSs=38&submit=Go%21)) and read the release notes for the BIOS updates to see if you are affected by the issues addressed.

The very first item on the 249 release MAY...MAY be of help here.

---

