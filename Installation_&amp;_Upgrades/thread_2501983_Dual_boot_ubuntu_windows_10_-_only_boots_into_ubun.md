---
title: "Dual boot ubuntu windows 10 - only boots into ubuntu - no boot selection menu"
date: 2024-10-28
forum: Installation &amp; Upgrades
---

### Post by yinnxbutu on 2024-10-28
This is on a Dell 7010 that started out with windows 7 and was upgraded to windows 10.  Several months ago I did a dual boot install of Ubuntu and it worked fine.  The menu with the boot choices popped up and I could boot into either windows or Ubuntu.  Now something has happened to cause that boot choice menu to not appear and so I cannot boot into windows but it will boot into Ubuntu.  I read many posts on this and similar problems and finally ran Boot-Repair and here are the results.  I did not do the repair because I wanted to see what you had to say about it.  I do know that in the bios screen it show everything being "legacy".  I guess it has been that way all along.  Any help you be is appreciated.  Should I go ahead and let boot-repair try to fix it? Thanks.

[https://paste.ubuntu.com/p/VndP5D39xh/](https://paste.ubuntu.com/p/VndP5D39xh/)

---

### Post by grahammechanical on 2024-10-28
Please clarify:

> Now something has happened to cause that boot choice menu to not appear  and so I cannot boot into windows but it will boot into Ubuntu

Does the boot menu pop up? Or does the system boot into Ubuntu without the boot menu appearing.

In Ubuntu open the terminal and enter this command

```
sudo update-grub
```

Watch the printout. Is Windows detected?

Regards

---

### Post by yinnxbutu on 2024-10-28
Yes the menu does not appear, and the machine just boots straight into Ubuntu. 

Here is what I got when ran sudo update-grub
[https://paste.ubuntu.com/p/gPMr7XnY5h/](https://paste.ubuntu.com/p/gPMr7XnY5h/)

---

### Post by tea for one on 2024-10-29
The text below is from your grub configuration
```
Warning: os-prober will not be executed to detect other bootable partitions.
```
Therefore, make an edit to /etc/default/grub
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0
[s]GRUB_TIMEOUT_STYLE=hidden[/s]
GRUB_TIMEOUT_STYLE=menu [COLOR="#0000FF"]# change hidden to menu[/COLOR]
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false [COLOR="#0000FF"]# add this line [/COLOR]
```
```
sudo update-grub
```
Any improvement?

---

### Post by yinnxbutu on 2024-10-29
No change on booting.  I did see this though.

```
mike-OptiPlex-7010:~$ sudo update-grub
Sourcing file `/etc/default/grub'
**/usr/sbin/grub-mkconfig: 1: /etc/default/grub: /boot/grub/grub.cfg.: not found**
```

---

### Post by tea for one on 2024-10-29
I'm beginning to suspect that you may have Ubuntu in UEFI mode and Windows in Legacy mode?
```
Line 230 -  Grub-efi would not be selected by default because legacy Windows detected.
Line 54 - /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
```
Can you allow Ubuntu to load, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
What is the output?

---

### Post by yinnxbutu on 2024-10-29
I get this:

```
mike-OptiPlex-7010:~$ [ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
Legacy
```

---

### Post by tea for one on 2024-10-29
When you ran sudo update-grub, did the command find Windows Boot Manager?

---

### Post by yinnxbutu on 2024-10-29
> **tea for one said:**
> When you ran sudo update-grub, did the command find Windows Boot Manager?

No sign of Windows. Here is what I get:

```
mike-OptiPlex-7010:~$ sudo update-grub
[sudo] password for mike: 
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 1: /etc/default/grub: /boot/grub/grub.cfg.: not found
```

---

### Post by tea for one on 2024-10-29
Having identified that both Windows and Ubuntu are installed in Legacy mode, now's the time to run the recommendation from boot-repair (refer to lines 228 - 230).

---

### Post by yinnxbutu on 2024-10-29
I ran boot-repair and it seemed to be working. At least it thinks it worked but when I rebooted it still does the same thing, boots straight to Ubuntu. So, if you think of anything else please let me know. I really appreciate your help!

---

### Post by tea for one on 2024-10-30
Back to square one - but, never mind, let's see..........
From your comment, I deduce that the Grub menu does not appear when you power on the PC.
Is that correct?

Power on from cold and tap the left shift key (say, every half second), any sign of Grub?

---

### Post by yinnxbutu on 2024-10-30
Yes, a grub menu came up that time, but there's no windows selection.  It says hit "e" to edit, and then it shows a bunch of stuff.  Then I backed out. I'll try to attach some pics from the screen.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294433&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294434&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294435&stc=1[/IMG]

---

### Post by oldfred on 2024-10-30
To dual boot both systems if on one drive must be in same boot mode, or both BIOS or both UEFI.

Windows has to have MBR(msdos) partitioning for old BIOS/Legacy/CSM boot.
Windows has to have newer gpt partitioning for UEFI boot. Microsoft has required UEFI/gpt installs by vendors since release of Windows 8 in 2012. So all newer hardware is UEFI.
Windows 7 originally was BIOS only but later releases included UEFI/gpt boot, but only with UEFI Secure Boot off.
Note conversion from MBR to gpt totally erases a drive. So backups required.

Ubuntu allows UEFI install to MBR drives, but probably should not as it creates the problem you now have.
You can only have one boot flag per drive. UEFI has ESP that must have boot flag. Windows in BIOS mode must have boot flag on its boot partition or which every partition has boot files, your sda1. Often boot partition is a smaller NTFS partition before the "C:Drive" partition. 
UEFI & BIOS write hardware data to drive totally differently, so once you start booting you cannot switch. Or grub can only boot other installs in same boot mode.

You need to always have a Windows repair recovery flash drive & Ubuntu live installer to make repairs. 
Grub can only boot working Windows, so then you have to temporarily install Windows boot loader, fix Windows and then restore grub. Boot-Repair actually can install a Windows type boot loader (syslinux) to MBR to directly boot Windows.

---

### Post by yancek on 2024-10-30
If the link to boot repair in your initial post is current, the problem is that you have/had both windows and Ubuntu installed in Legacy mode.  From boot repair, line 5 shows:  Grub2 (v2.00) is installed in the MBR of /dev/sda AND line 47 shows sda5 is an EFI partition with only ubuntu boot files.   Line 91 in boot repair shows the drive is not gpt therefore windows can't boot EFI even if it had EFI boot files which it does not.  Do you have Legacy/CSM boot enabled in the BIOS/

Just saw the post by oldfred above.  Make the suggested changes.

---

### Post by tea for one on 2024-10-30
Now that boot-repair has re-installed Grub, can you return to post 4 and see if your /etc/default/grub config includes the OS-Prober
If not, make the changes and update-grub.

---

### Post by yinnxbutu on 2024-10-30
I did the /etc/default/grub and OS-Prober line is still there. Ran update-grub but nothing has changed.
So I ran boot-repair again and let it do it's recommended repair. But still no luck.
Then I booted into my Windows flash drive and clicked to troubleshoot startup problems and it said was not able to repair startup. 

I'm wondering if there is easy way to just uninstall Ubuntu so as to be left with just windows.  Then, if still cannot boot into Windows maybe I can reinstall Windows and start again there. (?)

---

### Post by yancek on 2024-10-30
>  I'm wondering if there is easy way to just uninstall Ubuntu so as to be left with just windows

There is no point in doing that.  If you want to remove Ubuntu and just have windows you would just go into windows and use Disk Management to format the partition(s) on which you have Ubuntu to an ntfs filesystem.  Since you can't boot windows you would need some windows recovery disk/usb.

You never indicated if you enabled Legacy/CSM boot in your BIOS.  You can see that both windows and Ubuntu are Legacy installs so enable Legacy/CSM in the BIOS.  Your efi partition isn't much use for a dual boot since it only has Ubuntu files in it.

When you ran boot repair the last time, did you boot in UEFI mode or Legacy mode?  Should be Legacy mode.

---

### Post by tea for one on 2024-10-30
Which Windows iso do you have?
Does it boot in Legacy mode?
Have you backed up your personal data from both Windows and Ubuntu?

---

### Post by yinnxbutu on 2024-10-30
> When you ran boot repair the last time, did you boot in UEFI mode or Legacy mode?  Should be Legacy mode. 

Yes it is Legacy

---

### Post by yinnxbutu on 2024-10-30
> **tea for one said:**
> Which Windows iso do you have?
Does it boot in Legacy mode?
Have you backed up your personal data from both Windows and Ubuntu?

1) Windows 10
2) It is supposed to, but I can't get it to boot to Windows.
3) Yes, both are backed up.

