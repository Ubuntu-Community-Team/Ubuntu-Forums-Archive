---
title: "Can’t install because it wants an EFI Partition…I have none, it says its a bad idea"
date: 2021-06-26
forum: Installation &amp; Upgrades
---

### Post by slaytanicprion on 2021-06-26
I formatted a 1 TB drive to ext4 to install 20.04  LTS, I'm tired of using live sessions from usb that are doomed to crash  eventually and also not let me use all the power of my desktop. The bar  on the drive with Linux Mint 17.3 is green, because grub is installed  there I guess, but it's not formatted as EFI, none of my  drives/partitions are, this motherboard is able to deal with BIOS style  installs but also EFI. It seems like it's a very bad idea according to  the installer to go ahead, but I can just press delete after the boot  screen where memory, drives external and internal are listed and get  into the fancy gui that is UEFI I guess and change the boot drive order.
 
It shows the 1TB drive I formatted to ext4 in orange, tells me I  should create an EFI partition even if I decide to go ahead, of 35MB at  least, and I got really annoyed by then. This desktop had Mint 17.3 and  Win7 (until it became useless last year after January, everything  windows on that ntfs drive was removed). I wonder what would happen if I  format the drive with Mint 17.3, so I would have no hard drives with  grub installed on it and the drive that had win7 still has an MBR, but I  know how to get rid of that.

 Is all of this EFI stuff necessary? The last Linux I used installed  permanently on a drive was Mint 17.3 and it seems like things have  changed software-wise but there's nothing that changed with this desktop  except for a usb 3.0/eSATA-III dock for mechanical HDD's that are  normally internal that is plugged to an usb 3.0 hub, hot swap and all.  It's not relevant to the problem here so...am I being scared away from  installing? I'm really tired of running live sessions!


 If it matters, it's Ubuntu MATE 20.04 LTS. My system has never needed efi partitions to boot previous ubuntus or linux mints I had. Even the "Something Else..." installation menu sees the old drive with Mint 17.3 on it and says it is ext4. I'm stumped, my motherboard is this ```
ASUSTeK model: M5A97 LE R2.0 v: Rev 1.xx 
  serial: <superuser/root required> UEFI: American Megatrends v: 2701
``` Firmware is up to date to the last revision. It seems like it's able to deal with old BIOS type booting AND UEFI. The "BIOS" when I press delete at boot is a fancy gui and I can use the mouse and select the order of the drives it should look at to boot from. 

I kind of skipped learning this kind of stuff as it wasn't needed back in 2017 when I assembled that PC. Is going ahead despite the warning and creating an EFI partition of 35MB minimum really needed at all with 20.04 ? If so it's weird, I can point my bios gui/uefi/whatever to any drive that is bootable so what's happening here? Should I format it to gpt like I did for my newest drive, it's an internal drive in a hot swap dock, I just formatted it to gpt because it's the newest thing, I don't really know what it does, but the install menu doesn't see that, in fact you can't format something to GPT in there, it just sees it as ext4 because I formatted it to that format, the one with LM 17.3 is just a regular old 500gb drive that will not die that's ext4 and back then we were never asked about all of this EFI stuff. Sorry for being ignorant about this but like I said, when I pieced together this PC in 2017, I just bought the parts, put back the drives that OS's on, and told it to boot from the drive that had Mint on it and that was it, grub showed up and all was fine.

Help for what should be a very basic thing (installing ubuntu) in these crazy times please? From yet another live session, all the best to you all.

---

### Post by MAFoElffen on 2021-06-26
Just a note- UEFI has been around since 2002. You say yourself that your system supports both. If so, it can support "Either", meaning it depends on how you have your BIOS Setting set which would be listed in the Boot Mode as Either Legacy(BIOS) or UEFI. 

If you already formatted the drive, make it even easier on yourself... How? Set the BIOS Settings however you wan to boot (either BIOS or UEFI)... Then "Delete" your partition. You don't have anything on it anyways. Make sure the partition table is GPT.. **Then** start your install.

The logic in the installer will see what ever boot mode your system is set to and create it's own plan to install it. It will not give your warnings or messages that conflicts with what you want to do.

One note to that... Resetting your system's boot mode, may effect how and if your Install media/LiveCD image boots or not, depending how you created it. Some are as UEFI, some as MBR, and some are made to be able to boot as either. But what method it is booted "as" is how it's going to want to install. The installer wants to succeed.

---

### Post by slaytanicprion on 2021-06-27
I gotcha, but I haven't messed with this, I think the system boots the old school way, because the systems on it didn't ask me about EFI. Linux Mint 17.3 I used until it couldn't be updated anymore, and all it wanted at the install screen in "Something else", was for me to select an ext4 partition and and to create a swap partition. Now I read and know that 20.04 doesn't need a swap partition, but this insists on having me create an EFI partition, I could ignore it, but I didn't. So, you're saying I can ignore the 2 warnings about EFI/unable to boot/failing to install and continue installing? Only thing I would need is make the drive GPT...I forgot how I did that to the internal drive on an external dock (which is not the recepient of the install obviously), gparted does it right? Because the install process doesn't allow one to do this. 

