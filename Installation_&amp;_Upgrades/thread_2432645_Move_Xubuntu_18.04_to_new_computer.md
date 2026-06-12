---
title: "Move Xubuntu 18.04 to new computer"
date: 2019-12-05
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2019-12-05
My current computer is a six-year old System76 that originally had Xubuntu 13.10, then dist-upgraded to 14.04, then to 16.04, and recently to 18.04. It still works fine, but lusting for power I bought a Lenovo P73 that will be delivered today. 

Now, I know that I will get lots of replies extolling the virtues of a fresh install, but I refuse. I have over 250 .desktop files in /usr/share/applications, half of which are not in the repos and which took a lot of effort to install. It would take me half an hour just to get the desktop configured the way I want it, and lots more time to get applications set up. I do a lot of work with ancient languages (Greek, Latin, Samskrit), plus I am a movie fan and have 50+ applications for encoding videos, editing subtitles, etc. When I did the fresh install of 13.10 it took me over a week to get things set up the way I needed them. Therefore, if you want to post a 'fresh install' admonition, save your time. :)

There is a greater than zero possibility that a fresh install may become the only way to do it, and I might end up condemned to a week of configuration travails, but I will not do so without giving an OS transfer my best shot.

The new computer will come with Windows 10 Home on a 1TB NVMe drive. I plan to wipe it out and partition the drive with a 100G partition for / and 900G for /home. I can handle this much easily. The part that I need help with is transferring / and /home from my old computer to the new one. Copying the files is no problem; making the / partition bootable is. 

I have searched the forums and I find lots of posts about UEFI, but none discuss transferring Ubuntu to the new computer. For what it's worth, I don't care about security for the boot process.

If this has already been covered elsewhere, a link would be helpful. Otherwise, all suggestions will be gratefully received!

---

### Post by yancek on 2019-12-05
Is the Xubuntu install UEFI or Legacy?  Guessing it is Legacy and if so and you have an EFI partition with the windows 10 (this is the default), you should be able to install Grub EFI files to that partition with boot repair. The link below explains it, the section under Converting Ubuntu into UEFI mode.  There is a link to boot repair on that page.  Another method described at the 2nd link below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://linuxsuperuser.com/reinstall-grub2-efi-bootloader-ubuntu/](https://linuxsuperuser.com/reinstall-grub2-efi-bootloader-ubuntu/)

---

### Post by oldfred on 2019-12-05
Bit more difficult to convert BIOS install to UEFI. But main difference is grub and some settings which reinstall of grub handles.
You can keep gpt partitioning & BIOS boot if you have a 1 or 2MB unformatted partition with bios_grub flag. I started using gpt with my BIOS only system in 2012. Expected to eventually convert to UEFI, so in 2012 started formatting new drives with both an ESP & bios_grub. 
Now sure how well NVMe works with BIOS. NVMe is very new, BIOS is very old.

So you say you have no backup. And then your data may not be very valuable as hard drives fail, sometimes without any warning. And then everything is gone.
You can export list of installed apps to make it easy to reinstall. If you used ppa, you can export them. If you downloaded .deb, you need to back those up also. 
All your user settings are in /home, no reconfiguration required if you restore /home. Users often like / & /home on separate partitions to make it easier to reinstall and just reuse configuration. Newer version may have some changes, but its same issue with upgrades. If a server type install, you may have some additional folders in / that should also be backed up.

---

### Post by John Jason Jordan on 2019-12-06
> **yancek said:**
> Is the Xubuntu install UEFI or Legacy?  Guessing it is Legacy and if so and you have an EFI partition with the windows 10 (this is the default), you should be able to install Grub EFI files to that partition with boot repair. The link below explains it, the section under Converting Ubuntu into UEFI mode.  There is a link to boot repair on that page.  Another method described at the 2nd link below.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://linuxsuperuser.com/reinstall-grub2-efi-bootloader-ubuntu/](https://linuxsuperuser.com/reinstall-grub2-efi-bootloader-ubuntu/)

Thanks for the links. 

I'm pretty sure my six-year old System76 computer is not UEFI. System76 sells only Linux computers, you know. The new Lenovo certainly is UEFI, however. If my System76 computer is BIOS, then that sounds like what I would want to continue on the Lenovo, assuming it's possible. 

The computer arrived, but I haven't opened the box yet. There is a local Linux user group which will be having a hands-on fix-your-computer session on the 15th, with people in attendance far smarter than me. I believe I will leave the box unopened until then. Meantime, thanks to your links, I can try to educate myself as much as I can.

---

### Post by John Jason Jordan on 2019-12-06
> **oldfred said:**
> So you say you have no backup. And then your data may not be very valuable as hard drives fail, sometimes without any warning. And then everything is gone.

