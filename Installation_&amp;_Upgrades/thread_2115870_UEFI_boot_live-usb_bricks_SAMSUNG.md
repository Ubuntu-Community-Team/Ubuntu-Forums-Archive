---
title: "UEFI boot live-usb bricks SAMSUNG"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by Olympe on 2013-02-14
Hi,

I have a new Samsung, and now, after reading about this bug:

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

I'm worried about trying to run Ubuntu.

Thankfully I found that thread before starting to install Ubuntu on my laptop, which is Samsung 530u3c-b01se
BIOS version P05AAJ.



I read that thread almost completely, but I'm still somewhat confused. (And don't understand all these issues discussed in the thread)
 I'm wondering now what to do. I want to first just try running Ubuntu 12.04 from usb.


I have created a bootable usb with the latest 12.04 on it, the 64 bit version. (is this the right one for my Samsung?)
 from
[http://cdimage.ubuntu.com/precise/daily-live/current/](http://cdimage.ubuntu.com/precise/daily-live/current/)


I created the usb using Unetbootin, to be able to get the latest daily build of 12.04.



Now, should I try and do everything Fabri Velas #128 on that linked thread did, or should I just disable fast BIOS mode, enable ACHI, and keep UEFI Boot Support disabled, and then just try booting from the usb?

(The default setting for ACHI mode control is Auto)



Also,  some things either I don't understand, or they are different on my  computer in comparison to Fabri Velas'. For example, on Boot tab I don't  have an option of Secure boot.. 
 

I want eventually a dual boot with Windows 7 and Ubuntu 12.04 (or the latest, is it 12.10 now.)



So what is the safest option to try now?


And should I update by BIOS version?

---

### Post by Olympe on 2013-02-14
(MY BIOS, obviously)

Update: so I tried (without installing) to run Ubuntu from that usb and it seems to work fine!

So what should I do now, to use both Windows and Ubuntu?

I wouldn't mind even using Ubuntu from that usb as long as the bug is fixed, but how do I do that in a way that changing between the two systems is as easy as possible? 
Now if I want to go back to Windows, I have to restart the computer and remove the usb. Then if I want to come back to Ubuntu, I have to choose again "try without installing" and all my settings (for date and time,  wireless..) are gone and I have to set them again..

Any advice?

---

### Post by Anaximander Thales on 2013-02-14
> **Olympe said:**
> So what should I do now, to use both Windows and Ubuntu?

I wouldn't mind even using Ubuntu from that usb as long as the bug is fixed, but how do I do that in a way that changing between the two systems is as easy as possible? 
Now if I want to go back to Windows, I have to restart the computer and remove the usb. Then if I want to come back to Ubuntu, I have to choose again "try without installing" and all my settings (for date and time,  wireless..) are gone and I have to set them again..


As far as ease of switching between systems -- I'd go with Oracle VirtualBox for windows.  You can install Ubuntu in the Virtual Machine.  You can boot into windows, and when you want to use Ubuntu, boot it up while in Windows and use it.  You'll be able to switch between the systems and have both running at the same time.

You can reverse this if you'd like (Ubuntu with Windows in a VM), however I have heard that Windows 7 doesn't play as nicely in a VM as XP does.  I'd just VM ubuntu and leave windows as is.

Some caveat's -- You'll be sharing resources between both systems.  Shouldn't be an issue, but you'll want to play around with the VM settings to get a performance YOU'RE happy with.  Also, to make sharing resources easier between the two systems (and to keep duplication down) -- check out this article from LifeHacker ([Article]("http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems"))

---

### Post by oldfred on 2013-02-14
I think the suggestion for those with Samsungs with the issue is to only boot in BIOS/Legacy mode. But now they have proved even Windows can brick a Samsung.

Posted some more info here. Some models have booted ok.
[http://ubuntuforums.org/showthread.php?t=2115789](http://ubuntuforums.org/showthread.php?t=2115789)

---

### Post by Olympe on 2013-02-14
Thanks Anaximander Thales, that sounds like a solution!

oldfred,
that's what I was thinking, but then what some people on that thread did was they used uefi after all.. (see eg. #119)

So I'm not sure how I should proceed if I want that dual boot..  
Anyway I need quite specific instructions as I haven't set up a  dual boot before, and it's some time since I last installed Ubuntu ..

---

### Post by kurt18947 on 2013-02-14
> **oldfred said:**
> I think the suggestion for those with Samsungs with the issue is to only boot in BIOS/Legacy mode. But now they have proved even Windows can brick a Samsung.

Posted some more info here. Some models have booted ok.
[http://ubuntuforums.org/showthread.php?t=2115789](http://ubuntuforums.org/showthread.php?t=2115789)

That's my understanding as well.  UEFI and the Samsung implementation is the problem.  Using 'legacy mode' or whatever it's called does not cause a problem.   It seems like avoiding UEFI for a few months might be wise, let the "oh crap we didn't test that" surprises  work themselves out.

---

### Post by oldfred on 2013-02-14
Is your model one of those that they say has the issue. If it is then I would only consider BIOS boot, but that is a hassle as you have to go into UEFI/BIOS and either turn it on or off to switch boot from Windows to Ubuntu & vice-versa.

If not one of the models then it is your call. It seems some have had it work and at least they did not immediately brick the system.

I would make sure BIOS/UEFI is up to date and check often with Samsung site. I would also backup very often just in case.

Make sure you turn off secure boot in UEFI and fast boot in Windows. Make sure you know what key to get into UEFI before it boots Windows. Many systems seem to just have a Windows menu item to go back into UEFI, but then Windows is always the default boot.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    Is your system also an UltraBook with Intel SRT. That adds more complications.

With UEFI you have gpt partitioning so there is no more 4 partition limit. You can use Windows Disk tools to shrink the Windows partition and create as many partitions as your want. Only use Windows to shrink Windows, but use gparted to create new partitions.

A separate NTFS shared data partition is highly recommended especially with Windows 8. Grub2 uses grub-efi which installs its boot loader to the efi partition if installed in UEFI mode. But Boot-Repair can convert a BIOS/legacy install to UEFI. And you need Boot-Repair since grub2's os-prober has a bug on finding the Windows efi boot correctly.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Olympe on 2013-02-14
> **oldfred said:**
> Is your model one of those that they say has the issue. If it is then I would only consider BIOS boot, but that is a hassle as you have to go into UEFI/BIOS and either turn it on or off to switch boot from Windows to Ubuntu & vice-versa.

I think my model is affected by the bug, it is just the one mentioned on the title of the bug report [SIZE=2]530U3C.[/SIZE][SIZE=2][SIZE=2][SIZE=2]
[/SIZE][/SIZE]
[SIZE=2]https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557[/SIZE] 
[/SIZE]
[SIZE=2] I don't know i[SIZE=2]f the end part of the model number makes a difference though?
[SIZE=2]Mine is [/SIZE][/SIZE][/SIZE][SIZE=2][SIZE=2][SIZE=2]530u3c-b01se..

[/SIZE][/SIZE][/SIZE]

---

### Post by oldfred on 2013-02-14
I image last digits are either options or slightly different versions for different markets or language.

---

### Post by Qpassa on 2013-02-27
I was going to create a new thread but then I have read your messages oldfred. Thanks, so avoid UEFI and all will be OK... right?
Should I follow this guide?
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Thanks
> Hello:
I am a new user but I have used Ubuntu since version 8.* . I have never needed to ask help in these forums but I want to now if, at this moment, is safe to install Ubuntu ( daily build) on a Samsung NP530U3C ( before these were a piece of brick). I am going to buy a new one so I would appreciate your answer.
Regards

---

### Post by oldfred on 2013-02-27
@Qpassa
Those instructions are for a UEFI install. 

If you want a BIOS install you have to choose that from the UEFI/BIOS menu and boot in BIOS/Legacy/CSM mode. How you boot install media is how it will install.

---

