---
title: "Can we install and run Ubuntu 8 / 9 (x32) on a x64 bit machine?"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by brainbugg on 2011-03-04
Hello, I see only a black screen after the language selection screen during the setup of Ubuntu 9 and 8, I tried it many times, with different DVDs. What is the problem? I think my distro is x32 (though there's nothing written on the cover) and my laptop is x64 bit (Dell Inspiron 5610 . Is it because of that reason?

Can't we install x32 bit Linux on x64 machine? but with Windows, we can, and I've done it...

---

### Post by oldos2er on 2011-03-04
Yes, you can run a 32-bit OS on a 64-bit processor; I doubt this has anything to do with your problem. Have you checked the disc integrity of the CDs or DVDs you're using? Did you burn them at the slowest possible speed?

---

### Post by brainbugg on 2011-03-04
> **oldos2er said:**
> Have you checked the disc integrity of the CDs or DVDs you're using? Did you burn them at the slowest possible speed?

The first two DVDs (Ubuntu) and (Kubuntu) were original DVDs requested from right from Ubuntu's website. The third one was the one I burnt using Nero without any errors. Besides, I get the same errors.

Any other ideas?  :confused:

---

### Post by Skaperen on 2011-03-04
I've seen the Ubuntu install hang in these older versions due to the hard drive having a geometry setting with 256 heads.  There has been some past misconceptions by the developers of several tools that MBR geometry was limited to 255 heads.  But, 256 is in fact perfectly valid.  But many of these tools (some have since been fixed) do wrong things when faced with such a geometry found in the MBR.  I have not had the opportunity to test this in newer versions.  But it definitely is a problem in 9.04 and the symptom is a hang during the install.

If you do not need to save any data on the disk, the simple work around for this problem (I'm not sure this is the problem you have) is to zap the partition table on the disk (which destroys all data).  This can be done by booting a LiveCD and doing:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=34
```

---

### Post by brainbugg on 2011-03-04
> **Skaperen said:**
> I've seen the Ubuntu install hang in these older versions due to the hard drive having a geometry setting with 256 heads.  There has been some past misconceptions by the developers of several tools that MBR geometry was limited to 255 heads.  But, 256 is in fact perfectly valid.  But many of these tools (some have since been fixed) do wrong things when faced with such a geometry found in the MBR.  I have not had the opportunity to test this in newer versions.  But it definitely is a problem in 9.04 and the symptom is a hang during the install.

If you do not need to save any data on the disk, the simple work around for this problem (I'm not sure this is the problem you have) is to zap the partition table on the disk (which destroys all data).  This can be done by booting a LiveCD and doing:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=34
```

Thanks for the answer. 
I'm not an advanced user of Ubuntu. But yes, i understand that u mean the probable problem is something about the Master Boot Record, and yes the installation does hang during the install, with a black blank screen.

I can run the LiveCD, and hit that command. But I have two drives with NTFS file system (I want them intact, thought I have removed Windows already), will it pose any risk to the data I have in those drives?

P.S. Do you think installing the newer versions rather than the older ones will help?

---

### Post by Skaperen on 2011-03-04
> **brainbugg said:**
> Thanks for the answer. 
I'm not an advanced user of Ubuntu. But yes, i understand that u mean the probable problem is something about the Master Boot Record, and yes the installation does hang during the install, with a black blank screen.

I can run the LiveCD, and hit that command. But I have two drives with NTFS file system (I want them intact, thought I have removed Windows already), will it pose any risk to the data I have in those drives?

P.S. Do you think installing the newer versions rather than the older ones will help?
DO NOT RUN THE COMMAND I GAVE.  Yes, it poses a risk.  My command will wipe the entire drive.

You can, instead, do the following command to see if the situation might be present.  If it shows that it is, it probably is.  If it shows not, it's still possible that it is.  Sometimes, this command gives wrong answers.  Anyway, boot an Ubuntu disk and choose "try Ubuntu" to run the Live CD.  Then open a terminal and do this command:

```
fdisk -lu /dev/sda
```

Note around the 2nd line of output where it says "heads" and "sectors".  If it says "256 heads" then you have the problem.

Since you have data on this disk, do not run the command given in the previous post.  You will need to make 2 backups of that data to proceed safely.

This is all assuming this particular problem is what is causing your blank screen and hanging situation.  There are other possible causes.  I'm just describing one of them I know about.  Your problem may be something else.

---

### Post by oldos2er on 2011-03-04
> **brainbugg said:**
> The first two DVDs (Ubuntu) and (Kubuntu) were original DVDs requested from right from Ubuntu's website. The third one was the one I burnt using Nero without any errors. Besides, I get the same errors.

Any other ideas?  :confused:

So, did you run the 'Check disc integrity' option? I think it's one of the selections of the first menu that pops up. You could also do this: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
It helps to rule out any potential disc problems. Also, have you tried the discs in a different machine?

Can you tell us the hardware specs of the computer?

---

