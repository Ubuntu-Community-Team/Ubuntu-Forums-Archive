---
title: "Windows keeps trashing my MBR !"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by asearle on 2010-01-23
Hi everyone,

I had a problem with grub where everything would hang with the message 'grub loading .' and then the boot selection screen would never arrive.

I found some instructions on the Ubuntu site (Using the Ubuntu Desktop/Live CD ... Overwriting the Master Boot Record) and was able to fix the problem.  Great!

The main command is ...

sudo grub-install --root-directory=/media/root /dev/sda

But now I find that, after repairing the problem, I can boot Windows (everything works fine) but when I reboot the 'grub loading' problem returns and I have to fix the problem again.

Arrgghh!

What can this be?  How can I stop Windows messing up my MBR every time I boot?

Any tips would be most welcome!

Regards,
Alan Searle

---

### Post by asearle on 2010-01-24
I've just tried again and booted to Windows so that I could install all updates for Windows and for my virus scanner.  My suspicion was that it was maybe a virus that was trashing my grub/MBR ... but I have the same problem:  I get to GRUB Loading and no further.

I will fix it again and boot to Ubuntu (which doesn't trash my MBR) but I must say that this problem is driving me crazy.

How can it be that I can fix the problem easily but, every time I boot Windows, I find that next time I boot, the MBR is buggered again.

Arrgghh!

Can anyone help me with this?

Regards,
Alan

---

### Post by oldfred on 2010-01-24
There are some windows virus scanners that see a non windows boot loader and assume that it is a virus. Also issues with several other programs particularly HP. Notes from other threads:

HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. 
Thus it seems the my antivirus scans the master boot record and as it finds something strange (Grub), it kind of deletes it and make my Boot bugged.

---