Also, what does an orange partition disk rectangular bar mean at install? The drive I want to install it on is seen like this. It sees the old Mint 17.3 install and shows it as green, and the other drives/partition of various colours, but they don't seem to have anything meaningful behind the colour code, one other internal drive with 3 partitions on it, shows a partition in orange, and the drive where I want to install has only one drive-wide ext4 partition and its shown as orange. I'll look how to turn that partition to GPT mode myself. But as I read you...the Ubuntu Mate installer just assumes things are working in EFI mode and that I have to either format the drive to be an EFI partition, and if I ignore that, I'm told a 35MB EFI partition should be made, but I think I can ignore that too. Maybe turning it to GPT will get rid of those messages.

So I know what to do in this live session right now with the drive. I'll see what happens when it inevitably crashes or I get enough courage/get fed up enough to press the reset button and try again and select Install from the USB drive grub menu. I think the usb drive might be booting using EFI, but the old way past its time Mint 17.3 on an internal drive, just showed up in grub and that was it. It seems like the USB stick with 20.04 WANTS EFI...I just woke up because I was hungry and refreshed this and saw your response, but I seem to recall after ignoring the original "format this drive to EFI" warning, the installer wouldn't continue unless I created a 35MB EFI partition, but that might be my brains just wanting to go back to sleep right now ;) I'll turn the drive to GPT tomorrow and then try again and see what happens. I don't think I have to fiddle with anything in the BIOS, other than once Ubuntu MATE is installed, I'll have to switch the boot order for the drives, because right now the first one after the BD-R/DVD-RW/CD, optical for short, is the one with LM 17.3, which I will clean out with OS-Uninstaller once this is all done with.

---

### Post by MAFoElffen on 2021-06-27
So let's see... You say it has Mint 17.1 on it somewhere? And a blank Partition? Is Mint still working?

If you're in Mint (or any Linux LiveCD image), if you open a Terminal session, paste and enter this command in:
```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS]
```

That will tell you what boot mode the system booted as...

---

### Post by slaytanicprion on 2021-06-27
I'm on a live session of Ubuntu MATE 20.04. I'll get the disk list for  you, which isn't "complete" because one external is turned off.  

```
sudo lshw -C disk
  *-disk                    
       description: SCSI Disk
       product: EZAZ-00GGJB0
       vendor: WDC WD20
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sdf
       version: 0106
       serial: 00000000000000000000
       size: 1863GiB (2TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=6 guid=b53648e4-c450-4e79-b448-f7fe152f8f9f logicalsectorsize=512 sectorsize=512
  *-disk
       description: SCSI Disk
       product: DataTraveler 3.0
       vendor: Kingston
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sde
       version: PMAP
       serial: EE03D85155E9
       size: 115GiB (124GB)
       capabilities: removable
       configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sde
          size: 115GiB (124GB)
          capabilities: partitioned partitioned:dos
          configuration: signature=f844846e
  *-disk
       description: SCSI Disk
       product: Expansion
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdd
       version: 0708
       serial: NA8K6MSK
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512 signature=628822a0
  *-cdrom
       description: DVD-RAM writer
       product: BD-RW   BDR-209M
       vendor: PIONEER
       physical id: 0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.50
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: ATA Disk
       product: WDC WD2000JD-22H
       vendor: Western Digital
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 2D08
       serial: WD-WCAL81786689
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=00095704
  *-disk:1
       description: ATA Disk
       product: ST1000DM003-1CH1
       physical id: 2
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: CC47
       serial: W1D45DY8
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=d88eb14d
  *-disk:2
       description: ATA Disk
       product: WDC WD10EFRX-68J
       vendor: Western Digital
       physical id: 3
       bus info: scsi@5:0.0.0
       logical name: /dev/sdc
       version: 1A01
       serial: WD-WCC1U0505191
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=000ee848

```

