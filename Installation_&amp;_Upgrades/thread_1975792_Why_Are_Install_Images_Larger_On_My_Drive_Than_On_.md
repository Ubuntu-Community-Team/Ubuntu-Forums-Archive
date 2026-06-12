---
title: "Why Are Install Images Larger On My Drive Than On the Mirrors?"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by buzzingrobot on 2012-05-07
Why are 12.04 install images larger on my drive than on Ubuntu's mirrors?

I whined here and elsewhere last week that every 12.04 install CD I burned and tried failed to boot, producing an error message about needing to load a kernel.

Today, someone told me that the images were simply too large for the CD's.  Sure enough, they are.  

I see images typically sized at 695-698MB on the mirrors.  But, when they're on my Mac's drive, they measure 730-732MB, too big for a 700MB CD.

So, what accounts for the difference? Is it down to different file systems?

---

### Post by wilee-nilee on 2012-05-07
The cd's/iso's are compressed for install.

---

### Post by oldfred on 2012-05-07
I wonder if that is why some Windows folks are having trouble burning CD?

I used Ubuntu to burn the ISO and it burned & installed without any issue. But maybe some burners do not like the oversize ISO. My CD says it is 730.9 and as an ISO on my hard drive it is 732.2 but the difference is often rounding or sector size or something.

---

### Post by buzzingrobot on 2012-05-07
> **wilee-nilee said:**
> The cd's/iso's are compressed for install.

Right, but the image would not be decompressed as it was written to my drive.

---

### Post by wilee-nilee on 2012-05-07
> **buzzingrobot said:**
> Right, but the image would not be decompressed as it was written to my drive.

A image is a clone a cd is compressed, your syntax makes this confusing to be honest.

---

### Post by buzzingrobot on 2012-05-07
> **oldfred said:**
> I wonder if that is why some Windows folks are having trouble burning CD?

I used Ubuntu to burn the ISO and it burned & installed without any issue. But maybe some burners do not like the oversize ISO. My CD says it is 730.9 and as an ISO on my hard drive it is 732.2 but the difference is often rounding or sector size or something.

Seems likely.  My CD's were 700MB but I'd forgotten that, so I was trying to fit a 732MB cat in a 700MB bag.

I'm just curious why the images on the mirrors show different sizes locally.

---