I'm sorry, I must have not made something clear - I do have backups. The old computer has a 512GB SSD with 80GB / and 420GB /home partitions, and it has a second 1TB SSD that I use for backups. Everything on / and /home is backed up to the second disk. Once I have the 512GB drive cloned to the 1TB NVMe in the new computer I will remove the second SSD in the old computer and install it in the new computer, where it will continue its function as backup storage.

---

### Post by oldfred on 2019-12-06
I would still back up Windows.
You may find you do not like system & decide to sell it. Then it almost always needs Windows.
Or find one application that needs Windows, so you want to dual boot.

I just was at nearby MicroCenter, 256GB USB3 flash drive was $23. I find that useful for backups even though flash drives are slow. You only need the very low cost smaller flash drives for the Ubuntu installer. 
I find downloading & creating flash drive to be the slowest part of an install. And then partitioning can be slow if you have to move data.
But once organized, I can install in 10 minutes or less when installing from SSD or HDD to SSD, flash drive with toram parameter, so only copy into RAM, is still just over 10 minutes. Full install to flash drive is over 45 minutes. 
I would then be prepared with flash drives when you go to meeting.

---

### Post by CatKiller on 2019-12-06
> **John Jason Jordan said:**
> The old computer has a 512GB SSD with 80GB / and 420GB /home partitions, and it has a second 1TB SSD that I use for backups. Everything on / and /home is backed up to the second disk. Once I have the 512GB drive cloned to the 1TB NVMe in the new computer I will remove the second SSD in the old computer and install it in the new computer, where it will continue its function as backup storage.

I wouldn't personally do it that way. 

What I would do is do a fresh install on the new machine, and then replace the contents of the new machine's drive from the backups that you already have. You'll still have your old machine fully functional throughout, should you run into any trouble, and if your backups aren't sufficient for being used that way then you want to discover that *before* you, say, rip out your working drive and stick it in a new machine.

The biggies are switching from BIOS to UEFI, which you won't have to do because you're simply installing it as UEFI, and the fact that your partitions' UUIDs will be different. For the bootloader that won't matter - your freshly installed UEFI Grub will point to your freshly created partition - and for partition mounting it's just an edit of your /etc/fstab after you've copied it to the new drive so that it accurately lists the new partitions. 

Minimal fuss, zero downtime. The installation part takes about 20 minutes, and install and copy is probably going to be quicker than clone and resize. 

You probably aren't switching from 32-bit to 64-bit but, if you were, then you'd want to approach it differently by fresh install, install new packages from old list, copy config files. You probably also aren't using proprietary drivers, either, but, again if you were, that would be another wrinkle that you'd need to smooth by removing the proprietary driver prior to the transfer.

---

### Post by John Jason Jordan on 2019-12-06
> **oldfred said:**
> I would still back up Windows.
You may find you do not like system & decide to sell it. Then it almost always needs Windows.
Or find one application that needs Windows, so you want to dual boot.

I do not wish to ever boot Windows. And shortly after Windows 10 came out I bought the Pro version and installed it in Virtualbox, so I have no need to dual boot. As for selling the computer, I can't conceive of ever doing that.

---

### Post by John Jason Jordan on 2019-12-06
> **CatKiller said:**
> What I would do is do a fresh install on the new machine, and then replace the contents of the new machine's drive from the backups that you already have. You'll still have your old machine fully functional throughout, should you run into any trouble, and if your backups aren't sufficient for being used that way then you want to discover that *before* you, say, rip out your working drive and stick it in a new machine.

The biggies are switching from BIOS to UEFI, which you won't have to do because you're simply installing it as UEFI, and the fact that your partitions' UUIDs will be different. For the bootloader that won't matter - your freshly installed UEFI Grub will point to your freshly created partition - and for partition mounting it's just an edit of your /etc/fstab after you've copied it to the new drive so that it accurately lists the new partitions. 

I thought of doing it that way. But to clarify, if I do it that way, when I copy everything from / and ~/ on the old computer to the new installation, I would not copy /boot, right? And probably other things as well. Trying to figure out what to copy and what not to copy sounds challenging.

And to clarify, I'm only going to rip out the backup SSD from the old computer, not the / and ~/ drive, so the old computer will always be bootable. And I had problems in the past with UUIDs, so I always give partitions a label, and then define them in fstab with LABEL=. I am comfortable with editing fstab.

I borrowed a USB device that will take the NVMe drive from the new Thinkpad, so I could do all this from the old computer, then put the NVMe drive back into the Thinkpad. And I have an assortment of 256GB USB3 drives, and even one that is 512GB, should they become useful. 

The debate is whether your way will work better than copy everything, then do a boot-repair.

---

