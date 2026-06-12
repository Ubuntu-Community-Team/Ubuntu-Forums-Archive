---
title: "Installation Error - Please Help (new user)"
date: 2017-10-15
forum: Installation &amp; Upgrades
---

### Post by rookieuser1 on 2017-10-15
**Background:**
I think I have what is a basic problem, but I am very unfamiliar with Ubuntu and installing operating systems so I would really appreciate some advice on my situation. I have read a number of forum posts seeking a solution, but haven't had much luck - a number of them probably contain the answer I need, but the situations are always at least slightly different and I don't have the comfort level needed to apply their suggested solutions to my situation. I'll explain the problem and the couple things I have tried.

I have a Windows 7 HP laptop for work and there was a program that I needed Ubuntu to use. My goal was to install Ubuntu and run it when I needed to, but not let if affect my Windows 7. 

I followed the following guide:
[https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653](https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653)

I messed up somewhere, and now am unable to boot either Windows 7 or boot Ubuntu. I would now just like to get back to Windows 7 as it was before. Getting Ubuntu would be a bonus, but I really need to get the laptop to boot the Windows without erasing anything.

**What I did:**
I created the partition on my hard drive with roughly 50 GB. Everything looked as it did in screenshot of guide. I then downloaded Ubuntu. I didn't have a CD so I installed Universal USB Installer. I didn't have a USB either, and I think this is where I messed up; I was working on something else on the side, and it was Friday afternoon, so I didn't read over this part of the guide and installation process as I should have. On the Universal USB Installer, I simply selected the Ubuntu, selected the ISO file, and then for selecting USB Flash Drive, I went to the drop down list and selected the only option available, which must have been some built in memory and was one that only had 100MB of space or so. I assumed that maybe it was some flexible memory storage that would burn the Ubuntu on it, and that is where the operating system would be stored. After it finished, I closed it and wasn't sure where ISO file was installed. I finished something I was working on and then rebooted, not really expecting anything because I was unsure where Ubuntu was.

**Problem:**
I rebooted the device, and logged into the Check Point Endpoint Security, and then the Ubuntu window appears. I wanted to make sure I selected the right option, so I read over list multiple times to avoid accidentally erasing drive, and I missed the fact there was a timer. When the timer expired, it was over the first option, "Try Ubuntu without installing", which is what I wanted anyways and what I hope Ubuntu automatically selected, but I am not actually sure. An Ubuntu screen appeared and then there was another screen that showed the error:

(initramfs) Unable to find a medium containing a live file system

**Goal:**
I have seen multiple posts about initramfs, but right now my main goal is just to get back onto Windows 7 without erasing anything as that's what I really need for work. 
[B]
My Attempted Solutions:[/B]
On this screen, I wasn't sure what to do, and still don't. I have shut down and restarted number of times, and eventually I pressed 'esc' to get to the HP Startup Menu. I have seen multiple suggestions pointing to press F8 to get to recovery or safe mode, but on my HP at least, F8 doesn't do anything. On the HP Startup Menu, there is options for F (1,2,3,6,7,9,10) but no F8. I went to F10 Bios setup and did multiple attempts of various things such as un-selecting boot from USB (even though no USB actually inserted, but thought maybe the Universal USB Installer created some 'pseudo USB'). None of that changed anything, each time it went right to the Ubuntu Screen, and didn't give me the option for Windows. 

Another thing I tried was going to a second (Windows 7) laptop and using and actual USB Flash Drive this time to add install Ubuntu on the USB using the Universal USB Installer. On the laptop I'm having issues with, I have at this point reset all settings for BIOS and everything else I changed back to default settings. I plugged the USB into the problem laptop hoping I could at least get Ubuntu to load, but same problem happened. 

