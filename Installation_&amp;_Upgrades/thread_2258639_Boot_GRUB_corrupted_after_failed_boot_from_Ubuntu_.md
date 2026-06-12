---
title: "Boot GRUB corrupted after failed boot from Ubuntu CD"
date: 2014-12-29
forum: Installation &amp; Upgrades
---

### Post by ozark_hillbilly on 2014-12-29
Hello,

I am kind of in a bind currently. I made an attempt to boot my computer from a backup CDROM containing 12.04 LTS. I simply wanted to check the cd to make sure it was bootable. After waiting a long time with the startup Ubuntu dots blinking on and off on the screen and what appeared to be the CDROM being accessed (or I thought it was anyway) I hit the ESC key and received:

zip: stdin: Input/Output Error  (on the screen, line after line) 

Not good I'm thinking. I then attempted to boot up normally off the hard drive. The BIOS goes through its checks and then the screen that has which OS's to choose from shows up (it says GRUB at the top). Normally it proceeds past this point automatically unless you interrupt it. Now it remains at this screen and you cannot select any of the choices. The top choice is highlighted, which is the 12.04 LTS OS, but hitting the enter key does nothing. I have booted off a version 10.04 Ubuntu CD to get to this point. 

What are my options to get the system to boot up properly? If I select install Ubuntu 10.04 LTS off the cd the install process asks if I want to "Write previous changes to disk & continue?". I don't really want to change the partition size or anything. Is it necessary to install 10.04 alongside the other already installed 12.04 to get things straightened out? Or, can I go into a file area somewhere and look for something that is currently not correct?

Any assistance is greatly appreciated,

Ed

---

### Post by Bucky Ball on 2014-12-29
Don't install 10.04 LTS as it is no longer supported, unless you are using the server version.

If 12.04 LTS is not working for you, perhaps try 14.04 LTS and see if you have the same issue. Did you check the disk for defects and the md5sum?

Your other option is Boot Repair, but as I say, you should avoid 10.04. Good luck. ;)

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by ozark_hillbilly on 2014-12-29
Ran the boot repair terminal commands and came up with this:

ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 3C48D16124B50277AF10D27F32B18A1260D8DA0B
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]
Ign [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) lucid/main Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]           
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                          
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [184kB]                  
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [14B]                       
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages [1,386kB]                 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [606kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,867B]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [246kB]          
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,267B]   
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages [6,208B]            
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources [659kB]                    
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources [3,775B]             
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [797kB]           
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [4,630B]    
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources [338kB]            
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]     
Fetched 4,367kB in 39s (112kB/s)                                               
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && (boot-repair &)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package boot-repair
ubuntu@ubuntu:~$ 

What is necessary to make the boot-repair package locatable?

Thanks.

---

### Post by ozark_hillbilly on 2014-12-29
I tried to use Synaptic Package Manager to see if I could locate 'boot-repair' but found nothing. Under Synaptic Package Mgr Software Sources -Other Sources I did find this:

[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu)

and it has a check mark next to it....

---

### Post by oldfred on 2014-12-29
All the repositories for 10.04 are closed so you cannot run updates.

Boot-Repair only has versions for current systems, so no Lucid.
 Precise, Trusty, Vivid, & Utopic all should work now with current ppa

---

### Post by ozark_hillbilly on 2014-12-29
If I can't use the 10.04 CD to repair my corrupted boot loader what are my options to getting things straightened out? I have no CD's later than 10.04. 
Can I attempt to go to version 14 (?) with my GRUB toasted? If so, what are the steps?
I do have a backup of my /Home data on a separate drive.

It seems like you should be able to somehow access the GRUB file(s) and correct the corrupted area. I can see all the data on my boot drive when booted up with the Live CD (10.04).

I am stuck at this point folks. :confused:

Ed

---

### Post by ozark_hillbilly on 2014-12-29
@OldFred

The link in your response to "UEFI boot repair" seems to be about a situation where the user is using Windows 8 as well as Linux. That's not really my predicament. Although I have multiple OS's (Ubuntu & Windows XP) I could boot from before the GRUB was trashed.

Ed

---

### Post by ozark_hillbilly on 2014-12-29
Thread closed. Still have trashed GRUB loader. Moving to Installation & Upgrade forum to seek further assistance.

---

### Post by oldfred on 2014-12-29
The UEFI link is my signature, not intended specifically for your issues.

Unless you started to install 12.04 from that CD, it should  not have modified your old install. Does 12.04 boot in live mode? 

Bit late but you always should have a working live installer for repairs with a current version of Ubuntu.

---

### Post by ozark_hillbilly on 2014-12-29
Scenario:

After a failed attempt to boot off a cdrom drive with what I thought was a good 12.04 LTS backup disk my system is now unresponsive. The screen stops where you select your OS. No keyboard input is recognized. The reason this all started was I was having hardware issues and wanted to make sure my backup disk was OK. It was not and somehow my boot loader is now "toast."

I only have a good Live CD for 10.04 LTS to boot from & work off of. That is what I am using at the moment. The Boot-repair utility is no longer supported for 10.04 so that screws me going in that direction.

What are my options? Update to the latest LTS? If so, what is the correct process to do this while currently running under a 10.04 CD?

I can see ALL my 12.04 LTS Linux data on the boot drive. Everything is there I just can't use it right now.

I am not a fluent Linux user as far as getting into the inner workings of file systems and such. I can do Terminal command functions and look at data in various locations but really have no in-depth knowledge of Linux.

I need to rely on you, the forum participants, to direct my actions as I am totally lost at this point. 

Someone throw me a life preserver please.... I'm sinking fast..... :lolflag:

---

### Post by nerdtron on 2014-12-29
Well I think it is still possible to restore GRUB, but if the install was 10.04 and the system is 12.04, hhhmmm I'm not sure on the version of GRUB that will install.

If you still have access to your data via a live cd, it's always a good idea to start copying now, and do the restoration/experimentation later when you have safely copied your data.

---

### Post by ozark_hillbilly on 2014-12-29
I failed to mention that I do have my /HOME user data backed up on a separate hard drive. A restore process should get that data back if needed.
I just need a push in the right direction now.

Thanks.

---

### Post by oldfred on 2014-12-29
Merged your old thread back into your new one. You can request a thread be moved just by requesting the the report thread icon. That is not just for spam, but any issue you may have.
Users need to see what already has been suggested to avoid duplication. We all are volunteers and do not want to waste effort where not needed.

---

### Post by Bucky Ball on 2014-12-29
> **ozark_hillbilly said:**
> 
What are my options? Update to the latest LTS? If so, what is the correct process to do this while currently running under a 10.04 CD?

I can see ALL my 12.04 LTS Linux data on the boot drive. Everything is there I just can't use it right now.



First up, try this. Boot into 10.04 and:

```
sudo update-grub
```

... in a terminal. Reboot. Does 12.04 LTS show? If you can see it there on a partition, then perhaps it is installed. After that command, reboot and see if it is now on the grub menu at boot.

Failing this, boot 10.04, go for an update and see if '12.04 is available' is shown at the top of the update screen. LTS releases can be upgraded directly to the next LTS, leap-frogging the interim releases in between. This can be problematic, though, so disable any third-party PPAs you may have installed manually first. 12.04 also has Unity rather than Gnome desktop environment so it is quite different and you may/may not like it.

If I were you, though, I'd be tempted to download 14.04 LTS and do a clean install. You need to have 'Show Long-term support releases' enabled. Use 'Something Else' when you get to the partitioning section and install 14.04 to the 12.04 / partition.

---

### Post by ozark_hillbilly on 2014-12-29
Bucky Ball,

Here is what terminal command generated:

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 

You asked : "Does 12.04 LTS show? If you can see it there on a partition, then perhaps it is installed. After that command, reboot and see if it is now on the grub menu at boot."

12.04 is the first choice on the startup Grub menu. It's just that even though it is highlighted as a choice the enter key, or any key input, does not invoke it.

What do mean by disabling any 3rd party  PPA's? Is this software loaded from a repositiory or website? Is there a way to determine/list which PPA's I have installed?

If I download 14.04 while running 10.04 Live CD where do I enable "'Show Long-term support releases' ? Will 'Something Else' be a menu choice when performing the upgrade?


Ed

---

### Post by ozark_hillbilly on 2014-12-29
OldFred: "Unless you started to install 12.04 from that CD, it should not have modified your old install. Does 12.04 boot in live mode?"

How does that work -booting 12.04 in live mode? I only have 10.04 as a working Live CD. I do have the 12.04 backup cd but that is the one that trashed my grub. Is there another way to invoke it besides from an initial pc boot?

---

### Post by Bucky Ball on 2014-12-29
Boot from the 12.04 disk. When you get to the list of options, choose 'Try Ubuntu'. That will get you to a desktop. That is 'live' mode.

There is no way of invoking it other than that that I'm aware of.

---

### Post by MAFoElffen on 2014-12-29
Correction to above-- boot from your 10.04 LiveCD (you should boot from a LiveCD that is the same version as the one you are trying to repair...) into the Live Image. You should then chroot into your installed system.

