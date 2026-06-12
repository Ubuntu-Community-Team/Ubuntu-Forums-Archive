---
title: "Installation wizard wiped XP partition....recovery of data possible?"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by modnar on 2008-07-06
Okay, my story:

I decided to install Ubuntu 8.04 on my machine; I used the LiveCD's installation wizard, and arrived at the partition menu.  Instead of choosing XP/Ubuntu dual-boot, I thought I would choose "use the entire hard drive" because I had read about some feature called Migration Assistance that would transfer over all the files I had in My Documents from XP.

When I reached the end of the installation wizard, with no Migration Assistance in sight (and the "install" button there ready to press), I decided to cancel the install, open it again, and choose the dual-boot option.  Alas, the partition manager wouldn't load, so I restarted the LiveCD and opened up the install wizard once again...only to see no XP/Ubuntu dual-boot option in existence.

I mistakenly tried to use FixMBR and Fixboot, etc., before reading around and using the command "fdisk -l" on the LiveCD.  The output showed that my main hard drive was now a Linux partition.

...

Long story short, is there any way to recover my data, even though my hard drive appears to have been reformatted (I haven't actually installed Ubuntu, yet)?

If there isn't, someone shoot me.  I believe the installation process is misleading and dangerous...no changes should be made before reaching the end of the wizard.  If one suddenly reconsiders partitioning options, or gets cold feet and decides to quit out of the wizard, it looks like one will be screwed.  Also, where is this Migration Assistance?

---

### Post by Pumalite on 2008-07-06
You can take it to a Hard Drive Recovery Shop. Very expensive. The best way to dual boot with XP is to get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. Shrink XP. Right click on XP, choose 'resize' from the menu. In the new space, make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.
Remove Gparted. Boot your Ubuntu Live CD, go Manual and choose the partitions already prepared.

---

### Post by theravenproject on 2008-07-06
> If there isn't, someone shoot me. I believe the installation process is misleading and dangerous...no changes should be made before reaching the end of the wizard

    Unfortunately that is not right...any time you go to install an OS on your HDD, before the installation media can even begin to coonsider installing it's payload onto your HDD-you have to edit the partition table in order to nake room for the new os.  If you chose to reformat the whole HDD under one partition then that is exactly what it did-and yes that is permanent and no I do not think you can recover your data really...you cannot blame the installation wizard for this becuase it asked you in very lain english-whether to reformat your entire hdd or set up dual boot and you chose the former-not becuase the install wizard was misleading but becuase you were mistakenly educated about "Migration Assistance"/Undereducated on the subject...Sorry friend-I am not trying to be harsh just real bro-your Win is gone now as is it's entire partition probably turned into a big ext3 part now...You can look into HDD Recovery Software/Services from your Computer Repair man../Online and may find a solution...good luck and remember:  ALWAYS RESEARCH IN DEPTH BEFORE INSTALLING ANYTHING NEW!!!!

---

### Post by modnar on 2008-07-06
Yeah, I'll definitely research in the future...for now I'm going to try out "Easeus Data Recovery Wizard Professional" (with purported support for ext2/ext3; I guess I'll check back here if it actually works.

---

### Post by theravenproject on 2008-07-06
Good luck friend!

---

### Post by Herman on 2008-07-06
:) Since Ubuntu itself only occupies the first 1.8 or so GB of the hard disk, it will probably only have overwritten the old Windows operating system files, so all your personal files will quite likely still be easy to recover.

I don't know anything about "Easeus Data Recovery Wizard Professional", but I imagine it will probably work okay.

If it was me I would try first with [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and see if I could restore the entire file system. You never know, that might just work, even though the file system blocks will have been overwritten already. You would need to use TestDisk to 'search deeper'. It would be worth a try.
TestDisk is installable in the Ubuntu Live CD and it's already in the GParted LiveCD that Pumalite linked you to in an earlier post.
Even better, [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/") is a special version of Ubuntu dedicated to this kind of work.
If TestDisk doesn't give you a complete recovery, (return your computer to the way it was before you ran the installation CD), I would turn to [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec"), which comes with TestDisk.
I use Ubuntu Rescue Remix in an external USB hard disk drive because it's easier to use Photorec that way, especially if the external hard drive can be larger than the hard disk containing the data to be recovered.

I made a web page about how to use TestDisk in case it's any use to you, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html").

Good luck with it, don't give up, there is a good chance you'll be able to recover all of your files.
Regards, Herman :)

---

### Post by modnar on 2008-07-06
I was going to have to wait for a week or so to use the Easeus software (my external hard drive is currently out of commission), so I think I'll just go ahead and try out your method.  The thing is, I never actually finished the installation; the partition manager just formatted it to ext3, so hopefully I'll have good results.

Thanks!

---

