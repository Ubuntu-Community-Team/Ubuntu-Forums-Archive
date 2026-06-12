---
title: "External drive boot issue UEFI"
date: 2021-05-27
forum: Installation &amp; Upgrades
---

### Post by arkeo on 2021-05-27
Hi everyone, I tried to search these fora but I couldn't seem to find an answer, so I apologize if this has already been dealt with.

I've got a Huawei Matebook D (Ryzen 5, 8/256), so since my internal disk (well, M2) is small I didn't want to dual boot from the same drive. I've got an older M2, slapped into an USB 3.1 gen 2 ext case or whatever it's called these days, and installed 21.04 on it. While installing I took particular care not to place GRUB on the internal (Windows) drive. My idea was to press F12 during startup, select the correct disk, and then just go.
Seems pretty straightforward, right? By the way, both Ubuntu and Windows boot in UEFI mode.
The "problem" arises when I skip the F12 key-press, or the external Ubuntu drive is disconnected: I get a GRUB prompt. Switch off, restart, go through the F12 routine, select the internal (and at this point *only*) disk drive and Windows boots just fine. Ubuntu itself presents no problems whatsoever.
As I said, I took real care not to install the GRUB bootloader on the main drive, so that if I wanted to boot Hippo (I need it to test for printers/scanners and various possible issues in office environments) I'd like to be able to boot a bit more easily. I mean, I *know* that if I wanted to boot Ubuntu I'd have to choose manually the startup disk, but why do I get a GRUB prompt even when the disk is disconnected and GRUB shouldn't be there at all on my internal disk *in the first place*?
:confused:
I'm really at a loss here, so any help would be appreciated.
It's an annoyance, nothing more, but I still can't understand *why* this happens...

PS: fast-boot in Windows is disabled.

Thanks a lot to everyone!

Cheers :)

---

### Post by arkeo on 2021-05-27
Erasing the ubuntu EFI directory from Windows makes booting Ubuntu impossible, either via BIOS (it doesn't show at all) or F12 "select boot disk" but at least GRUB has gone. It shouldn't be there at all. Sometimes I miss LILO. And I hate UEFI. :D

---

### Post by oldfred on 2021-05-27
Moved to your own thread, since other thread is for that users issues.
Unless contributing the OP's issues, you should start your own thread with your issue.

Issue is somewhat similar.
With UEFI you have to have  an ESP on the external drive.
And the Ubiquity installer makes it just about impossible to do that.
Very old bug report with multiple work arounds.

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079)

If you have a working install, create an ESP - efi system partition FAT32 100MB or larger. And then copy /EFI/ubuntu & /EFI/Boot from internal drive to external drive. External drives always boot from /EFI/Boot/bootx64.efi. But full install of grub needs /EFI/ubuntu files also.
You  also have to edit fstab with external drive's UUID, oras a major update or grub reinstall will just reinstall grub to ESP specified in fstab.
Or reinstall grub manually or with Boot-Repair choosing the externals drive's ESP.

If you need detail instructions based on your install:

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

See also link in my signature below.

---

