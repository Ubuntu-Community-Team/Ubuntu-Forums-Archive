---
title: "Getting Grub2 repaired after installing Linux"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by irv on 2014-09-05
I finely took the plunge and Installed Pepperment 5 seeing it is a Ubuntu based Linux. Okay, I installed it on a Windows 8.1 laptop; an Asus Q500. What I did was shrink the HD and setup a partition to install Linux on. The Install went well but it rebooted into a black screen with a prompt where you could enter a few commands. I saw that the grub was not working.

So I booted into the BIOS, if that what you call it now. (Hate these new computers BIOS') I saw that it was set to boot into Pepperment so I changed it to boot into Windows again.

After seeing I could boot Windows again I booted the Live USB to repair the Grub2 menu. Now here is what I did.
First I made sure I mounted the Linux partition then went to a terminal and enter these commands:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair 
```

When I typed the command, apt-get install -y boot-repair it told me it could not find it. So when I typed boot-repair it just said, “command not found.”

This is the point I am at right now and am not sure where to go from here? The OS is installed all I need to do is get it to book. Any Ideas?
Thanks

---

### Post by fantab on 2014-09-05
check the output of the second command, 'sudo apt-get update' to see if there were any errors...

---

### Post by irv on 2014-09-05
Okay, I tried this after failing to fetch  [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)

I booted with an Ubuntu 14.04.1 USB which did the same thing as in the Peppermint USB. I looked at the URL and got the 404 Not Found error. Looks to be a bad URL.
I then installed the Synaptic package manager and ran it. I then went to Settings -> Repositories. Then "Other Software" tab, and select the line [http://ppa.launchpad.net/yannubuntu/boot-repair/u](http://ppa.launchpad.net/yannubuntu/boot-repair/u)... main and then click on the Edit button. In the new window that pops up change the distribution: field to "quantal" (without quotes). And did the same for the source entire.  Did the apt-get update and install boot-repair.
This time it ran but at the end of the repairing the grub I got this error:

> An error occurred during the repair. 

Please write on a paper the following URL: 
[http://paste.ubuntu.com/8260715/](http://paste.ubuntu.com/8260715/) 

In case you still experience boot problem, indicate this URL to: 
[email]boot.repair@gmail.com[/email] 

You can now reboot your computer. 

I sent this to the email address because when I rebooted I got the same problem: No grub menu.

---

### Post by irv on 2014-09-05
> **fantab said:**
> check the output of the second command, 'sudo apt-get update' to see if there were any errors...

Yes there was some errors because of not finding the [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages).

I was thinking maybe it is the 64bit boot-repair problem. Maybe I should try the 32bit? But I really don't want to use it.

---

### Post by fantab on 2014-09-05
Quantal has long been [EOL...]("https://wiki.ubuntu.com/Releases") that url won't work.
Try with either 12.04 or 14.04, that is, Precise or Trusty.

---

### Post by irv on 2014-09-05
> **fantab said:**
> Quantal has long been [EOL...]("https://wiki.ubuntu.com/Releases") that url won't work.
Try with either 12.04 or 14.04, that is, Precise or Trusty.

I tried Trusty, but that's where I get the errors. The only one that will let me load boot-repair is saucy (13.10) but it also errors out.

Let me ask another question. Is there a way to boot into linux from the prompt I get at boot up. I tried typing "boot" and it said I need to load the kernel. If I can find out what kernel I could try boot (name of kernel) or something like that.

---

### Post by fantab on 2014-09-05
> Using a [COLOR=Red]Asus 3632QM laptop with 8gig RAM, 750gig Hybrid.[/COLOR]

What is "750gig Hybrid"? Is that the HDD?
If it is then perhaps that is the issue... Some OEM's set up both HDD and SSD in some kind of proprietory RAID... If the mobo is Intel then perhaps you must disable 'Intel Smart Response technology' or Intel smart strorage.
Related info:[ http://askubuntu.com/questions/234111/how-to-boot-ubuntu-from-ssd-drive-which-cannot-be-selected-as-boot-device]("http://askubuntu.com/questions/234111/how-to-boot-ubuntu-from-ssd-drive-which-cannot-be-selected-as-boot-device")

Are you dual booting?
If you have windows, what version, was it pre-installed?
Can you post the output of:
```
sudo parted -l
```

---

### Post by irv on 2014-09-06
My drive is a Hybrid and I have my main drive sda setup like this:
The first 300 MB is the EFI System Partition
Second 900 MB Recovery Partition
Third 350 MB Recovery Partition
Forth 20.01 GB Recovery Partition
Fifth 166.97 GB Primary Partition (Linux OS)
Sixth 510.01 GB Primary Partition (Which is the boot partition)

This is how it came except for the last two. I shrunk the Windows Partition and created the 166.97 GB for Linux leaving me with 510.01 GB for Windows.

Now here is the part I don't understand:
In my BIOS under the boot section I have the following.
Windows Boot Manager
Peppermint (PO: HGST) with a long number
Ubuntu (PO: HGST) with the same long number
Ubuntu (PO: HGST) with the same long number.

Now I tried to install Unbutu on the hard drive once before but it wipe my Windows 8 so I needed to reinstall it but it left the this Ubuntu entry.  Then I installed it on a USB and it added the second Ubuntu entry. And when I installed Peppermint this last time it added that entry. I can move these up and down in the boot order but the only one that works is the Windows boot manager.

I just tried this to clean this up but it didn't do a thing.
I booted with the Windows 8 DVD and ran Repair and went to a prompt. From there I ran
bootrec.exe /rebuildbcd
bootrec.exe /fixmbr
bootrec.exe /fixboot

But when I went to the BIOS it didn't clean out anything. I was in hope that it would clean it up and I could do a boot.repair again.

---

### Post by ubfan1 on 2014-09-06
No swap partition, OK if you have enough ram, but I always use a swap if I have a spinning platter (since it doesn't wear out like flash).
You can clean out the old efi boot menu with efibootmgr when you get things running, don't worry about them now.
Not sure what peppermint does if it does not use the Ubuntu bootloaders for secure boot, but if you are not running secure boot, grubx64.efi could be the same.
At the grub prompt, you should be able to type:
set root=(hd0,5)
linux /vmlinuz
initrd /initrd.img
and then boot
The links in / make typing the names a little easier, but again, if using secure boot, this wont work since the links are wrong.
The efi partition should just contain a FAT filesystem with the bootloaders.  The usual place for the Ubuntu bootloaders is /EFI/ubuntu, and I guess peppermint makes its own directory.

---

### Post by irv on 2014-09-08
> **ubfan1 said:**
> No swap partition, OK if you have enough ram, but I always use a swap if I have a spinning platter (since it doesn't wear out like flash).
You can clean out the old efi boot menu with efibootmgr when you get things running, don't worry about them now.
Not sure what peppermint does if it does not use the Ubuntu bootloaders for secure boot, but if you are not running secure boot, grubx64.efi could be the same.
At the grub prompt, you should be able to type:
set root=(hd0,5)
linux /vmlinuz
initrd /initrd.img
and then boot
The links in / make typing the names a little easier, but again, if using secure boot, this wont work since the links are wrong.
The efi partition should just contain a FAT filesystem with the bootloaders.  The usual place for the Ubuntu bootloaders is /EFI/ubuntu, and I guess peppermint makes its own directory.

I tried running the commands you listed above and when I ran boot it displayed a lot of text on the screen but went by so fast I couldn't read it. It stopped at a initramfs> prompt and that is far as I could go.
I thought I would clean out the clean out the efi boot list by running the the efibootmgr so I open a terminal in Windows 8 and typed the command efibootmgr and it gave me the message it could not find command. I take it I was to run it there?
What I was thinking about doing is cleaning out the list and then installing Ubuntu 14.04.1 on the sda5 partition. But I didn't want to installed it until I get things cleaned up.

---

### Post by ubfan1 on 2014-09-08
sudo efibootmgr -v   should be run on an Ubuntu system (live install fine, but I think you still need to install the efibootmgr package.).
Are you running with Secure Boot disabled?   Also, just to check, you turned off "fast startup" in the Windows power options, turned off any dynamic partitions in Windows, and disabled Intel Smart Resp Tech if present.  Now in the BIOS/UEFI settings, turn off fast boot to give yourself some time to hit a function key at power-up.  Secure boot should also be turned off, I think I had to do that on an Asus X200 to boot off a USB.    Two things to read first are:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
Your efibootmgr listings (without the -v) at the end of your paste showed peppermint once, but then the next listing didn't -- only two Ubuntu listings were present.

---

### Post by Nistegmos on 2014-09-08
I know this isn't what most people want to hear, but you might want to try Grub4DOS as a really easy to use alternative.  The downside is that I don't think it works with GPT, only MBR; so you can only have 4 partitions on each drive if you choose to use it.  The upside is that it's very easy to create and edit the boot menus and I have verified that it works despite having the normal boot stuff on disk and doesn't seem to touch the /boot folder at all.

---

### Post by irv on 2014-09-08
Okay, here is where I am at. I did install efibootmgr and clean up the list, which went well. Now for my big screw up:
One thing about this Asus laptop and Windows 8 is I have to turn off Secure boot and fast boot in order to use the F2 key to get to the BIOS. Well after cleaning everything up I installed Ubuntu 14.04, but I forgot to turn Secure boot and fast boot back on. Because of this I wiped my windows and not only that but wiped my recovery also.

I call Asus because they do not put the key code on the laptops any more to reinstall Windows. He told me I had to wait until tomorrow before they can send it. Well I didn't want to wait so I installed 8.1 from a DVD I have, but it is installed on another PC so I would need to get the right code and enter it tomorrow. When I went to install everything seemed to be going well but after 4 hours I just stopped it. I had no way of getting into anything else but this have installed Windows. 

I finial had to take out the hard drive so I could boot to the BIOS and turn off Secure boot and fast boot again to be able to boot the BIOS from the F2 key again. I put the hard drive back in, put the install USB for Ubuntu and rebooted and pressed the F2 and turn on Secure boot and fast boot and put the boot order to boot on the USB first so I could install Ubuntu. This time I wiped everything and have just Ubuntu running and for now that is the way it is going to stay. Maybe later I will install Peppermint to run with Ubuntu but for now I am good to go.

I got away from Windows for a few years and when Windows 8 came out I like it so I keep using it, but now that I am back to Ubuntu I am really happy again. I know I am going to miss a few things, but right now I am staying with Ubuntu. Maybe all things happen for a reason.

Thanks for all the help on this one and I am going to mark it solved.

---

### Post by fantab on 2014-09-09
The 'fast boot' or 'fast startup' feature in Windows8 is actually a 'hibernation' feature. This feature keeps Win in a 'hibernation mode' when you think you've 'shutdown' the PC.
When this feature is enabled, Ubuntu's installer won't see any partitions on the HDD and assumes it to be 'empty' and reformats the entire HDD for Linux use.
Hibernating or enabling 'fast startup' in a dual boot setup is a bad idea...

---

### Post by irv on 2014-09-09
One thing about this Asus laptop is no mater if I have them turn on or off it doesn't see Windows when Installing Ubuntu or any other Linux. You have to setup a partition before you start.
Before I had installed Ubuntu I had already installed Peppermint on its own partition. When I went to install Ubuntu it saw Peppermint and I had the choice to either run along side or replace it. I chose to replace it and it replaced everything my windows, my recovery, and Peppermint. Even though they were on different partitions. This is not right. Why can Ubuntu install on what you tell it to. I was thinking it was replacing Peppermint. 
Like I said the only good thing is I am Windows free again. By the way I didn't loose any files I had them in Onedrive on Windows. It worked like UbuntuOne did when we had it. I had just gotten more space when UbuntuOne stopped it's storage. They refunded my money. Too bad they stopped.

---

### Post by oldfred on 2014-09-09
Known issue with installs not seeing Windows 8 and totally erasing drive.
        
 Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

With Windows 8 or any multiple install system, only use Something else install option. 
      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by irv on 2014-09-09
Thanks Oldfred, good to see you still out here. I will use your links if I ever install Windows again. Right now I will just use Ubuntu. I'm one who always liked using Unity desktop. I Know some don't like it but I do.

---