### Post by TheFu on 2019-12-06
The idea that a reinstall means starting all over from the beginning isn't true.  It is just like moving houses. We get a new roof, new plumbing, new electrical lines, new fixtures that work just a little different, and carpeting.  Then we bring in our furniture, nick-knacks, drapes, shower curtains, valences, and boxes a few minutes later.  It is our HOME, just improved, faster, more efficient, perhaps with a nicer garage.

I'm with CatKiller.  Start with a fresh install. This solves so many issues.  With a basic fresh install, we get all sorts of HW optimizations and the ability to change the underlying hardware, GPU, storage setup, file systems, for the better.

After the minimal fresh install with the DE I wanted, I'd copy/restore from backups, most of my personal data, personal settings, basically my HOME.  Actually, I'd restore all the HOME directories for every userid. That includes root in /root/. Then I'd restore the system settings, configurations, data.  This the stuff that servers need, themes for desktops, whatever DBMSes, websites, stuff that is server specific, but not userid specific.  
There is one problem with this method.  It requires that we know which config files in /etc/ and /lib/ need to be restored to the new system.  We cannot blindly restore them all, since that will break things the installed setup for the new machine.   If you use rsync in a --dry-run mode, finding a list of different files could be a good first step.  Next, you could use diff to compare those files.  Hopefully, you'll remember the files you've changed over the years.  For example, I use an HTTPS-DNS-proxy. This isn't part of the default installs, so everything related to that tool in /etc/ is new.

Don't forget any crontab files from the old install.  I dump those for each account using **crontab -l** as part of my backup process.  If you keep all the cron stuff in /etc/, then you'll have that.  I keep my crontabs in /var/spool/cron/ and dump the files into /root/backups/ ... which is where I keep lots of the system information needed for recovery that isn't stored in /etc/.

Do you use virtual machines?  Where are those stored?  With libvirt, the default location is /var/lib/libvirt/ for the storage and /etc/libvirt/ for the VM settings.  But I use LVM for the block storage of my VMs.  That means the storage from them isn't mounted on the host machine - it is just an LV for each guest VM.  Let's assume you have an excellent way to backup VM storage, so it is only the XML VM virtual hardware config that needs handling.  I treat VMs like physical machines and back them up using the process I've outlined here.  The VMs recovery process requires a fresh install of an Ubuntu Server, then I restore configs, data, and programs.  Most of my servers don't have any local user accounts, so the /home/ backup is pretty tiny when compared to a desktop. Tiny:
```
$ du -sh /home/ 
621M    /home/
```

I wouldn't restore ANY media files, yet. That's for after everything else.  I keep media files outside /home/ ... so it doesn't get mixed in with files that change all the time, daily.  Having a HUGE home is something I avoid.  Makes versioned backups much easier and more efficient.  Anyways, 

Now we have a nearly ready system. IME, the install is about 15 min. The HOME directory and system stuff another 15 minutes.  We're 30 min into the process.  

Only 1 thing remains.  Programs. We haven't installed any yet.  There are 2 sorts in my world.  Custom build, outside APT and packages inside APT.  My backups include /usr/local/ and a list of all manually installed APT packages.
```
# Daily dump of current packages to $HOME/backup
 `$aptmark showmanual | tee /root/backups/apt-mark.manual`;
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade

```
Those commands will capture the manually installed APT packages into a file.  The command below it will reload those using the file and install them.  Be certain each config and data files for the programs/packages have already been placed correctly, with the correct permissions first.  This step takes about 15 minutes, tops.

So, in 45 minutes, we have a newly installed system, all our settings, data, configs, with all our programs back.  All that is missing are huge media files which could take hours, days, weeks, to reload.  But when we reboot and login using our account, it "feels" just like our old box, but faster.

I've restored systems using this method about once a year the last 9 yrs.  Got a new laptop earlier this year - it worked well.  Thankfully, that restore wasn't due to a failed disk or corrupted settings or failed server upgrade.  I've had those previously too.  Trying to restore an email server with the entire company waiting after a failed version upgrade isn't exactly fun.

Unfortunately, as with most things, the more you practice, the better you get at this stuff.  The first time I attempted it, I found some critical information was missing.  I worked the problem and after about 5 attempts, finally have everything necessary for a clean restore AND many extra pieces of data that are helpful for failures we don't always consider.  Because my backups are done using a script, that script gets a little better every time I find sometime new that would be helpful. The last improvement was in August.

BTW, boot-repair hasn't worked too well with UEFI setups.  You can manually reinstall grub, then update grub, if you like.  Just be certain to keep the connected disks to a minimal number when doing that.

---

### Post by CatKiller on 2019-12-06
> **John Jason Jordan said:**
> I thought of doing it that way. But to clarify, if I do it that way, when I copy everything from / and ~/ on the old computer to the new installation, I would not copy /boot, right?