Mint 17.3 is alone on the never dying (that I should replace anyway  since my usb stick with ubuntu mate 20.04 has almost as much space)  200gb WD. I want to install on the ST1000DM003-1CH1 Seagate Internal.  I'll turn it to gpt with gparted as you said I should. Hope that helps.  Win7 MBR is left on the 1TB WD (internal) on its first partition, it  doesn't really matter, it shows in grub menus but lead to a failed boot,  it wasn't an issue when I installed 17.3 over 17.1. I'm going back to  Ubuntu (but keeping MATE) because Mint is always lagging on kernel  updates for the most part. I can't do the command you want as I  obviously don't bother booting in a severely dated OS, plus I forgot the  password to the 2 accounts in there, it's been this long. I was using  Win7 after that until it died, don't want to use win10 at all on this  desktop. So live sessions of 18.04 and now 20.04 is all I've been doing  since a while, now that I have the disk space to move data around and am  able to clear an entire drive, I had these issues. Sorry I can't  produce the command results you'd want to see.
```

*-disk                   
       description: SCSI Disk
       product: EZAZ-00GGJB0
       vendor: WDC WD20
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sdf
       version: 0106
       serial: 00000000000000000000
       size: 1863GiB (2TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=6 guid=b53648e4-c450-4e79-b448-f7fe152f8f9f logicalsectorsize=512 sectorsize=512
  *-disk
       description: SCSI Disk
       product: DataTraveler 3.0
       vendor: Kingston
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sde
       version: PMAP
       serial: EE03D85155E9
       size: 115GiB (124GB)
       capabilities: removable
       configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sde
          size: 115GiB (124GB)
          capabilities: partitioned partitioned:dos
          configuration: signature=f844846e
  *-disk
       description: SCSI Disk
       product: Expansion
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdd
       version: 0708
       serial: NA8K6MSK
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512 signature=628822a0
  *-cdrom
       description: DVD-RAM writer
       product: BD-RW   BDR-209M
       vendor: PIONEER
       physical id: 0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.50
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk:0
       description: ATA Disk
       product: WDC WD2000JD-22H
       vendor: Western Digital
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: 2D08
       serial: WD-WCAL81786689
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=00095704
  *-disk:1
       description: ATA Disk
       product: ST1000DM003-1CH1
       physical id: 2
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: CC47
       serial: W1D45DY8
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=d88eb14d
  *-disk:2
       description: ATA Disk
       product: WDC WD10EFRX-68J
       vendor: Western Digital
       physical id: 3
       bus info: scsi@5:0.0.0
       logical name: /dev/sdc
       version: 1A01
       serial: WD-WCC1U0505191
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=000ee848

```

Mint 17.3 is alone on the never dying (that I should replace anyway since my usb stick with ubuntu mate 20.04 has almost as much space) 200gb WD. I want to install on the ST1000DM003-1CH1 Seagate Internal. I'll turn it to gpt with gparted as you said I should. Hope that helps. Win7 MBR is left on the 1TB WD (internal) on its first partition, it doesn't really matter, it shows in grub menus but lead to a failed boot, it wasn't an issue when I installed 17.3 over 17.1. I'm going back to Ubuntu (but keeping MATE) because Mint is always lagging on kernel updates for the most part.

---

### Post by yancek on 2021-06-27
> tells me I  should create an EFI partition even if I decide to go ahead 

The Ubuntu iso is capable of booting in EFI mode or Legacy mode and you should be able to select which option you want from your BIOS firmware boot options.  You are seeing this because you are booting the Ubuntu flash drive in EFI mode.

The color codes (orange) vary with the type of filesysem and this would be an ext filesystem.

Changing a drive from msdos to gpt will delete all data on the drive and you will be warned about that if you use GParted.

UEFI is much better than the older Legacy system but you need to learn it to know that.  

If you keep windows 7 and install Ubuntu, you need to install it in Legacy mode or it won't boot windows from Grub.  windows of course, won't boot Ubuntu unless you go through a convoluted process of modifying its bootloader (bcd).

If you want to install Ubuntu to the Seagate drive, it would be simpler if you disconnected other drives or disabled them in the BIOS (if possible).  If that's problematic, be carefull during the install so you get the correct drive.  Allso if the drive type if GPT and you want to install Ubuntu in Legacy mode, you will need an unformatted bios-grub partition.  Lots of posts here at the forums and online about how to do this.

---

### Post by slaytanicprion on 2021-06-27
Windows is non-existent and am not using it, an old win7 MBR is left, everything windows has been deleted which I already said previously.

The usb key grub menu that I use for this live session...the menu goes away pretty fast if I don't press the down arrows, should have made 30 seconds with unetbootin when I made it but oh well...I don't see an option to Install Ubuntu in another way, but it might just be that there is what I want there (there's other options below Try Ubuntu/ Try Ubuntu (safe graphics mode)/Install Ubuntu but I can't say what they are, I know the last one at the bottom has firmware in it. If one can produce the menu I'm seeing in a picture and tell me how to install in a non-EFI way, I'd be glad. It's Ubuntu MATE 20.04 LTS if that matters/gives a different usb key menu than plain Ubuntu or other subflavours. Thanks for finding the way forward! If I can just boot the usb key in legacy mode, that will make things much simpler to me.


> **MAFoElffen said:**
> So let's see... You say it has Mint 17.1 on it somewhere? And a blank Partition? Is Mint still working?

If you're in Mint (or any Linux LiveCD image), if you open a Terminal session, paste and enter this command in:
```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS]
```

That will tell you what boot mode the system booted as...

I can't get into that old OS, forgot the password. I only left grub because I used win7 until it was useless by feb 2020.

---

### Post by Impavidus on 2021-06-27
> **slaytanicprion said:**
> 
Also, what does an orange partition disk rectangular bar mean at install? The drive I want to install it on is seen like this. It sees the old Mint 17.3 install and shows it as green, and the other drives/partition of various colours, but they don't seem to have anything meaningful behind the colour code, one other internal drive with 3 partitions on it, shows a partition in orange, and the drive where I want to install has only one drive-wide ext4 partition and its shown as orange.In gparted the colours indicate the partition type, like ext4, ntfs, fat32 or swap. In the installer (if I remember correctly; I don't install Ubuntu that often), the colours are only chosen to make sure adjacent partitions have different colour.
> 
I'll look how to turn that partition to GPT mode myself.
That doesn't make a lot of sense. Partition tables are in MBR mode or GPT mode, partitions are not. Actually, I can't make much sense of you post anyway, so you may be confused.

