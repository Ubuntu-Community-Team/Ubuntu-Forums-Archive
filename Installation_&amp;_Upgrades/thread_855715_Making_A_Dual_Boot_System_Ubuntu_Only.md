---
title: "Making A Dual Boot System Ubuntu Only?"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Bosconian on 2008-07-10
Right now, Ubuntu doesn't meet my needs but I am not 100% happy with Windows either. What I have decided I would like to do is run both in a dual boot system for a while and see if I can overcome my "issues" with Ubuntu.

If I was able to reach a point where I was happy with Ubuntu, I would want to delete the Windows partition, move the Ubuntu partition to the beginning of the drive and resize it to fill the drive. Is this plausible and easy to do? I just wouldn't want to start tweaking Ubuntu to my satisfaction to then have to reinstall it.

I have XP already and would install Ubuntu second. So XP would the first partition, Ubuntu the second.

---

### Post by hansdown on 2008-07-10
Welcome bosconian. You can try ubuntu for as long as you like on dual boot. The help and tutorials in this forum are very good. Also,cruising the forums will also help you alot. People here are most helpful if you need anything.

---

### Post by Pumalite on 2008-07-10
This might help:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by oneporter on 2008-07-10
I've actually been wondering about this myself lately.  I found [this thread]("http://www.linuxforums.org/forum/gentoo-linux-help/36449-possible-merge-partitions.html") helpful.

I think it's possible, but it might be better, as one poster suggested, to format the windows partition to ext3 when you're ready and then to move your /home folder to the new partition.  That way you would be able to try out different distros using one /home folder (all your settings would transfer, or at least that's how I understand it).

Hope that helps.

---

### Post by werries on 2008-07-10
To specifically answer your question.
Yes, you can remove the windows partition via gparted with a livecd, and expand the ubuntu ext3 partition into the space.

---

### Post by halitech on 2008-07-11
> **werries said:**
> To specifically answer your question.
Yes, you can remove the windows partition via gparted with a livecd, and expand the ubuntu ext3 partition into the space.

question here, I have an old compaq armada laptop and the cd doesn't work. I have windows and Xubuntu installed on the same drive (12gig) and since I now has wireless working on it (main reason I was keeping windows on it) is there a way of removing windows without having a working cd rom?

---

### Post by sande87 on 2008-07-11
> **halitech said:**
> question here, I have an old compaq armada laptop and the cd doesn't work. I have windows and Xubuntu installed on the same drive (12gig) and since I now has wireless working on it (main reason I was keeping windows on it) is there a way of removing windows without having a working cd rom?

yes there is. you can install a partitioning program in xubuntu. gparted should work, youll just have to install it through synaptic or apt.
"sudo apt-get install gparted" should get it installed for you. and from there you format the windose partition to ext3. 

I dont know if ubuntu will automount it for you, but if you use the "Disk Mounter" in you panel you can do it from there. Disk Mounter will detect all the partitions thats not currently used by Ubuntu, and a disk icon will appear, and you can mount it by clicking it and selecting mount.

---

### Post by halitech on 2008-07-11
ok, I have installed gparted and it looks like I can remove the partition and format it as ext3 but I guess what I should have asked was is there some way of removing the partition and add the free space to / without having a boot cd as my / is only 3.7gig (36% free) and I'd like a little more room for it.

filesystem  size    used   free         mounted on
/dev/sda1  4.3gig  3.2gig  1.1gig       not mounted (windows)
/dev/sda2  3.7gig  2.2gig  1.4gig  62%  /
/dev/sda3  2.8gig  138meg  2.5gig  6%   /home

---

### Post by Pumalite on 2008-07-11
Post a screenshot of Gparted.

---

### Post by halitech on 2008-07-11
here you go

---

### Post by Pumalite on 2008-07-11
No proble. Backup everything first. Use Gparted Live CD ( works with unmounted drives/partitions):
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Delete sda1. Right click on sda2 and choose 'resize' from the menu. Resize to the left.
It takes quite a while.

---

### Post by halitech on 2008-07-11
> **Pumalite said:**
> No proble. Backup everything first. Use Gparted Live CD ( works with unmounted drives/partitions):
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Delete sda1. Right click on sda2 and choose 'resize' from the menu. Resize to the left.
It takes quite a while.

therein lies my problem, I don't have a cd rom (physically not there and will also not boot from USB) so I can't boot the Gparted cd, thats why I'm wondering if there is another way of doing it from within Ubuntu.

---

### Post by Pumalite on 2008-07-11
sudo apt-get install gparted
At the Terminal:
gparted

---

### Post by halitech on 2008-07-11
I know that will let me remove the windows partition but can I use it to resize the / partition to include the free space?

---

### Post by Pumalite on 2008-07-11
See if there is a way of installing Gparted Live CD to a USB.

---

### Post by halitech on 2008-07-11
there is but I also can't boot from USB so that option doesn't really help me either

---

### Post by halitech on 2008-07-11
seems like I may be out of options so I am going to re-install using Unetbootin and use the entire disk. Seeing as how I just installed, not like I have anything on there to start with so might just be easier.

---

### Post by sande87 on 2008-07-12
well, i cant say that i have used gparted my self. I think there might be a merge option. If there is, you might have to boot the gparted livecd to do it. If I had the same problem, i would just backup all my files on a USB disk or another computer, then reinstall everything. Well, thats me.. Im a volatile user, it seems I can only learn the hard way :P Im actually reinstalling my box in 5min :P

---

### Post by halitech on 2008-07-12
there could be a merge option but no way to test and not doing it on my main system. I actually rebooted into windows, ran the Unetbootin and this time told it to use the whole drive and reconfigured the network (actually the wireless went flawless this time) and conky (cheated as I had saved my conkyrc file and its been running all day fine :)

I'm actually making 2 sets of debian boot floppies as I type this on the laptop (its the only machine I have with a working floppy) so if/when I kill it, I can reinstall using the netboot Debian install from floppies.

---

