---
title: "[SOLVED] Will the new Windows 8 PCs work with only Ubuntu installed?"
date: 2013-04-02
forum: Installation &amp; Upgrades
---

### Post by JimS on 2013-04-02
...
RE:  New laptop with Windows 8 installed.

Will these new Windows 8 PCs, laptops in particular --- work with only Ubuntu installed?
With no Windows installed, only Ubuntu.

If not, why?

Have you seen it done successfully (or unsuccessfully)?

Or is dual-boot the only way to get Ubuntu onto a 2013 laptop?

I don't want Windoz on my new (under $400usd) laptop if I can help it.

JimS
...

---

### Post by oldfred on 2013-04-02
What brand? Some seem more forgiving than others. Some have modified UEFI code that with secure boot on they will only boot the Windows efi file. That is not per the UEFI standard.

Only a couple of posts have been total erasing Windows drive. One or two used UEFI, not sure if secure boot worked or not. Others revert to CSM/BIOS/Legacy mode, but that will not boot Windows as it is a UEFI with gpt partitioning only. And CSM does not have secure boot. But then we never had secure boot on any system until Windows required it with Windows 8 on new computers.

 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security
      
 New Linux UEFI boot loader - hash based no key
[http://mjg59.dreamwidth.org/23113.html](http://mjg59.dreamwidth.org/23113.html)

     One user posted he always buys a better system, but with only a hard drive. Then he total removes hard drive and puts it on shelf in case he ever wants to sell system and installs a new SSD and installs Ubuntu.

Ubuntu will install in either UEFI mode or BIOS mode to gpt partitioned drives. But it depends on how you boot install media. If you boot in UEFI mode it installs in UEFI mode.

---

### Post by cybergalvez on 2013-04-03
I have ubuntu unstalled on my new lenovo, it originally came with 8 preinstalled. The only bummer is that you can't take what was installed and put it on VB

---

### Post by JimS on 2013-04-04
...
Oldfred, thanks for your reply.
I took back the ASUS x501a laptop because it had no optical drive
and I think in the future I may want one.  I do have a new portable usb
optical drive, but with UEFI win8, I wasn't able to boot from it.  I did
get the ASUS to boot from usb-stick.  But I didn't install Ubuntu, just
tested the live session.

Now I have a HP2000.  I've successfully booted my Ubuntu-secure-remix
(Ubuntu 12.10) usb-stick and tested the live session.  I suppose soon
I'll have to get up the courage to install it.  But I couldn't get the optical
disk version of Ubuntu-secure-remix to boot from the optical drive.
Also having a problem getting directly to the bios so I can change
boot order.  Work-in-progress!!

Thanks also for the urls.  I read both plus a couple others of similar
topic.  So it seems for the commoner, like myself, we are going to have
to wait until May/June.  And I'm still not sure if I will be able to run
Linux only on my laptop.  I still don't understand the hardware and
firmware involvement.  So it is still not clear to me if it is possible
to run Linux on a 2013 win8 laptop with win8 removed just as we
could do with Vista and XP laptops.  But it seems we can't as yet.

I'm very busy now with preparing to move to California USA.  Since
I'm 74 years old, it is a tiring experience and I don't get much time
to concentrate on this issue.  So I'll probably just be satisfied with
dual boot win8 and Ubuntu-secure-remix for now.

Thanks again.
...

---

### Post by oldfred on 2013-04-04
Some users with HP, hopefully they use similar UEFI implementations.

 HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6 
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by JimS on 2013-04-05
...
Oldfred, thanks again for your reply.
I had heard of a HP p6 YouTube video,
where they wanted to alter the Win8 partitioning
because of too many primary partitions,
but I couldn't find it.

I installed Ubuntu secure remix, but forgot to do
the last part, running the boot repair tool.  
As a result grub doesn't work as yet.  But I'm
confident that tomorrow I'll get it working,
time premitting.

see this series:
Practical UEFI Secure Boot, a 3-part series by channelintel.
[http://www.youtube.com/watch?v=eAnlhkbMang](http://www.youtube.com/watch?v=eAnlhkbMang)
Part 1. Installing uefi, was over my head in places.
Part 2, installing Windoz 8, was not so difficult.
Part 3, installing Ubuntu, was great IMHO.
But this series didn't tell me if Ubuntu can be the sole OS.
I think it can be done, but not with newer Intel CPUs.
My new HP laptop has an AMD E-300 processor.

If you are builting a PC, it might be a good idea
to check what processors are UEFI.

Good night

JimS the Septuagenarian
...

---

### Post by oldfred on 2013-04-05
With UEFI you have gpt partitioning and there is 128 partitions essentially all primary. So partitioning is not an issue, but UEFI with secure boot is. And it really is the secure boot. Some work, Some only boot Windows with secure boot, some only boot both with secure boot off. It seems every user has to experiment.

But all UEFI have CSM or BIOS mode, so you can revert to BIOS. But if Windows was pre-installed it will only work with UEFI. If you have to have BIOS, then you have to also buy a full new install of Windows.

Of course with BIOS you are back to the 4 primary partition limit. Windows has to boot from primary partition, but Linux works just fine from logical partitions.

---

### Post by grahammechanical on 2013-04-05
May I ask a question? Speaking without practical experience of any of these issues, I wonder which holds most risk from installing Ubuntu on these machines?

1) Using the Install alongside option?

2) Use the Entire Disk (Erase Contents) option?

