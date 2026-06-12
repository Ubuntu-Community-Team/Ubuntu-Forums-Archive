---
title: "Ubuntu 14.04 Grub Error After Install Win 8.1"
date: 2015-02-11
forum: Installation &amp; Upgrades
---

### Post by s.boone35223 on 2015-02-11
Last year I blew away my Windows 8 trying to work through some Ubuntu 14.04 upgrade issues.  I recently saw a Youtube video where Windows 7 was installed on an Ubuntu 14.04 PC. 
Step 1.  I shrunk my Ubuntu partition
Step 2. Successfully installed Windows 8.1 on the unallocated space (240GB)
Step 3. Used Easy BCD 2.2 to create Ubuntu boot menu.  I saw Ubuntu on the hard drive.  After installation, the computer boots to the Grub Rescue> prompt.  Cannot get back to Windows without resetting PC.
Step 3.  Reset PC, then rebooted using live Boot-Repair boot USB.  Boot repair will not repair Grub with message 'Filesystem repair requires to unmount partitions.  Please close all your programs.  Then close this window.'  My boot information report is at [http://paste.ubuntu.com/10177356/](http://paste.ubuntu.com/10177356/).
Is my Ubuntu salvageable?  If so, I need simple step by step actions to accomplish.  Any assistance will be appreciated.

---

### Post by yancek on 2015-02-11
> Used Easy BCD 2.2 to create Ubuntu boot menu

Look at the info for sda1.  It is an efi partition so you are using UEFI/GPT to boot both windows and Ubuntu.  You can see both windows and Ubuntu files on that partition.  
You should have an option somewhere in your BIOS to select UEFI/GPT or MBR/Legacy and you want UEFI/GPT.  Try changing that.  EasyBCD is just a front-end for a modified Grub built to run on windows.  I don't know if it is capable of booting UEFI/GPT, you might investigate that.

Also, sda2 shows as a windows recovery partition but the format shows a Linux filesystem, ext4.  I don't think it will be of much use but there may be some way to repair it.

---

### Post by oldfred on 2015-02-11
With UEFI, you should not need EasyBCD except perhaps to repair Windows.

The sda2 is Windows system reserved. It must have no format, but is shown as ext4. You can use gparted and at bottom of types of formats is none.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

You show a lot of kernels, once booting house clean some of those.

You also show too many UEFI entries. Some older systems became total bricks (return to mfg) when UEFI NVRAM became over half full. But even if system is working best not to have too many UEFI entries.
This shows many duplicates?

efibootmgr -v

---

### Post by LostFarmer on 2015-02-11
I do not know the correct way to fix problem but suspect your main error is sda2 and sda3 has the same UUID, that should never happen.

   Your ubuntu was installed as / on sda2 but would say it is now on sda3 but your grub.cfg says sda2 and likely your /etc/fstab will also be wrong.

---

### Post by s.boone35223 on 2015-02-11
I verified that BIOS is set to UEFI.  Using Gparted, I changed boot to msftres and format from ext4 to clear.  Sda2 still shows the red flag symbol.  When I rebooted, Windows 8.1 loaded.  I am not following the articles you referenced.  Would it be easier to start over or try to salvage what I have?

---

### Post by oldfred on 2015-02-12
Gparted will show unformatted partitions like the bios_grub or Microsoft reserved as errors. And it shows encrypted partitions including encrypted swap as an error as it cannot read it.
 Other errors then need to be reviewed.

If you re-install be sure to sue only Something Else. There is a major bug where entire drive is erased with the auto install options, particularly on reinstall where it says it overwrites Ubuntu but overwrites entire drive. Bug is fixed but not in most of the current ISO.

Re-install is a relatively quick way to redo things.

But I think you should also house clean UEFI entries.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
modprobe efivars
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by s.boone35223 on 2015-02-12
Sorry I am slow, but . . . once I run the sudo efibootmgr -v and see the efi entries, how will I know which ones I need to remove?

---

### Post by oldfred on 2015-02-12
Boot-Info script showed many duplicates as it ran the sudo efibootmgr command as one of its commands. It looks like you had many duplicates.

---

### Post by Gvarelov on 2015-02-13
Dropping to grub_rescue prompt (as per official GRUB2 documentation) is a sure sign that GRUB's normal module didn't load. GRUB can't locate its "prefix" directory anymore. And that's where the module resides. It is unclear where are you standing right now after you applied advice from previous posters. Are you still getting the grub_rescue? Do you still need to restart to get your Windows install? And how is that you get GRUB the first time and then after restart get Windows?
Can you issue the 
```
set
```
command while at grub_rescue shell? Can you make a note of the value of the "prefix" variable?

---