### Post by ubfan1 on 2021-05-27
And do add yourself to the [https://bugs.launchpad.net/ubuntu/+s...y/+bug/1396379]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379")  's "Does this affect me?" list.  It'll never get fixed until the heat gets turned up.

---

### Post by arkeo on 2021-05-28
> **ubfan1 said:**
> And do add yourself to the [https://bugs.launchpad.net/ubuntu/+s...y/+bug/1396379]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379")  's "Does this affect me?" list.  It'll never get fixed until the heat gets turned up.

Done!

Sorry,it's 6.30am and I slept very little. So my brain is not fully functional yet. One quick question though: what if I lost three hours of my time on this Earth physically disconnecting the internal hard drive, then boot from USB stick and install Ubuntu on the external drive? Would that work? Would future upgrades to Ubuntu pollute the internal Win hd with GRUB?

I promise I'll dig deep into the details mentioned, right now it's just too early. Plus, /me hungry! :D

---

### Post by ubfan1 on 2021-05-28
Grub-install works just fine, it installs to where you tell it, and upgrades should be fine.  Just the Ubuntu installer suffers from TMC (Too Much Code) and thinks it is so smart it can ignore user input.

---

### Post by arkeo on 2021-05-28
> **oldfred said:**
> Moved to your own thread, since other thread is for that users issues.
Unless contributing the OP's issues, you should start your own thread with your issue.

Sorry, it just happened so many times that after searching a while and couldn't find anything 100% pertinent I'd reply to a thread that seemed to be about 90% so. It seemed more polite, and moderators made sure I understood that! ;)
Won't happen again!

> 
With UEFI you have to have  an ESP on the external drive.
And the Ubiquity installer makes it just about impossible to do that.
(...)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.

Yes, that's what I mentioned in my last post, but my main worry is that after a simple update/upgrade everything would return as it is now: both systems unbootable, Win with a simple workaround, Ubuntu "unreachable". Unless having an ESP on the external HD somehow prioritize it over the ESP on the internal (W10) HD. Maybe unmounting it before an update? Or skipping GRUB/Kernel upgrades altogether?

> Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

I'll try to take a look at it but it seems a bit out of my league--I wouldn't want to end up with both systems theoretically working, data still intact but everything basically out of reach... :eek:

> Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)


Hmmm, that'd mean (I think) fiddling with BIOS at every boot, toggling UEFI vs Legacy. Windows complains A LOT when installed in UEFI mode and then you switch to Legacy (have to re-authenticate with P-i-t-A 2FA MS Account for example)...

At this point--well, in a coupla months at least since installing Ubuntu is easy as a cuppa, while reinstalling Windows is a Nightmare from Whatever Street you live in--wouldn't it be easier to just disable UEFI in BIOS and then trying the same procedure in "Legacy mode"? No OS should bother about ESPs, right?

Well, at the time they said M$ wanted UEFI to make it harder for Linux users, especially dual booters--it seems like they have succeeded, and no amount of WSL can fix that, I need to test stuff natively. ](*,)

> Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/1056079#1056079)

I'll check it out, but I fear W10 won't be happy (well, it never is anyway)...

> If you have a working install, create an ESP - efi system partition FAT32 100MB or larger. And then copy /EFI/ubuntu & /EFI/Boot from internal drive to external drive. External drives always boot from /EFI/Boot/bootx64.efi. But full install of grub needs /EFI/ubuntu files also.
You  also have to edit fstab with external drive's UUID, or as a major update or grub reinstall will just reinstall grub to ESP specified in fstab.


I haven't had to deal with fstab since Slackware in 2004, it's been a bliss ever since... I'll leave it as my last resort. :(

Thanks for all the precious info! Cheers! :)

---

### Post by oldfred on 2021-05-28
You only have to change boot/esp flags once during install, then after install restore boot flag to internal drive's ESP.

Your /etc/fstab has the mount of the ESP where grub reinstall will go with a major update. That just needs to be the correct ESP.

Most do not want to disconnect a drive, so the other workarounds are available.

Major grub updates or Windows updates will normally reset that system to be default or first in UEFI boot order. So you may have to change boot order on occasion. 

Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2
see also 
man efibootmgr

---

### Post by ipv2 on 2021-05-30
> **arkeo said:**
> what if I lost three hours of my time on this Earth physically disconnecting the internal hard drive, then boot from USB stick and install Ubuntu on the external drive? Would that work? Would future upgrades to Ubuntu pollute the internal Win hd with GRUB?

i have a desktop with fossa on the internal sata hdd & this my primary rig for work & play & everything else.

on the same desktop i have a portable seagate connected via usb on which i keep testing various operating systems.

i do not want the fossa messed up even the slightest so what i do is disable sata controllers in the bios when i am trying out operating systems on the portable seagate.

