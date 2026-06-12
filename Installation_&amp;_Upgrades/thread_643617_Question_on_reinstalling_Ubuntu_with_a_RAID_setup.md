---
title: "Question on reinstalling Ubuntu with a RAID setup"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by xskull on 2007-12-18
Hey everyone, 

I have a system that I need to reinstall Ubuntu on. Most all of my files that are important are on separate partitions or drives, so I know during the reinstall not to format those areas. However, there is one new concern that I have not had the pleasure of dealing with before on a reinstall....RAID. 

My main storage drives are in a RAID 1 configuration. Again, the OS directories are not a part of this drive. My question is, if I reinstall Ubuntu, will it find the RAID again? Will the data still be present? I'm making a back up of all the files JUST in case something goes wrong, but it would be nice just to start the reinstall and just sit back and relax like this OS normally lets me do :D. 

Thanks.

---

### Post by rsw686 on 2007-12-18
Yep you can reinstall, but you'll need to switch to a virtual console to bring up the raid. Here's a link to a write-up on what worked for me.

[http://www.excalibur-partners.com/archives/18](http://www.excalibur-partners.com/archives/18)

---

### Post by fain on 2007-12-18
Ubuntu needs to incorporate raid installs default in its installation. I know Suse has this feature Ubuntu should too.

---

### Post by xskull on 2007-12-18
Thanks for the replies. I'll give it a try as soon as I am ready to reinstall.

---

### Post by rsw686 on 2007-12-18
> **xskull said:**
> Thanks for the replies. I'll give it a try as soon as I am ready to reinstall.

I forgot to mention those instructions are for the text based install. I've never done the LiveCD install so it might be different. Since the data is on a separate drive than where you are reinstalling Ubuntu to its not the end of the world if you can't bring up the raid during the install. Just don't make any partition changes to the drives the RAID is installed on. Afterwards you can use those same commands and add an entry to /etc/fstab to automatically mount the RAID array.

---

