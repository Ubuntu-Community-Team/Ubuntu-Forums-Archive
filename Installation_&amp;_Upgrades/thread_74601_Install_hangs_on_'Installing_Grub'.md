---
title: "Install hangs on 'Installing Grub'"
date: 2005-10-12
forum: Installation &amp; Upgrades
---

### Post by chrestomanci on 2005-10-12
Hi.

I am attempting to install the AMD64 version of 5.10 Breezy Badger on a new seral ATA (SATA) hard drive. The installer always hangs at 0% on the 'Installing Grub' screen. If I try instaling lilo instead that gets stuck at 50%.

My system has an AMD64 3200 cpu, 1Gb ram, Via chipset. The drive I am using is a 250 Gb Segate Barracuda 7200.7 SATA drive that was purchced for the purpose and has never been prevously used. When installing, I setup about 8 partions for varous purposes, rather than taking the default of one big partion. I accepted the default ext3 partion type.

Do you have any suggestions on how to proceed? Does grub/lilo have a problem with SATA discs? would I be better of trying to instala 5.04 Hoary and then upgrading?

---

### Post by GTvulse on 2005-10-12
Bet you didn't use EXT2/3 for your boot partition but rather ReiserFS or something different.

That's a bug of the Debian installer that has bitten me more than once. If you took the precaution to create a boot floppy (you are given that chance unless the installer crashes really hard), Just boot from the floppy and install grub from the fully running system like: ```
sudo grub-install /dev/sda
``` if installing to the MBR, else, you know what partition you used. If you don't have a boot floppy, you will need to boot up the install cd in rescue mode, follow the procedure to mount your root partition and do as described above.

---

### Post by chrestomanci on 2005-10-12
[QUOTE=dradul]Bet you didn't use EXT2/3 for your boot partition but rather ReiserFS or something different.[/QUOTE]
The installer selected ext3 as the default filesystem for all partions. I did not create a seperate '/boot' partion, so the '/boot' directory would have been part of the '/' root partion. Also, when setting up the '/' partion, I looked in the mount options for a 'notail' option, as I would if I where running reiserfs, but there was no such option avalable.

---

### Post by GTvulse on 2005-10-12
Then the only thing left is a bug in the interaction of the SATA driver in the installation kernel (which is different to the actual kernel installed in your HD, btw) and your particular hardware. The procedure I outline above is your best bet for recovery yet.

---

### Post by ikd69 on 2005-10-12
I have experienced the same problem using an AMD64 3000+ and a seagate 200GB SATA drive.  I used ext3 and created separate partitions for /boot, /, and /home.

I also noticed that when either one of the root or the /home partitions were larger than 100G, the installer left me waiting at 0% :confused: .  This did not happen when I resized both partitions to 95G.

Strange things!!!

ikd

---

### Post by chrestomanci on 2005-10-13
[QUOTE=ikd69]I have experienced the same problem using an AMD64 3000+ and a seagate 200GB SATA drive.  I used ext3 and created separate partitions for /boot, /, and /home.

I also noticed that when either one of the root or the /home partitions were larger than 100G, the installer left me waiting at 0% :confused: .  This did not happen when I resized both partitions to 95G.[/QUOTE]
Thanks for the suggestion, but unfortunately that did not fix it for me.

I tried reducing the the size of the home partion to 95gb, and filling the rest of the HD with some unused partions (all less than 100gb) but the instalation still got stuck at the same point.

I might try setting up lilo on that system using knoppix or suchlike. Do you know if a 32 bit version of lilo can start a 64 bit kernel?

---

### Post by ember on 2005-10-17
I happened to have the same problem, I tracked down the problem to the point that it is rather unimportant, how large your partitions are, yet your "/"-partition, there your boot directory, must be under 100G.

So I propose as a workaround (at least that's what I did), to create two partitions, one that is your root partition and the rest for home. The root partition must not end beyond 100G.

After that, the install worked for me relative painless.

---

### Post by chrestomanci on 2005-10-18
**All** my partions are under 100Gb. Unfortunately this workarround is not working for me.

Here is what the partion table looks like (I mounted the drive on another computer)
> 
[FONT="Courier New"]/dev/sda2             2.1G  176M  1.8G   9% /kubuntu64
/dev/sda1             449M  7.9M  417M   2% /kubuntu64/boot
/dev/sda5             9.2G  1.9G  6.9G  22% /kubuntu64/usr
/dev/sda6             7.4G  776M  6.3G  11% /kubuntu64/var
/dev/sda7             4.4G  129M  4.0G   4% /kubuntu64/usr/local
/dev/sda8             1.8G   33M  1.7G   2% /kubuntu64/tmp
/dev/sda9              88G  129M   83G   1% /kubuntu64/home
/dev/sda10             88G  129M   83G   1% /kubuntu64/downloads
/dev/sda11             29G  129M   27G   1% /kubuntu64/var/Bakups
[/FONT]
There is also a 2Gb swap partion in there as sda4, which obvously does not appear in the output of the mount command.

I think I will next try setting up the disk with **All** the space above 100Gb as unused, and then put a home partion there after the install completes.

---

### Post by Innova on 2005-11-16
I also am hanging when the installtion tries to install grub.  

Hardware:
Athlon 64 x2 3800+
Epox nForce4 Ultra MB
Hitachi 7k250 ATA hard drive

I am installing the i386 version of breezy badger.

Has anyone found a solution to this problem yet?

---

### Post by chrestomanci on 2005-11-16
I got my system installed.

What I did was to setup the partions so that all the space on the drive above 100Gb was unformated & unused. I also used the offical 5.10 Breezy Badger release instead of the prevew release candidate I was using before.

However, my plan was to format the unused space & set it up as a large /home partion, but I found that my command line tools such as cfdisk and mkfs could not access the space, so there may be a bug in 64 bit ubuntu that prevents unserland tools from accessing large SATA discs.

I have not used that system recently so I have not had much chance to investigate the problem. It could be nothing.

---

### Post by Innova on 2005-11-16
My disk setup is as follows:

100GB windows XP.
Remaining 150GB to Ubuntu (I used the defaults).

I am assuming that Grub was unable to write to the MBR for some reason, but I don't know why.

I have IDE0 Primary as my HD and IDE1 Primary as my DVD Burner.  I thought this post was similar:  [http://ubuntuforums.org/showthread.php?t=66160&highlight=grub+hangs+installing](http://ubuntuforums.org/showthread.php?t=66160&highlight=grub+hangs+installing)

But since my install drive is IDE0 Primary, and I don't have any other drives, this probably isn't the same.

The biggest problem is that after I reboot from the hang, I could no longer boot Windows XP.  Even after running fixmbr from recovery mode it would not boot.  I had to do a re-install.

---

### Post by dogson on 2005-12-11
[QUOTE=Innova]I also am hanging when the installtion tries to install grub.  

Hardware:
Athlon 64 x2 3800+
Epox nForce4 Ultra MB
Hitachi 7k250 ATA hard drive

I am installing the i386 version of breezy badger.

Has anyone found a solution to this problem yet?[/QUOTE]

bump, same problem 
Sempron 64 2800+
MSI NEO-V VIA K8M800
Samsung Spinpoint 250GB SATAII

---

### Post by Pentagonees on 2006-02-04
*bump*

I have the exact same problem. Isn't there any workaround or solution for this situation?

---

### Post by chrestomanci on 2006-02-05
[QUOTE=Pentagonees]*bump*

I have the exact same problem. Isn't there any workaround or solution for this situation?[/QUOTE]
The work around I found was to setup the disc so that all the partions where below the 100Gb Limit, and to proceed with the install. When everything was installed and working, I created and formated the extra partions I needed above that limit, and then re-arranged mount points and copied data so that everything worked. It was a bit of hassle, but not a great deal.

I am also booting my system using Lilo, which may or may not be a factor.

---

### Post by Pentagonees on 2006-02-06
Thanks for the reply! Not sure though if this solution works for me since all my partitions are way below 100 gig's. My first SATA disk contains Win XP with two partitons (20 gig's and 60 gig's). My second SATA  disk, the Kubuntu one, is setup as follows:

/boot: 15 MB
swap: 2.1 gig's
/: 17.4 gig's
/home: 20 gig's
/usr/local: 20 gig's
/var: 20 gig's

Could this problem be related to the SATA chipset (in my case the Silicon Image 3112 (sil3112))?

---

### Post by chrestomanci on 2006-02-06
[QUOTE=Pentagonees]Could this problem be related to the SATA chipset (in my case the Silicon Image 3112 (sil3112))?[/QUOTE]
Possibly, but I do not have that chipset, and I am suffering the same problem, so it can't be the only cause.

---

