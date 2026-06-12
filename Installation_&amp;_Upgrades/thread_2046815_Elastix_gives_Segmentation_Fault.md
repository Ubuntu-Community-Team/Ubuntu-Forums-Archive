---
title: "Elastix gives Segmentation Fault"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by Tickon on 2012-08-23
I just installed elastix (image registration) from the Ubuntu  (12.04) repository, but I keep getting a "Segmentation fault (core  dumped)" error just after the "Reading images..." message. 

Its the first time I see a program straight out the the Ubuntu  repository that doesn't work, so I find it quite strange... 

I can't rule out a usage problem, but I followed the usage instructions closely, so it seems like an installation problem to me. 
I tried all kinds of images formats: png, jpg, tiff, dicom I tried on a  32bit and also a 64bit system, with always the same result. I used the  command this way: 
elastix -f Xray.dicom -m Xray_moved.dicom -p param_affine.txt -out out1 

where the param_affine.txt is the default parameter file found there:  [http://elastix.bigr.nl/wiki/index.php/Default0](http://elastix.bigr.nl/wiki/index.php/Default0) 

Elastix seems like a very powerful tool for image registration, I would  really like to be able to use it! 
Any idea what the problem might be? or how could I get around it? or how  I could test what might be wrong? 

Thanks for your help.

---

