---
title: "WinXP/ Ubuntu. How do I fix this?. Or can I?"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by stana on 2010-04-28
Greetings everyone and Thank You in advance for any help you can provide. 

 I have a question...But first..Windows sucks. 

With that said, here is what happened. I had Winxp on 1 partition and ubuntu 9.10 on he other partition. So far so good. Everything was working, grub2 was happy I was happy.

Then I developed a major problem with my Verizon Aircard and Winxp. In the end, I had to reinstall XP. Needless to say, Winxp overwrote Grub. Ouch. So, I installed Ubuntu on a 9gig partition. That recreated Grub and I am able to use my original install of Ubuntu.... Im happy....

At the moment, I have WinXP on 1 partition (27gig). The original Ubuntu install on a second partition (27gig), and a second Ubuntu install on a 3rd partition, (9gig). Its a 60 gig HD on my lappy.

So, here is my problem. I would like to remove the 9gig install of Ubuntu. Give that 9 gigs back to the original install of Ubuntu and fix grub so it only shows my Winxp install and Ubuntu.

Without reformatting the whole HD, and reinstalling both OSs, is their a way to do this AND still preserving GRUB and not messing anything up?. 

PLEASE say "thats easy just follow these moron proof instructions and you will be all set". I hate to format the whole HD and start all over but, if thats the easiest way to go, then so be it.

Thanks,
Stan Amster

---

### Post by David Batty on 2010-04-28
you should have Gparted installed in Karmic. see [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
But if you want to mess with the karmic partition then you should do  this from a live CD

---

### Post by wilee-nilee on 2010-04-28
You might post a screen shot of gparted so we can see exactly what the hard drive looks like.

---

### Post by stana on 2010-04-28
> **wilee-nilee said:**
> You might post a screen shot of gparted so we can see exactly what the hard drive looks like.
[IMG]http://www.newenglandphotography.net/hd.jpg[/IMG]

I want to remove the 4.9GB and the 280MB partitions. My real concern is how will removing these partitions affect GRUB?. Will GRUB still be intact or am I better off reinstalling Ubuntu and write this off as a learning experience?

Thanks

---

### Post by max-power2717 on 2010-04-28
I certainly don't think you'll be better off formatting and reinstalling: indeed, I think that would the most painful way for you to resolve your dilemma.

Grub can easily be reconfigured to suit your changes to the partitions, and so can your system - that's one of the *really* elegant things about linux OSes. It's just a matter of knowing what to change. Hopefully the knowledge you acumulate resolving this issue will come in very handy for you down the track. 

You can safely unmount and remove the two unwanted partitions from GParted when you're booted into your preferred (original) ubuntu installation, leaving free space on the drive. But you can't use it to move and resize your original ubuntu installation because GParted can't alter a mounted partition (you'll do this from the live CD below).

When you remove the two partitions, make sure the file /etc/fstab does not contain reference to either of those partitions. If you find any lines in that file which reference either of those partitions, comment them out with a # at the begining of the line to deactivate (for now).

This is where you'll need a live CD (one which includes GParted or some other partition editor - many have GParted). Once booted from the live CD you can then move and resize the partitions on the HDD as desired with GParted. I'm guessing you'll want to move your 1.2GB swap space and extend your original ubuntu root partition to fill the gap. Depends on the current layout of the partitions. 

That takes care of the HDD - and grub should have no problems booting your original root partition. However grub will still have an entry for booting the temporary (now absent) ubuntu OS. That can be fixed in the grub configuration. I'm only just getting to know the new grub 2 system now, (installed it for the first time last night as it happens,) so I can't give you detailed directions at this time. 

However, I know the key lies in changing or removing one of the scripts in /etc/grub.d/ and then running update-grub in order to generate the new grub configuration (which is stored in /boot/grub/grub.cfg). I'm led to believe that one must never touch the grub.cfg file directly. [This very well written tutorial]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId514088") will likely give you more than enough information to help you remove the unwanted boot options.

Also, for future reference, grub has a utility (grub-install) which is used to update a disk's (or partition's) MBR. It's very easy to use in grub 2. When you have to do a windows installation down the track, and it (inconsiderately) overwrites your MBR, you can boot into a linux OS (perhaps using a live CD) and use grub-install to rewrite the grub image back to the MBR. That'll save all the fuss of having to install and remove a temporary OS just to restore the MBR.

I hope this helps.

---

### Post by max-power2717 on 2010-04-28
Sorry, just an after thought: there's something called OS Prober included in grub2 by default. It's discussed in that tutorial I provided the link for. I'm not sure how it works, but it might be the easiest option for you to reconfigure your grub. Read about in the tutorial (link repeated here): [http://www.dedoimedo.com/computers/grub-2.html#mozTocId835620](http://www.dedoimedo.com/computers/grub-2.html#mozTocId835620)

