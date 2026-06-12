---
title: "How to open a partittion of previous installation?"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by mastermind008 on 2010-01-01
I had 3 partition with my laptop.

1.Ubuntu 9.10 System(root)
2.Media partion called "Projects"
3.Windows 7 partition.

I had a problem with my 'PHS100' HSDPA modem while connecting to the internet, and once I plugged it to another PC, it didn't work for my Laptop again when I boot it with Ubuntu. So I have to boot my laptop with windows, then the indicator becomes green, after that I can reboot with Ubuntu & use my modem as normal. Once my windows partition got currupted & I re installed windows 7 to the same partition that I had allocated for windows(above mentioned partition 3.

Then I saw That my entry points to log in to Ubuntu had been removed & boot screen doesn't give me any option to select ubuntu, but it boots with windows 7 automatically. When I boot with a Ubuntu Live CD, and tried to open the "Ubuntu (ext-3)media partition (Projects, above mentioned partion 2) it didn't allow me, even if I knew the root password of previous installation.

What can I do to open that partition again, without losing any data?

I downloaded an ISO of Ubuntu 64-bit again, and tried to install again to the above mentioned partition 1.But unfortunately that ISO image had some errors and installation was failed. So I'm gonna download it again & install it again on 'Partition 1' (as Above mentioned, without making any change on 'Projects' partition (2).

Please help me to overcome this problem.

---

### Post by tommcd on 2010-01-01
> **mastermind008 said:**
> ... I re installed windows 7 to the same partition that I had allocated for windows(above mentioned partition 3. ...

Then I saw That my entry points to log in to Ubuntu had been removed & boot screen doesn't give me any option to select ubuntu, but it boots with windows 7 automatically. ...

This is the expected behavior. When you reinstall Windows it overwrites the master boot record (MBR) so grub2 no longer controls booting your computer. You could have just reinstalled grub2 from the Ubuntu 9.10 live CD:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)
[http://ubuntuforums.org/showthread.php?t=1306900](http://ubuntuforums.org/showthread.php?t=1306900)
However reinstalling Ubuntu to the original Ubuntu partition will accomplish the same thing, just with more work.
Since you tried and failed to reinstall Ubuntu with the corrupted CD, your current Ubuntu install is quite likely broken. So download and burn a new CD. If you are burning the CD from Windows, use either Iso Recorder or Infra Recorder, and be sure to burn the CD at the slowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then when you boot the CD, first choose the option "check CD for defects". If the CD passes the check then it is ok to install with it.

---

### Post by SecretCode on 2010-01-01
A windows install will wipe out the boot entry for linux. But it should not have touched the existing ubuntu installation, so you should not have needed to reinstall.

Do you know if your original boot loader was grub, or grub2, or windows' loader?

> **mastermind008 said:**
> When I boot with a Ubuntu Live CD, and tried to open the "Ubuntu (ext-3)media partition (Projects, above mentioned partion 2) it didn't allow me, even if I knew the root password of previous installation.
But could you see partition 1, which has the Ubuntu installation on? 

How did you tried to access partition 2 'media' and what error message did you get?

---