---

### Post by tea for one on 2024-10-30
What actually happens when you boot the Windows installer?
Does it stall somewhere?

---

### Post by yinnxbutu on 2024-10-31
> **tea for one said:**
> What actually happens when you boot the Windows installer?
Does it stall somewhere?

When you asked this I thought I'd go try it again. When I booted to the windows 10 flash drive it gave choices of what to do. I selected "troubleshoot repair boot problems" then it said it was not able to repair windows boot.  Same result as before.
So I considered using the same flash drive to just reinstall windows.  But before that I found another flash drive I made using macrium. I booted to it and it had a choice of repairing windows boot problems. So I ran it and it
fixed it, so now the computer boots straight into windows 10. However I guess that messed up Ubuntu because can't get back into grub. I rebooted several times with shift key, esc etc but so far it just goes straight to windows.
I think this is progress, I suppose I can just reinstall Ubuntu as I did before and have dual boot back again.

---

### Post by tea for one on 2024-10-31
Yes, I think that it is a bit of progress.
Previously, Grub wouldn't boot Windows because Windows was not in a bootable condition.
Now that you have successfully repaired Windows, good old Microsoft has resumed its dominance over the boot process.
I would now run boot-repair again and, fingers crossed, it will re-install Grub to the disk and recognise a working Windows.