Computers boot in BIOS mode or UEFI mode. UEFI mode is modern and has been the standard since 2012, when Windows switched to it. Just use UEFI mode unless you have some specific reason not to do so. Accepted reasons are dual booting with another OS already installed in BIOS mode or an UEFI not conforming to standards (some computers build before 2015 or thereabouts) and refusing to boot Linux. Windows 7 and before usually use BIOS mode, Windows 8 and up usually use UEFI mode.

Partition tables (you need one on every drive) can be MBR mode or GTP mode. On Windows MBR must be paired with BIOS and GPT with UEFI for bootable drives; Linux doesn't care. Still, it's recommended to use GPT if you use UEFI. GPT is also required on drives larger than 2TiB. The partition table lists the partitions on the drive. Each partition has a filesystem, like ext4 or fat32. Normally we install Ubuntu on an ext4 partition.

On an UEFI system you need an EFI partition on every bootable drive. It has a FAT32 filesystem. On a bootable GPT partitioned drive on a BIOS system you need a bios_grub partition. That's probably not what you want.

Naturally, whenever you change from MBR to GPT or back, all data from the drive will be wiped. And, although Windows always confuses the terms, a drive and a partition are completely different things.

---

### Post by MAFoElffen on 2021-06-27
do this in a terminal so I can see the partitions...
```
sudo fdisk -l
```
I'm assuming, from the way you said, that the old OS'es do not have a sentimental attachment. But I also thing that you "might" want to keep soem of the data? Or not.

What is your plan?

What do you want to end with?

Is the external USB drive part of that plan?

After telling me that... We'll go from your plan and try to get you there.... Because , wht... This is post #9 and I don't see that you've gotten any wheres yet... LOL

---

### Post by slaytanicprion on 2021-06-28
>I'm assuming, from the way you said, that the old OS'es do not have a  sentimental attachment. But I also thing that you "might" want to keep  soem of the data? Or not.

Nah, Mint 17.3 can go away, I only kept  it around because it made easy to select win7, out of laziness. I don't  care if the drive it's on (the old 200gb 3gb/s SATA that will not die)  dies, I backed up all data I needed that was on it eons ago. When 17.3's  newer kernels wouldn't work with my AMD proprietary video driver. It's  severely out of date and I even forgot my password, like win7, none are  needed, I wouldn't be using live sessions on this desktop since almost 2  years if that wasn't the case heh.

> What is your plan?

I want Ubuntu Mate installed on the 1TB  Seagate that's in there. It seems it would be the easiest if I disabled  all other drives in the bios at boot, something I hadn't thought of.  Also maybe change how the usb flash drive boots, because it looks like  from what I'm told that it is booting in EFI mode, hence why it wants to  install Ubuntu Mate that way too.

> What do you want to end with?

Ubuntu Mate 20.04 as the only OS on the 1TB internal Seagate drive.

>Is the external USB drive part of that plan?

Which  one? The 2TB seagate that's a regular external drive is for data only  and so is the 2TB WD that's on a hot swap dock that's a regular 3.5"  HDD, that thing is really useful, when I get more drives, that dock  which looks like an old cartridge based console with the HDD sticking  out, that can also take in 2.5" drives is gonna be very useful, but it's  only for data. I might install it as eSATA-III if I want to clear up  some usb 3.0 slots, apparently the speeds are comparable and I have the  adapter. They're just data drives, I wouldn't put an OS on an external  drive, even though one can these days, I don't think they should, even  if the dock makes systems think they are internal drives.

I don't  know why so many are confused or asking me irrelevant questions/giving  me irrelevant things to do. (it's not you and it only happened one time,  that's why I try to flood my OP's with as much details as possible,  which can lead to complications.

What I understand now is that  the usb key flash drive does this, it boots in EFI, thus wants to  install in EFI. I don't know how to make it so that it boots using  legacy mode, I mean, I know my way around this BIOS, I have to tell it  to use different numbers than what it defaults for, for my Corsair  Vengeance 4x4gb sticks, so that they run at the advertised speed  (1866mhz), so I should be okay with finding out how to do this. Another  solution might be to boot up and disable all other drives other than the  drive I aim for installation, but if the USB installation/live session  flash drive boots in EFI I don't think that makes any difference. I  don't have drives over 2TB right now, got 2 of em and they are external,  so EFI can wait for when I get something over 2TB, which will be a  while, hard drives have stopped going down in price according to time  like they used to, can't believe a 3TB/4TB mechanical regular drive will  cost me over 100 bucks no matter what unless I'm lucky and happen to  look at newegg or amazon or call local shops who would have something  reasonable, but it looks like the market is frozen in the state it is  now since a long while. So that doesn't really matter.

