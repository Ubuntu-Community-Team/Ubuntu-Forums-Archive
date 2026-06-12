---
title: "New system any comments on it's specs for Linux?"
date: 2016-09-28
forum: Installation &amp; Upgrades
---

### Post by Roger_Williams on 2016-09-28
I was going to buy a used laptop but decided I could get a good deal on a new laptop. This is the laptop I purchased [http://www.dell.com/ca/p/inspiron-15-5555-laptop/pd?oc=ni155555_btsb_b2823e&model_id=inspiron-15-5555-laptop](http://www.dell.com/ca/p/inspiron-15-5555-laptop/pd?oc=ni155555_btsb_b2823e&model_id=inspiron-15-5555-laptop) any comments on it's eligibility to be used with Linux? 

My only real concern before purchase was the max RAM because I wanted to be able to run virtual machines without them being unusable. I think to begin I'll run Ubuntu with a virtual Kali but may at some point dual boot Ubuntu and Kali.

---

### Post by Impavidus on 2016-09-28
You can run a typical Linux system in 2 GB, so 12 or 16 GB should be enough for a virtual machine. The hard drive is a bit slow, but shouldn't keep you waiting more than a minute a day. I don't know about the integrated AMD graphics, which might need some attention.

---

### Post by Bucky Ball on 2016-09-28
There's a [few of these]("http://www.dell.com/en-us/shop/productdetails/inspiron-15-5000-series") and thinking the GPU may change depending on which you go for. The description they give in the link you provided is for the 5000 series and the description of the GPU generic. Guess you need to go for a specific model in the series to find specific GPU ... or something.

People seem to have Ubuntu 16.04 working on the 5000 series, though. Here's some guy on Youtube with it running on a 5000 series.

[https://www.youtube.com/watch?v=ikVufNLjnqc](https://www.youtube.com/watch?v=ikVufNLjnqc)

Here's some links from oldfred.

[https://ubuntuforums.org/showthread.php?t=2318848&p=13463018&viewfull=1#post13463018](https://ubuntuforums.org/showthread.php?t=2318848&p=13463018&viewfull=1#post13463018)

---

### Post by Roger_Williams on 2016-09-28
> **Impavidus said:**
> You can run a typical Linux system in 2 GB, so 12 or 16 GB should be enough for a virtual machine. The hard drive is a bit slow, but shouldn't keep you waiting more than a minute a day. I don't know about the integrated AMD graphics, which might need some attention.

> **Bucky Ball said:**
> There's a [few of these]("http://www.dell.com/en-us/shop/productdetails/inspiron-15-5000-series") and thinking the GPU may change depending on which you go for. The description they give in the link you provided is for the 5000 series and the description of the GPU generic. Guess you need to go for a specific model in the series to find specific GPU ... or something.

People seem to have Ubuntu 16.04 working on the 5000 series, though. Here's some guy on Youtube with it running on a 5000 series.

[https://www.youtube.com/watch?v=ikVufNLjnqc](https://www.youtube.com/watch?v=ikVufNLjnqc)

Here's some links from oldfred.

[https://ubuntuforums.org/showthread.php?t=2318848&p=13463018&viewfull=1#post13463018](https://ubuntuforums.org/showthread.php?t=2318848&p=13463018&viewfull=1#post13463018)

Thanks guys here's the GPU [COLOR=#444444][FONT=Trebuchet MS]AMD A10-8700P APU with RadeonTM R6 Graphics featuring 10 Compute Cores (4 CPU + 8 GPU). [/FONT][/COLOR]I never even noticed the HDD was a 1TB. I've got a 750GB in my current latop that I would prob use I think it's faster. I'm happy to see that it should be able to run Ubuntu no/minimal problems.

---

### Post by oldfred on 2016-09-28
As a new system you may need 16.04, but with AMD graphics 14.04 often works better.
 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).  

If open source AMD driver works then you are ok.
Otherwise you may have to wait for final release of the new AMD driver. Beta is out now and can be installed, but best to only use in a test install.
      
 AMDGPU-PRO  beta Radeon RX 460/470/480 vs. NVIDIA Linux GPU Benchmarks
[http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1](http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1)
How Ubuntu 16.04 Is Performing With AMDGPU/Radeon Graphics Compared To Ubuntu 14.04 With FGLRX
[http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu-1604-amd&num=1) 
    
      
 Other issues:
[http://askubuntu.com/questions/794529/amdgpu-pro-install-on-ubuntu-gnome-16-04-with-r9-285](http://askubuntu.com/questions/794529/amdgpu-pro-install-on-ubuntu-gnome-16-04-with-r9-285)
[http://askubuntu.com/questions/794529/amdgpu-pro-install-on-ubuntu-gnome-16-04-with-r9-285-and-rx-480](http://askubuntu.com/questions/794529/amdgpu-pro-install-on-ubuntu-gnome-16-04-with-r9-285-and-rx-480)

---

### Post by Roger_Williams on 2016-10-13
Been on vacation just got back Tuesday and it was waiting for me =D I've formatted, partitioned the drive and installed Kali without any problems. Now I'm looking at installing Ubuntu but wondering if I should use grsync to restore the etc and home folders I backed up from my other laptop? The customization I did are not so much that I couldn't do it all again in a day or two. However if there is an easier way I'd rather do it that way. I'm just worried about screwing up this installation with drivers from my old laptop or something. What do you guys think?

---

### Post by SeijiSensei on 2016-10-13
Reinstalling /home shouldn't be an issue.  You might consider creating a separate partition for /home in case you need to futz with the OS again.

Copying stuff from /etc can be more problematic depending on what you're running and how customized it is.  Copying it all over in one fell swoop can be a recipe for problems.  Try taking things one application at a time.  For instance, if you're running Apache, move the new /etc/apache2 directory to /etc/apache2.old, then copy the old /etc/apache2 over and try to start the server.

---

### Post by Roger_Williams on 2016-10-13
> **SeijiSensei said:**
> Reinstalling /home shouldn't be an issue.  You might consider creating a separate partition for /home in case you need to futz with the OS again.

Copying stuff from /etc can be more problematic depending on what you're running and how customized it is.  Copying it all over in one fell swoop can be a recipe for problems.  Try taking things one application at a time.  For instance, if you're running Apache, move the new /etc/apache2 directory to /etc/apache2.old, then copy the old /etc/apache2 over and try to start the server.

Yes hadn't even thought of that approach. Thanks for your help :)

---

