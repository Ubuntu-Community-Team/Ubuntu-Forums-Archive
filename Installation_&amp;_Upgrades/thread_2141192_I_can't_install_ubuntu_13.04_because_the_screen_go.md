---
title: "I can't install ubuntu 13.04 because the screen goes black after I click install"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by lexen on 2013-05-01
I am trying to install ubuntu 13.04 64 bit off a DVD, but every time I choose Install and press enter, it loads for a bit, then the screen turns off and it doesn't turn back on again.  After a bit I hear the login noise, so I know something is working, I just can't see it.  I get the same error if I run the LiveDVD option.

I have a Nvidia card and I am hooking up to an HD TV through a VGA cable, so that could be messing things up.

Any help you can give would be greatly appreciated.


Thanks,
Lexen

---

### Post by oldfred on 2013-05-01
I have nVidia and have had to use nomodeset on every live installer boot and first boot after install or until I install the nVidia drivers. This has been since about 10.10 when they made some kernel changes to include video. Also which port video defaults to may be an issue, but I am not sure how you control that. 

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
apt-get update
sudo apt-get install linux-headers-generic

---

