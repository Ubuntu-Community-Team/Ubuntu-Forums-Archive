---
title: "When doing upgrade to 10.10: error: Input/output error during read on /dev/sda"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by l0uismustdie on 2010-11-01
Hello.  I have been having some trouble with a Gateway-MT6460 that was running 32-bit Ubuntu 10.04 so I decided to upgrade to 64-bit 10.10.  When attempting to do the upgrade though I am faced with this error during installation:
```

ERROR!!!
Input/output error during read on /dev/sda
Retry Ignore Cancel

```
Any ideas what might be going on here?

Additionally if I try to cancel through this error I am presented with 
```

Warning!
Error fsyncing/closing /dev/sda: Input/output error
Retry Ignore

```

Retry and ignore here will not get me anywhere.

---

### Post by l0uismustdie on 2010-11-07
bump?

---

### Post by tommcd on 2010-11-07
Are you trying to do a dist-upgrade from 32bit to 64bit Ubuntu? If so, this is not possible. You would need to do a clean install of 64bit Ubuntu.
I do not think that switching from 32bit to 64bit will solve any problems you may be having though.
```

ERROR!!!
Input/output error during read on /dev/sda
Retry Ignore Cancel

``` 
As for that error, be sure to burn the CD at the slowest possible speed. Also, be sure to run the option "*Check disc for defects*" when you first boot the Ubuntu CD to be sure the CD is valid. This error sounds like a bad CD.

---

### Post by l0uismustdie on 2010-11-08
I am trying to do this install from a USB key.  I tried your suggestion though and made a new key from a new download but this turned out to have the same results.  Any other ideas?

---

### Post by tommcd on 2010-11-08
Is /dev/sda your internal hard drive that you are trying to install Ubnuntu on? A usb drive would usually be listed as /dev/sdb, with sda being the internal hard drive.

All of the googling I have done points to a corrupt file system as the source of errors like this. In other words, /dev/sda is corrupt.

According to this:
[http://support.gateway.com/s/Mobile/2007/Oasis/2905931R/2905931Rsp2.shtml](http://support.gateway.com/s/Mobile/2007/Oasis/2905931R/2905931Rsp2.shtml)
Your Gateway-MT6460 has an optical drive. Can you boot from the optical drive? Have you tried burning a Ubuntu CD and installing from that. That would be the easiest way to go.
Also, verify the md5sums of the Ubuntu iso image you downloaded to be sure it is not corrupt.

---

### Post by psusi on 2010-11-08
Your drive may be failing.  Open the disk utility and look at the SMART statistics for errors.

---

### Post by l0uismustdie on 2010-11-15
Yeah...so I looked at the SMART statistics and it looks like this HD is just going down to drain so to speak.  Thanks for all your posts.

---