Looks to  me like I have to force the usb key to boot in regular mode, so that  installing Ubuntu will be as easy as it was, pick an ext4 partition (and  now I don't even need to create a swap partition, one less PITA) and go  ahead. Which is what I did with this exact mobo/cpu in the past when I  installed Mint. But I gave up on Mint, except for the MATE interface,  creature of habit, closest thing to gnome that was around then when  plain Ubuntu really didn't like (aka, booted up to the main screen and  froze) with 12.10 way back when I forced it not to use Unity and to use  gnome.

The only drive that has multiple partitions is the internal 1TB WD you see in there, this one
 WDC WD10EFRX-68J

first partition is the only ntfs partition I have left, where win7 WAS, there's still a win7 MBR, but that doesn't matter if I just install 
Ubuntu on another drive I cleared for it, the 1TB internal seagate, then it has 2 ext4 partitions just for data. There's no other multiple partition drives.

So I need to know how to boot the usb installation drive in "legacy" mode, that's about it. My motherboard's handbook is somewhere safe, I didn't throw it in the
garbage like so many uncaring people out there, I'll look into this. But if any of you want to look up the pdf handbook for it online and give me the
solution, please go ahead :) I don't mind that the system will not be using EFI still, until I have a drive with an OS on it that's over 2TB, it's not
something that matters to me, it will then because I won't have a choice, plus I'll likely have a newer motherboard by then that was manufactured not
within that window of time where they were hybridized to slowly move customers to full EFI all the time, this one came out in 2015, it's a bit of the
"weak" link in this desktop, but I was paying big bucks (bigger than Americans, in Canada we get ripped off ever since our currencies aren't equal/close-to-equal
for like 15 years which ended abruptly in early 2016). The amdfx-8350 black edition was 330 with taxes (279 without), I wanted to cover my cpu needs for
at least 7-8 years, which it is doing thankfully, and I got a huge cooling tower making overclocking the octocore to 4.2ghz happen like nothing.
Funny how it gets to me 4 years after I pieced together the whole thing.

---

### Post by tea for one on 2021-06-28
> **slaytanicprion said:**
> So I need to know how to boot the usb installation drive in "legacy" mode, that's about it.

Have a quick look at this picture

UEFI: KingstonDataTraveler 3.0PMAP - This boots in [COLOR="#0000FF"]UEFI [/COLOR]mode
KingstonDataTraveler 3.0PMAP - This boots in [COLOR="#0000FF"]Legacy[/COLOR] mode

The clue is UEFI followed by a colon.

To double check after entering a live session, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"

```

Just to add more confusion, I think that you should install in UEFI mode with GPT, but it is your choice.

---

### Post by oldfred on 2021-06-28
When Microsoft released Windows 8 in 2012, it required Windows to be installed in UEFI boot mode to gpt partitioned drives.
Some early UEFI have had issues, but after a year or two most issues have been worked around.

I started converting to gpt partitioning with my install in 2010, I still had XP on MBR drive back then. System was BIOS only.

If drive may be used in newer UEFI system later, I suggest converting to gpt which will erase it and add both an ESP and bios_grub partition. 
You only need ESP in future for UEFI and it should be 300 to 500MB unless a tiny drive and then 50 to 100 will work, but offer less future flexibility.
You only need bios_grub 1MB unformatted with bios_grub flag for BIOS boot on gpt drives.

How you boot install media UEFI or BIOS/Legacy/CSM is then how it installs.
Some tools to create installer may make it UEFI only or BIOS only. 
If created for either boot mode, you should have two options in UEFI boot menu for flash drive. One clearly UEFI like UEFI:PMAP and other just PMAP.
The PMAP seems to be used by some, others use name or label of flash drive.

---

### Post by slaytanicprion on 2021-06-28
> **tea for one said:**
> Have a quick look at this picture

UEFI: KingstonDataTraveler 3.0PMAP - This boots in UEFI mode
KingstonDataTraveler 3.0PMAP - This boots in Legacy mode

The clue is UEFI followed by a colon.

To double check after entering a live session, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"

```

Just to add more confusion, I think that you should install in UEFI mode with GPT, but it is your choice.


