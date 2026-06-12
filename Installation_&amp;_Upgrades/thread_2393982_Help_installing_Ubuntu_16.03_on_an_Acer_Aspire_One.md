---
title: "Help installing Ubuntu 16.03 on an Acer Aspire One Cloudbook 14 Celeron N3050"
date: 2018-06-11
forum: Installation &amp; Upgrades
---

### Post by makerblock on 2018-06-11
Disclaimer:  I have limited experience with Ubuntu, but would really like to run it on this new laptop instead of Windows 10.  I'd like to try installing it side-by-side with Windows 10, before removing Windows 10 completely.

Things I've done so far:
[LIST]
[*]I've been following these [two]("https://ubuntu-mate.community/t/ubuntu-beginners-guide-complete-how-to-install-and-run-first-update/955") [guides]("http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html")
[*]Created a Windows 10 restore/backup USB drive
[*]Created an Ubuntu 16.03 USB drive
[*]Shrunk the Windows partition down to 27GB [using this guide]("http://www.everydaylinuxuser.com/2015/11/how-to-shrink-windows-10-to-make-space.html")
[*]Disabled UEFI using these [two]("https://www.howtogeek.com/175641/how-to-boot-and-install-linux-on-a-uefi-pc-with-secure-boot/") [guides]("https://www.appgeeker.com/recovery/disable-uefi-secure-boot-in-windows-10.html")
[/LIST]

By fiddling with the UEFI settings, I can get the computer to either boot to (1) a full screen of error messages which doesn't respond to the keyboard or (2) a totally blank screen with no prompt, which is also unresponsive to the keyboard.  I can post a picture of the error messages, if that's helpful.

Any help is greatly appreciated.

Thank you in advance!

---

### Post by makerblock on 2018-06-11
Update:

[LIST]
[*]I started following parts of [this guide]("https://forums.linuxmint.com/viewtopic.php?t=245855#p1317851"), specifically, managing the UEFI settings
[*]I inserted the Ubuntu USB drive and booted to the "GNU GRUB" Ubuntu booting options (try, install, etc)
[*]Pressed "e" to edit the Ubuntu booting options
[*]I added "*acpi=off" after the "linux" prompt*
[*]I could then boot into Ubuntu "Live"
[LIST]
[*]At first the trackpad didn't work even though the keyboard does
[*]Then I rebooted (still into "Ubuntu Live"), and the trackpad works!  But the keyboard doesn't...
[*]When I tried to install Ubuntu onto the computer, I got the error "You need at least 8.6 GB disk space to install Ubuntu. This computer has only 2.0 GB."
[/LIST]

[*]Then I tried just installing Ubuntu (editing the command to include "acpi=off")
[LIST]
[*]The keyboard works, but I'm getting the same error "You need at least 8.6 GB disk space to install Ubuntu. This computer has only 2.0 GB."
[/LIST]
[/LIST]

Any help or insight appreciated :)

Thanks in advance

---

### Post by hans12345 on 2018-06-11
Can you give us the specs of your laptop? Is it a 32 GB SSD model?

Maybe tell us what the partition sizes are?

My impression is that you have insufficient drive space. Win 10 probably takes nearly all the available space.

---

### Post by makerblock on 2018-06-11
Hi Hans12345!

Thank you so much for your reply!  Yes, it's a 64GB SSD model.  

If it helps, looking at "Disk Management" in Windows 10, there's 500MB used by UEFI, 500MB used by recovery, and about 27GB used by Windows with about 30GB free.  

Following one of the guides linked in one of my earlier posts, I partitioned the Windows drive to 35GB, leaving a 20GB partition.  I was hoping to install Ubuntu alongside Windows 10, with the goal of removing Windows entirely after I'd had a chance to get used to Ubuntu.

The full title of the laptop is, "Acer Aspire One Cloudbook 14 Celeron N3050 Dual-core 1.60GHz 2GB MEM 64 GB Flash".  

Please let me know if you need additional information or any other specifics.

Thank you so much for helping out!

---