formatting, installing, uninstalling no matter what i do on the portable seagate the fossa on my internal sata hdd remains untouched. 

when i need fossa i enable the sata controllers in the bios & boot in to it. this saves me the trouble of manually connecting / disconnecting drives.

hope this is useful for you.

---

### Post by sudodus on 2021-05-30
> **arkeo said:**
> 
What if I lost three hours of my time on this Earth physically disconnecting the internal hard drive, then boot from USB stick and install Ubuntu on the external drive? Would that work? Would future upgrades to Ubuntu pollute the internal Win hd with GRUB?


[SIZE=4]Disconnecting and reconnecting the internal drive[/SIZE]

I think the time lost for physically disconnecting and reconnecting the internal drive is a small fraction of those three hours, probably less than one hour. And you must do the other work anyway.

This is the most reliable way to make things work, when you want to install a complete Ubuntu system into an external system in UEFI mode. There are shortcuts, ways to turn off the automatic [re]direction of the EFI system partition into the internal drive, and they work in some computers, but maybe not in yours.

There is a very detailed description in [this link](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312).

But if you are happy with Ubuntu 20.04 LTS, you can simply clone a compressed image of an already installed system into your external drive according to [this link](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS).

---

### Post by sudodus on 2021-05-30
[SIZE=4]Second computer dedicated to Ubuntu[/SIZE]

Another alternative is to have a second computer, not necessarily a brand new one, and dedicate that computer to Ubuntu. Refurbished enterprise class computers are often worth the money. Furthermore, such computers are often very compatible with Ubuntu (and other linux distros). If there is no internal drive in it, you can easily create a portable external drive (for example an SSD connected via USB).

[SIZE=4]Persistent live system with Ubuntu[/SIZE]

By the way, how much will you work with Ubuntu? Will it be a main working system, or only a testing system for software that is mainly targeting Windows or MacOS?

If Ubuntu is only a testing system, it may be enough to install a persistent live Ubuntu system in your external SSD. It is very easy with mkusb according to [this link](https://help.ubuntu.com/community/mkusb).

---

### Post by arkeo on 2021-06-01
Thank you, it is! Every comment is much appreciated!
Yeah I suppose I could do that with a desktop but unfortunately this otherwise nice Huawei laptop doesn't allow me to do what you suggested: the BIOS gives very VERY limited options, plus I don't think the stupid thing even has a SATA controller -- NVME / M.2 disks should be on the PCI bus, am I correct? So, obviously you can't disable PCI, my only options are M.2 or USB (and BTW, it's got 2 but it looks like only one of'em is bootable)... Maybe I should just shut up & shell out another 500 for a second laptop, but that'll hurt my pride as well as my wallet! ;)

---

### Post by arkeo on 2021-06-01
> **sudodus said:**
> [SIZE=4]Second computer dedicated to Ubuntu[/SIZE]
(...) Refurbished enterprise class computers are often worth the money. Furthermore, such computers are often very compatible with Ubuntu (and other linux distros).

Thanks, I just mentioned the idea of doing it the easier way and just buy another laptop. Your quote about refurbished enterprise class computers made me ponder though -- I fondly remember installing Debian on a Silicon Graphics O2 (yep, it still wasn't called SGI) but that kind of hardware gets obsolete pretty fast -- serial ports & VGA while at that time the original iMac gave us the blessing of USB to the masses! I'm exaggerating, but only just a bit... :)

Back to the point, I'd like to move away from Windows for practical and ideological reasons. And also I'd need a working, stable Ubuntu machine (VMs are not an option). The biggest challenge I had to face over the years is printers, especially Wi-Fi and/or multi-finctional. Openprinting.org helps a lot, but I think there should be more support upstream. I can't raccommend to a whole editorial staff to switch to GNU/Linux (any distro) if the local printers/scanners won't work "right out of the box". Sadly it's hard enough to have them switch to Libre Office -- which is straightforward enough IMO... :rolleyes:

