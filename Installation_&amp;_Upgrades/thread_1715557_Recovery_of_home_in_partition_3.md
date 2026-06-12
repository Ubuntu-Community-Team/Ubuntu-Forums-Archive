---
title: "Recovery of /home in partition 3"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by colintivy on 2011-03-27
Hi folks!

I have got myself into a bit of a fix. Anticipating the delayed update to 10.04.2, I created a new partition (sda3) for /home on my laptop. Sadly,and in my ignorance, I formatted this to ext3. I carefully transferred my /home from sda1 and it all looked fine.The partition was duly labelled as /home. When I upgraded to 10.02.2 from Update Manager I found all sorts of problems, particularly with logging in. Username and password were all inherited from 8.04, were not rejected but failed to complete the Log-in, merely returned to the log-in page. I have got round this by using the FailSafe Gnome feature and 10.04.2 runs fine.But I want to get everything working properly.

As a by-product of my mistake, sda3 looks like another HD with all my data safely therein but is unseen by sda1 which has a normal /home in it but I now have two /homes of a sort. What I want to do is to save my old /home to a USB thumb drive to preserve it but cannot do so because of permission denial, probably due to two versions of names or something. Using root privileges does not seem to get over this. Any clues?

It has been suggested that I should reinstall 10.04.2 (for which I now have a LiveCD) which will involve setting up the partitions again (specifying /  and /home). If I leave my sda3 as it is, will the original formatting be removed and will the data survive? (which will remove the need to save it elsewhere. Luckily I do have a back-up using Simple Back-up from late December which is not too stale which could be a backstop. 

I see that the poorly documented FailSafe actually makes use of a different video driver to get going. This puzzles me because my laptop was quite happy with 8.04 (and experimentally 9.10) in this respect. Any advice on how to look further into this?

---

### Post by Sean Moran on 2011-03-27
> **colintivy said:**
> Hi folks!
What I want to do is to save my old /home to a USB thumb drive to preserve it but cannot do so because of permission denial, probably due to two versions of names or something. Using root privileges does not seem to get over this. Any clues?

I assume you know the directory of /dev/sda3 partition, possible /media/HOME or whatever label you've given the partition.  Regarding the permissions problem, have you tried to change the permissions recursively to RW-R-R so that all the files can be read to copy to the USB drive?  ie.

sudo chmod -R 755 /media/HOME 

Substitute whatever directory /dev/sda3 is mounted to for /media/HOME.  The -R is for recursive directories, and 755 means read-write-execute, read-execute, read-execute for owner, group and everyone.  That should hopefully change the permissions for everything on the /dev/sda3 partition to be readable by everyone, thus allowing all files to be copied to another location.  

I might be offtrack here, because you may have already tried this.  I'm not sure why root privileges would not allow you to copy files from one source - even if it's thinking of itself as a r/o filesystem - to another target where the write privileges allow it.

---

### Post by Dutch70 on 2011-03-27
If you don't re-format sda3 during installation you shouldn't lose anything. That's the main purpose of a /home. Always best to have back-ups.

You don't have the mount point for /home set to sda3, that's why "sda1 does not see it" as you said. You can reset the mount point, but it's easier to do during installation. You'll also get better, more organized help if you follow "one problem/one thread".

No idea about your log-in problem, but you probably should post your graphics card, or the output of "lspci" without the quotes. Please put it between code tags by highlighting it & clicking the "#" symbol in the toolbar.

I also have to ask, how big is "/" now?

---

### Post by colintivy on 2011-03-27
Hi Sean & Dutch

Thanks to you both, that all looks very promising and I will explore, I am off on hols tomorrow for two weeks so there will have to be a bit of silence, so do not think I am ignoring you. sda3 is shown as/media/_HOME right now.

My problem seems that I formatted sda3 to ext3 before putting in the /home data as I said above. So I am not sure if that gets "undone" when I respecify the partitions during a manual install, and whether the existing (old) /home is overwritten or left alone. 

I included the log-in problem in case it was somehow due to the two /homes and log-in details being not identical. I have just read, but not fully understood, an article in April issue of Linux Format about the complications that arise from the security palaver with log-in and password details, which made me suspicious.

My sda1 / is ext3 11.18GB half used, sda2 swap is 517.72Mb (RAM 512Mb) sda3 /home ext3  8.72 GB  1/8th used.

---

### Post by gordintoronto on 2011-03-27
> **colintivy said:**
> My problem seems that I formatted sda3 to ext3 before putting in the /home data as I said above....



You have my personal guarantee that this did not cause any part of your problem. It's a complete red herring, and thinking about it will slow you down from finding the right answer.

Windows "out of the box" doesn't see EXT3 partitions, but that is the only down side.

---

### Post by oldfred on 2011-03-27
It sounds like you only did the first parts of the move command procedure. The last parts include editing fstab to mount the new /home partition as the new /home and housecleaning out the old /home inside the / (root) partition.

Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

Also depending on how you copied the data you may not have peserved all you ownership & permissions. If issues.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

Do not run any of the above  command at / (just /home/$USER) as that will remove root as the owner and make you system unuseable. I did something similar and had to reinstall.

---

