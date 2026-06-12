---
title: "Error while installing Ubuntu 10.04 via Wubi"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by androidcupcake on 2010-09-22
I am trying to install Ubuntu from Windows using Wubi. 

Here's the screenshot of the error I receive: 

[http://dl.dropbox.com/u/2387250/Error.JPG](http://dl.dropbox.com/u/2387250/Error.JPG)

I have all the installation files in the same folder as Wubi. 

P.S the above error message appears when I am not connected to the internet.

When I am connected to the internet, Wubi tries to download the files. 

Here's the screenshot: [http://dl.dropbox.com/u/2387250/Capture.JPG](http://dl.dropbox.com/u/2387250/Capture.JPG)

My question: 

I have a 32-bit Intel motherboard. Why is it trying to download "amd64.iso" ?? :confused:

And why is it trying to download the files off of the internet when I have all the installation files in the same folder.

Screenshot of the files in the folder: [http://dl.dropbox.com/u/2387250/wubi%20folder%20files.JPG](http://dl.dropbox.com/u/2387250/wubi%20folder%20files.JPG)

I have previously successfully installed Ubuntu within Windows without Wubi downloading the "amd64.iso" files or without any such problem. 

Solution??

Thanks!

---

### Post by Chame_Wizard on 2010-09-22
Using WUBI can give problems and has [a limit]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29#Limitations").

I never used WUBI,always fresh installs with the Live CD/DVD(and soon via USB stick.

---

### Post by bcbc on 2010-09-22
wubi.exe looks for the .iso within the same folder. It look like you've got the .iso mounted - or are you running it from a CD?

If wubi.exe can't find a suitable .iso it downloads one from the net.

You can also override wubi.exe with the "--32bit" command line option so that it downloads the 32bit .iso - but it will automatically take whatever .iso it finds in the same folder provided it is valid and also the correct version (the same exact release as wubi.exe). It still needs internet access to check the md5sum of the .iso, or you can supply "--skipmd5check" instead (but I don't recommend this)

---

### Post by androidcupcake on 2010-09-24
> **bcbc said:**
> wubi.exe looks for the .iso within the same folder. It look like you've got the .iso mounted - or are you running it from a CD?

If wubi.exe can't find a suitable .iso it downloads one from the net.

You can also override wubi.exe with the "--32bit" command line option so that it downloads the 32bit .iso - but it will automatically take whatever .iso it finds in the same folder provided it is valid and also the correct version (the same exact release as wubi.exe). It still needs internet access to check the md5sum of the .iso, or you can supply "--skipmd5check" instead (but I don't recommend this)

Thanks mate! I dumped the Wubi aside and installed it separately. So far so good :)

---

### Post by bcbc on 2010-09-24
> **androidcupcake said:**
> Thanks mate! I dumped the Wubi aside and installed it separately. So far so good :)

That's a good idea. Wubi is good to try out ubuntu or if you're not ready or able to repartition your drive. A proper install is always better.

---

