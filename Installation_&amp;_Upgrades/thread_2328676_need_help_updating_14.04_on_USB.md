---
title: "need help updating 14.04 on USB"
date: 2016-06-23
forum: Installation &amp; Upgrades
---

### Post by sam_baker2 on 2016-06-23
hi, I am trying to update a USB with xubuntu 14.04 on it and it has not been updated in about 6 months. When I try to boot it up, the xubuntu splash screen comes up briefly, then the screen goes black with nothing but a little blinking curser in the upper left corner.  Is there a way to bypass this and get the gui to run?  thks

---

### Post by oldfred on 2016-06-23
Is this a full install of Ubuntu or the flash drive installer version?

What hardware, brand, model & video card/chip?

Most often video driver issue.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by sam_baker2 on 2016-06-23
thks for reply oldfred
This is ( I believe ) a full install off of a CD
 Xubuntu 14.04 LTS

This is a Lenovo laptop Thinkpad, Intel chip 4 core, 4 G ram.
The video card is :
```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```
Don't know what chip it is.
I tried changing no splash to nomodeset, but that didn't work.

---

### Post by oldfred on 2016-06-23
Intel often needs a different setting than nomodeset, and many laptops need other settings also:

 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# very new Skylake may need this (not yours, just for reference):
      
 Skylake needs this boot parameter:  i915.preliminary_hw_support=1 
    # Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic 

Some versions seem to be missing a package also?

 [http://ubuntuforums.org/showthread.php?t=2324014](http://ubuntuforums.org/showthread.php?t=2324014)
[https://plus.google.com/114536168681668531284/posts/AcTu9Kmep3o](https://plus.google.com/114536168681668531284/posts/AcTu9Kmep3o)
I checked the difference between xubuntu and lubuntu ISO, and this
package is missing :
xserver-xorg-video-intel
> If you have people affected by black screen, or no X starting, or no
lightdm starting, with Intel card, could you advise them to install
this package, reboot, and see if it's working (and report back) ? 



I have links to a lot of different Lenovo models, but issues do not seem consistent across  many models, only very similar models. Other brands often have same issue across many or most models.

---

### Post by sam_baker2 on 2016-06-23
thk oldfred.
I tried downloading xserver-xorg-video-intel and that didn't work.
I have been wanting  to install 16.04 on this usb anyway, so I think I will
get the .iso and do that. There is nothing much on the chip anyway.

---

### Post by oldfred on 2016-06-23
You cannot install the xserver-xorg... in the live installer, only after you have installed.

Which model Lenovo is it?

---

### Post by sam_baker2 on 2016-06-25
I completely upgraded to 16.04, and everything works, but when i do a sudo apt-get update, i get this:

```

Hit:1 http://security.ubuntu.com/ubuntu xenial-security InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [94.5 kB]
Ign:4 http://extras.ubuntu.com/ubuntu xenial InRelease                              
Ign:5 http://extras.ubuntu.com/ubuntu xenial Release                                
Hit:6 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease     
Hit:7 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease      
Ign:8 http://extras.ubuntu.com/ubuntu xenial/main Sources
Ign:9 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages
Ign:10 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages
Ign:11 http://extras.ubuntu.com/ubuntu xenial/main all Packages
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en
Ign:14 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons
Ign:8 http://extras.ubuntu.com/ubuntu xenial/main Sources
Ign:9 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages
Ign:10 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages
Ign:11 http://extras.ubuntu.com/ubuntu xenial/main all Packages
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en
Ign:14 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons
Ign:8 http://extras.ubuntu.com/ubuntu xenial/main Sources
Ign:9 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages
Ign:10 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages
Ign:11 http://extras.ubuntu.com/ubuntu xenial/main all Packages
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en
Ign:14 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons
Ign:8 http://extras.ubuntu.com/ubuntu xenial/main Sources
Ign:9 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages
Ign:10 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages
Ign:11 http://extras.ubuntu.com/ubuntu xenial/main all Packages
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en
Ign:14 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons
Ign:8 http://extras.ubuntu.com/ubuntu xenial/main Sources
Ign:9 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages
Ign:10 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages
Ign:11 http://extras.ubuntu.com/ubuntu xenial/main all Packages
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en
Ign:14 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons
Err:8 http://extras.ubuntu.com/ubuntu xenial/main Sources
  404  Not Found [IP: 91.189.92.152 80]
Err:9 http://extras.ubuntu.com/ubuntu xenial/main amd64 Packages
  404  Not Found [IP: 91.189.92.152 80]
Err:10 http://extras.ubuntu.com/ubuntu xenial/main i386 Packages
  404  Not Found [IP: 91.189.92.152 80]
Ign:11 http://extras.ubuntu.com/ubuntu xenial/main all Packages                                                                                                                                
Ign:12 http://extras.ubuntu.com/ubuntu xenial/main Translation-en_US                                                                                                                           
Ign:13 http://extras.ubuntu.com/ubuntu xenial/main Translation-en                                                                                                                              
Ign:14 http://extras.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata                                                                                                                       
Ign:15 http://extras.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons                                                                                                                          
Fetched 94.5 kB in 6s (14.3 kB/s)                                                                                                                                                              
Reading package lists... Done
W: The repository 'http://extras.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/xenial/main/source/Sources  404  Not Found [IP: 91.189.92.152 80]
E: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.152 80]
E: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/xenial/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.152 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

```


when I do a sudo apt-get install samba, I get this:

```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

So, I did a sudo dpkg --configure -a, and I get this:

```

dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 4.4.0.24.25); however:
  Version of linux-headers-generic on system is 4.4.0.21.22.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-generic

```

Any ideas?

---

### Post by oldfred on 2016-06-25
I do not know what this is?
[http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu)

Did you add a ppa? It looks like that site then does not have xenial?
So you should remove from sources list.

---

