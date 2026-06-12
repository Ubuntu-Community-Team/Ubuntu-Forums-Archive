---
title: "Migrating Ubuntu 16.04 from HDD to SSD with Windows Dual Boot"
date: 2017-06-01
forum: Installation &amp; Upgrades
---

### Post by bl79 on 2017-06-01
So my current system is a 128GB SSD, a 1TB HDD and a 2TB HDD (also 16GB of RAM and an i5-2500k 3.3Ghz sandy bridge quad core CPU)

I've got Windows 10 installed on the SSD and Ubuntu 16.04 installed on the 2TB HDD with 3x separate partitions for swap, root and home. I've got my dual boot going and everything is groovy.

I just purchased a 500GB SSD and want to freshly install Windows 7 on it. I also want to clone my Ubuntu install onto it as well. Here I reach a fork in the road: I enjoy using Ubuntu as my primary OS for normal, casual tasks but still need Windows for things like video & photo editing, CAD work etc. My initial plan was to dual boot both Windows 7 and Ubuntu on the new 500GB drive and then also run a Windows 7 virtual machine inside the Ubuntu install. The idea being I could pop in and out of Windows from Ubuntu for simple things like accessing microsoft onenote and other basic Windows tasks. Then if I needed to use photoshop or something more resource intensive (or run into driver issues) I could just shut down and boot natively into Windows (admittedly a bit of a hassle).

It then occurred to me that maybe a more efficient way of doing this would be to only install Windows 7 and then run Ubuntu virtually. I don't think this would be a huge issue as most of my Ubuntu work is basic internet browsing and libreoffice document editing etc. My main concern with this option is 1) being able to clone my current Ubuntu install to the virtual install (I think this is doable) and 2) Running into issues due to the virtual machine not being totally independent. Example being Windows seems to struggle with my WiFi - Ubuntu currently works fine but from what I can tell if I was running Ubuntu as a virtual machine Windows Wifi issues might propagate through. The notion of having 2 totally separate OS is a bit comforting.

Not sure if anyone has input on the pros/cons of those 2 strategies but I'd be eager to hear.

Regardless of all that, I think step 1 is to create an clone/image of my current Ubuntu install as I'd like to preserve all of the customization I've got. From what I can gather the two popular options for this are either clonezilla or remastersys. My goal with either software is to both create a snapshot of my current Ubuntu install for backup purposes as well as use said snapshot to restore Ubuntu when transferring the install to my new SSD (or virtual machine).

My current plan based on my reading would be:
[LIST=1]
[*]Run windows 7 install CD and reformat my current 128GB C: drive to a D: drive for storage (NTFS). This will wipe my current Windows 10 install (thank god)
[*]Partition my 500GB SSD for a fresh Windows 7 install. Probably somewhere ~250GB for Windows (assuming I dual boot)
[LIST=1]
[*]Otherwise I guess I'd just format the entire thing if I decide to run Ubuntu virtually, then install VMware along with a fresh virtual install of Ubuntu
[/LIST]

[*]Run Ubuntu off a thumb drive and partition the remainder of the 500GB SSD and install a fresh version of 16.04
[*]Ensure I've got my GRUB loader working correctly (I had to play a bit with this initially since my Ubuntu and Windows installs were on different drives)
[*]Restore my fresh Ubuntu install using the snapshot I created with clonezilla or remastersys. Now I have Ubuntu exactly like I have it now
[/LIST]

