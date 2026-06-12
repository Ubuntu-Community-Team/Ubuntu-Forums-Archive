---
title: "Installation of Ubuntu &quot;TO&quot; (not from) USB key/thumb drive"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2012-08-20
Need a synopsis of correct method of installing Ubuntu TO a USB thumb drive, i.e. so that the operating system can be installed, configured & ran from the USB drive.

Thanks.

---

### Post by kurt18947 on 2012-08-20
I have a 8 GB. drive with Xubuntu installed on it.  I used Gparted to delete the USB drive's FAT partition and create an ext2 partition.  Then I installed as per usual.  I used the 'something else' or 'advanced' choice on the installer to make sure the install **and GRUB **went onto the the USB drive -  sdb, sdc or whatever.  Sda is most likely your internal hard drive, be sure nothing gets written there.

I have not done so yet but I want to get a USB 3 flash drive and try a 'real' install (not a live install) on one of those.  They seem to have read/write speeds that exceed commonly available USB 2 flash drives.  I'm thinking they may be faster even on a USB 2 port.  Perhaps something like this:

		[     [IMG]http://images17.newegg.com/is/image/newegg/20-233-210-TS?$S125W$[/IMG]    ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820233210") 		
		 [  (112)]("http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16820233210") 		 		     			     				    Compare 			    
 			 		
 	 	 	     	         		    [ 			     			    CORSAIR Flash Voyager 16GB USB 3.0 Flash Drive Model CMFVY3S-16GB 		    ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820233210") 		
 		 		  		
[LIST]
[*]**USB Specification:** USB 3.0
[*]**Read Speed:** up to 52 MB/s
[*]**Write Speed:** up to 23 MB/s
[*]**Dimensions:** 74mm x 23mm
[*]**Model #: **CMFVY3S-16GB
[*]**Item #: **N82E16820233210
[*]$18.99 from NewEgg.
[/LIST]

---

### Post by wpshooter on 2012-08-20
> **kurt18947 said:**
> I have a 8 GB. drive with Xubuntu installed on it.  I used Gparted to delete the USB drive's FAT partition and create an ext2 partition.  Then I installed as per usual.  I used the 'something else' or 'advanced' choice on the installer to make sure the install **and GRUB **went onto the the USB drive -  sdb, sdc or whatever.  Sda is most likely your internal hard drive, be sure nothing gets written there.

I have not done so yet but I want to get a USB 3 flash drive and try a 'real' install (not a live install) on one of those.  They seem to have read/write speeds that exceed commonly available USB 2 flash drives.  I'm thinking they may be faster even on a USB 2 port.  Perhaps something like this:

		[     [IMG]http://images17.newegg.com/is/image/newegg/20-233-210-TS?$S125W$[/IMG]    ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820233210") 		
		 [  (112)]("http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16820233210") 		 		     			     				    Compare 			    
 			 		
 	 	 	     	         		    [ 			     			    CORSAIR Flash Voyager 16GB USB 3.0 Flash Drive Model CMFVY3S-16GB 		    ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820233210") 		
 		 		  		
[LIST]
[*]**USB Specification:** USB 3.0
[*]**Read Speed:** up to 52 MB/s
[*]**Write Speed:** up to 23 MB/s
[*]**Dimensions:** 74mm x 23mm
[*]**Model #: **CMFVY3S-16GB
[*]**Item #: **N82E16820233210
[*]$18.99 from NewEgg.
[/LIST]

Thanks.

What do you mean by "REAL" install - I don't understand, sounds like what you described earlier would be a real install ???

---

### Post by oldfred on 2012-08-20
Most installs to a USB flash are the installer or liveCD version. Some add persistence to save some data, but that does not let you update system.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

An install to a flash drive is not really different than any install to a second drive. You have to use manual install to get the option on which drive's MBR to install the grub2 boot loader which must be the flash drive.

Also for flash you may want some of the settings like a SSD to reduce writes as flash is slow writing. USB ports are also slower than SATA ports but my full install of Ubuntu works reasonably well even if not speedy.  Having more RAM helps as Linux caches data in RAM which can help speed things.

A lighter weight version may work a bit faster as it does not load the larger applicatons.
Installs to 4GB flash, newer of Ubuntu versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Now a bit older but installer has not really changed much:
It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

