---
title: "Can´t install Ubuntu alongside Windows 7 -already tried several suggestions"
date: 2015-04-13
forum: Installation &amp; Upgrades
---

### Post by Santiago_Slaby on 2015-04-13
[COLOR=#111111][FONT=Ubuntu]I have this notebook:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Notebook Kelyx Pcw20 Amd C70 Dual Core 14 1tb 8gb[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I can´t install Ubuntu alongside Windows 7.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Before I started I shrank the C: drive in order to have some unallocated space. When I run the Ubuntu installer, the "Install alongside Windows 7" option does not appear. After trying some commands to get Ubuntu to recognize the unallocated space, the installer remains the same. I tried "Something else" and made two partitions from the unallocated space (a bigger one for the OS, and one smaller for the swap).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Everything goes well, then when I restart, can´t boot windows (but is still there), from BIOS I just can select the HD and not much more, always with the same result. I followed the tutorial to update Grub. And then, disaster unleashed. When I restarted the notebook there was some nonsense text screaming about kernel.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I repaired the windows boot with the windows DVD. And formatted the Ubuntu partition and placed it back to windows.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]How can I install Ubuntu from the installer without deleting windows 7? (I think that´s the best way)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][B]The windows partition was properly shrunk with Disk Management and there´s plenty space. And yes, it´s a basic disc.

Here´s a print screen of the boot info - [s29.postimg.org/nz84i0mcn/boot_info_sl.jpg]("http://s29.postimg.org/nz84i0mcn/boot_info_sl.jpg")[/B][/FONT][/COLOR]

---

### Post by oldfred on 2015-04-13
When you have Ubuntu installed and have issues, you need to use live installer and then install Boot-Repair. Sometimes it can fix it, but if you post the Summary report then someone can suggest what to repair.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Post this if Ubuntu is not installed, from terminal in live installer:
sudo parted -l


 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by Santiago_Slaby on 2015-04-14
So, you´re suggesting me to install again, choose "something else" and make the 3 ubuntu partitions myself?

I thought that, after all the issues I had, there was a reason the "install along windows 7" that was good enough...

---

### Post by Santiago_Slaby on 2015-04-14
Please, I need some guidance about my particular situation, I already read very different ways and I don´t know which is the appropiate...

---

### Post by Tom_Daly on 2015-04-14
I'm right here with you.  I have a new machine and Ubuntu does not see Win7 exists. "something else" doesn't even see the Win7 partitions but sees it as a bare drive.  I've tried gparted, etc.  I cannot even get Ubuntu to boot if I allow it to wipe the drive.  Win7 installer sees the GPT partitions but cannot use them.  I'm digging and digging but so far your problem is the most similar to mine and you seem to making the same headway I am; nil.  :(

---

### Post by Bashing-om on 2015-04-14
Santiago_Slaby; && Tom_Daly; Hello ....

What is a possibility is that Windows is using up the alotment of 4 primary partitions on the hard drive.
Let's check that.
From the liveDVD(USB) -> try ubuntu mode -> terminal:
Post back the outputs - between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT][INDENT]good thing to know
[/INDENT][/INDENT]

---

### Post by Santiago_Slaby on 2015-04-14
Hi Tom! Glad I have company to whine with ;)

Hi Bashing-om

The Terminal reported two partitions, the 630 gb Windows and 100 mb reserved for system.
It didn´t recognize the unallocated space I reserved for the future Ubuntu installation.
Seems I´m doing fine. What´s next Bashing-om?

Thanks!

---

### Post by Bashing-om on 2015-04-14
Santiago_Slaby; Yeh ;

Seems you are doing fine.
What I would do is fire up GParted from the liveDVD and make up the partitions for 'buntu there. In the install stage point the installer to these partitions using the "something else" install option.

Might be good to show us a screen shot from GParted of the drive as it is presently, for additional advise before proceeding.


[INDENT][INDENT]should workie great
[/INDENT][/INDENT]

---

### Post by Santiago_Slaby on 2015-04-30
Hi Bashing-om, I apologize for having not replied the past couple of weeks, I changed my job and school went a bit overboard. I´ll be giving you news at this particular predicament, sometime soon.

---