Is this a reasonable approach? Any fatal flaws in my process?
This is the best clonezilla tutorial I've found so far but it doesn't cover making a backup .ISO exactly. I assume it's a similar process? Then follow the same instructions to just outright replace the fresh partition with the image. Given my root and home partitions are separate I figure I can just follow the instructions twice to create an image of each?
[http://www.dedoimedo.com/computers/clonezilla.html](http://www.dedoimedo.com/computers/clonezilla.html) 

Obviously I'm a bit overwhelmed with all the options and details. Any guidance would be much appreciated.

---

### Post by oldfred on 2017-06-01
Windows 10 default install is normally UEFI if hardware is UEFI.
But it depends on how you boot installer UEFI or BIOS.
Windows 7 DVD is BIOS only but can be converted to UEFI installer if copied to flash drive and files moved/renamed.

If sandy bridge system, it is UEFI hardware with CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

So are current installs UEFI or BIOS. Do you want UEFI or BIOS?
Are drives gpt or MBR(msdos)?
Normally gpt is used with UEFI, but Ubuntu can boot in BIOS mode from gpt partitioned drive.
Windows only boots in BIOS mode from MBR partitioned drive.
And Windows only boots in UEFI mode from gpt partitioned drive.

I started obsoleting my XP install soon after install of Ubuntu, but had one application that I needed for Windows so kept it for years. But I had Ubuntu on another drive and when converting Ubuntu from 32 bit to 64 with with new install changed to use gpt with BIOS boot on Ubuntu drive. Later with small SSD I configured for both the ESP - efi system partition for UEFI boot and the bios_grub partition for BIOS boot. BIOS for current BIOS only system and UEFI if I wanted to move drive to new UEFI system.

I do not know VM.

I do prefer with Ubuntu new clean install. You then get system configured correctly for new drive or VM. And then you copy /home or all your data into install. All user settings are in /home. Only if you have custom hardware configuration settings may you need those from /etc or if a server install may need other folders with database or Internet apps and files.
While a copy can be done  many users have issues with reinstalling grub, making sure there are no duplicate UUIDs, resetting fstab and a few other places with new UUIDs and other settings.

---

### Post by bl79 on 2017-06-05
Thanks for the input! It was a Windows 7 machine that got spyware tricked into installing Windows 10. I think everything was bios based

I've got ahead and installed a new windows 7 on sda1 and sda2 (the 500gb ssd). I also installed ubuntu 16.04 on sda5 and sda6 (for / and home respectively). Lastly, I then made a clone of my original ubuntu 16.04 install (still present on sdd5) and restored the image of the sdd5 root to my sda5 root (along with sdd6 home to sda6 home). My goal was this would simply clone everything to the 500gb SSD and I could basically pick up where I left off.

Now I think this may have worked but I've run into trouble with the boot loader. The boot loader recognizes my sdd5 ubuntu install and my windows 7 install but offers no option to boot into my newly cloned sda5 ubuntu install. 

No problem I thought, I'll just boot into the sdd5 original ubuntu and then follow the ChRoot instructions here to reinstall grub on sda
[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot) 

So I tried that but still no dice, same issue. Basically my options are "ubuntu" "advanced options for ubuntu" "windows 7 (sda1)" and then "Ubuntu (sdd5)" and "ubuntu advanced options (sdd5)". But even if I select the "ubuntu" option that doesn't have a partition listed it still boots into the sdd5 ubuntu.

Lastly I tried boot-repair which seemed promising. I changed the advanced options to install sda5 as the default to boot to. It appeared to recognize the sda5 cloned install but then once I applied the changes and followed the terminal instructions I was left with the same issue. Maybe worth noting that I told the boot repair to install grub on the broad sda drive and not the sda5 (this was explictly an option). I would've though this was the right move but maybe not?

Any insight would be great. I think I'm pretty close to having this all work if I can just sort out the booting. Then I'll tackle the VM stuff later

---

### Post by oldfred on 2017-06-05
Post link to Summary report from Boot-Repair.

When you clone install, it copies UUID.
Do you have same UUID in two partitions, that is not allowed.
Or when you cloned data, does grub have same UUID in all its files.

I have seen cases where users had booted & updated with duplicate UUIDs, but sometimes system used one partition and sometimes the other making a real mess to try to straighten out.

---

### Post by bl79 on 2017-06-06
OK cleaning this post up as I make progress. Stream of consciousness below the line

Anyway, definitely a UUID problem when cloning. I need to assign new UUIDs to at least my sda5 root, possibly sda6 /home (?). Happy to report that if I unplug the sata for the sdd5 drive where my legacy ubuntu install is on then Ubuntu boots properly from sda5 and even appears to find the correct /home and swap.

So now I intend on plugging everything back in and giving new UUIDs to my sda5 root and sda6 /home. I'll follow [this thread]("https://ubuntuforums.org/showthread.php?t=1786292") and use tune2fs (thanks oldfred!). Once I change the UUID I suspect I'll need to change the fstab for 2 reasons: 1) seems like even if I get the GRUB working with a reinstall/update my sda5 root will be referencing the old sdd6 /home. 2) I'm not certain GRUB will correct itself without modifying fstab anyway (although in that thread you suggest an install/update of grub to the main sda drive, so should work?)

Question at this point would be if I'll need to alter anything in fstab or similar to make sure that my sda7 swap partition is appropriately used by the new sda5 install. Could also use some hand-holding on modifying the /home UUID in fstab (which I anticipate will be an issue if not updated)

 
_______________________________________________________________________
Ah, I think that was my mistake. Per gparted the UUIDs of both my sda5 (new SSD ubuntu install, which I then cloned) and sdd5 (legacy ubuntu install, which I imaged) are now the same. 