Good spot, you are correct. Conceptually to me that was all part of the bootloader that would be all spangly-new, but I should have specified. You'd end up with a new install with your existing applications and configurations.

> The debate is whether your way will work better than copy everything, then do a boot-repair.

To be honest, I don't think either will take that long and, as long as your existing drive is still safely tucked up in your old machine, neither is destructive to what you already have. Having the ESP all set up for you by the installer, rather than having to do it manually or rely on an automatic script, seems cleaner and more sensible to me, but you could just do one and then do the other if whichever you picked first goes pear-shaped.

---

### Post by John Jason Jordan on 2019-12-06
> **CatKiller said:**
> To be honest, I don't think either will take that long and, as long as your existing drive is still safely tucked up in your old machine, neither is destructive to what you already have. Having the ESP all set up for you by the installer, rather than having to do it manually or rely on an automatic script, seems cleaner and more sensible to me, but you could just do one and then do the other if whichever you picked first goes pear-shaped.

Yeah, that makes sense. I have decided that I'm going to do the copy-and-fix-grub method. If that fails, then plan B is to do a fresh-install-and-copy.

---

### Post by TheFu on 2019-12-06
> **John Jason Jordan said:**
> Yeah, that makes sense. I have decided that I'm going to do the copy-and-fix-grub method. If that fails, then plan B is to do a fresh-install-and-copy.

Seems like a good plan. And you'll KNOW which works when all done.

I've unplugged HDDs and physically moved them into other systems a few times. 
I've also used ddrescue to completely clone disk A ---> disk B, including the boot sectors, partition tables - EVERYTHING.  Always needed to fix the fstab and udev rules for networking stuff.  Last time I did this, it was moving from an AMD E-350 APU system into a Pentium G3258 system that supported UEFI.  Ran it in legacy BIOS mode until the next OS upgrade, then did a fresh install and restored backups.  Not having any weird HW helps.

---

### Post by John Jason Jordan on 2019-12-16
> **TheFu said:**
> Seems like a good plan. And you'll KNOW which works when all done.

Success!

I started by removing the 1TB NVMe drive from the new computer and putting it into a USB adapter that I could plug into my old computer. Using GPartd I nuked the various Windows partitions and then created a 100GB root partition and a 900GB home partition, giving them labels as Root and Home. Then I copied everything from the root of my old computer to the new root partition. It took nearly half an hour to copy 30GB. I was impatient and unwilling to spend the time it would take to copy /home from the old computer to the new drive, so I just copied the .dot files, figuring that this would give me most of the configurations, and I would copy the rest later.

All prepared, I moved the NVMe drive back to the new computer and pressed the power button, crossing fingers and holding my breath. Nothing happened. Nothing at all, except that the keyboard lights came on. It took an hour of searching the net until I finally discovered that my partitions were the default that GPartd uses, where I needed them to be msdos partitions. Back to the drawing board. All my work so far went down the drain, as I had to delete my partitions and create new ones. Except that this time I decided to use dd to clone the root partition from the old computer, so I ended up with a root partition of only 30GB. Finally, I went back to GPartd and used it to enlarge the new root partition to 100GB, and then created a second msdos partition of 900GB for home. And this time I decided to be patient and copy all of /home to the new Thinkpad /home partition.

It took about three hours to copy /home from my old computer to the new one (390GB), and then a couple hours fixing boot problems. The old computer had / and /home defined in fstab by LABEL=Boot and LABEL=Home, plus several external drives. I anticipated this would be a problem, so I used a Knoppix USB stick to # the external drives, and changed 'Boot' to 'Root,' (because that is the label that I used on the new partition). But it still wouldn't boot. It took a while to figure out that it wasn't finding /home and /, but when I eventually realized what was happening I changed them to /dev/sda1 and /dev/sda2, but still no joy. Then I tried /dev/nvme1 and /dev/nvme2, and when they also failed I was ready to tear my hair out. Finally I used UUIDs, and then I heaved a sigh of relief when the familiar Xubuntu login screen appeared. And here I am, typing on this shiny new Thinkpad.

There are still some things to fix - font sizes are first on my list. The old monitor was 1920x1080 and the new one is 3840x2160 UHD. I was amazed that Xubuntu finally delivered the right resolution - in spite of quite a few error messages about NVIDIA during boot, due probably to different drivers. Also wifi isn't working; it doesn't even appear at an ifconfig command. I suspect the BIOS, but not to worry; I can fix it.

I'm just posting this to let everyone know that if you have a ton of configurations and applications installed you may find it massively easier to copy your installation to a new computer instead of doing a fresh install and then spending days getting everything istalled and set up. I haven't tried all of my hundreds of applications yet, but everything that I tried is working just as before. 

And, of course, I also want to say thanks to all who helped with moving my Xubuntu 18.04 to the new computer!

---

