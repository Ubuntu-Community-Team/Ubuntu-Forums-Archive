---
title: "Cannot install Ubuntu 13.04 using a USB stick"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by i2000s on 2013-07-05
Hi,

I cannot install Ubuntu 13.06 desktop release using a USB stick. When I booted my computer with the USB stick, I got a black screen with a flashing cursor. It did not even show any options! I am running on a Thinkpad X200 tablet computer. The USB stick was created using the Universal USB Installer 1.9.3.6 released on Jun 26. Any thought? Thanks.

Bests,
Qi

PS: Solved! See last page.

---

### Post by i2000s on 2013-07-05
I checked the MD5SUM stuff already. It is correct.

---

### Post by sudodus on 2013-07-05
- Try other methods to make the USB boot drive. See this link

[https://help.ubuntu.com/community/In...n/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

My personal favourlte is to clone the Ubuntu iso file to the USB stick with dd (and some guiding help from a script), but there are several reliable methods, that you find in the link. Maybe Unetbootin would be my second choice, or first choice, if directly from Windows.

---

### Post by i2000s on 2013-07-05
I am trying Unetbootin. This software was very hard to download due to my slow internet connection. The download failed many times until the last time a minute ago... I am running on a Win 7 OS to make the bootable USB stick. The computer has an integrated Intel graphic card. I will report the result shortly.

---

### Post by sudodus on 2013-07-05
- I think Ubuntu should work with that computer. If Ubuntu will be slow you can use another flavour with a lighter desktop environment

for example Xubuntu with XFCE.

You may have better luck with the long time support version 12.04 LTS if it is a driver issue.

---

### Post by i2000s on 2013-07-05
Ok, I did Tried UNetBootin to remake the bootable USB stick. Turns out, it doesn't work. The same black screen showed up after reboot, the same flashing cursor lead me nowhere...

---

### Post by i2000s on 2013-07-05
Ok, I did trie UNetBootin to remake the bootable USB stick. Turns out, it doesn't work. The same black screen showed up after reboot, the same flashing cursor lead me nowhere...

My Thinkpad does not have any DVD/CD reader. USB stick is the best hope for me. So, please help! Thanks in advance.

---

### Post by sudodus on 2013-07-05
- Will you get any output text at all (before the flashing cursor)? By any of the methods (Unetbootin or Universal USB Installer)? 

- Are you sure, that the computer tries to boot from the USB drive (and not from some other device)?

- Can you test the USB drive, if it can boot another computer?

- Try with some boot options (start with one at a time, then maybe more than one). See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You can try with the boot option 'text' (without quotes). If there is a problem with the graphics, text should work.

- As I wrote before: "You may have better luck with the long time support version 12.04 LTS if it is a driver issue." And if you have a slow connection, I suggest you use a torrent to get the iso file.

---

### Post by i2000s on 2013-07-05
1. I am sure the computer is booting through the USB stick. When I pulled the USB stick out, it showed something like "booting operation system error" and then jump to Windows startup menu.
2. I don't know what is the message before the flashing cursor. There is a fast jumping screen before the flashing cursor. It was so fast that I cannot read.
3. I used this USB stick to install Ubuntu 10.10 to my X61 tablet before. So, the hardware should be fine.
4. I have tried press F1-F12, and also ctrl+Alt+F* to try to switch to text mode. Nothing happened. No response, except when I tried some random key, the computer started to beep after my pressing the key. I guess nothing was read from the USB stick, and hence I cannot see any "option". 

I am downloading Ubuntu 12.04 now. It may take a while. Going to sleep now... Thanks for  your prompt response!

---

### Post by i2000s on 2013-07-05
I tried Ubuntu 12.04 by going through the exact process I used for 13.04, but no smoke. When I made the USB stick using UNetbootin, but I did not format it--just overwrite it. Now, I have no idea what is the problem. I may try my USB stick on other computers, if I have a chance.

---

### Post by sudodus on 2013-07-05
Yes try the stick on another computer! You should delete all the files before running Unetbootin again (but I don't know how important it is with two so similar installations as 13.04 and 12.04). By the way, how was the USB drive formatted? I think Unetbootin wants a partition with FAT32, not a file system without a partition.

But there are USB drives, that work well as storage devices, but do not work as boot devices. What USB drive is it (brand, model and size)?

-o-

Next try some other boot options.

---

### Post by ubfan1 on 2013-07-05
If you wait at the flashing cursor for 5 min, do any messages ever show up?  Like "Media not found.../dev/sdb"?

---

### Post by i2000s on 2013-07-05
Hah, I finally found the problem! I didn't format my USB stick into proper USB-HDD format. So, I downloaded a software called BOOTIC and reformat my USB stick into the correct FAT32 format, and then everything works. 

Now, here comes a new problem:
I logged in Ubuntu using the "try Ubuntu without installing" option. When I clicked the "Install Ubuntu 12.04 LTS" button, I couldn't find the "Install alongside Windows 7" option. All I have is erasing the whole disc to install Ubuntu, or "Something else". In the "Something else" option, I only see the "/dev/sda" device which is my hard drive with Windows 7, but I cannot select any partition to install it. I always warning me that this installation will erase the all disc or something like that. In fact, I have left over 20G free space (unformated) for this installation. But I cannot see it.

What should I do now? Thanks.

I am going to restart my computer and see if I can find any change with a direct installation option chosen at the beginning...

---

### Post by i2000s on 2013-07-05
Hah, I finally found the problem! I didn't format my USB stick into proper USB-HDD format. So, I downloaded a software called BOOTIC and reformat my USB stick into the correct FAT32 format, and then everything works. 

Now, here comes a new problem:
I logged in Ubuntu using the "try Ubuntu without installing" option. When I clicked the "Install Ubuntu 12.04 LTS" button, I couldn't find the "Install alongside Windows 7" option. All I have is erasing the whole disc to install Ubuntu, or "Something else". In the "Something else" option, I only see the "/dev/sda" device which is my hard drive with Windows 7, but I cannot select any partition to install it. I always warning me that this installation will erase the all disc or something like that. In fact, I have left over 20G free space (unformated) for this installation. But I cannot see it.

What should I do now? Thanks.

I am going to restart my computer and see if I can find any change with a direct installation option chosen at the beginning...

---

### Post by sudodus on 2013-07-05
Congratulations, that the booting works now :KS

I suggest that you inspect the drive /dev/sda with ***gparted*** (it comes with the install iso, so you can run it from the live USB drive).

If you cannot see the free 20 GB, you might have created dynamic partitions with Windows. That is a proprietary partitioning scheme, and it cannot be managed by linux. So you need to change it to normal msdos partitioning (which is good unless you have UEFI, which needs gpt).

But remember to backup

1. your personal data
2. Windows

before tampering with the partitioning.

---

### Post by i2000s on 2013-07-05
Thanks, sudodus. I tried the gparted inspection. It shows my hard drive/partition is unallocated. I can see all my windows partitions are mounted through the file management browser, anyways. Maybe this is a problem of my Momentus XT hard drive which is hybrid hard drive with 4G flash hidden partition in it. I am googling it for better solution. Will report shortly. 

BTW, I don't have any spare hard drive to backup my data. So, everything should be ensured. Lol :(

---

### Post by sudodus on 2013-07-05
You can at least backup your personal data to a cloud server, Ubuntu One, Cloudme, Dropbox, Google Drive ... (or to a DVD but it is not as safe, can easily be scratched). Because editing partitions and installing operating systems work most of the time, but sometimes the target drive is corrupted. And we never know when it is going to happen.

I think you found it. The problem is probably with the special driver of that hybrid drive. It might not exist for linux. But if it is well designed, maybe standard drivers work (and the special organizing to use the 4G flash will be done internallly).

---

### Post by i2000s on 2013-07-05
Found this:
[http://askubuntu.com/questions/141656/ubuntu-12-04-does-not-see-windows-already-install-on-my-computer-dual-installat](http://askubuntu.com/questions/141656/ubuntu-12-04-does-not-see-windows-already-install-on-my-computer-dual-installat)

Do you think I should follow that post? I will find a way to backup some important data from my hard drive. Thanks for your reminder.
PS: I tried, but it didn't work for me. So, I am checking my partition property in Windows 7...
It shows that all my partitions are "basic", nothing shows "dynamic". I have C, D, E, F, G plus a system reserved partition. Only two primary partitions are allocated. The unallocated free space of 20 G can be seen in my windows disc management browser.

---

### Post by i2000s on 2013-07-05
I posted the problem of installing Ubuntu in my disc in a seperated post: [http://ubuntuforums.org/showthread.php?t=2160168](http://ubuntuforums.org/showthread.php?t=2160168)

---

### Post by sudodus on 2013-07-06
In that link the reply is partly discussing raid. I have not used raid myself, but seen in many threads at these forums, that if a raid drive is reused, there may be fragments of the raid configuration, that disturbs gparted, when trying to make partitions. I don't know if raid is your problem, it might be. but I think it is probably that you might need a special driver for the Momentus XT hybrid drive.

If the Momentus XT drive is using raid, and the installed Windows depends on it, you cannot remove it and expect that Windows will continue working. It might be a better idea to install Ubuntu to another drive, for example an external drive (eSATA, USB3 or USB2). What kind of external drives could be connected to your Thinkpad?

---

### Post by i2000s on 2013-07-06
I can use another USB2 normal external HDD to install Ubuntu. In any cases, I would figure out how to make my hybrid Momentus XT HDD work, because I am ordering another Momentus XT 750G hard drive for my research works. I have also tried Fedora 19 for installation, which also failed to recognize my partitions in the Momentus XT HDD.

---

### Post by sudodus on 2013-07-06
I have no more idea how to do it, but it is certainly possible, particularly if you have Ubuntu on one drive and Windows on another one.

Good luck :-)

---

