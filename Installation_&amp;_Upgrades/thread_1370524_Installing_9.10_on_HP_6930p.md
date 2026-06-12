---
title: "Installing 9.10 on HP 6930p"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by Daug on 2010-01-02
Hello All--

I'm planning to install Karmic on my HP 6930p, along side the existing XP Pro OS. XP Pro has the entire disk (except for a 1GB HP partition). When I boot from the Ubuntu CD, I get no option to "Install Side-By-Side." I've seen this option in guides online, but it's not there when I boot from the CD that I burned (got it here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)).  All I get are the options to erase and use entire disk, or specify partitions manually.  I want to keep my existing XP partition, and split the HDD between the two OS's, so I want to make sure I do this right.  Any Advice?  Thanks.

---

### Post by Daug on 2010-01-02
Forgot to mention: I also have the option to "use largest continuous free space," as well.

---

### Post by Daug on 2010-01-02
Update(if anyone's interested =):

I booted into the liveCD, and ran gparted thru terminal. Saw a warning symbol on the NTFS partition, and selected get info on that partition. The error said that gparted was unable to read all NTFS files, and advised me to boot into Windows and run chkdsk /f. So I'm going to try that, and see if I can repair the NTFS filesystem first, then dual partition..

---

### Post by Daug on 2010-01-02
This solution worked.  I ran "chkdsk /f" (start>run) in XP, and then rebooted twice.  After that, I booted the Karmic CD, and chose Install.  The side-by-side option was then available.

Hope this helps anyone else with the same problem..

Happy Linuxing =)

---