### Post by Santiago_Slaby on 2015-04-30
[[img]http://s24.postimg.org/v23hxwech/Screenshot_from_2015_04_30_01_19_20.jpg[/img]](http://postimg.org/image/v23hxwech/)

---

### Post by oldfred on 2015-04-30
While you should be able to use the auto install option, with Windows 8 and it always on hibernation the installer would delete Windows if it did not show its partitions. Then the only safe way was Something Else and manual partitioning. But make sure you have hibernation off in Windows 7.

You have Windows 7 and available primary partition which always used to work. But still safer to manually partition. If you use Windows to shrink Windows some more and reboot immediately so it can run chkdsk, then you can manually in advance create a shared data partition with NTFS format. You cannot do that during install. The advantage of a shared data partition is then you can set the Windows system partition as read only and avoid the potential of issues in Windows.

And with manual install, you also can have a separate /home if desired. If you use shared data a lot you may not need the separate /home. 

Links to example installs with Something else in my post above.

---

### Post by Bashing-om on 2015-04-30
Santiago_Slaby; Hi !

+5 ^^ 

[INDENT][INDENT]prior prudent planning preventing pi** poor performance
[/INDENT][/INDENT]

---

### Post by Santiago_Slaby on 2015-04-30
Hi Bashing-om! It´s been a while ;)
Hello Oldfred! I´ll follow your "something else" guide and if I get stuck I´ll let you know.

Thank you all for your patience.

---

### Post by Santiago_Slaby on 2015-04-30
It would help a lot if your tutorial was made specifically for someone who wants to dual boot windows 7 and ubuntu.

---

### Post by Santiago_Slaby on 2015-04-30
So, Oldfred, should I first make the NTFS partition for Ubuntu from Windows?

---

### Post by Santiago_Slaby on 2015-04-30
I´m sorry, your tutorial is way too wide for me. I need something more specific.

---

### Post by oldfred on 2015-04-30
You can create the NTFS from either Windows or gparted.

Did you look at the step by step?
It shows every screen you see and what to do?
What are you missing in  the way of info.

---

### Post by Santiago_Slaby on 2015-04-30
I´m still not sure about creating the /root /swap and /home. And I can´t find the step by step from the tutorial pretty clear.
As I stated in the beginning of the post, once I created those and it would only boot Ubuntu. So then I followed the advice of updating Grub2 and the boot was ruined completely, so I had to place the windows dvd and repair the system.

---

### Post by Santiago_Slaby on 2015-05-01
At the tutorial, at the example there are two hard disks with two different versions of Ubuntu, makes everything so confussing... I need something closer to my situation...

---

### Post by Santiago_Slaby on 2015-05-01
This example would be the closest to my situation?

"[COLOR=#000000][FONT=Verdana]Here's the ASUS VivoBook example from earlier. More complicated, but still very much doable. We begin with a very large 450GB NTFS partition /dev/sda4. We have to [/FONT][/COLOR][COLOR=#FF0000][FONT=Verdana]resize[/FONT][/COLOR][COLOR=#000000][FONT=Verdana] it, by say about 100GB, and then in the free, unallocated space, we create three partitions for the Ubuntu installation. Namely, we have a 25GB root (/), that would be /dev/sda7, then a swap partition measuring 4GB in length, and that would be /dev/sda8. Finally, there's the home (/home) partition, and it goes into the remaining 73GB /dev/sda9. You will see this again, almost ad nauseam, in the dedicated dual-boot tutorial."

Sorry, I´m still kind of lost[/FONT][/COLOR]

---

### Post by Santiago_Slaby on 2015-05-01
Well, I achieved to install Ubuntu in the NTFS partition, making with the installer the root, home and swap in the process. The C: drive with Windows is still untouched, but now it only boots un Ubuntu, as I expected -and as happened before-.
What do I do now?

---

### Post by oldfred on 2015-05-01
First run this from terminal:
sudo update-grub

If that does not show it added a Windows boot entry to grub menu (at bottom) then install Boot-Repair and run the Summary Report. Post the link it gives so we can see what the details are of your install.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Santiago_Slaby on 2015-05-01
I know you noticed how noob am I, so I already ran out of shame. 
Grub clearly recognized the presence of windows 7. 
Now, how do I operate Grub? Should it start before Ubuntu runs? it is an executable program inside Ubuntu?

---

### Post by Santiago_Slaby on 2015-05-01
I achieved it. Thank you.



Thank you.




Thank you.

---

### Post by oldfred on 2015-05-01
Grub is both a boot manager or menu system and boot loader for Linux and other systems.

Parts of grub are in many places. 
All BIOS based systems start with BIOS checking hardware, then loading MBR which has just a bit of boot code. Then grub has its menu and more code in the Ubuntu partition which is used to load kernel and start Ubuntu. Or chain load back to Windows so it can use its boot code to start up.

---

### Post by Santiago_Slaby on 2015-05-01
One more unexpected thing. Everything WAS fine. Used both OS with no real changes, just test them.
I started my notebook with Ubuntu, asks my password, I place it, and then... the background - wallpaper remains without any icons. The mouse pointer reacts normally. I can even create new folders. But nothing really starts. 
What´s going on!?

---

### Post by Santiago_Slaby on 2015-05-01
Should I make a new thread?

---

### Post by oldfred on 2015-05-01
It seems it is past boot issues, so yes a new thread. 
In that thread mention what video card/chip you have. It sound like a video issue, but could be some other driver also.

---