---

### Post by qyot27 on 2024-10-31
> **oldfred said:**
> Windows has to have newer gpt partitioning for UEFI boot. Microsoft has required UEFI/gpt installs by vendors since release of Windows 8 in 2012. So all newer hardware is UEFI.
While OEMs may be required to use UEFI, an end user can still install Windows 10 (and presumably even Windows 11, but I don't know) in MBR mode.  I did it unwittingly back in 2020(?) when I relented and installed Windows on my main setup, even though the existing Ubuntu installation was UEFI/GPT.  Entirely separate boot drives too; grub could see the Windows partition, but couldn't boot from it; if I wanted to boot Windows, I had to use the motherboard's boot menu to do it.

The wrench in this was that I used VirtualBox to install Windows to the drive so it couldn't touch the existing Ubuntu installation.  What I didn't realize at the time was that VirtualBox defaults to MBR, so that's how Windows installed itself.

> Note conversion from MBR to gpt totally erases a drive. So backups required.
Backups are of course recommended, but Windows 10 does have a utility to do an in-place conversion from MBR to GPT post-install.  I used it to fix that above situation so that my Arc A770 could actually be configured properly (because settings related to turning on Resizeable BAR require UEFI, but setting it to UEFI only caused Windows to stop booting, which made me finally realize what had happened when I'd installed it).  Afterwards Grub could boot either OS without an issue...until a couple weeks ago.  I'm not sure if it was a Windows update, or the installer for 24.10, but I'm back to needing to use the motherboard's boot menu to get into Windows.

---

### Post by yinnxbutu on 2024-11-01
> **tea for one said:**
> Yes, I think that it is a bit of progress.
Previously, Grub wouldn't boot Windows because Windows was not in a bootable condition.
Now that you have successfully repaired Windows, good old Microsoft has resumed its dominance over the boot process.
I would now run boot-repair again and, fingers crossed, it will re-install Grub to the disk and recognise a working Windows.

Yes, I think that will work, but now I'm thinking of just using a separate computer for Ubuntu and avoid dual boot issues. 

 Thanks for all your help and the others that contributed too, I never would have figured this out by myself.

---

### Post by tea for one on 2024-11-02
> **yinnxbutu said:**
> but now I'm thinking of just using a separate computer for Ubuntu and avoid dual boot issues
Yes, fully agree.
> If you can possibly manage it, have one OS per computer
If you absolutely must have more than one OS per computer, at least have one OS per disk
If you absolutely insist on having more than one OS per disk, understand everything written on this page
The above quotation was slavishly copied from the Recommendations (scroll towards end) here:-
[https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/](https://www.happyassassin.net/posts/2014/01/25/uefi-boot-how-does-that-actually-work-then/)
It's worth a look, especially for PC users who like to experiment (i.e. dilettante (myself) rather than professional)

---

### Post by oldfred on 2024-11-02
I had a working Windows/Ubuntu dual boot on one drive working well.
Then hardware issues & Windows corruption erased my working Ubuntu. Gave up on dual boot on one internal drive & now use an external SSD with Ubuntu on Windows laptop. Actually external SSD is a copy/backup of my desktop install. So far that has worked much better.

Have had no issues with multiple installs of Ubuntu & other Linux systems on same drive other than managing grub & boot order. I just have to keep main working LTS install as default boot & add others to its grub menu.

---

