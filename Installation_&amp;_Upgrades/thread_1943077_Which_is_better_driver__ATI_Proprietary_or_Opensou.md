---
title: "Which is better driver?  ATI Proprietary or Opensource"
date: 2012-03-18
forum: Installation &amp; Upgrades
---

### Post by livewire94 on 2012-03-18
I installed the Propretary ati driver and my screen gets garbled graphics while logging into Ubuntu.  Is there much difference in performance and temp with using proprietary driver over the opensource one?

---

### Post by mastablasta on 2012-03-19
what graphics card/chip do you have? 
 
it really depends on that i think. fo rosme proprietary work better. i think they enable propper hardware acceleration or for example make the hybrid graphics work (which extends battery life, reduces temp...).

---

### Post by Mark Phelps on 2012-03-19
Unless you're doing intensive 3D gaming, there's little need for the proprietary drivers.  I used to install them by default because it was the only way I could get 1920x1280 resolution and multiple monitor support.

But with 11.10, I get both of those with the default open-source Radeon drivers.

---

### Post by TBABill on 2012-03-19
Radeon works fine, but it also runs hotter. I have a HD4250 and using the catalyst (12.2) it runs cooler than with the Radeon driver.

---

### Post by bcarlowise on 2012-03-19
The proprietary driver from AMD/ATI is definitely better. As others here have stated, it provides the full performance benefit of the GPU and allows your system to run cooler. The frame rate is phenomneal with the proprietary drivers so if you're gaming you will definitely want to use them. I don't game but I like my machine to run as cool as possible. If you're getting "garbling" it either because you did not install the drivers correctly or you are using an old version of the proprietary drivers and logging into Gnome3. Download the latest AMD driver from here:

[http://support.amd.com/us/Pages/AMDSupportHub.aspx](http://support.amd.com/us/Pages/AMDSupportHub.aspx)

and follow the instructions here to uninstall your current driver and install the newly downloaded current TI driver:

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