For instructions on that, while you are trying to do that-- bring up a browser, go to this forum, go to 2d half of the third post of my sticky (link in my signature line). Follow those directions to chroot into your installed system. THEN you can use those commands to either try to upgrade grub. 

If no love on that, Get familiar with how the source list is laid out. oldfred was partially correct in that 10.04 is EOL. The repo's are no longer at Ubuntu --- The old repos, with the last version of updates are now archived at digitalocean. I've repaired and updated Lucid systems to their repo's... then changed it back to do my do-upgrade-release to newer versions. When I do someone's intermeduiate release that is EOL, those are the repo's I have to hit to get to an LTS, so that I can jump to a latest LTS upgrade.

Of course you could always install recent Grub 2 to your system from a recent LiveCD Image, but from 11.04 on, there were major changes in Grub2 that involved KMS(kernel mode setting)... so there were minor changes in what 10.04 kernels used as boot options and what Grub2 will try to pass , in the automated update scripts.

Of corse if you have the old alternate install disk for Lucid, you could edit your sources list to that and use that as a local repo.

---

### Post by Bucky Ball on 2014-12-29
> **MAFoElffen said:**
> 

oldfred was partially correct in that 10.04 is EOL. 

Oldfred is wholly correct that 10.04 LTS is EOL. It is no longer supported by Canonical or these forums. See [here]("http://ubuntuforums.org/showthread.php?t=2229730").

If you can find repos elsewhere, great, but those repos are not officially supported by Canonical. ;)

---

### Post by MAFoElffen on 2014-12-29
> **Bucky Ball said:**
> Oldfred is wholly correct that 10.04 LTS is EOL. It is no longer supported by Canonical or these forums. See [here]("http://ubuntuforums.org/showthread.php?t=2229730").

If you can find repos elsewhere, great, but those repos are not officially supported by Canonical. ;)
Right. I never said they were supported. 

