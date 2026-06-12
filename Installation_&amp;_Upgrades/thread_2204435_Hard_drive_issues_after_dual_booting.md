---
title: "Hard drive issues after dual booting"
date: 2014-02-08
forum: Installation &amp; Upgrades
---

### Post by RedeyeJedi on 2014-02-08
After using ubuntu on it's own for years, I bought a ne 1TB hard drive for my computer and decided to use the 64GB SSD I have to dual boot with Windows 8. I also have a 2TB external drive which is just one large NTFS partiton.

I have the SSD split into 2 32GB partitions, one for Windows, one for ubuntu. I have the 1TB drive currently with 2 partitions on. A 300GB storage drive for Windows and a 500GB drive for Ubuntu, leaving a few hunder GB unassigned to save for later. Both of these partitions are NTFS, to make accessing from both ubuntu and windows easier.

After installing windows I have been using it almost exclusively for a few weeks. I got pretty fed  up with it today and decided to switch back to Ubuntu. I use clementine as my default player and decided to play some music. I tried playing an album I had saved on the 2TB external drive. I dragged the files into clementine and got an error "LibraryBackend: disk I/O error Unable to fetch row" This has happened with multiple files, all of which are .flac. If I try play anything from my library in clementine (saved on the 2TB drive) clementing goes grey and closes.

I gave up and decided to leave it till later to sort out. I then tried to download a torrent using transmission. I set the download location to the 500GB partition. Transmission hung at starting the torrent then said there was no space on the device. I changed the location to the 300GB partition and got the same problem. I also tried to use the 2TB external drive which I have used in the past and the download has stalled with no explanation. 

The drive works fine under windows and the 2TB used to work fine under ubuntu a couple of weeks ago. I'm thinking that maybe there is some issue with the drives not mounting correctly but after a bit of googling couldn't find anyone with the exact same problem and I've learnt in the past that it's not the best idea to randomly change settings etc.

I do remember reading something about windows 8 never properly shutting down and going into a sort of hybrid-hybernation mode but can't find it again, could this be causing my issues?

I'm going to carry on searching round to see if I can find a sloution but I'd really appreciate a hand with this.

If you need anymore info from me let me know

Massive thanks in advance for any help

Thanks
Richard

---

### Post by RedeyeJedi on 2014-02-08
[http://ubuntuforums.org/showthread.php?t=2204435&p=12923586#post12923586](http://ubuntuforums.org/showthread.php?t=2204435&p=12923586#post12923586)  I posted this over in multimedia and video but I think it would probably be better of here, not sure how to move it though.  Sorry for the double post, hope someone can hele me.  Thanks

---

### Post by oldfred on 2014-02-08
Merged and put into installation as that may be closer to your issues.
You can request a Admin or moderator to move it using the report post icon. That is not just for spam, but any issue that may need help or review.

Is Windows still hibernated or the fast boot which is always on hibernation?

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by RedeyeJedi on 2014-02-08
Thanks for merging them for me  I'm going to switch over to windows now and see if turning off hybernation works. Do you have any ideas what I can do next if it doesn't?  Thanks

---

### Post by RedeyeJedi on 2014-02-08
After having another read of the links you posted, I think that might not be my problem. They seem to say that it does not hibernate if you do a restart, which makes sense, and I switched over to ubuntu by using the restart option in windows.  Is there some way I can check to make sure the hard drives I have connected are mounted properly?

---

### Post by oldfred on 2014-02-08
Are you mounting with fstab or manually with Nautilus.

Post this from terminal to see your mounting commands:
       cat /etc/fstab

---

