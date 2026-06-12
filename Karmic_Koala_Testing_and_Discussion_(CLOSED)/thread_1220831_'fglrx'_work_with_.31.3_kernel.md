---
title: "'fglrx' work with .31.3 kernel?"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-07-23
I have an onboard  ATI Radeon  HD 3200 graphics. Wondering if I can install 'fglrx' using  'Hardware Drivers' with out causing my machine to 'bork'.
I know it didn't work with  .29 and .30 kernels. Also, what all would I need to install to make it work?
Thanks for any insight

---

### Post by taavikko on 2009-07-23
HD 3250 doesn't work with newest kernel and fglrx.
Better to stick to functional radeon driver :)

---

### Post by DougieFresh4U on 2009-07-23
> **taavikko said:**
> HD 3250 doesn't work with newest kernel and fglrx.
Better to stick to functional radeon driver :)

Thanks
Figured it wasn't happening.

---

### Post by alphacrucis2 on 2009-07-23
> **DougieFresh4U said:**
> I have an onboard  ATI Radeon  HD 3200 graphics. Wondering if I can install 'fglrx' using  'Hardware Drivers' with out causing my machine to 'bork'.
I know it didn't work with  .29 and .30 kernels. Also, what all would I need to install to make it work?
Thanks for any insight

I think the 3200 is legacy as far as as ATI are concerned. ie no support from ATI in any fglrx drivers released since March. You can't run the older fglrx drivers (ie. those released before March) in Jaunty and they certainly won't work with Karmic. Incompatible x.org version. 

[URL="http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20"]http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20
[/URL]

---

### Post by qamelian on 2009-07-23
> **alphacrucis2 said:**
> I think the 3200 is legacy as far as as ATI are concerned. ie no support from ATI in any fglrx drivers released since March. You can't run the older fglrx drivers (ie. those released before March) in Jaunty and they certainly won't work with Karmic. Incompatible x.org version. 

[URL="http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20"]http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20
[/URL]
Nope. According to the release notes linked to on this page, the onboard 3200 is still supported by the current FGLRX.

---

### Post by DougieFresh4U on 2009-07-23
> **qamelian said:**
> Nope. According to the release notes linked to on this page, the onboard 3200 is still supported by the current FGLRX.

Thanks for replies
I don't see ATI Radeon HD 3200 in this list of supported.
But I do have 'fglrx' installed on my Jaunty partition and have no problems that I am aware of.
EDIT: Sorry I take that back. Upon reading the next page it says
[B]ATI Integrated Product Family Support
         The ATI Catalyst Linux software suite is designed to support the following ATI
         desktop products:
                           AMD Chipset Product Support
          ATI Radeon HD 3300 Series       ATI Radeon 3100 Series
          ATI Radeon HD 3200 Series       ATI Radeon 3000 Series
[/B]

---

### Post by taavikko on 2009-07-23
I'm eagerly waiting for Mesa7.6 And drm to provide the functionality for my laptops HD 3250...

Who needs closed binary blobs anyway ;)

(nvidia users don't bother)

---