I have tried a few commands such as fdsk and GRUB or something along those lines (can't recall actual commands), but both of them were unfamiliar commands.
[B]
Question Summarized[/B]
Is there anything on the Startup Menu or any other bootup menu or option that would allow me to ignore the Ubuntu boot and just boot from Windows? None of the Bios settings I tinkered with seemed to change anything, as the machine targeted to boot from Ubunutu each time - this could be because of the way I used Universal USB Installer in selecting some local storage space to burn the ISO file onto.

I really appreciate any help.

---

### Post by Bashing-om on 2017-10-15
rookieuser1; Hello;

No, at this time is not a hopeless situation.
Let us begin by knowing what the partitioning is.

Boot up that ubuntu installer to "try ubuntu" , At the desktop activate a terminal with key combo ctl+alt+t.

Here post the output - Between code tags - of terminal commands:
```

sudo fdisk -lu
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

with the idea all we need to do is properly install grub ( GRand Unified Bootloader) .

[INDENT][INDENT]thus a tale gets told
[/INDENT][/INDENT]

---

### Post by rookieuser1 on 2017-10-15
Thank you for your response. 

I am currently unable to get to the actual desktop of Ubuntu. After I select try Ubuntu, it get's to some error about not seeing the right file, and end up at a black screen where I can enter some commands. Those commands all start with "(initramfs)" at the beginning of each line of code I enter. I tried to press the ctrl+alt+t but nothing happened. When I enter "sudo fdisk -lu" from the screen I'm at, it says sudo not found, and when I enter it without sudo, it says fdisk not found.


Edit, here is what I'm seeing and the code I'm entering:

```

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

(initramfs) sudo fdisk-lu
/bin/sh: sudo: not found
(intramfs) fdisk-lu
/bin/sh: fdisk-lu: not found


```

---

### Post by Bashing-om on 2017-10-15
rookieuser1; Well - not .

Let us "suppose" that you have a bad copy as the install medium.

Verify:
Boot the install medium.
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen ->
"check disk for defects"

what does the checker report ?

got to have a
[INDENT][INDENT]firm foundation
[/INDENT][/INDENT]

---

### Post by rookieuser1 on 2017-10-15
I went through that process, and there are a number of lines but the last one is:

```

[ end Kernel panic - not syncing: VFS: Unable to mount root fson unknown-block(0,0)

```

---

### Post by Bashing-om on 2017-10-15
rookieuser1; UNgood -

no errors found is the only acceptable outcome when one runs  "check disk for defects" .

At this point you find another means to make up the install medium and we try again.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

[INDENT]hate when this happens
[/INDENT]

---

### Post by ian-weisser on 2017-10-15
If you only need Ubuntu for occasional use, why dual-boot?
Dual-booting, as you have seen, is risky, unsupported by Windows, and requires some bit of skill.
Consider looking into Virtual Machines, which are free, fully supported by Windows, and much easier to set up (and to delete when finished).

---

### Post by leunam12 on 2017-10-16
What you have to do is insert a Windows 7 installation disk and follow the guide below:

[https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues](https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues)

---

### Post by mastablasta on 2017-10-16
> **rookieuser1 said:**
> 
I followed the following guide:
[https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653](https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653)

perfect as step 2 deals with backing up the system, so you can easily restore it in case something goes wrong. you did did follow the guide and backed it up, right?

> 

**What I did:**
.... I didn't have a USB either, and I think this is where I messed up; ...
...I went to the drop down list and selected the only option available, which must have been some built in memory and was one that only had 100MB of space or so... 

you overwrote you windows boot partition. you now need another PC where you can do this:

> **leunam12 said:**
> What you have to do is insert a Windows 7 installation disk and follow the guide below:
[https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues](https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues)

after that make sure you check the MD5SUM  of the downloaded image: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
then you need USB drive where you will "burn" the Ubuntu image.

before you press install make sure correct disk space is selected and do a backup of the OS before doing the install. Backup programs: 
Redo (works on older PCs): [http://redobackup.org/](http://redobackup.org/)
Clonezilla (works on latest PCs but perhaps not so user friendly interface): [http://clonezilla.org/](http://clonezilla.org/)

finally as others mentioned, for you needs a VM such as virtualbox is a better solution providing you have the RAM for it: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
for older PCs Lubuntu in VM is a better choice.: [http://lubuntu.net/](http://lubuntu.net/)

if you go with the virtualisation you can also just download the virtual image that is then loaded to for example Virtualbox (no install needed): [https://bitnami.com/stacks](https://bitnami.com/stacks)

---

### Post by slickymaster on 2017-10-16
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by xanizen on 2018-05-28
The solution [here (link)]("https://askubuntu.com/a/713799/834778"), solved it for me.

In \Isolinux\isolinux.cfg, change the first occurence of, quiet splash --, to, break debug --
After you get [the error messages]("https://imgur.com/Nu1Uel6"), unplug the USB flash drive, and plug it back in, and you'll see an ['Attached SCSI disk']("https://imgur.com/aYluWPD"), prompt. Then type exit and press enter; 15-30 seconds later you'll see green [OK] texts scroll by fast.

When installing windows 7 a few months ago, I had to resort to physically removing the flash drive and plug it back in.

The fact this problem remains unfixed since 2013 is very worrisome.

---