Can you suggest a seller of those legacy workstations? That really got my attention! :) Possibly based in the EU? Thanks!

---

### Post by arkeo on 2021-06-01
> **ubfan1 said:**
> Grub-install works just fine, it installs to where you tell it, and upgrades should be fine.  Just the Ubuntu installer suffers from TMC (Too Much Code) and thinks it is so smart it can ignore user input.

Correct me if I'm wrong, I often am, are you suggesting to use a different installer? How would I accomplish that?
Or maybe, what about using the Server edition? IIRC it's very manual and text only, so I should be able place GRUB where *I* want it, not where the installer decides... Thank you for all the info!

---

### Post by sudodus on 2021-06-01
> **arkeo said:**
> Can you suggest a seller of those legacy workstations? That really got my attention! :) Possibly based in the EU? Thanks!

I have bought second hand computers for me and friends from

[Inrego (in Swedish)](https://www.inrego.se)

[Inrego (for international sale)](https://www.inrego.com/)

and I am satisfied with their products (and response, if/when problems). You might be able to find vendors of similar products, that operate closer to your location ...

---

### Post by oldfred on 2021-06-01
The Ubuntu installer is Ubiquity.
But they are working on a totally new installer.

Once we found the various work arounds, it is possible to install to external drive.
Always best to partition in advance with any drive, so it is gpt partitioned and has an ESP - efi system partition. 
Then grub can be installed or repaired if a workaround during install did not work.

---

### Post by ubfan1 on 2021-06-01
grub-install will do the job, see man grub-install for all the options.  It will allow you to specify the locations you want, and not arbitrarily change them.  Some options may require specific packages be installed, like grub-efi-amd64-signed fot the --uefi-secure-boot.  I did file a bug 6 years ago on the combination of removable and uefi-secure boot, [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1453980](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1453980) , but no-one else seemed to be affected -- probably has been fixed by now. Just check that if you select secure boot, shimx64.efi is really used instead of grubx64.efi.

---

### Post by arkeo on 2021-06-02
My apologies, I've only noticed your reply last night, probably didn't notice it because this forum has been *extremely* helpful. Kudos to all of you, really.

3 hrs was of course an exaggeration, but would you think that that approach (disconnecting the internal M.2) would be a solution to my... not problem, maybe nuisance?

Thank you!

---

### Post by arkeo on 2021-06-02
Thanks!
I only mentioned the EU because of customs...tariffs? Sweden doesn't use the Euro but we're both part of the EU, so no tariffs applied here! :)
There's a weird registration process though, just to download a brochure, a list of what they've got in stock? Still very much interested! :)
Cheers!

---

### Post by sudodus on 2021-06-02
> **arkeo said:**
> My apologies, I've only noticed your reply last night, probably didn't notice it because this forum has been *extremely* helpful. Kudos to all of you, really.

3 hrs was of course an exaggeration, but would you think that that approach (disconnecting the internal M.2) would be a solution to my... not problem, maybe nuisance?

Thank you!

I think so. I have used this method many times, and it works well for me.

---

### Post by sudodus on 2021-06-02
> **arkeo said:**
> Thanks!
I only mentioned the EU because of customs...tariffs? Sweden doesn't use the Euro but we're both part of the EU, so no tariffs applied here! :)
There's a weird registration process though, just to download a brochure, a list of what they've got in stock? Still very much interested! :)
Cheers!

There is no such registration when buying via the web site in Swedish. My guess about the registration is that they think that you might become an agent (not an end user). But I may be wrong, you should ask one of the contact persons directly (for example via email).

---

### Post by arkeo on 2021-06-02
Yep, problem solved they actually called me from Sweden herself! This is real customer service! I'm going for a 3-day vacation in Rome so I don't think I'll be easily reachable but I'd like to thank you all, each and everyone who replied to this thread. Thanks! :)

//edit for mis-spelling

---

