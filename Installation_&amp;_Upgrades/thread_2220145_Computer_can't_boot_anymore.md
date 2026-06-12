---
title: "Computer can't boot anymore"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by omeprazol on 2014-04-26
Hello!

I have a serious problem with my main computer. I have built it myself and had it since 2010. It's an ASUS [FONT=arial]P6TD Deluxe motherboard with a I[/FONT][FONT=arial]ntel Core™ i7 Quad Processor i7-930. The graphic card is [/FONT][FONT=arial]XFX Radeon HD 5830 1GB GDDR5. 1 sdd of 125 gb, 1 hdd of 500gb divided into 2 partitions, and a old hdd of 20gb. I have been using windows 7 on it for most part, but latly I cind of had to swich to windows 8.1 (a long and unrelated history). A coupple of month ago, I decided to try Ubuntu, since I have been interested of it for quite some time, and installed Ubuntu 12.04 LTS on my old 20 gb hdd and made bios boot from that drive. After some minor problems, I succeded to install it and could boot both to Ubuntu and Windows thrue the GRUB menu.

Then the expansion to D3 released and henceforth I had to be in Windows for some time. Today when I read that the new LTS been released, I decided to switch over to Ubuntu again. When there the uppdater poped up and wanted to update a lot, did that and rebooted the computer. But when Ubuntu tried to load again, it just hanged while starting up. Nothing happend. Tried to reboot again whith recovery mode, same result. Rebooted again and choosed to start with an older version (or whatever it's named in the grub menu), then it worked! Thought that it must had gone something wrong with the update last time and that it might be better a secound time, som I whent to the updater and updated everything again. But this time as I rebooted I didn't get to the GRUB menu, I got to a prompt with a previus message saying something like "hit TAB to se a list of possible commands". I googled it and found a guide how to load a ubuntu iso file from the grub rescue prompt, downloaded the 14.04 LTS AMD64 iso to a usb and succeded after quite some time and choosed to update my existing ubuntu to the newer version. It didn't work. Burned the iso to a cd and tried to replace the existing Ubuntu, same result.

Used try Ubuntu and downloaded and run GRUB-Repair, didn't work.

Googled some more and found some1 that had similar problem who discovered that the install was according to a efi boot although hes computer (adn mine) didn't had that, just old BIOS and henceforth could fix it by removing the efi files and load the corresponding for BIOS versions. Tried the command they suggested, but it couldn't find the files to delete and could copy the new ones either.

Now every time I try to boot, I got "error: file '/boot/grub/i386-pc/normal.mod' not found. Entering rescue mode..." I've tried in BIOS to switch back boot to the ssd (where Win 8 is) but with the same result. Have tried to insert bootable cd's, both Ubuntu and Windows 8, but the computers can only boot on them occasionly, for most part, the only thing I got is that damed error message!

I have run out of ideas, please help me! My computer is atm totaly useless, can't use either Ubuntu nor Windows!

Thanks in forehand!

(sorry for the bad explaining, isn't verry good in english, and Ubuntu and linux is still pretty new to me)[/FONT]

---

### Post by Bashing-om on 2014-04-26
omeprazol; Tough luck !

No computer is no fun.

OK, can you boot that liveDVD to the desktop in "try ubuntu" mode ?

We can then take a look around and see what we do not want to do, might be best then to wipe the KNOWN partitions with ubuntu's partition editor and (re-)install from scratch ? ( any data now that ya need to save in the ubuntu install ?).

In a situation ss described, In My Opinion, best to start fresh and see what then happens.

[INDENT][INDENT]my thoughts
[INDENT][INDENT][INDENT]others are welcome
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by omeprazol on 2014-04-27
Thats the strange part... It's not allways that I can boot from any cd's (or from the win partition for that matter). But whatever reason, my computer decided to be a little nice to mey while waking up this morning, so I have now succeded in booting in Ubuntu trial mode, so now I can give U a little more info.

When I ran GRUB-repair it created a logg, here it is: [http://paste.ubuntu.com/7340631/](http://paste.ubuntu.com/7340631/)

I have no important info on the HDD containing Ubuntu, that partition we can wipe how many times we whant, but if we need to wipe all partitions even in other drives, then it gonna be a massive datamoving opperations...

---

### Post by omeprazol on 2014-04-27
Tried to remove all partitions on my ubuntu hdd, remake them exaktly as theye were before and installed Ubuntu again. Now I got a new error message while trying to boot...

error no such device:4aba6ea0-d6ad-4ddd-985a-97e1934b6aff.

And once again I am unable too boot from cd...

---

### Post by omeprazol on 2014-04-27
seems that in my eager to switch back and forth betweed the win ssd and ubuntu hdd as the primary drive in BIOS in order to check if the computer could boot from any drive, I forgot to switch back to the ubuntu1 before trying to reinstall it. Now it gives me another error message while trying to boot from ubuntu hdd...

error: invalid extent.

---

### Post by Bashing-om on 2014-04-27
omeprazol; Weelll,

UpFront, I am not Windows literate.

Looks to me like however, there is going to be a problem booting Windows.
Windows 8 = UEFI = GPT partitioning ->
Ubuntu should be set to match.
So, why am I seeing the old legacy msdos booting setup ? Again I say What I do not know fills a much larger book than that of what I do know. 
> 
Disk /dev/sda: 128GB -> Partition Table: msdos
Disk /dev/sdb: 500GB -> Partition Table: msdos

I totally expect these Partition tables to be "GPT" for Window 8 !
> 
Disk /dev/sdc: 20.4GB
Partition Table: msdos

Which again I had expected to see 'GPT' Partitioning to dual boot with Windows 8. Maybe as the operating systems being on different hard drives will not matter. 

------------
sda is Windows hard drive, I do not see the expected EFI boot partition, but, the boot flag is set ( legacy ???).
sdb is a Windows hard drive - again I see not EFI boot partition, so maybe this disk is all "data" ?
sdc is ubuntu set up under the legacy msdos partitioning and looks good for that scheme. But, I do not know that would work if Windows were reverted to EFI/GPT .

My concerns at this time.
What have you done to change the partitioning scheme from GPT ( for what is Window's default) to 'msdos' partitioning ?
When you set in the boot manager at system start up to boot the 1st hard drive (Windows), what results ?
When set to boot the 3rd hard drive at startup (ubuntu), what results ?
From ubuntu's grub menu (sdc), what results when you boot Windows ?


I must say at this point
[INDENT][INDENT]if it works, do not fix it !
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-04-27
omeprazol; Yikes !

Consider my last post.

As it presently stands, we can make it to where you can boot ubuntu on the sdc drive, Getting Windows back in a workable state is beyond my knowledge. No sorry about that.


When this all settles down, and you think about what you need to do -- and others have had an opportunity to look at this thread --- then we will do something

[INDENT]Right Wrong or Otherwise
[INDENT][INDENT][INDENT]when it's broke
[INDENT][INDENT][INDENT]do something
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by omeprazol on 2014-04-27
kind of have made an half victory...

Figured out that the times I could boot from dvd's (both win8 and ubuntu) was when I have hade the computer turned of for longer times, pref without power source. I removed the ubuntu hdd, set up BIOS to the win ssd as the primary (bootable) disk, booted to win8 cd, whent to prompt and used bootrec /fixmbr

Now I have at least win8 back. Unfortantly it resulted in me giving up Ubuntu, and considering the verry odd behavior of the computer, I don't know if I dare try it again on my main computer, at least not untill I've understood what happend...

Does any1 have a clue?

---

### Post by omeprazol on 2014-04-27
> **Bashing-om said:**
> omeprazol; Weelll,

UpFront, I am not Windows literate.

Looks to me like however, there is going to be a problem booting Windows.
Windows 8 = UEFI = GPT partitioning ->
Ubuntu should be set to match.
So, why am I seeing the old legacy msdos booting setup ? Again I say What I do not know fills a much larger book than that of what I do know. 

I totally expect these Partition tables to be "GPT" for Window 8 !

Which again I had expected to see 'GPT' Partitioning to dual boot with Windows 8. Maybe as the operating systems being on different hard drives will not matter. 

------------
sda is Windows hard drive, I do not see the expected EFI boot partition, but, the boot flag is set ( legacy ???).
sdb is a Windows hard drive - again I see not EFI boot partition, so maybe this disk is all "data" ?
sdc is ubuntu set up under the legacy msdos partitioning and looks good for that scheme. But, I do not know that would work if Windows were reverted to EFI/GPT .

My concerns at this time.
What have you done to change the partitioning scheme from GPT ( for what is Window's default) to 'msdos' partitioning ?
When you set in the boot manager at system start up to boot the 1st hard drive (Windows), what results ?
When set to boot the 3rd hard drive at startup (ubuntu), what results ?
From ubuntu's grub menu (sdc), what results when you boot Windows ?


I must say at this point[INDENT][INDENT]if it works, do not fix it !
[/INDENT]
[/INDENT]


- My motherbord does not support efi, hence why my computer is and should use "legacy setting" (whitch is normal settings for my motherboard).
- previusly: [COLOR=#000000]error no such device:4aba6ea0-d6ad-4ddd-985a-97e1934b6aff. (now it boots again)
- [/COLOR][COLOR=#000000]error: invalid extent.
- couldn't reach grub menu, only grub rescue[/COLOR]

---

### Post by Bashing-om on 2014-04-27
omeprazol; Well, yeah.

I do have a vague idea of what is going on. One must make sure when booting Windows 8 that one is booting in EFI mode, that the OS is setup for that UEFI system.

Like I have advised, I am not Windows literate. but there are those I can contact here on the forum that are !..
If it is your desire to proceed to install ubuntu and dual boot your system; I will be more than happy to get another's attention and see if (he) is in a position to render aid.

[INDENT][INDENT]which way did he go,
[INDENT][INDENT][INDENT]George[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by omeprazol on 2014-04-27
I dont have a UEFI system, my motherboard doesn't support it, but I'm starting to wounder if Ubuntu tried to start up as 1 (in that case I can understand why a little, even if I don't se how to fix).

Windows in now running again, so that part is fixed again. the problem now is to understand why Ubuntu fail to boot after installation, multipple times...

---

### Post by Bashing-om on 2014-04-27
omeprazol; Well,

Wonders Never cease and I never stop learning.
Windows 8 will install and run on the old legacy partitions. Great !

Should be no big deal to get this straightened up.

Let's leave the Windows' Hard drive alone (sda ? is it ?) and set up booting from ubuntu on sdc.
In this scheme of things, bios set to boot from sdc, we will chainload Windows onto ubuntu's grub. If at anytime there is a problem booting sdc, one can change the boot order in bios to boot sda .. sound good ? I like the idea of not messing with the Windows' boot loader - never can tell what might happen and is nice to know the other system can boot !

Do we now need to check the system installation on sdc ? or can we proceed to install grub to the MBR of the sdc hard drive ?

[INDENT][INDENT]more than one path
[INDENT][INDENT][INDENT]to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-04-27
Windows 8 will boot in BIOS mode from MBR partitions, it just is most Windows 8 systems are pre-installed and those all are UEFI systems with gpt partitioning.

While I regularly suggest Boot-Repair, I do not like its reinstall grub2's boot loader to every hard drive with its auto fix when you have multiple hard drives. I assume it is so users do not have to change BIOS to boot Ubuntu drive or use one time boot key. It just make Ubuntu work.
But it really is better to keep each install on a separate drive and have that install's boot loader in the MBR of that drive. 
And Boot-Repair can do that under its advanced mode. Choose Windows and install its boot loader to sda. And choose your Ubuntu install on sdc and install its boot loader to sdc and then change BIOS to boot sdc.

In your case you always want to keep a Windows boot loader in the MBR of sda.

---

### Post by Bashing-om on 2014-04-27
@ oldfred;

Heaps of appreciation for the clarification.

@ omeprazol; As you see we are all here for you, Let us know how you prefer to proceed.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by omeprazol on 2014-04-28
Thanks alot for the informations! I now see some steps that I did wrong and resulted is some of the errors...

It seems I should have sticked to the rule I'm recomending others... "don't use the recomended install, allways the advanced"!

Thats why I couldn't boot from sda after switch in BIOS, GRUB-Repair had altered the MBR of that disk too...

But it doesn´t explain the odd behavior of refusing to boot from cd's unless powered down for some time, or why GRUB failed to be installed propperly several times. Considering I whiped all partitions in sdc and reinserted new ones before last install, I can´t see why it couldn't be installed propperly... I had no such problem when I installed 12.04 a coupple of months ago.

At the moment I´m feeling still a little shaky after all the troubble, and is happy I do have a working computer again... Let's see if I have recovered some strength and energy later on this day to reinsert sdc and give it another try. But in the meantime, anyone have any suggestions why it has failed earlier, or rather how to do so it doesn't fail again?

---

### Post by omeprazol on 2014-04-28
I have now plugged in sdc again, set BIOS to load from it. Started up on the Ubuntu cd, choosed install, something else, erased every partition on sdc (ext4 and swap) and redone them (same size) and formated them, and choosed sdc at the bottom (according to what I can understand, that setting let u choose where the installation program shall put GRUB, or something like that).

Once again I'm reaching grub rescue instead of menu, this time with the message "error: invalid extent.", at least I got some variations on the theme ;)

I'm lodaing "try ubuntu" atm in order to run GRUB-repair, this time not the recomended but advanced option ;) any other suggestion?

---

### Post by omeprazol on 2014-04-28
enough for today... now Boot/repair wont work either...

This is what I get trying to install bootrepair in "try ubuntu" mode.

```
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpt6jagg1p/secring.gpg' created
gpg: keyring `/tmp/tmpt6jagg1p/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpt6jagg1p/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty InRelease
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/main Translation-sv_SE
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/main Translation-sv
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/restricted Translation-sv_SE
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/restricted Translation-sv
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/restricted Translation-en
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Bra http://security.ubuntu.com trusty-security Release.gpg                  
Ign http://ppa.launchpad.net trusty Release.gpg                             
Bra http://security.ubuntu.com trusty-security Release
Ign http://ppa.launchpad.net trusty Release                             
Ign http://archive.ubuntu.com trusty InRelease                          
Bra http://security.ubuntu.com trusty-security/main amd64 Packages
Bra http://security.ubuntu.com trusty-security/restricted amd64 Packages
Ign http://archive.ubuntu.com trusty-updates InRelease                  
Läs:1 http://security.ubuntu.com trusty-security/main Translation-en [3 972 B]
Bra http://archive.ubuntu.com trusty Release.gpg                               
Bra http://security.ubuntu.com trusty-security/restricted Translation-en 
Bra http://archive.ubuntu.com trusty-updates Release.gpg                 
Bra http://archive.ubuntu.com trusty Release                             
Bra http://archive.ubuntu.com trusty-updates Release                           
Bra http://archive.ubuntu.com trusty/main amd64 Packages                 
Fel http://ppa.launchpad.net trusty/main amd64 Packages                 
  404  Not Found
Bra http://archive.ubuntu.com trusty/restricted amd64 Packages          
Ign http://ppa.launchpad.net trusty/main Translation-sv_SE
Ign http://ppa.launchpad.net trusty/main Translation-sv
Ign http://security.ubuntu.com trusty-security/main Translation-sv_SE
Ign http://ppa.launchpad.net trusty/main Translation-en                  
Ign http://security.ubuntu.com trusty-security/main Translation-sv       
Bra http://archive.ubuntu.com trusty/main Translation-sv
Ign http://security.ubuntu.com trusty-security/restricted Translation-sv_SE
Ign http://security.ubuntu.com trusty-security/restricted Translation-sv
Bra http://archive.ubuntu.com trusty/main Translation-en
Bra http://archive.ubuntu.com trusty/restricted Translation-sv
Bra http://archive.ubuntu.com trusty/restricted Translation-en
Bra http://archive.ubuntu.com trusty-updates/main amd64 Packages
Bra http://archive.ubuntu.com trusty-updates/restricted amd64 Packages
Bra http://archive.ubuntu.com trusty-updates/main Translation-en
Bra http://archive.ubuntu.com trusty-updates/restricted Translation-en
Ign http://archive.ubuntu.com trusty/main Translation-sv_SE
Ign http://archive.ubuntu.com trusty/restricted Translation-sv_SE
Ign http://archive.ubuntu.com trusty-updates/main Translation-sv_SE
Ign http://archive.ubuntu.com trusty-updates/main Translation-sv
Ign http://archive.ubuntu.com trusty-updates/restricted Translation-sv_SE
Ign http://archive.ubuntu.com trusty-updates/restricted Translation-sv         
Hämtade 3 972 B på 6s (639 B/s)                                                
W: Misslyckades med att hämta http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
E: Kunde inte hitta paketet boot-repair
ubuntu@ubuntu:~$ sudo apt-get install boot-repair
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
E: Kunde inte hitta paketet boot-repair

```

---

### Post by oldfred on 2014-04-28
For Boot-Repair, there is not a trusty version, yet. You change to use the saucy version which works just fine.

Instructions on changing to saucy included in new instructions here.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

OR:
 Only if trusty 14.04, you need a work around to install, Boot-Repair for 14.04 trusty not yet released
 ----------- WORKAROUND 0 sandyd  compiled it
 [https://launchpad.net/~sandyd/+archive/boot-repair](https://launchpad.net/~sandyd/+archive/boot-repair)
 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)

Did you create large / (root) partition? Some older systems need / inside the first 100GB of a drive. Or is BIOS set to IDE not AHCI?
I prefer smaller system partitions anyway and usually suggest 20 or 25GB for / and use rest of drive as /home or for data partition(s). I still have a NTFS data partition although not using XP anymore and a Linux formatted data partition.

---

### Post by Bashing-om on 2014-04-28
omeprazol; Hey,

See oldfred's last.

I do not know why you are having such difficulties installing grub - Hard to say when we are not looking over your shoulder.

Not to take away from that most excellent tool -boot-repair - , but I too have had some unpleasant experiences with it and have learned a bit about the complexities of the boot manager.

If you so desire we can indeed install grub manually from the liveDVD and see what results.
If you do so decide to do the manual install, show me what we are working with:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
If all looks good it is a simple matter to install grub to the MBR of that hard drive.
Take it from there and see what happens.

[INDENT][INDENT]it is a process
[INDENT][INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by omeprazol on 2014-04-28
> **oldfred said:**
> For Boot-Repair, there is not a trusty version, yet. You change to use the saucy version which works just fine.

Instructions on changing to saucy included in new instructions here.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

OR:
 Only if trusty 14.04, you need a work around to install, Boot-Repair for 14.04 trusty not yet released
 ----------- WORKAROUND 0 sandyd  compiled it
 [https://launchpad.net/~sandyd/+archive/boot-repair](https://launchpad.net/~sandyd/+archive/boot-repair)
 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)

Did you create large / (root) partition? Some older systems need / inside the first 100GB of a drive. Or is BIOS set to IDE not AHCI?
I prefer smaller system partitions anyway and usually suggest 20 or 25GB for / and use rest of drive as /home or for data partition(s). I still have a NTFS data partition although not using XP anymore and a Linux formatted data partition.

I probably should have told U this earlier...

sdc is a very old disk (starting to wounder if it may have starting to fail...) It's not even a sata disk, it's connected with an old school flat IDE cable (together with the DVD-R/W) and has the size of 20 GB (probably a verry large disk at the time it was fabricated). The first part of the disk I created as an ext4 disk (13983 MB) and the rest as a swap disk. I just coppied the sizes and types as the previus Ubuntuinstall had done.

now for U´r secound question... Yes, BIOS is set to IDE. Was a time ago I was dealing with those settings, but if I'm not remembering it wrong, I cind of have to have that setting, otherwise I can't use sdc or the dvd. But I can be wrong about that, as I said, It was a long time ago I was checking those different settings. Does this setting change anything?

Think I take workaround 2... seems to be easiest and I'm feeling lazy ;)

---

### Post by omeprazol on 2014-04-28
went pretty much as the last times... end up with grub rescue and still with message: "error: invalid extent."

report from Boot-repair: [http://paste.ubuntu.com/7353952/](http://paste.ubuntu.com/7353952/)

---

### Post by oldfred on 2014-04-28
I do not see anything wrong with install.

But if old IDE drive, you may need IDE in BIOS.
But you need correct jumpers on drive and correct cables. I have messed that up so many times that I only use SATA now. Plus I really hate those little tiny jumpers on the drive. 

You need drive jumpered for cable select and use the 80 conductor cable. 
If 40 conductor cable, you may be able to jumper as master, but no idea if it will work. The old master/slave and old BIOS only booted from a Master.

       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

Did I mention how much I hated the old IDE/PATA drives and the little tiny jumpers. :)

---

### Post by omeprazol on 2014-04-28
> **oldfred said:**
> I do not see anything wrong with install.

But if old IDE drive, you may need IDE in BIOS.
But you need correct jumpers on drive and correct cables. I have messed that up so many times that I only use SATA now. Plus I really hate those little tiny jumpers on the drive. 

You need drive jumpered for cable select and use the 80 conductor cable. 
If 40 conductor cable, you may be able to jumper as master, but no idea if it will work. The old master/slave and old BIOS only booted from a Master.

       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

Did I mention how much I hated the old IDE/PATA drives and the little tiny jumpers. :)

I do have the settings for IDE in BIOS sett. thats what oldfred asked about...

Anyhow, I haven´t checked the jumper setting on the sdc nor the DVD, but it worked without any problem last time with 12.04, and I haven't changed anything of that sort since... let's see when I can look that up in closer look (gonna be hard, it's in the middle of the cable-djungel with all the power cables passing by, not to mention the IDE cable itself...)

...and yea, I hate them aswell! Sitting atm and wounder if it isn´t time to by a new DVD on sata and get rid of the IDE (throw away the sdc).

Is it doable to reduce 1 win partition in size on sdb and install ubuntu on that even if the ext4 partition probably not gonna be in the beggining of the hdd and then let BIOS boot from sdb?

In that case, we could se if avoiding ide solves our problem...

---

### Post by oldfred on 2014-04-28
That should work.
There are a few exceptions. Some older BIOS only boot from first 137GB of a drive. And the IDE setting may emulate that even if a bit newer system. Do you have AHCI or LBA as other settings for drive.
ACHI may cause issues booting Windows so you need to check.

I upgraded motherboard in 2009 and have many fully bootable partitions beyond 137GB. And the issue seems to be more with USB hard drives. If necessary you probably could shrink sdb1 and add a /boot partition after it. And shrink sdb2 to make an extended partition wit / (root), /home (optional) and swap.

When I got my SSD, they said I had to have AHCI for trim to work. But then XP would not boot. But that was a good thing as then it finally weaned me off Windows. Windows 7 has a AHCI driver, so will work if driver enabled.

---

### Post by omeprazol on 2014-04-28
Happy times!

Ubuntu is once again on the system!

If it was the old disk starting to give up, or the master/slave setting making jokes (discovered while unplugging sdc that the DVD isn't a IDE, only looked like the ide cable went by) I don't know. Worked to remove it and install on new made partiton in sdb.

One good thing is that I finnaly has a reason to do something I'v whaited a time to do... get rid of that noizy old disk!!!

Thanks alot every1!!!

---

### Post by Bashing-om on 2014-04-28
omeprazol; Oh Joy !

You do good work, oldfred once more points the way.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

