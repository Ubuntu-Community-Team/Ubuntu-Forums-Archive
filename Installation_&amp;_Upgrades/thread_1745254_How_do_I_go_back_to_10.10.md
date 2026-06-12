---
title: "How do I go back to 10.10"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Hotel on 2011-04-30
Hi

I recently upgraded from 10.10 to 11.04, however 11.04 feels like it should still be in alpha. Apt-get gets an error every time it runs due to the failed install of Samba4, the desktop freezes (requires restart) whenever I try to open LibreOffice Calc and the computer only boot successfully every second time.
I have also had to completely change my setup due to the abysmal support for dual screens and the fast boot times which where the reason I switched from Windows have all but disappeared in the latest release.

Is there any way I can 'upgrade' back to 10.10 without reinstalling.

Thanks for any help,
HJED

P.S If you have not already upgraded to 11.04 DO NOT if you care about using your computer.

Edit: Also Banshee now crashes whenever I try to open it and Unity hides all of you WINE apps(I quickly switched to gnome classic)

---

### Post by Hedgehog1 on 2011-04-30
Right now this situation appears to be vestiges of pre-natty setup and video drivers causing this.

You only options are to reinstall 10.10 as a clean install, or reinstall Nattty as a clean install.  Either will get you stable, but I think you are leaning toward 10.10 right now.  You will need a LiveCD/LiveUSB of your target Distro.

Please copy your data to an external hard drive or USB Stick.

If you have a separate '/home' partition, this is much easier as you can do a manual install (called 'Something Else' in Natty) and format the '/' (root) partition, and DO NOT FORMAT the '/home' partition for a reasonably painless clean install.


***The Hedge***

:KS


p.s. You can reinstall Natty/11.04 and still use the 'Classic&#8217; UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293") *** EDIT - Saw your edit, you already know about the 'Classic' options.***

---

### Post by grants on 2011-04-30
how do you set up /home to be on a separate partition or by itself?

Do you do that with LVM? or simply when you do a fresh install select a partition and mount it at /home when you have more then 2 partitions (one for files one for swap)?

---

### Post by wilee-nilee on 2011-04-30
> **grants said:**
> how do you set up /home to be on a separate partition or by itself?

Do you do that with LVM? or simply when you do a fresh install select a partition and mount it at /home when you have more then 2 partitions (one for files one for swap)?

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Hedgehog1 on 2011-04-30
**wilee-nilee** - thanks for the link.  I forgot it...

***Here is an example of installing/upgrading with the three partitions:***


Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

The last partition to setup is the '/home' one:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]


***The Hedge***

---

### Post by wilee-nilee on 2011-04-30
> **Hedgehog1 said:**
> **wilee-nilee** - thanks for the link.  I forgot it...


"A beautiful set ah pictures".;)

Uncle Enzo

---

### Post by Hedgehog1 on 2011-04-30
> **wilee-nilee said:**
> "A beautiful set ah pictures".;)

Uncle Enzo

Uncle Enzo,

I find the pictures help overcome two language barriers:

(1) Many forum members do not speak English as a first language.
(2) Many forum members do not speak 'Linux geek' (yet).

I had a series of posts with a fellow who spoke little English and I speak no real Spanish.  The posts were mostly pictures back and forth, and in the end he was dual booting Ubuntu (with RAID, no less).

He found a Spanish speaking Ubuntu group a week later; but it was an interesting challenge. <***He never writes, he never calls***>

***The Hedge***

:KS

---

### Post by grants on 2011-05-04
I guess that answers my question. Thank you sir!

Any way to change your /home to a new partition after an install had been done on a single partition only?

---

