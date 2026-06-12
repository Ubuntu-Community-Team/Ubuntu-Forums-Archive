---
title: "windows partition too big"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by mystmaiden on 2012-05-30
Thanks to oldfred, I got my dual boot system working beautifully, but after loading all my personal files and programs on the Ubuntu partition, I realized it simply isn't big enough. What would be the safest way to resize the Windows partition now that everything is working so well?

thanks

mystmaiden

---

### Post by wilee-nilee on 2012-05-30
> **mystmaiden said:**
> Thanks to oldfred, I got my dual boot system working beautifully, but after loading all my personal files and programs on the Ubuntu partition, I realized it simply isn't big enough. What would be the safest way to resize the Windows partition now that everything is working so well?

thanks

mystmaiden

W7 has a virtual partitioner, disk manager I think it's called, you can do a resize while running. Not sure what windows release you are running.

---

### Post by mystmaiden on 2012-05-30
Thanks for the reply. I'm running xp in this case.

---

### Post by oldfred on 2012-05-31
If you are going to dual boot, I usually suggest a separate shared NTFS data partition. In fstab set the XP partition as read only and use the shared for any data you might want in both XP & Ubuntu. I still have my shared NTFS with Firefox & Thunderbird profiles & all our photos, but all new data now goes into a Linux data partition as I use XP so little.

If you have XP, you can use gparted from a liveCD to shrink it. First houseclean what you can and defrag it as that will make gparted take less time. Also Windows NTFS partitions like lots of spare space. Best to leave 30% free. At 10% free it become so slow as to be non-functional.

Only do one thing at a time in gparted and after changing XP's size immediately reboot and let it run chkdsk to fixup its new size.  Moving partitions with data can take a very long time.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by mystmaiden on 2012-06-01
Thank you, once again, Oldfred. I did as you suggested and resized the xp partition first then rebooted and let xp run chkdsk. It worked like a charm.

I have a question about the ntfs data partition you suggested. If I set it to read-only will it limit what I can do with those files too much? For instance, would I be able to re-tag an audio file? (that's just an example off the top of my head)

Like you,  I won't be using Windows much at all so I won't need much space for it.  I have one art program, my ipod and phone to use it for - that's pretty  much it. But how much free space is sufficient for the Precise partition?

mystmaiden

---

### Post by oldfred on 2012-06-01
No, I suggest setting the XP system partition as read only, just to avoid accidents. Even when I was in Windows I would changes settings to see all files & folders because I was "knowledgeable". But then I click & drag on some folder too fast and it moved a system folder and totally messed up Windows. I used to do that at least once a year. Ubuntu always shows all the Windows files & folders so it is best to default to read only. 

But then you set the shared data partition to read/write when  you mount in fstab. I was trying to learn Ubuntu and my wife wanted to check email & use Interent and all the settings were in Firefox & Thunderbird in XP, so I was always rebooting into XP. Once I created the shared data and since I had the same applications, I almost convinced my wife that Ubuntu was all we needed. She still complains whenever something does not work, but has forgotten the issues we had in XP and did not know all the maintenance I was doing to XP.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Examples of fstab entries:
from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

Set windows boot partition Read only - Morbius1:
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.

/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=000 0 0 

UUID style preferred over device style for mounting partitions in fstab.

---

### Post by mystmaiden on 2012-06-02
Thanks, Oldfred. Sorry I misunderstood. That makes a lot of sense, though. I hadn't thought of the difficulties you could run into on a dual boot system by just accidentally moving files, etc. I'll give it a try following your instructions in the morning when my brain is a bit more functional.

myst

---

