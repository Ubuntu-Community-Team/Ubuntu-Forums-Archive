---
title: "Can't find all the hdd partitions in the Ubuntu 18.04 Installer"
date: 2018-06-07
forum: Installation &amp; Upgrades
---

### Post by apurbadebnath on 2018-06-07
Experts, I have already written down the whole problem on Ask Ubuntu, please provide necessary help.

[https://askubuntu.com/questions/1044346/installing-ubuntu-18-04-cant-see-my-partitioned-hdd#](https://askubuntu.com/questions/1044346/installing-ubuntu-18-04-cant-see-my-partitioned-hdd#)

---

### Post by oldfred on 2018-06-07
Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Windows 10 fast startup will be an issue for you since you have BIOS/MBR boot. Grub only boots working Windows. Windows will turn fast start up back on with updates and then grub will not boot it. So you must have a Windows repair flash drive to restore the Windows boot loader and fix it after every time it turns fast start up on, or crashes and needs chkdsk. (You need that whether booting Ubuntu or not).
And you need Ubuntu live installer to restore grub after Windows is fixed.

With UEFI, both systems have boot loaders in ESP - efi system partition, so you can often boot Windows directly from UEFI. But still best to have repair flash drives.

---

### Post by QIII on 2018-06-07
In the future will you please post a complete support request here rather than asking our users to look elsewhere for your question?

Would you please take the time to edit your opening post to accomplish that now?

Not only is that proper netiquette, it also ensures that the support offered here will be internally consistent and complete -- and that users searching for an answer to similar issue can do a search for both question and answer here.  Also note the comment there:  
> Again, could you please post text files, dialogue messages, and program output listings as text, not as images?  The same applies here.  It is much easier to help you when such things are presented as text.  Images are fine when they add to understanding, but not when they are the primary means of communicating your issue.  However, if you use them please do not post large images.  Use the attachment functionality provided the the paperclip button in the toolbar above the text entry box.  That adds a thumbnail that users can click to enlarge if they choose to.  Some users have low bandwidth or data limits.

---

