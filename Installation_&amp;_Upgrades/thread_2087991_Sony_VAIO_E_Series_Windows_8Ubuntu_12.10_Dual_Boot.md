---
title: "Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by shadowspectre on 2012-11-25
Hello everyone :) Hope you guys had a Happy Thanksgiving...and Happy Black Friday shopping.  

I did...just got a nice deal on this Sony Vaio E series laptop.

model:sve151J11L
product name: SVE1512CXS

Came pre-installed with Windows 8 (64bit), as well as some sony-specific recovery-based partitions. I wanted to dual-boot with Ubuntu 12.10 (64bit).

[HTML]http://paste.ubuntu.com/1384853/[/HTML]

Windows 8 dual boot issues were apparently common, and online someone had said to use the windows boot manager to control grub (install grub to the linux root partition) and use a windows program to add it to the windows boot manager.

Well, that was the plan.  After creating some free space, installing ubuntu (choosing the bootloader to install in Ubuntu's partition), i restart.

Windows 8 does not load.
```
error: can't find command 'drivemap'
error: invalid EFI file path.
```

It appears that the install had overwritten Windows' bootloader files, but the pastbin above states Grub is at /dev/sda7 (my ubuntu install partition)

Okay, so that failed.  I tried to use boot-repair.  Installed it as directed on the Ubuntu website.  Ran it, using default settings.  It creates ```
 Windows UEFI loader
Windows UEFI recovery
```
and possibly                 ```
windows Recovery Environment (loader) (on /sda2)
``` I cant remember if Grub or boot-repair made it.

None of the above new Grub options work.  I would post the error messages, but, for example, "Windows UEFI loader" spits out a file name (very long one) and says it cant load the image.  Grub will not stay on that screen long enough for me to type it.  Is there a way to make Grub stay on an error message?

I am hoping we can create this dual-boot setup (and keeping Sony's recovery partitions and everything working as well).

If any more information is necessary, any clarifications, etc please let me know.

Thank you for any assistance.
Shadowspectre

---

### Post by YannBuntu on 2012-11-26
> **shadowspectre said:**
> I cant remember if Grub or boot-repair made it.

The UEFI ones were created by Boot-Repair. The others by GRUB, and won't never work.

You are using a UEFI system with SecureBoot enabled.
I updated Boot-Repair today for this situation, please update the boot-repair and boot-sav packages, then run the Recommended Repair and indicate the new URL that will appear.
Then reboot and try all the UEFI entries.

---

### Post by oldfred on 2012-11-26
> Windows 8 dual boot issues were apparently common, and online someone  had said to use the windows boot manager to control grub (install grub  to the linux root partition) and use a windows program to add it to the  windows boot manager.With the new UEFI installs that is about as wrong as it can be. I assume it refers to using EasyBCD to boot. But EasyBCD does not work with UEFI installs. Some with BIOS/MBR do use that, but generally we prefer grub2 boot loader as it is designed to multi-boot. Windows is only designed to boot Windows and EasyBCD is a workaround to make Windows work with other systems.

EasyBCD does not work with Windows 8
[http://neosmart.net/forums/showthread.php?t=11135](http://neosmart.net/forums/showthread.php?t=11135)

---

### Post by shadowspectre on 2012-11-27
Confession time.

Last night, I needed a working Windows 8.  So i reformatted the harddrive, reinstalled it, etc.

After seeing your reply in the morning, I used windows to shrink the partition down a little.  This left me with some Vaio partitions in front, then Windows 8, then free space, then Vaio Recovery Partition.  I booted an Ubuntu Live CD, and switched the free space and Vaio Recovery Partition.  Rebooting, the recovery Partition seemed fine. 

I then rebooted the Live CD and installed Ubuntu with Updates enabled.
However, last time, I chose the "do something else" option"
This time, I chose the "install Ubuntu along-side Windows 8"

Everything seemed okay, but I restarted, and it booted directly into Windows 8. 

I restarted, it did the same thing, so Grub didnt load.

I started up Ubuntu Live CD again.  Used the site listed below to install and run Boot-Repair using recommended settings.  It did the same things as last time, and the same Grub options, however none of the Windows-related ones work.

I installed Boot-Repair using this page: [HTML]https://help.ubuntu.com/community/Boot-Repair
[/HTML]

So, long story short...no luck.  

new pastebin: 
[HTML]http://paste.ubuntu.com/1391025/[/HTML]

> **YannBuntu said:**
> The UEFI ones were created by Boot-Repair. The others by GRUB, and won't never work.

You are using a UEFI system with SecureBoot enabled.
I updated Boot-Repair today for this situation, please update the boot-repair and boot-sav packages, then run the Recommended Repair and indicate the new URL that will appear.
Then reboot and try all the UEFI entries.

I checked the Bios, using the Vaio software, and i found no option stating "SecureBoot".  I don't doubt your findings, however, I am not sure how to turn it off.


> With the new UEFI installs that is about as wrong as it can be. I assume  it refers to using EasyBCD to boot. But EasyBCD does not work with UEFI  installs. Some with BIOS/MBR do use that, but generally we prefer grub2  boot loader as it is designed to multi-boot. Windows is only designed  to boot Windows and EasyBCD is a workaround to make Windows work with  other systems.

Yes, EasyBCD was the concept. Glad to know.  So where should I be installing Grub to? The default looks like it maybe placed it back in /dev/sda7 (ubuntu location)....should it be in /dev/sda? or /dev/sda3 (efi)?

Thanks for the help from both of you :D

---

### Post by shadowspectre on 2012-11-27
Well, it did create another entry ```
Windows Boot UEFI bootx64.efi
```

Here are the error messages:

Windows EUFI Loader
```
[CODE]/EndEntire
file path:  /ACPI(a0342d0, 0)/PCI(2, 1f) UnknownMessaging(12)/HD/3,363800, 82000, e00f17ce96589e4f, a9, 5d)/File(\EFI\Microsoft\Boot)/(File(bootmgfwefi.bkp)/EndEntire
error: cannot load image
```

Windows Boot UEFI bootx64.efi
```
/EndEntire
file path: /ACPI(a0341d0, 0)/PCI(2, 1f)/UnknownMessaging(12/HD(3,363800,8200,e00f17ce96589e4f, a9, 58)/File(\EFI\Boot)/File(bootx64.eti)/EndEntire
error: cannot load image
```

Windows UEFI Recovery
/EndEntire
file path: /ACPI(a0341d0)PCI(2, 1f) UnknownMessaging(12)HD (1, 800, 82000, 26d4d12a461c5041, b9, 10)/File (\EFI\Microsoft\Boot)/File(bootmgfw.efi.bkp)/EndEntire
error: cannot load image[/CODE]

Windows Boot UEFI bootx64.efi Recovery
```
/EndEntire
file path: /ACPI (20341do0, 0)/PCI (2,1f) /UnknownMessaging(12)/HD (1,800,82000, 26a4d12a461c5041, b9, 10)/FIle(\EFI\Boot)/File(bootx64.efi)/EndEntire
error: cannot load image
```

I hope I didnt make too many errors copying this.  I had to handwrite it, and then type my handwriting, so some spaces maybe be where they shouldnt be, and vice-versa.  Hopefully, it might help get an idea of the problem.  If you need a more accurate log, how do I go about finding that? Does Grub keep logs of these kind of errors?

---

### Post by YannBuntu on 2012-11-27
So now can you boot Ubuntu UEFI from the GRUB menu, but all the Windows UEFI entries fail.

1) please look into your BIOS, especially the "boot order" screen, and tell us if you see a Windows entry. If yes, tell us if you can boot into Windows via this entry.

2) please run Boot-Repair --> Advanced options --> untick the "Backup and rename EFI files" --> tick the "Restore EFI backups" --> Apply.
Indicate the new URL that will appear.
Reboot, try the "Windows UEFI loader" entry, and tell us what you observe.

---

### Post by shadowspectre on 2012-11-27
I went through the BIOS.  No Windows in the Boot Order.  However, I did find the settings for Secureboot.

I turned it off.
Restarted....and was able to choose Windows.

However, I restarted again, and now it only goes to Windows.  Grub no longer loaded.

I restarted, went into the BIOS and re-enabled SecureBoot.  However, it did not bring Grub back.

I am now back in linux using a Live CD.

Should I follow the instructions in your post now? Or disable Secure-Boot and use a live cd to use Boot-Repair?  Or should I try to play with any advanced SecureBoot settings to force it to load Grub?

---

### Post by shadowspectre on 2012-11-27
And, I believe there is nothing labeled Ubuntu UEFI in grub (when it was up).

It was simply Ubuntu
below was something along the lines of "advanced ubuntu settings".
Since Ubuntu did boot when Grub was up, and my BIOS is set to UEFI, I believe it is still UEFI Ubuntu..just not labeled as such in Grub; if that's relevant for you at all

---

### Post by oldfred on 2012-11-27
There should be two different menus.

One is booting into UEFI setting. 
From UEFI you should see both windows & ubuntu as boot options. Which ever you choose will be the default for rebooting. If you choose Windows it will just boot Windows.
Then from the ubuntu option you get the grub menu which has Ubuntu, Windows, advanced options, etc. 
So if UEFI is defaulting to ubuntu, grub should get you the option to dual boot from its menu.

---

### Post by shadowspectre on 2012-11-27
After disabling the SecureBoot...there is no bootloader (Grub) menu at all. Re-enabling SecureBoot did not bring it back.
 
However, if SecureBoot is the problem for this dual-boot issue...would it be wise to disable it and use boot-repair? Or should we try to fix this problem while keeping Secure Boot enabled?

---

### Post by YannBuntu on 2012-11-27
As Windows currently can boot when SecureBoot disabled, I would leave the SecureBoot disabled, then run the Recommended Repair. Then please indicate the new URL that will appear, reboot and tell if you can see the GRUB menu.

---

### Post by shadowspectre on 2012-11-27
[HTML]http://paste.ubuntu.com/1392987/[/HTML]

Everything works now! Thank you YannBuntu and oldfred.

However, would it benefit you and your work on boot-repair if I try the quoted instructions with SecureBoot enabled?
> 
please run Boot-Repair --> Advanced options --> untick the "Backup  and rename EFI files" --> tick the "Restore EFI backups" -->  Apply.And, just out of curiosity, what is the purpose of SecureBoot?

---

### Post by oldfred on 2012-11-27
Secure boot is part of the UEFI standard to make it difficult for a user to install any other operating system. That is intended to reduce the security issue of anyone with physical access can boot with another system and copy your data.

In actuality it is Windows continuing to make it difficult to install any other system. It also makes it difficult to repair if you have to boot from another device which even if just Windows you may have to do.

       [http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)
[http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms](http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms)

---

### Post by YannBuntu on 2012-11-27
> **shadowspectre said:**
> [HTML]http://paste.ubuntu.com/1392987/[/HTML]

Everything works now! Thank you YannBuntu and oldfred.

Good job. So now you are in a "normal" situation.
Do both "Windows UEFI loader" and "Windows Boot UEFI bootx64.efi.bkp" entries boot Windows successfully?

> **shadowspectre said:**
> would it benefit you and your work on boot-repair if I try(..)

Thanks for proposing your help. I will ask you several tests that will help us understand UEFI and SecureBoot better, but please backup your documents first (better cloning your entire disk via CloneZilla), because this may break something if you do a mistake or if there is a bug I am not aware of.

First I will ask you this little test:
1) leave SecureBoot disabled (don't change anything in your BIOS)
2) from your installed Ubuntu, open a terminal and type:

```
sudo mv /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/ubuntu/shimx64.efi.old
```
Press Enter, type your password (nothing will appear). Then type:
```
ls /boot/efi/EFI/ubuntu | grep shim
```
The output should be "shimx64.efi.old".

3) reboot the pc
4) tell me if you can still observe the "normal" situation (GRUB menu appears and let you boot successfully both Windows and Ubuntu)

5) **if yes**, stop here.
6) **if not** (eg if you can't boot Ubuntu any more), please boot on a Ubuntu liveCD, and type:
```
sudo mount /dev/sda3 /mnt
sudo mv /mnt/EFI/ubuntu/shimx64.efi.old /mnt/EFI/ubuntu/shimx64.efi
```
then reboot the pc. This should revert the situation to original.

> **shadowspectre said:**
> And, just out of curiosity, what is the purpose of SecureBoot?

See [http://en.wikipedia.org/wiki/Uefi#Secure_boot_2](http://en.wikipedia.org/wiki/Uefi#Secure_boot_2)

---

### Post by shadowspectre on 2012-11-27
I figured it was Windows monopolizing, but I was hoping, it would be beneficial in some way to the rest of us.  And, wouldn't a live cd/usb, or hardware designed to copy data from one harddrive to another (I would assume said harddware would have software capable of ignoring the eufi partitons or something) negate "making it more difficult to install another operating system?

Did anything useful come out of the UEFI movement for anyone else besides Windows?  And, any news on a linux tablet; I remember hearing Canonical had something planned for that, based on it's Unity focus.

---

### Post by YannBuntu on 2012-11-27
we posted at the same time, please see above.

---

### Post by shadowspectre on 2012-11-27
I have learned this week that I can 100% reset this thing to factory settings (not as easy as my old Toshiba...since Vaio assumes u'd never touch the partitions...SecureBoot have a reason for that? hahaaha)...so I'm 110% willing to help...not that that would've changed regardless, hahahaha.  Okay,  going to back up the important stuff, and test all of that out for you.

---

### Post by shadowspectre on 2012-11-27
"Windows UEFI loader" and "Windows Boot UEFI bootx64.efi.bkp" both boot Windows properly.

I did the commands, everything worked fine.  So I have stopped at step 5 (didn't do step 6).

---

### Post by YannBuntu on 2012-11-27
ok, thanks. 
@OldFred: Conclusion of this first test: the "shim" files remain in the ESP after removing the shim packages, and they are not used when SecureBoot is disabled.

@shadowspectre: now let's try a 2nd test:

1) boot into your installed Ubuntu, and backup on a USB key the content of you /boot/efi folder. Make a ZIP file of it and attach it to your reply (or send it to me by email yannubuntu ATT gmail DOTT com)
2) enable SecureBoot in your firmware.
3) boot on your 12.10 CD, choose "Try Ubuntu", install and run Boot-Repair --> Recommended Repair.
4) Indicate the new URL that will appear.
5) Reboot the pc, the GRUB menu should appear. Please indicate what you observe when you select the "Windows UEFI loader" entry. Same for the "Windows Boot UEFI bootx64.efi.bkp" entry. And the "Ubuntu" entry.
6) **if one of the 2 Windows entries fail**, please run Boot-Repair --> Advanced options --> untick the "Backup and rename EFI files" --> tick the "Restore EFI backups" --> Apply. Indicate the new URL that will appear. Reboot and tell us what you observe when selecting the Windows entries.
7) **if still not good**, you can revert to "normal" situation by disabling SecureBoot, then running the Recommended Repair.