Thanks, you've been very resourceful so far ! I will do that when I get back on that desktop. But just so you know, I don't know it by heart, but this is the menu the closest to what I get when I boot from my flash drive (I searched on google image for the closest thing, I'm not sure exactly about what's below Install Ubuntu Mate (safe graphics), I know OEM Install (for manufacturers) is there, but I never used that before, there's the firmware thing and maybe something else, I'm sure there's no "Boot from Next Target" or "System Setup", but I'm not 100% certain, I'll have to move around the up and down arrow...when I made the installation usb drive with unetbootin, I didn't use the option to change the time it allows you to keep it idle, I usually do it up to 30 seconds, but it's 5 seconds by default, so that's why I'm not sure of whatever's below OEM Installation other than something about Firmware. I understand I should be given the choice right there, is that what you're saying? I couldn't find something closer than this really huge picture (sorry about that). When I get home I won't be rebooting until the live session just crashes sometime like usual or a sudden power failure, I've been living like this since Mint 17.3 became irrelevant in early 2020 shortly after win7 did the same, I'm underusing my most powerful machine and it's getting annoying to reinstall everything I need for safe internet browsing and other stuff, I can tell you heh. I'll get the result for that command tonight (EDST).

[IMG]https://ptpimg.me/0zoau2.jpg[/IMG]

---

### Post by tea for one on 2021-06-28
> **slaytanicprion said:**
>  I understand I should be given the choice right there, is that what you're saying? I couldn't find something closer than this really huge picture (sorry about that).

No, that is not what I am saying.
The huge picture is the Grub menu after you have selected whether to boot in UEFI or Legacy mode.

When you power up your PC, you invoke a dedicated key to access a one-time boot menu.
(e.g. Intel PC it is F10, for HP it is F9 etc)

Once you have reached the boot menu as this new attachment, you will see boot options for various devices..
If you still wish to boot the installer in Legacy mode, then avoid any entry with [COLOR="#0000FF"]UEFI:device_name[/COLOR]

If I wanted to boot in Legacy mode, I would select [COLOR="#4B0082"]USB: General USB Flash Disk[/COLOR]

---

### Post by oldfred on 2021-06-28
Please attach screen shots. Easy to do with Forum's advanced editor & the # icon.
If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots. Post #4 , also no larger than1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

You posted the grub boot menu for UEFI boot, although I now understand Ubuntu uses grub for BIOS boot with the most recent version. Older versions used Syslinux for BIOS & grub for UEFI.

Vendors use different keys for UEFI boot menu key. 
Should be same key you use to select to boot USB flash drive.
Often f12, HP uses  - escape + F9 for boot menu, F10 for bios setup, other vendors vary.

---

### Post by MAFoElffen on 2021-06-29
Back from a very busy weekend (After a big conference)...

@tea for one - Your post  #11... That was exactly what I asked the OP in My post #4. LOL

I agree with oldfred  on GPT. It was meant for large disks and files systems. The two biggest advantages are the greater number of primary partitions you can have from the root of the drive... and there being two copies of the partition table. Both those are biggies.

On EFI or BIOS Boot... I have only a few systems still that are BIOS Boot. I have both. On most boots, I don't really notice... Until something is wrong. There is some advantages to UEFI that I like. You'ld be surprised how convenient things are within UEFI, when you need to use them. Especially in Server Boards. It's like navigating in a desktop of it's own. For instance being able to update firmware straight from within the BIOS.

I also have an external 2-bay USB 3 drive dock... I love mine. Handy for repairs, recovering data, backup's, etc.If you wanted to re-org your internal 1TB, you could pass the data to a drive in that to transfer back onto it later. (or not)

BIOS or UEFI is a decision for you to make. I don't see it major either way. And that decision is??? And I'm sure you want to get what that is going right?

---

### Post by tea for one on 2021-06-29
> **MAFoElffen said:**
> @tea for one - Your post  #11... That was exactly what I asked the OP in My post #4. LOL

I agree with oldfred  on GPT. It was meant for large disks and files systems. The two biggest advantages are the greater number of primary partitions you can have from the root of the drive... and there being two copies of the partition table. Both those are biggies.

@[COLOR="#0000FF"]MAFoElffen[/COLOR] Yes, I saw your request in Post 4 but, in among all the correspondence, it remained unanswered. I hope the OP will now supply the terminal output following both our comments.;)

Also, I agree with you about GPT - not limited to four primary partitions. If only, we could encourage the OP to re-consider UEFI mode as well...............?

---

### Post by slaytanicprion on 2021-06-29
> **tea for one said:**
> No, that is not what I am saying.
The huge picture is the Grub menu after you have selected whether to boot in UEFI or Legacy mode.

When you power up your PC, you invoke a dedicated key to access a one-time boot menu.
(e.g. Intel PC it is F10, for HP it is F9 etc)

Once you have reached the boot menu as this new attachment, you will see boot options for various devices..
If you still wish to boot the installer in Legacy mode, then avoid any entry with UEFI:device_name

If I wanted to boot in Legacy mode, I would select USB: General USB Flash Disk

Okay, yeah, Delete is what is used to get into the BIOS, but I think it's F8 with my Asus Motherboard to get into the boot menu after the first screen listing memory, drives, keyboards, mouses, hubs. It's an Asus Motherboard with an Asus BIOS/UEFI.