### Post by hans12345 on 2018-06-12
Warning - I am not an expert on this so I hope someone else can jump in.
My comments:
You have a 20GB partition available. More than enough. The message says "You need at least 8.6 GB disk space to install Ubuntu. This computer has only 2.0 GB".  So it is trying to install in the wrong partition.
Have you looked for advice at   [https://askubuntu.com/](https://askubuntu.com/) ?
You should be installing Ubuntu 18.04. It is the current version and has the advantage that it uses a swap file and not a swap partition.

---

### Post by makerblock on 2018-06-12
Thanks hans12345,

Yeah, my guess is Ubuntu was trying to install into the 2.0GB flash drive.  I tried to use Ubuntu Live to access the C: drive, but with no success. Since all it could "see" was the space on the flash drive, my guess is that it didn't even recognize any part of the SSD, let alone the partition I had made just for it.

I'll download 18.04 and give it a whirl.  :)

Thanks for your help - and I'll give askUbuntu.com a shot.  (However, in case anyone else should find this post, I'll post an update here as I try more things)

---

### Post by makerblock on 2018-06-12
I just tried to install using Ubuntu 18.04 and am still getting the message [COLOR=#000000]"You need at least 8.6 GB disk space to install Ubuntu. This computer has only 2.0 GB"


[/COLOR]

---

### Post by westie457 on 2018-06-12
Have you disabled Fast startup in Windows?

If Fast startup is enabled you will have problems after the installation has completed.

Is the 20GB partition left as empty space or formatted to NTFS?

Any distro of Linux will not install to a Windows-style formatted partition (FAT32 or NTFS). Only Linux should be used to format the partitions for a Linux installation.

This is just one example of how to turn off fast startup. there are others. [https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by hans12345 on 2018-06-13
> **westie457 said:**
> 
...
Is the 20GB partition left as empty space or formatted to NTFS?

...



Good advice.

Format the empty partition to ext4 format.

---

### Post by makerblock on 2018-06-14
Thank you both hans12345 and westie457,

I've now turned off "Fast Startup" per that guide.  The 29.3GB partition is "Unallocated" space and unformated.  

As for "Fast Startup" causing a problem after installation - I can't even get to the installation options since booting into Ubuntu only gets me part way through before it says I don't have sufficient drive space.  It is unable to see the C drive or the unallocated partition.

In Windows Disk Management I see I can format it and assign a drive letter.  Do I want to do that?

As always, thank you for your help.

---

### Post by westie457 on 2018-06-14
> [COLOR=#000000]In Windows Disk Management I see I can format it and assign a drive letter. Do I want to do that?[/COLOR]

No you don't want to do that.

Next you should boot Windows as normal and open an 'Admin Command Prompt'. The quick way is press the Windows key + x and select it from the menu. 
In the Prompt type in - POWERCFG /H OFF hit Enter. This will remove  hyberfil.sys from your system freeing up space to shrink the main Windows partition some more if you need to.

Next  plug in your usb stick and reboot. Tap the F12 key until the 'one-time boot' menu appears select the UEFI USB and boot into try mode. This so you can check what works and what will possibly need fixing later.
In the Live environment start Gparted, here I would like you to post screenshot of the partitions on the main drive. If Gparted defaults to showing the usb stick as /dev/sda look near the top-right corner click and select another drive. 

The next steps and advice will come when we have a clearer picture of the situation.

---

### Post by makerblock on 2018-06-16
Hi westie457,

Okay, I've removed hyberfil.sys as instructed, then re-shrunk the partition so that I have a little over 32GB in the empty unformatted partition.

As you predicted, Gparted defaulted to showing the usb stick as "/dev/sda", but when I click on the top right corner, I'm not able to select any other drive.  I was able to take a screenshot, or, rather, I thought I was able to.  I saw it in the "pictures" folder when I was in the Ubuntu live environment. However, I can't locate it on the flash drive anywhere.

:/  

Suggestions?

Thank you!

---

### Post by westie457 on 2018-06-16
Okay not a problem, by default the Live DE does not save anything unless you save it elsewhere.
Instead could you post a screenshot of the disk management console in Windows. We can work with that.
Side question and not really relevant to your issue.Does your Wifi work in the Live DE?

---

### Post by makerblock on 2018-06-16
Yes, I can definitely get you a screenshot of Win Disk Management.  :)
Yup, the WiFi works.

---

### Post by makerblock on 2018-06-16
Here's the screenshot from Win 10 Disk Manager
[ATTACH=CONFIG]280118[/ATTACH]
Thanks!

---

### Post by westie457 on 2018-06-17
We have a solution and it goes like this.

With Secure Boot disabled boot from your Uefi Usb stick (hopefully you see a screen with some lines of text), select Try-mode.
From here you can set your wifi connection then click on the Install icon.
Follow the prompts until you get to the 'How to Install' screen, here choose the 'Something Else' option.
In the new window look for the partition marked as empty space, it should appear under a line that reads '/dev/mmblk0' or something similar.
Highlight this partition and click 'Add'. In the new window set the size to 20000-25000 MB, call it a Primary, place at the end of this space, format as Ext4 and set the mountpoint as / (root) click okay and follow the prompts again and wait.
Next, at the bottom of the partitioning window is a section 'Where to install Grub' click and then select the /dev/mmblk0 (or whatever it is called). Finally click on Install Now.

After this you should be booting your L/X/K/Ubuntu. Hooray.

The reason for leaving an area of empty space between the 2 OSes is because Windows might choke on 24 Gbs when the new round of major updates arrive and you can resize the Windows partition to alleviate this issue. 

With everything now working as it should reboot into the Uefi Settings, set Trust accepting the default suggestions until you get to name it what you want to. Reset Secure Boot to on. You are all done.

PS Apologies if this reads as baby-steps, it is intentional just in case someone else who does not know as much as you finds this and needs detailed help.

---

### Post by oldfred on 2018-06-17
Have you updated UEFI from Acer. Most systems need that anyway.

Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

Once installed you will need to set "trust". This is unique to all Acer but better than the work arounds many other systems require.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392

      [/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
[https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074](https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074) 
    [URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]
[/URL]

---

### Post by makerblock on 2018-06-17
westie457, oldfred,

Thanks guys!  I'll try these and report back.

---

### Post by hans12345 on 2018-06-17
I've been busy.

Use your Ubuntu installation USB to format the partition. I do not think Windows knows about ext4. 

Try initially just using the 'Try Ubuntu' option for the formatting. From memory, that should be OK. If not, start the installation normally until you get to the big step, when you choose the 'Something Else' option.

If all else fails, create for yourself a Gparted USB - see [https://gparted.org/liveusb.php]("https://gparted.org/liveusb.php"). This is a useful tool to have, and will help you format the empty partition.

Good luck.

---

### Post by makerblock on 2018-06-28
Hi guys,

Quick update - been swamped at work, but I did try all of the above.  Unfortunately, I never get to the "Something Else" option as nothing I've tried allows Ubuntu to recognize anything other than the USB flash drive.

Should I try to create a Gparted USB?

Thanks

---

### Post by makerblock on 2018-11-09
Thanks for your patience on this one.

After some frustration, I returned to this project of trying to install Ubuntu on this Acer Cloudbook.  I've finally made some headway.  In case anyone comes after me (and to help document my journey) here's what I did:


[LIST=1]
[*]I uninstalled some of the bloatware on the machine and then used the Windows Disk Management Tool to shrink the Windows partition, increasing the amount of unallocated space.  This was an odd process.  It did not want me to remove more of the space allocated to Windows.  About half the time it would say there wasn't sufficient free space to un-allocate.  And half the time it would let me shrink the drive by 10MB - 500MB at a time beyond what I had already shrunk it.
[*]I found [this old thread on Reddit]("https://www.reddit.com/r/linux/comments/4894rj/acer_aspire_cloudbook_cheap_laptop_that_runs/") that seemed to apply to my situation
[*]I tried [each of the guides on the linked page]("https://wiki.archlinux.org/index.php/Acer_Cloudbook")
[*]As of right now I have the laptop on and it looks like it is letting me install Ubuntu!
[LIST=1]
[*]Right now the laptop has "Touchpad: Basic", "Boot Mode: Legacy" (instead of UEFI!), and Boot priority order with the USBpic drive higher than the eMMC.
[*]Despite using the "edd=off" and "noapic" options, I wasn't able to install Ubuntu straight away, instead I selected "try" Ubuntu
[*]From here I was finally able to access Gparted and "see" the unallocated space.  I'm not sure which of the above options allowed this to happen, but some combination of the above must have worked.
[*]From inside the trial Ubuntu environment, I am able to start the "Install Ubuntu 18.04 LTS" process
[/LIST]
[/LIST]

I hope this is helpful to others!  

MakerBlock

---

