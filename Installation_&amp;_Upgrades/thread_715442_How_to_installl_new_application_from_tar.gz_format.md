---
title: "How to installl new application from tar.gz format"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by deepblue_tiano on 2008-03-04
Good day..Hello guys i downloaded installer like apache, php, mysql, gstreamer.. I got all this installer in tar.gz format, but i dont know ho to make this files to installed on my ubuntu system..I really appreciate your help guys..

---

### Post by kool_kat_os on 2008-03-04
first extract it...

---

### Post by taurus on 2008-03-04
Why not install those apps from synaptic or Add/Remove.  Easier to upgrade them later.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by scottro on 2008-03-04
sudo apt-get install build-essential

After that, you can take a look at

[http://home.nyc.rr.com/computertaijutsu/tarball.html](http://home.nyc.rr.com/computertaijutsu/tarball.html) 

The page goes into extracting and compiling tarballs

(The build-essential will give you the necessary tools to do the compiling.)

However, keep in mind that often, these programs will be looking for various 
dependencies and libraries and if they aren't installed where the program you're trying to compile thinks they should be installed, the build will fail.

---

### Post by kool_kat_os on 2008-03-04
> **deepblue_tiano said:**
> Good day..Hello guys i downloaded installer like apache, php, mysql, gstreamer.. I got all this installer in tar.gz format, but i dont know ho to make this files to installed on my ubuntu system..I really appreciate your help guys..

just for clarification ...tar.gz is Linux's equivalent of windows' .zip files

---

### Post by kool_kat_os on 2008-03-04
taurus

how did you really get all of your beans?:confused:...that is ALOT

---

### Post by deepblue_tiano on 2008-03-04
Thank you guys for the reply..Actually i am not connected to the internet thats why i downloaded those files and saved to my flash disk..and when i type in terminal ./configure it states that there is no configure script..

---

### Post by logos34 on 2008-03-04
> **deepblue_tiano said:**
> when i type in terminal ./configure it states that there is no configure script..
 
did you cd to the top of the folder?

---

### Post by deepblue_tiano on 2008-03-05
Yes i was inside  the folder that i extracted..

---

### Post by logos34 on 2008-03-05
What exactly are you trying to install?  Give me the name and I'll check it out...

Is there a README or INSTALL file in the directory?

---

### Post by zvacet on 2008-03-05
I think it is easyer way to download deb files.If you are willling to try go for [nonetdebs.](http://nonetdebs.homeip.net/)

---

