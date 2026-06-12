---
title: "Cannot install GRUB while installing Ubuntu on Acer"
date: 2018-03-31
forum: Installation &amp; Upgrades
---

### Post by thebittenpeach on 2018-03-31
Hello,

I have Acer Spin 1 (I understand there are lots of problems with this specific brand and type). It came with Windows 10 preinstalled.

I have had so many issues with just booting the LiveUSB of Ubuntu Budgie 17.10. I enabled secure boot and network mode and had to set UEFI trust file (bootx64.efi).

So now I wanted to install the OS. I decided for a clean install of linux. When it started installing, everything was going fine. It has stopped on installing GRUB package though. I have waited an hour and still no sign of progress. 

When the grub is about to install, the installing progress log says "started cleanup of temporary directories" . Then it starts saying things like "Warning: Source  ID 9454 was not found when attempting to remove it." And then it just repeats with different ID numbers. 

Would anyone be able to help me? I am worried that I will not be able to install anything now.

---

### Post by oldfred on 2018-03-31
The live installer is both UEFI & BIOS. You need to be sure you are booting in UEFI boot mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Grub often does not install, as you are installing in the wrong boot mode. UEFI expects an ESP - efi system partition and BIOS expects a bios_grub partition if drive is gpt. And if Windows is UEFI then drive is gpt partitioned.

       
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
        
 Acer Spin 5 Ubuntu 17.04 Needs Acer password & trust (same for all versions of Ubuntu & Acer if UEFI)
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238) 

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by thebittenpeach on 2018-03-31
> **oldfred said:**
> The live installer is both UEFI & BIOS. You need to be sure you are booting in UEFI boot mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Grub often does not install, as you are installing in the wrong boot mode. UEFI expects an ESP - efi system partition and BIOS expects a bios_grub partition if drive is gpt. And if Windows is UEFI then drive is gpt partitioned.

       
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
        
 Acer Spin 5 Ubuntu 17.04 Needs Acer password & trust (same for all versions of Ubuntu & Acer if UEFI)
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238) 

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

Thanks for replying. 

I have set the liveUSB to be GPT with UEFI, as my laptop uses UEFI (Insyde) and GPT partition.

I'm sorry because I don't really understand that much about this topic, so please have patience :)

I tried using Boot Repair ISO but it wasn't working (I could boot and run the repair but the repair was taking more than hour and I think it was just stuck as the installer in Ubuntu Budgie).

I will study the links you provided but I think I have done everything... I've set trust and supervisor password and all that. 

Someone wrote in some thread that I should enable network mode in UEFI which helped me to at least let me boot the LIVEUSB with Ubuntu. When I disable it, it isn't booting at all. 

I hope we can come to a solution :)

---

### Post by oldfred on 2018-03-31
Does live installer boot in live mode?

If so post this from live mode and terminal:

       sudo parted /dev/sda unit s print 

You can copy & paste here, if Internet is working with live installer which it should.
But longer text and to preserve formatting, best to use code tags.
You can easily add code tags with Forum's advanced editor, highlight code/text and click on # icon.


 How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by thebittenpeach on 2018-03-31
> **oldfred said:**
> Does live installer boot in live mode?

If so post this from live mode and terminal:

       sudo parted /dev/sda unit s print 

You can copy & paste here, if Internet is working with live installer which it should.
But longer text and to preserve formatting, best to use code tags.
You can easily add code tags with Forum's advanced editor, highlight code/text and click on # icon.


 How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

when I type the command in, it only reads the USB. And I suppose you didn't want to know about the USB right?

One more thing - I think that the problém might be the internal eMMC of my notebook. Is that correct? If yes, would you please provide some help to me? Thanks!

---

### Post by oldfred on 2018-03-31
If a MMC card then the device is not sda, typical hard drive.

try:
sudo parted -l

---

### Post by thebittenpeach on 2018-03-31
> **oldfred said:**
> If a MMC card then the device is not sda, typical hard drive.

try:
sudo parted -l 

I think I am doing something wrong.

ubuntu-budgie@ubuntu-budgie:~$ sudo -l
Matching Defaults entries for ubuntu-budgie on ubuntu-budgie:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin


User ubuntu-budgie may run the following commands on ubuntu-budgie:
    (ALL : ALL) ALL
    (ALL) NOPASSWD: ALL

By the way - I tried to change partitions exactly as showed on some site for UEFI... the grub is still stuck. (2 ext4 and 1 efi...)

Oh and also another thing - the log (when installing grub via ubuntu installer) also says :

"Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported"

Might help you guys to figure out what's going on... : )

---

### Post by Dennis N on 2018-03-31
You typed:```
 
sudo -l
```
It should be: 
```
sudo parted -l
```
Also, using code tags (#) around the output makes it clearer.

---

### Post by thebittenpeach on 2018-03-31
> **Dennis N said:**
> You typed:```
 
sudo -l
```
It should be: 
```
sudo parted -l
```
Also, using code tags (#) around the output makes it clearer.

```
Error: /dev/mmcblk0rpmb: unrecognised disk label
Warning: Error fsyncing/closing /dev/mmcblk0rpmb: Input/output error

```

(before that was, again, the USB stick)

---

### Post by oldfred on 2018-03-31
Its its normally:
/dev/mmcblk0

do not know about extra chars, unless that is how your MMC card is configured. And that may be the issue.
Please post entire command.


Post this also:
 lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT

---