---

### Post by shadowspectre on 2012-11-27
I will be unavailable for a few hours.  After that, I will jump right back into this.  Sorry for the delay.  One thing, the zip file is almost 25mb...this exceeds the forum's limit....as well as I believe my email's limit. Is there another way to send it?

---

### Post by YannBuntu on 2012-11-27
Then please just attach a ZIP of the following 3 files:
/EFI/Boot/bootx64.efi.bkp 
/EFI/ubuntu/grubx64.efi
/EFI/Microsoft/Boot/bootmgfw.efi.bkp

(but keep a backup of your 25MB ZIP)

---

### Post by shadowspectre on 2012-11-28
Turned SafeBoot on.  Used the Live CD to go through the Boot-Repair dance again, and this time...everything works.  I didnt check what Grub 2 had put in, only what you had requested!

Did you solve the mystery of SecureBoot and UEFI?

[HTML]paste.ubuntu.com/1394309[/HTML]

---

### Post by oldfred on 2012-11-28
Somewhat unrelated question.

You can only have one efi partition. In gparted it has the boot flag or in gdisk it shows gpt partition type ef00.

But you have efi boot files in two partitions and the sda1 looks like a vendor recovery (SONYSYS). Do you then have UEFI, or other instructions (or Sony hides) a way to change boot flag to make sda1 the efi boot partition just to boot into the recovery partition?

