---
title: "Installing alongside windows.  nvmeOn or sda?"
date: 2020-08-29
forum: Installation &amp; Upgrades
---

### Post by chruph on 2020-08-29
Hello.  I've decided to follow my heart and become a Linux user but like  many others I want to keep my  Windows 10 for emergencies.

I have a Dell Inspiron laptop with 128gb ssd and and 1TB of SD.

I followed the standard instructions to install Ubuntu and although this  meant turning off Intel RST (which windows is not happy about) I've got  Ubuntu up and running and I like it!

My problem is that its running off the HDD and boots very slowly.  I  feel like it would be better off on the my SSD but I can't find the  right tutorial specific to my situation.  When I looked at the current  partitions on the install screen I just felt overwhelmed by the amount  of them and didn't want to start splitting them up any more.   (Screenshots attached)

My perfect scenario would be both operating systems stored and bootable  on the SSD and all docs, pics and music stored on the the HD in the  neatest possible way. 

Could you help me do this or point me towards the relevant information?

Many thanks, Chris

ps:  I am re posting this from General Help to Installation and Upgrades as I realise that is the correct section.  Any administrators that see this, could you please delete the version in general help.  Thank you.

---

### Post by yapidumoac on 2020-08-31
Could you post screenshots of GParted as it may help undo the confusion?

---

### Post by oldfred on 2020-08-31
You want to keep 30% free in your NTFS Windows partition, or else it will get slower. At 10% free, you may not have room for a defrag. Although your NVMe drive may hide some of the issue.

You can put / (root) of 25 or 30GB on SSD and have /home or large data partition with all your data on the HDD. Bit more advanced is to keep /home inside / on SSD as it only needs the user configuration files which are small and put all your user data in a data partition on HDD. Disavantage of data partition is you have to manually create it, mount it in fstab, and give yourself ownership & permissions. Using /home all that is automatic. 

Older /boot & swap not now required.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme) &
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd) & 
[http://askubuntu.com/questions/581902/how-to-efficiently-partition-a-single-windows-ubuntu-dual-boot-disk](http://askubuntu.com/questions/581902/how-to-efficiently-partition-a-single-windows-ubuntu-dual-boot-disk) & 
[http://askubuntu.com/questions/610873/ubuntu-error-the-partition-table-format-in-use-on-your-disks-normally-require/610888#610888](http://askubuntu.com/questions/610873/ubuntu-error-the-partition-table-format-in-use-on-your-disks-normally-require/610888#610888)

---

### Post by chruph on 2020-09-01
Thank you.  I found the solution I needed in the end,  I just need to do a bit more research.  Things are less complicated than they initially seem to the new Ubuntu-user.

For the record, I sorted out my dual boot problem by using the following advice: [https://support.thinkcritical.com/kb/articles/switch-windows-10-from-raid-ide-to-ahci](https://support.thinkcritical.com/kb/articles/switch-windows-10-from-raid-ide-to-ahci)

and then I used this forum to help me reinstall Ubuntu on a partition on my SSD [URL="https://askubuntu.com/questions/1048854/how-to-install-ubuntu-18-04-on-ssdhdd-hybrid-with-proper-partitioning"]https://askubuntu.com/questions/1048854/how-to-install-ubuntu-18-04-on-ssdhdd-hybrid-with-proper-partitioning

[/URL]After a bit of updating everything is now working tickityboo  but I'm sure I will be returning here with some more obvious questions in the not too distant future 
:wink:

---

