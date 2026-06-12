---
title: "Can I upgrade from 13.10 32-bit to 64-bit?"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by leftyleo on 2013-12-28
I installed Ubuntu 13.10 not long ago... starting to set things the way I will like them, including web access and printers.
But I have just noticed that it installed the 32-bit version though I have a 64-bit processor (Intel® Core™ i3 CPU M 330 @ 2.13GHz × 4 )
with 8G ram .. 

My question is two-fold: 
Can I upgrade to the 64-bit version... without starting from scratch?  and the second part is whether it is advisable or not? (perhaps I should stick to 32bit os?)

Thank you (from a relative newbie)
LeftyLeo / Jim

---

### Post by vanadium on 2013-12-28
You cannot "upgrade": it is a fresh reinstall. I expect that you could resuse your user config data in the /home directory safely, provided you are installing an identical version (except for the fact that it is 64 bit.
 
64 bit Ubuntu uses more RAM. With sufficient RAM, 64 bit might be faster in some cases. In practice, you may prefer not to bother. If at some point in the future, you want to install a new version  of Ubuntu from scratch, you can then swith to 64 bit.

---

### Post by oldfred on 2013-12-28
I did the conversion with 9.10 as new 64 bit install.
Back up /home. Make a list of installed applications to make it easy to reinstall. If you made any specific system wide setting changes those would be in /etc. My backup procedure is just to do a new install so it covers the details.
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
You do not need temporary files.

 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

      
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

      
 Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)
      
 Post by VeeDub on choosing 64 bit:
[http://ubuntuforums.org/showthread.php?t=2133616&p=12594619#post12594619](http://ubuntuforums.org/showthread.php?t=2133616&p=12594619#post12594619)
[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)

   Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by leftyleo on 2014-01-08
Thank you everyone -  I think for now, as I am new, I will keep the 32-bit on this laptop.  I had hoped that a new install, even if i had to wait for 14.10, that the conversion / upgrade would be automatic if I chose it at upgrade time.  But that had to be major changes 32 to 64-bit OS. 

Thanks again and onward to learning Ubuntu (and probably Mint at the same time, to experiment on) 
-LeftyLeo

---

### Post by mastablasta on 2014-01-09
it can't be as easy as that because you need to replace all programs, drivers and libraries, not just kernel. as mentioned you can probably keep the settings and configs. i think you would benefit from 64bit and in my opinion in your case it is worth to do a reinstall. especially since you still basically just started. or oyu can do reinstall when 14.04 comes out. if you do the upgrade it will likely overwrite most of your settings anyway ;-)

---

### Post by oldfred on 2014-01-09
If you have a decent sized hard drive which it sounds like you may, just create a new 10 to 20GB partition and install the 64bit version. Lets you test it, and see if you like it.

---

### Post by Bucky Ball on 2014-01-09
> **oldfred said:**
> If you have a decent sized hard drive which it sounds like you may, just create a new 0 to 20GB partition and install the 64bit version.

^^^
This.

If you have created a /home and /swap partition for the other install, the new install can use them, no need to create new ones for it.

---