3) Do Something Else option?

Surely the Use the Entire Disk option must be the least risky of the three options. Especially, if we do not want to keep Windows. But as with many things Linux related someone has to be the first to experiment. I have heard of a serious problem with a certain Samsung product that would make the machine unusable due to improper implementation of the specification.

Is it possible to buy any machine meeting the Microsoft Windows 8 specification without Windows 8 pre-installed?

Regards.

---

### Post by oldfred on 2013-04-05
Several users have posted they totally erased Windows and system worked. Not sure if they converted to CSM/BIOS or not in all cases. A couple did convert to BIOS boot and with secure boot off and sytem set to use CSM or BIOS it worked like an old system. But they may vary by vendor.

Ubuntu will boot in BIOS mode from gpt partitioned drives. I gpt partitioning on my BIOS based systems as I have gpt on my SSD and even a flash drive. So either MBR(msdos) or gpt(GUID) will work with Ubuntu in either UEFI or BIOS mode booting. Ubuntu may work with secure boot without Windows on some systems, but some seem to have modified UEFI to only boot the Windows efi file. (Not per UEFI standard).

---

### Post by JimS on 2013-04-05
...
Just thought I'd check in for a moment.
Then it is back to fixing/painting our home.

I know about the 128 primary partitions w/ UEFI.
But at the time I was searching for the HP-P6 YouTube video, I didn't.

I've been told installing Ubuntu as the sole OS
depends on your processor/motherboard.
So Using the Whole Disk may be dangerous
on some of the new stuff, 
Intel processors especially.
I won't try it on my new HP2000 laptop.
I've been working side by side w/ windoz for years, so I can continue.

This evening I hope to get time to fix my grub.
Then I'll be back.

Thanks for the replys.
...

---

### Post by oldfred on 2013-04-05
I know one user posted that his standard procedure (not sure he did it with UEFI yet) is to buy a better laptop, but with only a hard drive. Then he buys a SSD, puts hard drive on shelf in case he later wants to sell system with Windows and installs Linux on SSD. :)

---

### Post by JimS on 2013-04-05
...
Ubuntu is now successfully installed on my new HP laptop
with help from Ubuntu, Community, Boot-Repair.
Funny thing - now my grub has over 10 entries.
Ubuntu is at the top, Windoz near the bottom, and a lot of EFI items in the middle.

Some new PCs may work with Windoz removed and some won't IMHO.
I get the bad feeling that more PCs will not work as time goes by.
So I'm not going to try to remove Windoz. 
I don't need it, but my laptop may.

I'm writing this message from my new HP using Ubuntu.
Thanks to all.
...

---

### Post by oldfred on 2013-04-05
You can backup & remove entries in grub's menu. All the entries in 25_custom were created by Boot-Repair and it saw a lot of HP .efi files. So it created an entry for all of them. Not sure if needed, but you may want a backup.
You can also turn off os-prober until it gets updated to create correct entries.

 # I add this line to grub configuration or turn off the execute bit on 30_os-prober
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub
Or one liner
 sudo echo GRUB_DISABLE_OS_PROBER=true >> /etc/default/grub 
sudo update-grub

      
 sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
gksudo gedit /etc/grub.d/25_custom
Then do:
sudo update-grub

---

### Post by JimS on 2013-07-17
Update
Added Sabayon, but didn't care for it.
I also added Lubuntu, but it didn't work fully.
Then I've added LinuxMint 15, both Cinnamon and xfce.
Xfce is my preferred choice currently.
Still have Ubuntu 12.10 which I use only for boot repair.
And Win8 is still on-board so I can do my genealogy.
Thanks for replys.

---

