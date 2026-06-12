---
title: "Installation of 14.04.1 Hangs at &quot;Running update-grub...&quot;"
date: 2014-09-23
forum: Installation &amp; Upgrades
---

### Post by 3guesses on 2014-09-23
Hi,

I have been trying out various Linux distros and to that end have installed them to a number of logical partitions on my MSI laptop from USB stick using the very excellent WinSetupFromUSB v1.4 (highly recommended, BTW).  Last night I tried to install Xubuntu 14.04.1 to a fresh 8GB /dev/sda16 partition and it hung at the "Running update-grub..." stage.  After a while I opened the debug (?) window, and the end of it said (excuse typos):

```
:
:
xubuntu linux-boot-prober: debug: linux detected by /usr/lib/linux-boot-probes/50 mounted-tests
/usr/lib/ubiquity/ubiquity/frontend/gtk-components/nmwidgets.py: 18: Warning: Source ID 14907 was not found when attempting to remove it
GLib.source_remove(self.timeout_id)

```

And these final 2 lines were repeated a lot of times (I think the "18:" alternated with "30:") with different ID numbers.  The ones I had room to write down were: 14932, 15019, 15087, 15100, 15158, 15165, 15195, 15245, 15303, 15309, 15336, 15388, 15432, 17190, 17220, 17705, 17730,17814, 17902, 17908, 17928, 18059, 18140, 18257, 18281, 18363.  I think the final ID shown was 19886.  I tried pressing Ctrl-C, but it didn't have any effect and in the end I pressed the power button on my laptop; this had the effect of cancelling the install and rebooting the machine.  I tried booting the installation, and it got as far as something to do with intialising CUPS but then hung, so it is not usable.

Last night I also tried to update my installation of Linux Lite 2.0 (which I believe is also Ubuntu-based), and that got most of the way through and then ran into problems during the update-grub stage - I don't know if it is the same problem?  I did Ctrl-C out of that and it seemed to recover, but when I tried to install some other software it reported that there was an error and I needed to run pkgtool (I think) manually to correct it, which again hung at the update-grub stage.

I had no problem when I installed Xubuntu 12.0.4 on /dev/sda7, but I don't want to try updating that in case I run into similar problems.

Can anybody help?

Thanks,

3g

---

### Post by TheFu on 2014-09-23
Please run **boot-info** - my signature has links.

---

### Post by oldfred on 2014-09-24
@TheFu
Signature not showing? If you update it, it immediately changes in all your old posts as it is dynamically reloaded.

Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by TheFu on 2014-09-24
Yeah - I tried to edit the original - there doesn't seem to be a way to add a signature after the fact.  My habit is NOT to put it into posts - habit won. See below for the link to the link to the link ... er ... or use google.

---

### Post by 3guesses on 2014-09-24
Update: I decided to delete some logical partitions and attempt the installation again.  The partitions I deleted were sda13 (Vector Linux 7.2.0: seemed to install OK, but kernel panic during boot), sda14 (PC Linux OS 2014: hung during boot), sda15 (Linux Mint 17: installed and booted OK), sda16 (Xubuntu 14.04.1: installation problem, hung during boot - as reported).  So I created a fresh 8GB sda13 partition and this time Xubuntu 14.04.1 installed OK and now boots no problem, so I'm guessing the previously extant installation of Vector Linux 7.2.0 and/or PC Linux OS 2014 were the cause of the Xubuntu 14.04.1 installation problem.  I did keep the debug window open during the install and did, however, notice what looked like a few weird errors being reported - if the install log is stored somewhere and you think it would be helpful at all I'm happy to post it.

Also, after the above action I was able to correct the problem with Linux Lite 2.0 (running "dkpg --configure -a" I think), so things are looking pretty hunky dory now.

I think I will try to install PC Linux OS 2014 again as the Vector Linux installation might have been the culprit in all of this.  Unfortunately, I've been having trouble registering at the VL website so I can't post there to try to sort out the problem with that install...

3g

PS **boot-info** sounds interesting - what is the link?

---

### Post by oldfred on 2014-09-24
Posted above.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

But I like to run the script just to document my system. And include that in my rsync backup script so I always have a current copy in my backup.

      
 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Not sure if anyone is still maintaining bootinfoscript. And with grub2 latest version it does not parse MBR correctly 
This fork fixes that minor bug.


 Few fixes in a fork of bootinfoscript
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

---

