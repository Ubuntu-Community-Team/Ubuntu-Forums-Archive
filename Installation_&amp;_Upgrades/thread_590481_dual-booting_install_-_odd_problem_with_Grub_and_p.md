---
title: "dual-booting install - odd problem with Grub and partioning"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by master_runner on 2007-10-24
So, for a good deal of time I was dual-booting Ubuntu 7.04 and Windows XP Home on my 160Gb hard disk without trouble. Well, when 7.10 came out I decided to reinstall rather than upgrade.

Now, after I installed 7.10, when I tried to boot Grub started and returned Error 18. A little looking around revealed that Error 18 is caused by the kernel being out of the 1023 cylinders that BIOS can reach, so you need to move GRUB (and the kernel?) to within 1024 cylinders.
However, this seems odd, as I never had this problem with 7.04. So, I've tried reinstalling a couple of times (using the "Use largest continuous free space" option for partitioning) and each time I get the same result. In addition, I'm told that new BIOSes should no longer have this problem, as they support large hard disks.

So, I suppose my first question, is why would this have just all the sudden become a problem when installing 7.10? I'm installing 7.10 right where 7.04 used to be, about 70Gb in to the drive.

My next question is, as you could probably guess, how to make it work. I'm told that this problem can be solved by putting /boot/ at the beginning of the drive. if that is the best solution, then how exactly do I do that? do I just manually partition and set a partition at the beginning with mountpoint /boot/ and the larger one at the end with mountpoint /? Or, is there a better solution than this?
as a note, there's already about 500Mb free before the big old Windows partition from an old diagnostic thingaling, so I can just put /boot/ there if necessary.

Relevant technical data:
160Gb hard disk (I think it's a Deskstar, if anyone cares.) on a Dell Inspiron 2200, currently running Windows XP in an NTFS partition occupying roughly half of the drive. I do all my partitioning with a Gparted LiveCD.

What I've done so far:
> Reinstalled a couple times, just to make sure. Still the same problem.
> Checked BIOS hard disk settings. System info indicates the hard drive is set to Auto, although there doesn't seem to be a way to change it. if it does need to be changed I suppose I can bother Dell about it.

Feel free to ask if you have any more questions.

Thanks for the help.

---

### Post by logos34 on 2007-10-24
> My next question is, as you could probably guess, how to make it work. I'm told that this problem can be solved by putting /boot/ at the beginning of the drive. if that is the best solution, then how exactly do I do that? do I just manually partition and set a partition at the beginning with mountpoint /boot/ and the larger one at the end with mountpoint /? Or, is there a better solution than this?
as a note, there's already about 500Mb free before the big old Windows partition from an old diagnostic thingaling, so I can just put /boot/ there if necessary.

If you've checked the[ Bios disk settings]("http://users.bigpond.net.au/hermanzone/p15.htm#18") a separate boot is the next thing you might try, even though it shouldn't be a cylinder limit issue.  And, yes, if you use the 500 MB partition (actually 100 MB is more than enough), assign it mountpoint of /boot.  

You might also try putting ubuntu on logical partitions.

---