I had previously followed this instructions here for boot-repair
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
I clicked the advanced option and had it make sda the primary boot device.

Hmm so I guess is there any way to recover what the appropriate UUID would be for my new sda5 500gb SSD now that I've over-written it? And even if I do recover the UUID it sounds like it's a bit of a pain to correct it? I should also probably note I cloned my legacy sdd6 (/home) to my new sda6 (/home) as well. Those UUIDs match as well.

Maybe it's just easiest to do a fresh install of ubuntu on my sda5 SSD and then rework it from there. How can I avoid writing over the UUIDs again though? I'm going to do some googling....

First thought that jumps out at me is to do a clean install of ubuntu. Record what the sda5 and sda6 UUIDs are. Then restore sda5 and sda6 from my clonezilla image. Lastly I'd have to manually edit fstab with the UUIDs that I recorded after a fresh install. Best instructions I can find are the top answer to this thread:
[https://askubuntu.com/questions/171446/how-to-fix-the-uuid-in-grub-after-restore-from-another-machine](https://askubuntu.com/questions/171446/how-to-fix-the-uuid-in-grub-after-restore-from-another-machine)

Ideally, if I perform the above steps, I'm hoping I can have sda5 (SSD ubuntu clone) boot as the default, but also have GRUB offer the option to boot sda1 Windows 7 (of course) and also my legacy sdd5 ubuntu (will probably eventually get rid of but nice to have both whynot)

OK, reading some more and it seems like I can assign sda5 and sda6 new UUIDs. Then may need to edit fstab but I'm hoping I can just chroot into sda5 from a live CD and reinstall grub. Then everything should be good? At worst run another boot repair? Seems like if they have unique UUIDs the boot repair should be able to find them all and sort it out? Also realizing my earlier plan of reformatting wouldnt work since the UUIDs are overwritten when cloning. My only option is to generate new UUIDs

---

### Post by oldfred on 2017-06-06
If you have both connected I do not think Boot-Repair will work or work correctly.
Best to disconnect old drive. So then you should be able to boot SSD.

You can directly see UUID:
       sudo blkid -c /dev/null -o list 
And you can edit fstab after changing UUIDs:
sudo nano /etc/fstab

And not just update grub with 'sudo update-grub' but full update
Grub remembers by drive/UUID where to reinstall.

 #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc  

"All" you have to do is replace old UUID with new UUID.

You can also manually boot if grub is misconfigured but functional.
If you can get to grub menu you can manually edit boot stanza with correct UUID.
Change from hd0,5 and sda5 to correct drive/partition you have your install.
      
 set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

This is why I usually suggest a new clean install. 
And then just copy /home into new install with cp or rsync.
Same command as here:
      
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by bl79 on 2017-06-09
Alrighty I think I've almost got it now. Thanks!

For posterity:
I generated new UUIDs for sda5 / and sda6 /home. Used tune2fs although I see now gparted also simply has a "new UUID" option if you right click on the partition.
Then I booted from a live CD and used chroot to install and update-grub on sda. This worked to get ubuntu to boot to my sda5 / root but my old sdd5 was mounted as /home as suspected.
I then altered etc/fstab using the directions above and top answer in this thread (note I didn't have to play with the config file): [https://askubuntu.com/questions/171446/how-to-fix-the-uuid-in-grub-after-restore-from-another-machine](https://askubuntu.com/questions/171446/how-to-fix-the-uuid-in-grub-after-restore-from-another-machine) 
You can find the UUIDs on gparted. Then it's as simple as just copy/pasting the correct UUIDs into fstab.

After that I rebooted and everything was great. After reboot I installed and updated grub as advised. I attempted to use oldfred's [COLOR=#000000]sudo dpkg-reconfigure grub-pc  instructions although it brought up a bunch of terminal queries and I got nervous and exited (it seemed similar to boot-repair...). Main question is when it prompts me to select a drive for grub, should I broadly select the "sda" option of the /root "sda5" option?

Otherwise it's working great. [/COLOR]Thanks for the help!

---

### Post by oldfred on 2017-06-09
Whether UEFI or BIOS the correct answer on where to install grub2's boot loader is always a drive like sda or sdb.
Almost never to a partition.

And with UEFI, grub knows to install UEFI boot files to the partition flagged as the ESP. For whatever reason though it only installs to the ESP on sda.
BIOS install will correctly install to the MBR of whatever drive you specify.

If you run these it will show drive where grub expects to reinstall, they need to match drive you want. If not the dpkg command resets the reinstall location.
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short

---