---

### Post by YannBuntu on 2012-11-28
Bad news: in your last log i see
```
SecureBoot disabled.
```

Please don't change your BIOS settings, and boot into your installed Ubuntu, then install and run Boot-Repair --> "Create BootInfo" from there, and tell us the new URL that will appear.

---

### Post by shadowspectre on 2012-11-28
There's an Assist Button which then gives you the ability to boot into that partition, I would assume it is hardcoded into some of the hardware....I have a feeling if I move that partition...the software would fail to work.


And YannBuntu....u just ruined my morning -,-   Hahaha

[http://paste.ubuntu.com/1395800/](http://paste.ubuntu.com/1395800/)

---

### Post by YannBuntu on 2012-11-29
> **shadowspectre said:**
> There's an Assist Button which then gives you the ability to boot into that partition

Good to know, thanks. Have you tried to boot into it (then cancelled) ? 
- if not, don't do it (because it may break access to Ubuntu)
- if yes, Boot-Repair has also added 2 entries linked to your Recovery partition: "Windows UEFI recovery" and "Windows Boot UEFI bootx64.efi.bkp recovery", they should have the same effect.


> **shadowspectre said:**
> And YannBuntu....u just ruined my morning -,-   Hahaha

Sorry i broke your dream, haha ;) 

> **shadowspectre said:**
> [http://paste.ubuntu.com/1395800/](http://paste.ubuntu.com/1395800/)

This log also shows "SecureBoot disabled." (normal because it was also disabled in live-session).

ok. So now the challenge is to setup your UEFI firmware (~BIOS) so that when you use Boot-Repair--> Create BootInfo from your liveCD it shows "SecureBoot enabled". Good luck :) (if you don't find it, please show us pictures of your UEFI menus)

---

### Post by shadowspectre on 2012-11-29
Email inbound with the requested pics.

According to my Bios, looking at the 3rd pic, "forcing SecureBoot" disabled, however that is not an editable option, only a status.

> So now the challenge is to setup your UEFI firmware (~BIOS) so that when  you use Boot-Repair--> Create BootInfo from your liveCD it shows  "SecureBoot enabled". 

Ummm....would it not be better to have that when I run Linux off my harddrive? Can we just hope for a second that I wont have to load an Ubuntu Live CD?....startup time for it isnt...pretty....hahahaha.

And just outta curiousity, what are we trying to accomplish here?  Glad I can help, and more than willing to, but i'm not sure what your goal is.....SecureBoot enabled while being able to boot into Ubuntu/Windows/Mac/BSD through Grub?

---

### Post by YannBuntu on 2012-11-29
> **shadowspectre said:**
> Email inbound with the requested pics.

Thanks. I resized and attached them to this post so that other helpers can see.

> **shadowspectre said:**
> what are we trying to accomplish here?

Final goal is to be able to boot all your systems (Ubuntu & Windows) in SecureBoot mode. For this, you need first to enable SecureBoot in your firmware, then convert GRUB&Ubuntu to SecureBoot mode via Boot-Repair.

I am not sure how to enable SecureBoot in your firmware. Maybe "Restore factory defaults" would be a good start, but let's wait suggestions from other helpers.

---

### Post by shadowspectre on 2012-11-29
okay :) I have the Live CD ready, so on your "Go!".

