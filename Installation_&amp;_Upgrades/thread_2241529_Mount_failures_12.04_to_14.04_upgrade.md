---
title: "Mount failures 12.04 to 14.04 upgrade"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by p3t3rholm3s on 2014-08-26
I have a 2012 HP Pavilion Slimline with a 1T Hard drive, 4GB RAM and it came pre-loaded with Windows 7 home. Installed Ubuntu 10.04 LTS in 2012 and have since upgraded to 12.04. Upgraded to 14.04 Aug. 18, the process took a little more than an hour and at some point a prompt asked a yes/no question (that I cannot remember.) I answered yes and it continued. When the upgrade was finished I pressed the restart option the Update Manager closed but the desktop froze.  After about 5 minutes I forced a shutdown. I selected Ubuntu at the grub menu below is what appeared Ubuntu did not:
Mount: mounting /dev/loop0 on /root failed: invalid argument
Mount: mounting /dev on /root/dev failed: No such file or directory
Mount: mounting /proc on/ root / sys failed: No such file or directory
Target filesystem doesn't have requested /sbin/init
No init found.  Try passing init = bootarg
BusyBox v1.21.1 (Ubuntu 1:1.21.0-1 ubuntu 1) built-in shell (ash)
Enter ‘help’ for a list of built-in commands
(initramfs)
The only way to get out of the screen was to do another forced shutdown. I have spent the week reading posts, bug reports, Wubi mega-thread, etc., and the only thing close to this problem was a thread of five posts "Trouble upgrading 12.04 to 14.04" but no solution.  I have burned a 14.04.1 iso DVD from the ubuntu site (though I think it is faulty as the graphics and options are dissimilar to what is shown on the site) and attempted the noorez hassam initramfs fix suggested by hakuna-matata but the terminal says that distribution is read only. Also purchased an external hard Drive and backed up my windows files and made a system image as I have read that a new install tends to erase rather than partition and confirmed as much by partially going through the install process to find that the Windows OS was not recognized and selecting something else did not inactivate the first option. Only need to retrieve (if possible) bank statement pdfs and a spreadsheet - how can I do that?

---

### Post by yancek on 2014-08-26
You mention 'wubi' in the last paragraph so I'm wondering if this was an install inside windows 7 of your Ubuntu?  Wubi is no longer supported on 14.04 though it might work with windows 7.

If you are getting a message that the filesystem is read only then you are  most likely trying to make changes on the DVD rather than the hard drive.

Retreiving your data can be done from the DVD.  You would need to mount the partition on which the data currently resides and also mount the partition you want to copy to.  Probably need to use sudo to copy.  Is that data on Ubuntu or windows?

---

### Post by p3t3rholm3s on 2014-08-26
Hello Yancek, I have seen your name on other threads. Yes my original install in 2012 was inside of windows (wubi) and I can see there is an ubuntu folder in my C Drive, a Wubi folder inside of that folder, a 130 kb wubildr text document (intalled on the 18th) and an 8 kb wubildr.mbr text document (intalled in 2012) in the C Drive but separate from the folders. And yes I have read endlessly on the unsupported status of wubi but am still unclear as to how to "mount" a partition, much less access Linux data stored inside of a windows partition that seemingly is not recognized. I am baffled as to where or how to start.

---

### Post by p3t3rholm3s on 2014-08-27
Blind trust has certainly been my problem. In wasting 8 days reading sanctimonious drivel by non-apologetic apologists that not so subtlety condemn my computer illiteracy as laziness and that paint my lack of contributions to the community as a member undeserving of meaningful advise, I have yet to see either a concerted effort to fix an obvious defect nor an intelligent stab to explain why something that previously was innocuous - the  release of new kernel via a notification that a new upgrade was available to download - became means to install a stealth corrupter of data for anyone foolish enough to accept the offer. Certainly valuable lessons have been learned, vocabulary has been increased, but it is time to do better research and find a less adversarial Linux distribution.

---

