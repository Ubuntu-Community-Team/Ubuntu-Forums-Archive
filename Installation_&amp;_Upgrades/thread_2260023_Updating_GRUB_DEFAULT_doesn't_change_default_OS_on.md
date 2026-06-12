---
title: "Updating GRUB_DEFAULT doesn't change default OS on dual boot machine"
date: 2015-01-08
forum: Installation &amp; Upgrades
---

### Post by rob-mengert on 2015-01-08
Hello everyone.  I have a dual boot of Ubuntu desktop 14.04 and Ubuntu server 14.04 on a machine.  I'm going to manage the machine through another host and was looking for a way in a deterministic fashion to boot either the desktop or server install without having to watch the machine boot and selecting from the grub menu. I wrote a script which rewrites GRUB_DEFAULT in /etc/default/grub based on what I would like to boot next.  


Running the script while the desktop install is active causes the next boot to go into the server install as expected.  Unfortunately running the same script on the server install does not force the next boot to go into the desktop install.  The server install seems to be modifying a different /etc/default/grub file than what is actually being used to boot the machine.  Running the script on the server to change the value of GRUB_DEFAULT from 4 (server install) to 0 (desktop install) does not work, when the machine boots next the 4th item is still highlighted in the grub menu and the server install boots again. 


```
#!/bin/bash


bootPref=$1


# Perform argument validation
if [ $# -ne 1 ] ; then
   echo -e "Too many parameters passed, acceptable parameters:\r
server \r
desktop"
   exit 0
fi 


# Confirm user is root
if [[ $EUID -ne 0 ]]; then
  echo "$(date +%m-%d-%y_%H-%M-%S) - $0 - You must be root, currently you are: $(whoami)" 2>&1
  exit 1
fi


case $bootPref in
  server)
  sed -i 's/GRUB_DEFAULT=./GRUB_DEFAULT=4/g' /etc/default/grub  
  update-grub
  ;;
  
  desktop)
  sed -i 's/GRUB_DEFAULT=./GRUB_DEFAULT=0/g' /etc/default/grub
  update-grub
  ;;


  *)
   echo -e "Invalid parameter passed, acceptable parameters:\r
server \r
desktop"
  
  exit 1


esac


cat /etc/default/grub


exit 0

```

The server partition was installed first and then the desktop partition.  Is there some grub magic required to get this working?  

Any help would be greatly appreciated, thanks in advance.

---

### Post by oldfred on 2015-01-08
You have two copies of grub, one for desktop & one for server. But only one copy is in control and boots from MBR into grub in one install. 

So you have to edit the correct copy of grub.

 
Reboot grub to different system default
[http://ubuntuforums.org/showthread.php?t=1310463](http://ubuntuforums.org/showthread.php?t=1310463)
sudo grub-reboot 1
sudo grub-reboot "Microsoft Windows 7"
Boot non-default entry only once
The command grub-reboot is very helpful to boot another entry than the default only once. GRUB loads the entry passed in the first command line argument, when the system is rebooted the next time. Most importantly GRUB returns to loading the default entry for all future booting. Changing the configuration file or selecting an entry in the GRUB menu is not necessary.
Note: This requires GRUB_DEFAULT=saved in /etc/default/grub (and then regenerating grub.cfg) or, in case of hand-made grub.cfg, the line set default="${saved_entry}".

---

### Post by rob-mengert on 2015-01-09
@Oldfred, thanks for the reply.  Your suggestion worked and I will mark the thread as solved.  Just out of curiosity, is there a way to allow both installs to modify the same grub configuration?

---

### Post by oldfred on 2015-01-09
With grub2 I always have had one grub in control and used it and lots of editing of 40_custom.

Back with grub legacy, I used a separate grub only partition. That does not have any of the auto update features that grub2 now has when inside a distribution. But I do install grub2 to flash drives and totally manually maintain a grub.cfg. You could do that. And with a partition boot do not have to edit with a kernel update in either install.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Or you could edit the working install directly and modify script to mount & edit that same working grub when booted in the other install, not its own grub.

With 2 installs, a major grub update in either install may reinstall its copy of grub into MBR. Then your working grub may change. To prevent that change or blank out the location to reinstall on the non-working install. Unchoose all options, then check again that reinstall location is blank.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

With second line you want this blank. This shows my drive:
grub-pc/install_devices: /dev/disk/by-id/ata-FUJITSU_MHV2160BT_PL_NY07T6A28HNP

---

