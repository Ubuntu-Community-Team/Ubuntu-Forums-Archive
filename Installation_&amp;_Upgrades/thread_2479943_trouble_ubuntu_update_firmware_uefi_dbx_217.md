---
title: "trouble ubuntu update firmware uefi dbx 217"
date: 2022-10-13
forum: Installation &amp; Upgrades
---

### Post by jgwphd on 2022-10-13
I have the "**exact**" problem described here: [https://askubuntu.com/questions/1432494/trouble-ubuntu-update-firmware-uefi-dbx-217](https://askubuntu.com/questions/1432494/trouble-ubuntu-update-firmware-uefi-dbx-217)  
What I am using to boot my Dell Precision 3240 is identified here: 

```
jgw-i9@jgwi9-Precision-3240-Compact:~/Desktop$ sudo efibootmgr -v | grep "Boot$(sudo efibootmgr -v | awk '/BootCurrent/{print $2}')"
[sudo] password for jgw-i9: 
Boot0000* ubuntu    HD(1,GPT,022047eb-4164-41df-b6df-bdd2e7bc6587,0x800,0x183800)/File(\EFI\ubuntu\shimx64.efi)
```

I am not a firmware secure boot expert expert and I am not following the advice at the link except for the part that my machine might become un-bootable ...so my question is: is this something I really need to fix? or will it go away when I do a fresh install of Ubuntu 22.10 in a week or two. Also, (I am guessing here) it seems to be impacting updates because of the "security" angle (but not sure - I assume this problem if it is not related to the firmware issue will go away when I do a fresh install of 22.10 too), for example 

```
jgw-i9@jgwi9-Precision-3240-Compact:~/Desktop$ sudo apt-get update
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) impish InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                     
Hit:3 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease                                                                                      
Ign:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security InRelease                                                                                
Ign:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish InRelease                                                                                          
Hit:6 [http://dell.archive.canonical.com](http://dell.archive.canonical.com) focal InRelease                                                                                          
Hit:7 [http://ppa.launchpad.net/unit193/encryption/ubuntu](http://ppa.launchpad.net/unit193/encryption/ubuntu) impish InRelease                                                      
Err:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security Release                           
  404  Not Found [IP: 185.125.190.36 80]
Ign:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish-updates InRelease     
Hit:10 [http://oem.archive.canonical.com](http://oem.archive.canonical.com) focal InRelease
Ign:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish-backports InRelease
Err:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish Release
  404  Not Found [IP: 185.125.190.39 80]
Err:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish-updates Release
  404  Not Found [IP: 185.125.190.39 80]
Err:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) impish-backports Release
  404  Not Found [IP: 185.125.190.39 80]
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu impish-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu impish Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu impish-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://archive.ubuntu.com/ubuntu impish-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
jgw-i9@jgwi9-Precision-3240-Compact:~/Desktop$
```

Any Advice appreciated!

---

### Post by jgwphd on 2022-10-13
**Removing duplicate post** - I don't know how i did this????  ...and how I got a duplicate thread. I was having connection issues and screen freezes at the time... sorry for any confusion.

---

### Post by oldfred on 2022-10-13
Do I see mixed impish &  focal in your updates?
You should only have one other the other & impish only supported until 2022-07-14.
cat /etc/apt/sources.list

If upgrading, not doing new install, you also need to make sure system is fully updated & all ppa & proprietary drivers are removed. You then restore them after update from you backups, if required.

---

### Post by grahammechanical on 2022-10-13
We need to clear up some possible confusion.

As far as far as I know the only firmware that Ubuntu updates is Linux firmware - a package containing Linux hardware drivers for the OS that is updated by the Linux developers from time to time. 

Another kind of firmware is put into an integrated circuit by the motherboard manufacturer. It tells the motherboard what kind of hardware is on the motherboard. That firmware can be updated but you need to check with the manufacturer about it. The UEFI/BIOS utility reads the code in this integrated circuit.

The Ask Ubuntu thread seems to be dealing with the Microsoft database that Microsoft uses to control (verify) what boot code can be run if secure boot is enabled in the UEFI/BIOS. Ubuntu developers have an arrangement with Microsoft to certify Ubuntu's Linux bootloader code. I think that this is completely different from your problem. Two years ago a serious security flaw was detected in the Grub bootloader. Once the flaw was fixed in Grub each Linux distribution had to update Grub in its distribution. But there was a problem. Existing ISO images of a distribution could not be updated. So, it was arranged for Microsoft to blacklist the old versions of Grub in its Secure boot database to prevent an ISO image from installation a distribution of |Linux with a very insecure version of its bootloader. That in my opinion is what the Ask Ubuntu thread was really about.

> E: The repository 'http://security.ubuntu.com/ubuntu impish-security Release' does not have a Release file. 
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

That is nothing to do with Secure boot or the Microsoft database or the firmware of your motherboard. Ubuntu Impish is Ubuntu 21.10 and it reached end of life on 14 July 2022. The archives or repositories for 21.10 have been given a different internet address from the internet address in your /etc/apt/sources.list files.

If you do a fresh install of Ubuntu 22.10 you will be installing a version of Ubuntu that only has nine months support. You will end up in the same situation you are in now. Better to install Ubuntu 22.04. It has five years standard support.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards

---

### Post by MAFoElffen on 2022-10-14
Please edit your first post to wrap your commands and output in ***[noparse]```
 Commands & Output Here 
```[/noparse]***...

One. I notice you are on 21.10. You say you are installing 22.10 fresh in a couple weeks. 21.10 is an interim release which will be EOS in July 2022. 22.10 is still DEV/TEST until it is released in a couple weeks. So you are skipping over 22.04.1, which is released and STABLE? Okay...

Two. You did not post the results of 
```

efibootmgr -v

```
...to compare what other efi files are there. So the information is incomplete to make any kind of determination of what is going on...

EDIT: Dang. Now I'm really confused on what is being asked. LOL oldfred is right on the mixed repo sources... double posts and a mess to try to weed through. Wow.

---

### Post by oldfred on 2022-10-14
Please do not duplicate thread. We all all volunteers and need to know what others have already suggested.

Merged rather than closed second post only because already comments in both threads.

---

### Post by jgwphd on 2022-10-14
As requested here is the output:

```
jgw-i9@jgwi9-Precision-3240-Compact:~/Desktop$ efibootmgr -v
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0008,0009,0002
Boot0000* ubuntu    HD(1,GPT,022047eb-4164-41df-b6df-bdd2e7bc6587,0x800,0x183800)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* load_efi    HD(1,GPT,022047eb-4164-41df-b6df-bdd2e7bc6587,0x800,0x183800)/File(\EFI\Ubuntu\loadefi.efi)
Boot0002* Linux Firmware Updater    HD(1,GPT,022047eb-4164-41df-b6df-bdd2e7bc6587,0x800,0x183800)/File(\EFI\ubuntu\shimx64.efi)\.f.w.u.p.d.x.6.4...e.f.i...
Boot0003* Onboard NIC(IPV4)    PciRoot(0x0)/Pci(0x1f,0x6)/MAC(a4bb6d8d551d,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0004* Onboard NIC(IPV6)    PciRoot(0x0)/Pci(0x1f,0x6)/MAC(a4bb6d8d551d,0)/IPv6([::]:<->[::]:,0,0)..BO
Boot0008* Onboard NIC(IPV4)    PciRoot(0x0)/Pci(0x1f,0x6)/MAC(a4bb6d8d551d,0)/IPv4(0.0.0.00.0.0.0,0,0)..BO
Boot0009* Onboard NIC(IPV6)    PciRoot(0x0)/Pci(0x1f,0x6)/MAC(a4bb6d8d551d,0)/IPv6([::]:<->[::]:,0,0)..BO
```


My question is simple. I am going to do a fresh install of 22.10 [wipe the hard drive clean and install 22.10] when it is available and I want to know if these two problems will go away when I do it or is there something I need to deal with sooner or later (i.e. is the boot problem going to be there after the new system install, I forgot about Impish reaching EOL - my bad). 

FWIW, the reason for skipping 22.04 is that I have found it to be unstable and have had a lot of issues on my other machines. One issue for example: [https://ubuntuforums.org/showthread.php?t=2477197](https://ubuntuforums.org/showthread.php?t=2477197)

---

### Post by MAFoElffen on 2022-10-14
Which your previous post was 22.04 previous to 22.04.1 where most of the problems with 22.04.x were sorted out and corrected.

I'm sorry, but I see a pattern of problems with the format of your posts, with what I thought was new, but since you posted one of your previous posts... You've been doing this for a while.

You don't seem to know that it is a Forum policy to wrap all commands and output from commands within CODE Tags. There are two reasons for this. First, it creates a format that is easier for Users of the Forum to read the post. Second, unwrapped commands and output does strange/weird things to the forums software.

Please edit your posts to correct that. In the future, please follow that policy.

To wrap output in CODE TAGS, the easiest way is to use the "Go Advanced" editor, select/hightlight what you need to wrap, then press the "#" Icon in the toolbar. Alternately, you could type [noparse]```
[/noparse] before your command/output, then type [noparse]
```[/noparse] after the end of it.

Let's keep you out of trouble with the Moderators and Admin's by doing things the right way... I'm surprised no one has warned you about that yet.  

Just a tip...

---

### Post by jgwphd on 2022-10-14
@MAFoElffen "Please edit your posts to correct that. In the future, please follow that policy." - I apologize i didn't read the policy or understand my impact. I'll be better in the future and I corrected my posts on this thread. 

BTW 22.04 was bad news to me on multiple machines, so I am anxious to get away from it. 

I still have my question asking for advice: I am going to do a fresh install of 22.10 [wipe the hard drive clean and  install 22.10] when it is available and **I want to know if these two  problems will go away when I do it or is there something I need to deal  with sooner or later (i.e. is the boot problem going to be there after  the new system install**, I forgot about Impish reaching EOL - my bad). 

FWIW, the reason for skipping 22.04 is that I have found it to be  unstable and have had a lot of issues on my other machines. One issue  for example: [https://ubuntuforums.org/showthread.php?t=2477197](https://ubuntuforums.org/showthread.php?t=2477197) my wife's machine has this annoying problem [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1970957](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1970957) and just a few hours ago I had friend bring over his HP laptop for an Ubuntu dual boot with windows 10 and we stumbled into the exact problem mentioned here today: [https://ubuntuforums.org/showthread.php?t=2479978](https://ubuntuforums.org/showthread.php?t=2479978) I am following that thread but I didn't look good telling him how wonderful Ubuntu was :-(  As a hobby I help out my family and friends and usually brag about Ubuntu...  but not about 22.04.

---

### Post by jgwphd on 2022-10-18
Can someone speculate **if **my boot problem ( described here: [https://askubuntu.com/questions/1432...e-uefi-dbx-217]("https://askubuntu.com/questions/1432494/trouble-ubuntu-update-firmware-uefi-dbx-217") ) will go away when I do a clean install of 22.10 (wipe hard drive and NO upgrade) or is this something I need to  deal  with sooner or later (i.e. is the boot problem going to be there  after  the new system install)? Many thanks for your patience with my help requests!

---

### Post by oldfred on 2022-10-18
No one can tell.
Best just to have good backups and do a new clean installs.

I find Kubuntu 22.04 works well on my Dell 11th Gen & a MSI motherboard that is 12th gen Intel.
But only Intel video and all firmware updates applied.

---

### Post by jgwphd on 2022-10-18
Ok, thanks. I'll wipe everything and start again with 22.10

---

### Post by tips2448 on 2022-10-24
I have a fresh install of 22.10, but I am facing this same problem.

The update is showing in Kubuntu's front-end update manager Discovery, but will not upgrade, but the update doesn't exist via the terminal 'sudo apt-get'.

---

### Post by jgwphd on 2022-10-26
I did a fresh of 22.10 and I still have the same problem. When I open the update tab using the Ubuntu software center and click on "update" I get the "**exact**" problem (messages and all) described here: [https://askubuntu.com/questions/1432...e-uefi- dbx-217]("https://askubuntu.com/questions/1432494/trouble-ubuntu-update-firmware-uefi-dbx-217") FWIW; when I go to the Software store (gnome) it shows the same update: Secure Boot dbx Configuration Update. When I click "update" I get a message "loading updates... this could take awhile"   but nothing happens and the device firmware update remains. No error message is given. Any suggestions appreciated.

---

### Post by oldfred on 2022-10-26
I uninstall fwupdate as my system is not in the database. Is yours in database or if not trying to update will not work.
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

---

### Post by jgwphd on 2022-10-27
@oldfred - Thanks. My machine (Dell Inc. Precision 3240 Compact) is on the list at [https://fwupd.org/lvfs/devices/com.dell.uefi091104a6.firmware](https://fwupd.org/lvfs/devices/com.dell.uefi091104a6.firmware) In the screen shot below is my firmware packages. It seems from synaptic "fwupdate" is a transitional package for fwupd. What should I install or uninstall or update (if possible). Your guidance is appreciated. Thanks![IMG]https://ubuntuforums.org/attachment.php?attachmentid=291197&stc=1[/IMG]

---

### Post by jgwphd on 2022-10-28
I went into the "Ubuntu Software" store and installed the "fwupd" package (see top left of the prior picture which indicates it is not installed at that time) and the problem went away after a reboot.

---