So when I reboot, I have to get into the boot menu (I think it's F8 for me, you guys can always check that out too, I showed my mobo's make in my first post I think and I'll be given the option on how i want to boot from the usb flash drive, OR, I have to hit delete to get into settings (bios, whatever) and change it there like with anything else?

As for how it boots into a live session 

```

[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
UEFI mode

```

mystery solved, that's why things aren't like they always were for me heh, where picking an ext4 partition and clicking continue was all that was needed (well that and making a swap partition but that's not needed anymore with 20.04 I understand). 

Thanks a lot. Now things are making a lot more sense. EFI might have been around since 2002, but I'm the type of guy who builds a computer so that it lasts a long time, the mobo I had before that was an Asus a8n-sli deluxe and it lived 9 years, did the same thing back then, paid big bucks for a double core AMD Athlon FX @ 4400mhz so that I wouldn't have to buy a new one for a long time...Asus mobos have never given me issues before, coupled with the OS's I'm installing. The Mint 17.1/17.3 usb drive installs on this current desktop and there was no such surprise issues. But I guess it's time for me to understand the difference between legacy and efi/uefi. I'm getting it. Although I don't want the Installation to want to go the EFI way right now, as I said, there's no reason for me to go there yet, maybe when I have drives with more than 2TB..

---

### Post by tea for one on 2021-06-29
> **slaytanicprion said:**
> As for how it boots into a live session 
```

[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
[COLOR="#0000FF"]UEFI mode[/COLOR]
```

You've booted into UEFI mode (which is modern and has useful features)

If you want to boot into Legacy mode:-

You have to make sure that Legacy is enabled in your UEFI/BIOS firmware
You also have to select the [COLOR="#0000FF"]Legacy_USB[/COLOR] in the boot menu (i.e.without [COLOR="#000080"]UEFI:[/COLOR])

---

### Post by slaytanicprion on 2021-06-29
Well..I haven't *really* booted in UEFI mode, I was oblivious to  that, after the start screen with the specs, the first device in the  boot order in the system settings boot...I'm not given a choice, but I  know that choice exists, to decide where to boot from on the fly. I  think it's F8. I'll be able to tell next time I reboot....obviously will  happen once I'm very comfortable with my live session...but I realize  one has to have updated kernels sometimes. Pretty sure it's F8 anyway, I  know it was that with my previous long-term main desktop, with the Asus  a8n-sli deluxe. Thank you all very much, now things come back to mind, I  do remember being asked about UEFI even on that motherboard while using  on-the-fly boot device choosing before it gets to the first boot  device, since I had no idea what it was, I didn't choose that. We'll see  soon!

---

### Post by MAFoElffen on 2021-06-29
Thank you for answering Tea For one and I on which boot mode you were booting from. (posts #4 & 11...
> **slaytanicprion said:**
> As for how it boots into a live session

```

[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
UEFI mode

```

mystery solved, that's why things aren't like they always were for me heh, where picking an ext4 partition and clicking continue was all that was needed (well that and making a swap partition but that's not needed anymore with 20.04 I understand).

Thanks a lot....
So you have been booting in EFI mode and not known that... That answers that question.

AS Tea for One said, he reasked that because you didn't anser previously... Just as in post #9, I had asked you for the layout of the 1TB internal drive. The drive you boot, from and what to install to...
> **MAFoElffen said:**
> do this in a terminal so I can see the partitions...
```
sudo fdisk -l
```

That would confirm what partitions are on that, and point to have in was laid out (a hint on the boot mode) when it was originally installed.

The reason I asked that and we still need to know... Is that it might have been EFI or not already. You are in UEFI boot mode now... And never noticed that. Most people do not know, nor care. But, the mode it boot's from affects the way the installer is going to want to install. With me so far?

So if that old disk was installed as BIOS Boot, it's going to have to create an EFI partition in the root of the drive. That could be "entetaining" if you wanted to keep anything on that... But then again, you have told me multiple times, that there is not.

I think I remember you saying back in post #7, that you forgot the old password into one of the old OS's... There is many ways to get into those. Physical Security. I could have explained how to get into those... But you said they were going away, so..

We need to know how it is laid out currently, to help you with, whatever boot mode you decide to boot from, to guide you through that.

Otherwise, becasue you told me that you didn't care about anything on that disk, just delete all the partitions and the partition table on that disk (start fresh), and just install fresh. Like I told you in Post #2... From there, you would just reset your BIOS Setting to boot into which boot mode you desire, BIOS Boot or UEFI boot... The boot your Installation Media. It would then Install it that way.

AS for Your Install media.. Yes. It has to be made to boot from that mode, but as oldfred and Tea for One have said, many USB creation utitilies these days, create USB install media to be able to boot either way. But some do not, or some you have to say, when you create it...

*** Still, patiently waiting on the partition layout of that disk...

---

### Post by slaytanicprion on 2021-06-30
```
Disk /dev/sdc: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: WDC WD10EFRX-68J
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x000ee848

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sdc1            2048  411631615  411629568 196.3G  7 HPFS/NTFS/exFAT
/dev/sdc2       411631616  846579711  434948096 207.4G 83 Linux
/dev/sdc3       846579712 1953521663 1106941952 527.9G  7 HPFS/NTFS/exFAT


Disk /dev/sda: 186.32 GiB, 200049647616 bytes, 390721968 sectors
Disk model: WDC WD2000JD-22H
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00095704

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 360245247 360243200 171.8G 83 Linux
/dev/sda2       360247294 390721535  30474242  14.5G  5 Extended
/dev/sda5       360247296 390721535  30474240  14.5G 82 Linux swap / Solaris


Disk /dev/sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1CH1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xd88eb14d

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953523711 1953521664 931.5G 83 Linux


Disk /dev/sdd: 1.84 TiB, 2000398933504 bytes, 3907029167 sectors
Disk model: Expansion       
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x628822a0

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1          64 3907024128 3907024065  1.8T  7 HPFS/NTFS/exFAT


Disk /dev/sde: 115.51 GiB, 124017180672 bytes, 242221056 sectors
Disk model: DataTraveler 3.0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf844846e

Device     Boot Start       End   Sectors   Size Id Type
/dev/sde1  *     2048 242221055 242219008 115.5G  7 HPFS/NTFS/exFAT


Disk /dev/sdf: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: EZAZ-00GGJB0    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B53648E4-C450-4E79-B448-F7FE152F8F9F

Device     Start        End    Sectors  Size Type
/dev/sdf1   2048 3907028991 3907026944  1.8T Microsoft basic data


Disk /dev/sdg: 931.53 GiB, 1000204885504 bytes, 1953525167 sectors
Disk model: Expansion       
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x000b3352

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdg1        2048 1953521663 1953519616 931.5G  7 HPFS/NTFS/exFAT


```

grub on the internal drives is installed where mint 17.3 is, but once I have 20.04 mate installed, it won't, it'll be on the 1TB internal seagate, which suddenly changed letters again back to what it always was (sdb), after a power failure, live sessions started seeing it as sdd, this is kind of strange, but it shows up at boot in the disk list. I won't be turning it to gpt after learning more deeply about what it meant. I kept it even as I stopped using it because I could transition to win7 for its final months, plus I had found a way to get the "business only" updates up to april 2020, but that drive even if it has win7 MBR, DOESN'T have win7, all folders related to win7 were trashed. 

I described the drives with multiple partitions using words, but I guess you wanted that, although it's a bit overkill. The seagate I want to install on, I had already moved all data from and formatted to ext4 for it to be ready to get 20.04 mate, there's no other partition on that drive. I don't care about grub on the tiny 200gb drive that won't die, because I will remove it when doing installation and have grub only be where I'm installing 20.04 mate, as it should be. I saw you guys asking about it, I thought my word was good enough :)

---

### Post by slaytanicprion on 2021-07-01
Well, all's well that ends well. One of you should have told me to go to my system settings at POST when disks and memory and cpu etc. are listed...all I had to do was boot directly from there from the non UEFI prefixed Kingston DataTraveler, showed up the old school blue and purple ubuntu install menu and that brought a smile to my face. Had to reboot to point it to the internal seagate as the first device to check after the BD-R. But thanks a lot to y'all, very helpful at making me understand what could have caused me headaches on other people's computers at times.

What's strange is that I'm pretty sure back when I installed Mint 17.1 (I upgraded within the OS, not from an outside flash drive or dvd), I think it gave me an EFI grub menu like I've shown you, but didn't ask me strange (to me) things about needing an EFI partition, all it wanted was a swap partition. But finally I have a fully update OS on a real hard drive, something I've been postponing to do since mid 2020, because usb live sessions on that particular flash drive (the 128gb helped I guess, before that the largest one I used was 32gb) could last forever. But we've had ridiculous 30 seconds long power failures a bunch around here for no reason, on fully sunny days or days like today where it's overcast, but its not windy nor raining at all, so I've been aggravated with all the reinstallations.

Thank you everyone who helped out, and to those who happen to be Canadian, happy Canada Day to you all, hopefully the temperature is good enough (or not too insanely hot like in Vancouver, where you guys always get mild winters and mild summers...hope you got your A/C's then). Here it's not needed today, currently just 18c here, 20c max forecast, no sun, no free music shows, but we'll have fireworks afterall since my province is doing very well regarding the bug.

---

### Post by tea for one on 2021-07-02
> **slaytanicprion said:**
> One of you should have told me to go to my system settings at POST

Ah, man......... We've only been on the case for 4/5 days - Give us a break ;)

---

### Post by oldfred on 2021-07-02
As in post # 15.

Or if you review the link in my signature. It along with many other useful suggestions are there.

---

### Post by MAFoElffen on 2021-07-04
> **tea for one said:**
> [QUOTE=slaytanicprion;14046644]One of you should have told me to go to my system settings at POST Ah, man......... We've only been on the case for 4/5 days - Give us a break :wink:[/QUOTE]
 They all did. (Almost everyone involved.) By many people, in many different ways, many times... he just didn't read and/or understand(?) ](*,)

He reached his goal. That is what is important!

---

### Post by tea for one on 2021-07-04
> **MAFoElffen said:**
> They all did. (Almost everyone involved.) By many people, in many different ways, many times... he just didn't read and/or understand(?) ](*,)

He reached his goal. That is what is important!

Yes, indeed, my feeble attempt at irony failed to hit the target.

I was wondering if it would be worth mentioning [Solved](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads), but I don't think that I'll bother ;).

---