---

### Post by Mark Phelps on 2010-04-28
A concern I would have is that the GRUB2 files are installed to one of those two Ext4 partitions.  Without knowing which one, if you remove the partition containing those files, GRUB  will not boot.

However, with an Ubuntu LiveCD, it should then be a simple matter (after partition removal) to reinstall GRUB2, then boot into Ubuntu, then run "sudo update-grub" -- and have your GRUB options back.

I would do this first, and after you have GRUB and booting working to your satisfaction, do the following:
1) Boot from a GParted LiveCD (which you can get from distrowatch.com)
2) Move the swap partition to the end of the drive
3) Expand the Ext4 partition to fill the unallocated space

---

### Post by oldfred on 2010-04-28
If you can still boot into the version you want to keep, just reinstall grub from that install.

reinstall from working system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

If not you can use the liveCd.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

Then you can use gparted to remove the extra install or keep it for future use as data or a test install.

---

### Post by stana on 2010-04-29
Hi Everyone and thank you for your help so far. Here is where I am at. 

I used GParted and deleted the unwanted partitions. Now my HD looks like this:

[IMG]http://www.newenglandphotography.net/hd2.png[/IMG]

Now, I have a whole set of new problems... GRUB. Grub was on the partition that is now unallocated. OOOPPSSS... I used the live cd and looked at the original install and went to /boot/grub/ and looked at the grub.cfg file. It is intact and still correct. That was a sigh of relief.

Now, I have 2 problems. HOW do I take the unallocated space and move it to my sda6 swap file and how can I get GRUB back?

I tried what 'oldfred' suggested. I booted from the live CD, used terminal and ran 
sudo grub-install /dev/sda. I got an error so I tried  sudo grub-install /dev/sda5. I still recieved errors. I tried sudo grub-install --recheck /dev/sda and i recieved the following: Auto detection of file system module failed. and then it wasnt me to use some options. 

So, where Im at is. GURB is gone. I have to use the live CD to boot up and my HD is a mess. 

Would I be better off reinstall Ubuntu or is their hope of fixing this mess?

Thank you for all your help everyone,
Stan

---

### Post by stana on 2010-04-29
I had a thought. If somehow I move the unallocated space to the swap file, in theory, I will be back to the way I was before WinXP made life difficult?. It was a thought....
And I have a headache...

---

### Post by Mark Phelps on 2010-04-29
> HOW do I take the unallocated space and move it to my sda6 swap file
You can't move it directly because there is a partition in the way.  You would have to move the Ext4 partition to the left and then expand your Swap partition to fill the space.

---

### Post by oldfred on 2010-04-29
The instructions I posted were to install grub2 from a booted system assuming you could still boot into your first install using the boot loader from the second. It then knows what partition grub is on. If from a liveCD you have to tell it which partition grub is on first by mounting it.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Find linux partition:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by max-power2717 on 2010-05-01
> Would I be better off reinstall Ubuntu or is their hope of fixing this mess?

Despite the "mess" I certainly think you're better off fixing the MBR and grub installtion than reinstalling ubuntu. Reinstallation will likely wipe out your existing settings and applications, and you'll have to start over (although, there may be special techniques to import these aspects from an overwritten installation - I don't know how one would go about doing that - anyone?). In any event, reinstallation will take a good deal longer than the restoration of the MBR + grub (once you've got the needed commands worked out for your system,) and it is somewhat of a brutish overkill solution for your problem - linux does make it reasonably easy to elegantly repair such problems (provided you have the background knowledge and understand the utilities that are required). 

Regarding reinstallation of grub 2: read the tutorial I posted the link for earlier (I think I did anyway: here it is again: [http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259](http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259)). That should arm you with a whole bunch of background knowledge of grub2 and the linux boot process.

Old fred is right: installation of grub2 from the live CD failed because the installation utility probably could not read the /boot filesystem (or folder). The portion of grub that resides in the MBR (so called stage 1) must know where the /boot filesystem is because certain files that grub reads to present OS boot options and boot the various OSes are contained in /boot. The grub installation utility configures the 512-byte stage 1 image of grub appropriately for yor system (including where/how to find /boot,) and then writes it to the first block of the target (which in your case is the entire hard drive - /dev/sda when viewed from ubuntu).

---

### Post by stana on 2010-05-03
> **oldfred said:**
> The instructions I posted were to install grub2 from a booted system assuming you could still boot into your first install using the boot loader from the second. It then knows what partition grub is on. If from a liveCD you have to tell it which partition grub is on first by mounting it.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Find linux partition:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda


Fred,
This worked GREAT. It saved me hours of frustration. Thank you so much.

---

