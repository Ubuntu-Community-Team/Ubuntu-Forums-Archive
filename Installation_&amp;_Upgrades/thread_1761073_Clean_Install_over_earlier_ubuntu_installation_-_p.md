---
title: "Clean Install over earlier ubuntu installation - possible? best way to go?"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by jiex on 2011-05-17
Hello
I have searched for an answer to this query but have not managed to find a clear answer. I ask your indulgence if the answer is here and I'm too inexperienced to find it. [I am still learning ubuntu.]
I have a PC that has 10.04 installed and no other operating system. The 1 TB hard disk has two partitions:
* 940 GB  NTFS for data storage
* 50GB ext4 (which has 10 GB extended and 10 GB sawp)
The system has become sluggish and slow and browsers and so on often "hang" for a few seconds prior to executing. There is an epiphany dependency problem that I cannot solve.
My questions are:
1. Is it possible to do a clean install on the 50GB partition from a live CD?
2. Is it better to do this than upgrade to 10.10 and thence to 11.04? [When I ungraded like this in the past, I had problems, so I would prefer a clean install].
3. If it is possible to do a clean install on the 50GB partition, should I reformat the partition and if so, can I do that from the live CD?
Most obliged for any info, including links. 
Thank you for an excellent forum and the help.
Regards
Jim

---

### Post by Dutch70 on 2011-05-17
1. Yes
2. A fresh install is always a better idea than an upgrade.
3. a)Yes it's possible, but you may need to choose your partitions manually. 
b)Reformat if you don't have anything there you care to lose. If you do, do not reformat.
c)You can do it from a live cd or usb stick.

I have a couple questions.
1. Why on earth are you using an ntfs partition for storage if you are not sharing it with windows? 
ntfs partitions have to be defragmented from time to time, or they will become very sluggish. Has nothing to do with which OS is pulling the files from the hdd. 
If you can back up your ntfs partition, I strongly recommend formatting it to ext4 and using it for a /home partition.
[[COLOR="RoyalBlue"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

2. Have you tried installing & using bleachbit to clean your system? There is no reason for Ubuntu itself to slow down, in fact it usually gets faster with usage. 
(minus the ntfs thing, which is a windows file system) 
You aren't having network issues are you?

---

### Post by mörgæs on 2011-05-17
'Yes' to all three questions.

If the machine is only for Ubuntu, I would format both drives with ext3 or 4. There is no advantage in NTFS, if you don't have Windoze on the machine.

Go for a clean install, not an upgrade.

---

### Post by jiex on 2011-05-17
Dutch 70 and mörgæs:
Many thanks for your responses. Much appreciated.
To answer your questions. I am more or less new to Ubuntu and I use the box largely to do torrent, but since it is on, I increasingly use it for web work and general day to day stuff. Very impressed with it.
The NTFS partition holds the media files that I stream over the network and which the other computers in the house access. Those computers are XP. The NTFS is also an artifact from when the drive was in an XP box. 
I do not know what bleachbit is, but I will look at it and play with it.
I should say there are other issues with the 10.04 install - such as the audio (on .ogg and .flac tracks) cutting out and then resuming after 5 or so seconds. I am hoping a fresh install will fix that. 
Another question - can I reformt the partition that contains ubuntu from within the live CD prior to installing 11.04?
Thanks heaps for your advice. You have been very helpful.
Jim

---

### Post by Ameet on 2011-05-17
Jim,

You can definitely reformat partitions while running off the live CD.  I would select the option for "Try Ubuntu", so you have a fully-functioning version of 11.04 running.  From there, you can use Gparted to reformat partitions, or other Ubuntu programs to archive entire file structures to an external HD if you want.  Then, there is an icon at the top left of the screen to "Install Ubuntu".  Click that and you are put back into the installation mode of the live CD.
Ameet.

 > **jiex said:**
> Dutch 70 and mörgæs:
Many thanks for your responses. Much appreciated.
To answer your questions. I am more or less new to Ubuntu and I use the box largely to do torrent, but since it is on, I increasingly use it for web work and general day to day stuff. Very impressed with it.
The NTFS partition holds the media files that I stream over the network and which the other computers in the house access. Those computers are XP. The NTFS is also an artifact from when the drive was in an XP box. 
I do not know what bleachbit is, but I will look at it and play with it.
I should say there are other issues with the 10.04 install - such as the audio (on .ogg and .flac tracks) cutting out and then resuming after 5 or so seconds. I am hoping a fresh install will fix that. 
Another question - can I reformt the partition that contains ubuntu from within the live CD prior to installing 11.04?
Thanks heaps for your advice. You have been very helpful.
Jim

---

### Post by jiex on 2011-05-18
Hi Ameet - many thanks for your reply. Very much appreciated. The responses have been most helpful. And one from Kentucky and one from Iceland; two places I have always wanted to visit. The internet is amazing!:D
Thanks again everyone.
Jim

---