And since I have semi-free time....anything else you need me to test/try for you? beyond just this little project...

---

### Post by oldfred on 2012-11-29
First screen looks like it is enabled. And it shows the two options that Microsoft required be available.

> Mandatory. On non-ARM systems, the platform MUST implement the ability for a physically
present user to select between two Secure Boot modes in firmware setup: "Custom" and
"Standard". Custom Mode allows for more flexibility as specified in the following:
    

The other screen looks like it is just to allow turning off all the secure boot settings with one option. Did not know there were all those settings.

---

### Post by YannBuntu on 2012-11-29
**@shadowspectre:** Thanks for proposing.
Here are some others things you can do:
- when you select 'Windows 8 (loader) (on /dev/sda3)' in the GRUB menu, does it boot Windows8 successfully?
- it would be nice if you could create your Launchpad.net account (if you haven't yet), this will be useful for your future contributions to Ubuntu and other FOSS projects.
- you can login to your Launchpad account and help translating Boot-Repair, here: [https://translations.launchpad.net/boot-repair/trunk](https://translations.launchpad.net/boot-repair/trunk)

**@oldfred:** if SecureBoot is indeed enabled, then i bet there is a bug in the Ubuntu installer (it does not use the right method to detect enabled SecureBoot)
Else, maybe we need the "Enforcing SecureBoot" option ?

---

### Post by shadowspectre on 2012-11-29
It does not work.  Same error as before.

Okay, I will get that account set up NLT tomorrow :)

How do we force secureboot? There is no option in my bios...only a status of if it is forced.

---

### Post by YannBuntu on 2012-11-29
> **shadowspectre said:**
> It does not work.  Same error as before.

Ok, then you can login to your Launchpad account, then go here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Click "Does this bug affect you?" --> Yes
> **shadowspectre said:**
> How do we force secureboot? There is no option in my bios...only a status of if it is forced.

ok.
I persist to think that your SecureBoot is NOT really enabled, although your firmware states "Enabled", because
shimx64.efi has been disabled (renamed to .efi.old) , so AFAIK the "signed" chain is broken, so if SecureBoot was enabled in the firmware, GRUB menu should not appear.

Please could you boot into your installed Ubuntu, and send me your current:
/EFI/Microsoft/Boot/bootmgfw.efi.bkp
/EFI/Boot/bootx64.efi
/EFI/Boot/bootx64.efi.bkp
/EFI/ubuntu/grubx64.efi
files?

also please send me the /EFI/Boot/bootx64.efi.bkp file of your previous ZIP.

---

### Post by shadowspectre on 2012-12-01
Done as requested.  Hopefully it will help.

---

### Post by harlequin_ on 2013-03-21
Hi,

Can you please provide a complete list of actions to achieve Win 8 - Ubuntu 12.10 dual boot on a Sony laptop? I followed this thread from start to end but it is fragmented which makes it not so easy to put in practice.

I've recently got a Sony Vaio S 15 laptop, Win 8 preinstalled (UEFI enabled). I'm not a new linux user, but I've spent the last 3 full nights trying to achieve a proper dual boot of Win 8 and Ubuntu 12.10. I tried a lot of suggestions, some of which are:

- Creating Ubuntu partitions from inside Win 8 (one for swap, one for the root and one for /home), and installing using the Live Usb (SecureBoot & Fast StartUp disabled).
- Creating Ubuntu partitions while installing ubuntu by choosing "Something else" (SecureBoot disabled)
- And finally installing by selecting "Install Ubuntu alongside Windows"

I failed each and every time. I am totally frustrated, and cannot work on my new PC. The most common problem I had was that after the Ubuntu installation and restart, it would directly boot into Windows 8, without any Grub options and alike. In these cases I tried to fix things with Boot-repair, however it did not change anything. Only in one of my many tries, after Boot-repair usage, I could get the Grub OS-selection menu at start-up, but then it gave the error "error: can't find command 'drivemap'error: invalid EFI file path." which I could not fix. That's how I ended up in this thread, but now I do not dare to follow it without a clear and complete list of instructions.

I am so very much frustrated. Please provide help in case you have time.

Best regards.

---

### Post by shadowspectre on 2013-03-21
Try it this simple way first, we can mess with partitioning later.
     Using the live CD, install ubuntu alongside windows 8. use default settings, dont add/create partitions yet.  Just see what happens
     Reboot
     Chances are, it didnt work.  Boot up the live CD, choose "try ubuntu"

open a terminal, copy and paste: 

     sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

press ENTER

and then copy and paste:

     sudo apt-get install -y boot-repair && (sudo boot-repair &)

Boot Repair should start, if not, you should be able to find the icon in your desktop environment or search for it.  Then run it and choose "recommended repair"  when it's finished, note the web address on a paper, reboot the pc.

You should have various options for booting now.  Try all of them dealing with windows 8, but usually the UEFI Windows 8 or something similar in name that works.  Just try them all and get back to us if it works or doesnt work.  

Sorry for long post, short on time.  Take care, good luck.

---

### Post by harlequin_ on 2013-03-21
Hi,

Thank you very much for the reply, greatly appreciated. Howeverwhen I read your message, I was doing my 4 (or 5th maybe) ubuntu installation, this time following another sort of tutorial. What I did was

1- Install a refresh Win 8 using Sony recovery area.
2- Disable Fast StartUp and SecureBoot.
3- Create some free space partition from within Win 8
4- Install Ubuntu 12.10 using advanced setup (created a primary efi partition of 250 MB, a root partition of 50 gb, a swap partition of 12 gb and a /home partition of about 400 gb).
5- Install Ubuntu 12.10
6- Restart

The computer again directly booted into Win 8. Then I again booted with Live USB and installed Boot-Repair. It as always welcomed me with a message saying "EFI detected. Please check options". I went into advanced options, GRUB location, and looked at what was ticked at "separate /boot/efi partition". It was sda3 (which is my Win 8 EFI partition -not the partition I created -sda7- during Ubuntu installation). I thought "ok.." and without changing anything pressed "appy" and followed the instructions. The process seemed like just fine, no errors etc. I rebooted and BAM. Again Windows 8 boot directly.

here's the first link to the summary: [http://paste.ubuntu.com/5635508/](http://paste.ubuntu.com/5635508/)

Then I booted with Live USB again, downloaded Boot-Repair and this time clicked "recommended repair". At the end it again said Boot successfully reapir. Gave me the link:

[http://paste.ubuntu.com/5635545/](http://paste.ubuntu.com/5635545/)

It also says at the end of its last message: "please do not forget to make your BIOS boot on sda3/EFI/ubuntu/shimx64.efi file!" I highly suspect that this is where I fail, because I don't know how to apply this recommendation.

When I did the restart I was again.. taken into Win 8 directly. I have no clue what to do anymore.

---

### Post by oldfred on 2013-03-21
You can only have one efi partition per drive. All systems create their own folder in that efi partition for their efi boot files.
Delete your sda7 or at least remove the boot flag with gparted so it is not seen as an efi partition.

Since the efi partition is like many MBR's you have to go into your UEFI menu, not Windows and choose what boot loader to use. I think it really will just say ubuntu as that is the folder name, not the detail of the efi files in the folder.

It looks like Boot-Repair found a lot of efi files that you may want to boot like Windows in the efi partition but other efi files in the recovery partition. Also grub has a bug and does not create correct chain entries yet.

       grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by harlequin_ on 2013-03-21
Hi, 
Thank you for trying to help. I deleted the sda7 partition, and restarted. It again booted into Win8.
I am sorry but there is *no* place in the Sony UEFI menu where you can choose for a boot loader.

After I deleted sda7, I restarted and using Live USB. I entered in the terminal, "sudo os-prober", and the output is
/dev/sda2:Windows Recovery Environment (loader):Windows:chain
/dev/sda3:Windows 8 (loader):Windows1:chain
/dev/sda8:Ubuntu 12.10 (12.10): Ubuntu:linux

---

### Post by oldfred on 2013-03-21
os-prober does not work with UEFI installs, you have to use Boot-Repair or manually create boot entries. see post #38 above.

---

### Post by harlequin_ on 2013-03-22
Hi, I finally got it fixed, but it was very short-lived..
First of all, boot-repair does not work for me. What I did was to follow this
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi/150640#150640](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi/150640#150640)
and this
[http://askubuntu.com/questions/159918/cant-dual-boot-ubuntu-12-04-and-windows-7-on-sony-vaio-s-15-2012](http://askubuntu.com/questions/159918/cant-dual-boot-ubuntu-12-04-and-windows-7-on-sony-vaio-s-15-2012)

and suggestions in both threads work. When I do the suggested changes, update-grub and reboot, I am welcomed by the GRUB screen and the Windows 8 entry I added is listed, and BOOTABLE. However after going into Windows successfully and then again rebooting, I cannot re-use the Windows 8 Grub menu item because it throws an error.

When I boot back into Ubuntu from Grub, I looks like  ALL CHANGES I HAVE DONE are gone in /EFI/Boot and /EFI/Microsoft/Boot. Even the .efi_BK backup files are gone. They are simply deleted. Now I cannot undo everything I did and login to Windows because every file I created is basically wiped out. I have no clue why and at this stage Google does not help. EDIT:When I replaced bootx64.efi and bootmgfw.efi from the recovery partition to /EFI/Boot and /EFI/Microsoft/Boot, grub menu disappeared and now I can login to Win. I think I'll return this computer.

[http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html](http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html)
[http://askubuntu.com/questions/91437/uefi-hardware-and-dual-booting-with-windows/130984#130984](http://askubuntu.com/questions/91437/uefi-hardware-and-dual-booting-with-windows/130984#130984)
[http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/)

Can somebody tell me how to prevent Win 8 (or maybe it's Sony Insyde) from resetting my changes in /EFI/Boot & /EFI/Microsoft/Boot?

---

### Post by oldfred on 2013-03-22
The manual changes suggested by askUbuntu are just the same changes Boot-Repair automates.

Do you have some setting in UEFI/BIOS or in Windows virus checker that is set to prevent changes to efi partition?

BIOS systems had these sometime:
 BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker

And some systems have virus software that prevented changing MBR in BIOS, so I would think new one's might do the same with efi partition.

---

### Post by harlequin_ on 2013-03-22
Hi oldfred, thanks for your answer. Later today I will check if pre-installed McAfee might be doing some nasty "fix" in /sda3/EFI/*. I think that I have no problem setting the dual boot disabled. I only did it once after I got the computer and then it never changed, it always stayed disabled.

Insyde H2O EFI bios does not have those menus/selections you mention. Tonight I'll again see what I can do. 5th night and I can swear that I do not do anything stupid or without understanding why I do it. It just does not happen.

---

### Post by harlequin_ on 2013-03-22
Hi oldfred, I have a quick question: Are you really sure that boot-repair does exactly the same things with what is suggested in those links? For instance [http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi/150640#150640](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi/150640#150640)

Does it indeed *replace* bootmgfw.efi with grubx64.efi or shimx64.efi? I do not think that it does this? I think it only adds it (shimx64.efi/grubx64.efi) to the list and prioritizes?
As far as I understand, the real nasty problem is that the firmware Sony uses does not respect the user input, but rather looks for the Windows 8 efi file that probably is hardcoded. I believe that is why boot-repair does not work in my case.

---

### Post by oldfred on 2013-03-22
You turn secure boot on, boot Boot-Repair in UEFI mode, and check the box that you have secure boot. Yann posted this in his mega-thread on Boot-Repair.

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.

 To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

---

### Post by harlequin_ on 2013-03-22
Could you please also tell me in what way to install Ubuntu. Does creating an unallocated partition from within Windows 8 is relevant, or can I do it while installing from Live USB? Would installing alongside Windows 8 just be enough? Or should I go into advanced options and choose sda3 (my EFI partition) for the bootloader to be installed as suggested somewhere else? ([www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/]("http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/") , > . The procedure is straightforward, except that you should be careful to install Grub in **/dev/sda3**.

---

### Post by oldfred on 2013-03-22
While many have not had issues using gparted or the installer to resize Windows we think it best to use Windows Disk tools to resize Windows. Windows has to do internal repairs after a resize, so best to do that before installing Ubuntu. And reboot a couple of times so it can run chkdsk and make other fixes. Never create partitions in Windows as it may convert to dynamic or LDM partitioning which does not work with Linux.

When resize is done during install sometimes then when booting Windows does not get to its repair from grub and has issues. Then you have to have the Windows repair flash drive, which no one ever makes before hand. 
You should have a liveCD or repairCD for the current version of every operating system installed. And good backups.

If you just want the default of / (root) & swap, then you can install Ubuntu into the unallocated space you created previously. And that works for most. But we often want to control sizes or have separate /home or data partitions. Then you have to use Something Else and manually create partitions, formats, and mounts.

With UEFI installs, grub2's boot loader is installed to the already exisiting efi partition. You can only have one efi partition per drive. The efi partition is not a /boot partition. But most desktops do not need a separate /boot partition anyway.
The efi partition is like the MBR, but now is more like many MBRs as you can have as many systems directly booting from the efi partition as you have installed. With MBR, you only could have one system booting.

Be sure to boot Ubuntu in UEFI mode. But a few computers have defective UEFI and will only let you install in BIOS mode. Boot-Repair can convert those installs to UEFI if required.
 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[URL="https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop"]https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop

[/URL] Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[URL="http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/"]http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/

      [/URL]
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    [URL="http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/"]
[/URL]

[URL="https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop"]
[/URL]

---

### Post by harlequin_ on 2013-03-22
Hi again,

oldfred, I followed your suggestions. Upon a fresh Windows 8 recovery, I allocated some free space from inside Windows 8, enabled Secure Boot and installed Ubuntu 12.10 alongside Windows 8.
When the installation finished and I restarted, it directly booted into Windows 8, without displaying a Grub screen.
Then I rebooted using the Live USB and installed boot-repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) , and ran it using the default advanced options, some of which were:
- Ticked SecureBoot and ticked Backup and rename EFI files

I believe it also purged and installed Grub. At the end of boot-repair I got the following message:

> An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/5638659/](http://paste.ubuntu.com/5638659/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 

Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].

Now I will try the same thing with SecureBoot disabled.

---

### Post by harlequin_ on 2013-03-22
I disabled the SecureBoot, booted with Live USB and used the Boot Repair again. This time I unticked "SecureBoot" under Grub options because I disabled it prior to my Live USB boot as I said. I ran the rest of the default advanced options, and I got this:

> An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/5638718/](http://paste.ubuntu.com/5638718/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 

Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].

Oh, I think I shouldn't forget to note that I also got the below terminal message towards the end of boot-repair run.

```
Creating config file /etc/default/grub with new version
cp: cannot create regular file `/boot/efi/EFI/ubuntu/grubx64.efi': Read-only file system
```

---

### Post by harlequin_ on 2013-03-22
SOLVED.

oldfred, thanks for all the help along the way. I appreciate the time you spent and also the effort. It is in a way funny, because your suggestion of enabling SecureBoot made BootRepair totally useless in terms of its accession to /sda3 (uefi partition), furthermore I could not do any changes manually with mounting it either (read only etc), but then, this also forced me to improvise and solve the problem :-).

Dear users, please do NOT follow or try to replicate any of the following.
As I noted, after I enabled SecureBoot and installed Ubuntu, I was totally unable to do anything on my EFI partition (/sda3), neither with BootRepair nor by the terminal. Therefore I disabled SecureBoot and booted into Windows 8 and deleted the Ubuntu partitions, and extended Windows'. Then I used Live USB to open Try Ubuntu again and used Gparted to delete my EFI partition (***which I had backed up when I first opened my fresh Windows 8 installation at the very beginning of all***), and allocated some space for an Ubuntu partition. Then I installed Ubuntu by manual partitioning (also formatted the deleted EFI partition) and after the installation when I restarted I was welcomed with a beautiful Grub screen (of course lacking a Windows entry). Then I booted Ubuntu and mounted my EFI partition, and configured in such a way by using my EFI partition backup that it would resemble a Windows 8-and-then-Ubuntu installation. Then I followed the instructions [here]("http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html"), chainloaded the backed-up Windows 8 .efi, updated Grub and then was able to dual boot Ubuntu 12.10 and Windows 8. Yay!

---

### Post by oldfred on 2013-03-23
Glad you worked it out.

Supposedly Ubuntu should totally work with Windows and secure boot. It is using the same Microsoft UEFI key. But some vendors modify UEFI to only boot Windows by filename. 
We normally suggest secure boot off, but Windows may only boot with it on. Then Boot-Repair usually has to do some file renaming. 

There also is a bug report on the locked efi partition. We are not sure how this is occurring, but it just may be corruption in the image used. Your fix of backing up, deleting, recreating & restoring is the main work around in the bug report.

The entire UEFI dual boot is not very easy and requires each user to do a lot to make it work. And each vendor does it just enough different that there is not just one procedure. Only a couple of vendors (or maybe even models within a vendor) have seemed to work reasonably well.

---