But the mirrors are still there. ([http://mirrors.digitalocean.com/ubuntu/dists/](http://mirrors.digitalocean.com/ubuntu/dists/)) They are exactly as what Conical stopped at. I mentioned they are archives... If someone needs them to get right... to make a lateral step to make things correct again, so that they can get going again into what is supported by Conical.

Just like my saying to use an alternate install CD as a repo. That is a commented out line that was in Lucid's sources list... It once was an accepted practice. That is no longer supported, but it is possible.

I'm all for getting a user up-to-date and current. I accept there are 100 ways to get to the same end. Some ways involve less work and less risk.

If the OP was into it, since his /Home is split out, there would be little risk in installing new and not telling the installer about it... Then delete the .gconf, .gnome*, .config and .cache directories from the old /home and then adding it to the new system. The system would just build new profiles and configs. His data would be safe.

---

### Post by Bucky Ball on 2014-12-29
> **MAFoElffen said:**
> Right. I never said they were supported. 

But the mirrors are still there. ([http://mirrors.digitalocean.com/ubuntu/dists/](http://mirrors.digitalocean.com/ubuntu/dists/)) They are exactly as what Conical stopped at. I mentioned they are archives... If someone needs them to get right... to make a lateral step to make things correct again, so that they can get going again into what is supported by Conical.

Just like my saying to use an alternate install CD as a repo. That is a commented out line that was in Lucid's sources list... It once was an accepted practice. That is no longer supported, but it is possible.

I'm all for getting a user up-to-date and current. I accept there are 100 ways to get to the same end. Some ways involve less work and less risk.

If the OP was into it, since his /Home is split out, there would be little risk in installing new and not telling the installer about it... Then delete the .gconf, .gnome*, .config and .cache directories from the old /home and then adding it to the new system. The system would just build new profiles and configs. His data would be safe.

+1. Got you and agree. ;)

---

### Post by ozark_hillbilly on 2014-12-30
Mafoelffen,

Looking at my attached screenshot which partition is the / partition? I'm guessing /dev/sda2.   Yeah.... I'm that dumb (about Linux) unfortunately....:rolleyes:

---

### Post by oldfred on 2014-12-30
The sda2 is the extended partition which is only used as a container for all the logical partitions. So that is not /. 

Probably sda7, since you have sda5 with the home label.

---

### Post by ozark_hillbilly on 2014-12-30
Did a mount of /dev/sda7 (OldFred seemed to think sda7 was my /) and tried to update grub.....

Terminal response:

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
root@ubuntu:/# 

Is there another logical step to do at this point? Are additional mounts necessary?

I did go ahead and umount /dev/sda7 /mnt for now. Would it be dangerous to leave it mounted when not actually using terminal mode for a length of time?

Ed

---

### Post by ozark_hillbilly on 2014-12-30
If I opt for a clean upgrade to 14.04 LTS (while running under 10.04 Live CD) should that clear up the corrupted Grub? Is there any downside to this considering my present situation? Can I jump directly to 14.04?

---

### Post by oldfred on 2014-12-30
What hardware?
They have changed to Unity which requires a better video chip/card. My laptop from 2006 only runs full Ubuntu if I change to fallback/gnome panel which looks just like (almost) your old gnome2. Others suggest Xubuntu or if limited RAM, Lubuntu.
My 2006 build with a Core2 Duo and video card from 2009 runs full Unity.
So what hardware you have makes a big difference on what flavor you may need.

If sda7 is root, this the mount from live installer and install of grub.
 sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If that does not work then a full chroot may, but any commands that want to download from Internet will not work.

---

### Post by ozark_hillbilly on 2014-12-30
Fred,

Terminal output:

ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ 


I guess a reboot should now be attempted? Do I need to unmount sda7 before rebooting?

Hardware: I am running an Intel Duo-Core Processor as well; 3 gig RAM. Unfortunately I only have/use motherboard video - no external graphics card currently. Do you have a minimum configuration video card recommendation I can pick up on the cheap so I can* maybe* run Unity?

Ed

---

### Post by oldfred on 2014-12-30
Do not know what is available for video cards. I have 9600GT which they have not made for a while and a 620GT which I only tried with Unity for a couple of minutes as I prefer fallback and the old menu. My monitor is also 4:3 so having menu on top makes more sense than on side.

---

### Post by ozark_hillbilly on 2014-12-30
Fred,

Reboot (after grub update/upgrade) was not successful and actually worse. I now have the *Black Screen Syndrome* that seems to have plagued many unfortunate users before me: grub is totally trashed. Is there a good thread/sticky that talks about minimum video hardware requirements to meet the demands of this new (?)  Unity software that is an element of the new release (14.04)? I don't want to get the cart before the horse on this upgrade. Also, is there no issues with jumping an LTS release (12.04 to 14.04) on the upgrade?

ed

---

### Post by Bucky Ball on 2014-12-30
LTS goes to the next LTS, leapfrogging the interim release in between. 10.04 LTS will go to 12.04 LTS. 12.04 LTS to 14.04 LTS. But not 10.04 to 14.04. That calls for a clean install. 

Upgrading this way can be problematic. Disable any third-party PPAs you may have manually installed prior to attempting it. They can cause issues. You want to get your machine as close to 'vanilla' as possible prior to a net upgrade.

---

### Post by ozark_hillbilly on 2014-12-30
"Disable any third-party PPAs you may have manually installed prior to attempting it. They can cause issues. You want to get your machine as close to 'vanilla' as possible prior to a net upgrade. "

If I don't know what that is (PPA) I probably don't need to bother asking if any are on my system. Is there a specific location to look for these being installed?

---

### Post by ozark_hillbilly on 2014-12-30
Fred,

11.04 according to Ubuntu doc ([https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)) was when Unity started being a part of OS. I read the requirements and am puzzled that my system was  functioning under 12.04 w/o a separate video card; the mobo video drivers are all there is. So going to 14.04 hopefully may not need a separate card after all!

ed

---

### Post by ozark_hillbilly on 2014-12-31
Can I use Update Manager on the 10.04 Live CD to do an upgrade to 12.04? I currently have 12.04 installed with a trashed Grub. Would an upgrade rebuild the Grub/ correct my boot problem? Or should I just go ahead and install 14.04? Is there any caveats to burning a USB stick with the iso file?

---

### Post by nerdtron on 2014-12-31
Just a fresh install of 14.04 (if you can) is the best option here. I'm not a fan on in-place upgrades as they left behind config files while the software upgrades. Much more of a hassle on my opinion.

---

### Post by oldfred on 2014-12-31
They say they have made improvements to Unity. My last few minutes with it, it was almost usuable. My main complaint for me besides my old 4:3 monitor is when I have more than one Windows of same application I have to click twice to find correct Window.

If old system ran ok, then I would expect 14.04 to be fine. I just thought that if used to 10.04 and old menu system something like fallback/gnome-panel may be better. Some have disliked the change to Unity, others now like Unity after trying it for a while. But it is different.

---

### Post by ozark_hillbilly on 2015-01-01
Update:

Downloaded 14.04 iso file 
checked iso w/ md5sum and it was correct
installed 14.04 into USB flash drive

changed BIOS to boot off USB 

Boot unsuccessful: dependent on how the 1st Boot device option was configured the computer reacted differently after getting to the verifying DMI Pool Data step in the boot sequence. Is there a correct USB type for the BIOS choice or does it matter? 
Choices: USB-ZIP    USB-HDD    USB-FDD   USB-CDROM

one error generated was "unknown keyword in configuration file."
                                     boot:

no keyboard input was accepted.


Is there a way to use the update/upgrade program on the 10.04 Live CD to install the 14.04 iso file I downloaded?
Or is it possible to invoke the 14.04 LTS on the USB drive while running the 10.04 Live CD.
I've got the ISO downloaded I just need a way to cleanly do the upgrade. When I run Update Manager under the Live CD it informs you that 12.04 LTS is available for upgrade. Is there a way to skip 12.04 and have my system changed to 14.04 straightaway?

---

### Post by nerdtron on 2015-01-01
> Choices: USB-ZIP    USB-HDD    USB-FDD   USB-CDROM

On my computer none of those choices works too. When I insert the flash drive and go to the BIOS, my san disk flash drive is listed as a hard drive itself. I need to explicit tell the BIOS to first boot the hard drive, but change the hard drive priority to San Disk, instead of my normal western digital hard drive.

Another option too is that some motherboards have shortcut key to "Choose a boot device" which I also have in mine. I just press F12 on boot up and it will bring a screen where I can choose which device to boot like: CD ROM, Western Digital HD, San Disk Flash Drive, PXE Boot. etc.

---

### Post by ozark_hillbilly on 2015-01-01
"When I insert the flash drive and go to the BIOS, my san disk flash drive is listed as a hard drive itself. I need to explicit tell the BIOS to first boot the hard drive, but change the hard drive priority to San Disk, instead of my normal western digital hard drive."

How do you check/invoke the BIOS_ after_ boot up to see how the flash drive is listed?

I did get to the Boot Menu w/ F12 and selected hard drive then San Disk but there was the same response on boot up:

"Unknown keyword in configuration file."

boot:

[no further activity on screen; no keyboard input accepted]


Update:

removed "ui"  from (syslinux folder) file syslinux.cfg as a possible fix for the "unknown keyword problem." 

# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo

 [ui was removed per another suggestion: [http://askubuntu.com/questions/141311/unknown-keyword-in-configuration-file-boot-error-when-booting-off-a-live-usb](http://askubuntu.com/questions/141311/unknown-keyword-in-configuration-file-boot-error-when-booting-off-a-live-usb) ]

**THIS FIXED THE PROBLEM!!!!** My USB flash drive now boots up (w/ 14.04 LTS)!!!! 

Making progress.....maybe this will be a good New Year... ):P

---

### Post by ozark_hillbilly on 2015-01-02
Update: Installed 14.04 LTS off of USB flash drive. Grub is still "bricked." Boot menu choices display but no keyboard input accepted. Forced to boot from USB flash. 

What next to correct Grub? update-grub or boot-repair maybe?

---

### Post by Bucky Ball on 2015-01-02
Hmm, that sounds like a problem I had on my machine that the grub with 14.04 actually fixed. 

If you boot the machine, get to the grub options and wait a while, does it boot into Ubuntu anyway? If so, if you restart Ubuntu (NOT shutdown the machine and press the on button but choose restart) does the keyboard now allow you to select a kernel/option?

---

### Post by ozark_hillbilly on 2015-01-02
"If you boot the machine, get to the grub options and wait a while, does it boot into Ubuntu anyway? "

What is a while? I waited a couple minutes.....do I need to go longer?

---

### Post by Bucky Ball on 2015-01-02
No, thirty seconds is about it. I couldn't use keyboard from a cold boot and so it would boot to Ubuntu after thirty seconds (default setting if there is no keyboard action). On restart keyboard was fine. Just took a punt the issues might have been related. ;)

---

### Post by ozark_hillbilly on 2015-01-02
Update:

did a re-install of 14.04 LTS and the Grub seems to be functional now. The system automatically booted into Ubuntu so I am closer to being* there*.

I want to keep this thread open a couple days while I clean everything up and try to get things back to where it was under 12.04 LTS. I will mark it solved at some point.... promise. 

Question: Should I have to restore anything off my backup to get my Desktop looking like it was under 12.04 LTS. Is there a way to look at the backup files easily and pick and choose what you want? Will restoring /Home bring things back to the Desktop? I realize I will have to download 3rd party stuff like Google Chrome & TOR to get it setup again.

---

### Post by oldfred on 2015-01-02
Almost all your settings are in /home. So if you have a copy of /home and restore it then all your settings should revert to that. 
Only if new software is so different and needs newer settings would further changes be required.You may want to back up the default /home system created before totally replacing it.

---

