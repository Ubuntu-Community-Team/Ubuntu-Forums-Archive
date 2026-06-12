---
title: "update-grub messing kernels, roots &amp; more upon installing &gt;one ubuntu"
date: 2016-06-11
forum: Installation &amp; Upgrades
---

### Post by lliseil on 2016-06-11
I'm testing a few Ubuntu versions before installing and helping with them at the local DIY house where we're building up a digital work shop.
For the record last time I tried to install an Ubuntu 14.04 LTS - Mageia 5 dual boot on a new, physical machine the Ubuntu [Grub-install messed up and prevented booting]("http://ubuntuforums.org/showthread.php?t=2306631&p=13410027#post13410027")). This time going all *buntu.

To test I'm using qemu/KVM with a virtual disk partitioned with a "physical" (MBR) partition and logicals (LVM).
Note I wanted to test installing the newer release after the "production" version, but went the other way for no good reason.

Using the network install aka Ubuntu MinimalCD I installed 
1. Slitaz Linux on a single physical partition (it uses grub legacy if I remember well)
2. **Lubuntu 16.04** with /boot on a large physical partition and "/" on lv1 (lvm2): all is fine
3. **Lubuntu 14.04** like its older sister with "/" on lv4: grub's borken:  found 37 entries of which 29 are broken (full version here [1]). Look how it mixes ubuntu kernels... 
```
### BEGIN /etc/grub.d/10_linux ### 
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-51c75e7b-854e-4323-80e1-d24448a826ee' {
  ...
  linux /vmlinuz-4.4.0-22-generic root=/dev/mapper/vg1-lv4 ro  splash quiet $vt_handoff
  initrd  /initrd.img-4.4.0-22-generic                                              
}
```
...and pretends to boot "Ubuntu 16.04 on partitionX" when in reality it boots Ubuntu 14.04 on partitionY (with 16.04's kernel ~8-0)
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 16.04 LTS (16.04) (sur /dev/mapper/vg1-lv1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-d6a187f0-4ecf-451d-9db9-313e089eb6de' {
  ...
  linux /vmlinuz-4.4.0-22-generic root=/dev/mapper/vg1-lv4 ro splash quiet $vt_handoff
  initrd /initrd.img-4.4.0-22-generic                                            
}       
```
[img]http://pic.al/fGd.png[/img]

4. **Lubuntu 12.04** : grub.cfg now has 22 entries of which 15 ones are broken and misleading [2]

5. **eOS 20151213** (based on Ubuntu Trusty): grub.cfg borken; so much that it actually takes half an hour to edit provided we are experts who never make a mistake (obviously #o) and won't break one or more Ubuntu.

[img]http://pic.al/gGd.png[/img] [img]http://pic.al/hGd.png[/img]

Actions I took
6. Booted in Lubuntu 16.04 and ran `os-prober`; it detected the four OSes just perfectly. Then run `**update-grub**`: found 28 entries of which 14 are broken [3]

I will now try to run `boot-repair` but I wished to ask: What am I doing wrong? and how do you add an Ubuntu to an existing one with a proper grub.cfg?

[1]: [https://ptpb.pw/Vdbt](https://ptpb.pw/Vdbt)
[2]: [https://ptpb.pw/DXG_](https://ptpb.pw/DXG_)
[3]: [https://ptpb.pw/RbeW](https://ptpb.pw/RbeW)

---

### Post by oldfred on 2016-06-11
Are you trying to use same /boot partition in all your installs? That will not work.
Each install, if it needs a /boot, needs a separate /boot. Normally with multiple installs you do not need /boot as a separate partition.
Only one install might need /boot partition as that seems standard with LVM. 
But grub2 can even directly boot into LVM. Never seen it but just a couple of days ago someone post Summary Repair for a flash  drive with grub2 and only one LVM partition. Grub loaded lvm driver to boot it.

 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2016-06-11
I suggest that what you are seeing is what we get when we mix Linux distributions that use Grub 2 with Linux distributions that use Grub Legacy. I saw this myself when Ubuntu first switched from Grub 0.97 (using /boot/grub/menu.list) to Grub 1.99 (using /boot/grub/grub.cfg) and I still had older versions of Ubuntu on the drive that used menu.list. 

You will notice that with Ubuntu and its flavours the previous kernels are listed in a sub-menu - Advanced options for Ubuntu. That is because grub.cfg allows for sub-menus which menu list does not. I also think that the Linux distributions that use Grub legacy will over-write the menu.list of other Linux distributions with their own menu list. And so you are getting both a menu.list file as well as the standard Grub 2 files such as those found in /etc/grub.d/. The result is multiple kernel menu entries when Grub os-prober is run.

Ubuntu developer Colin Watson did a lot of work to correct this in Ubuntu and its flavours. The answer is not to mix & match Grub 2 with Grub legacy. Or upgrade Grub legacy to Grub 2.

[https://help.ubuntu.com/community/Grub2/Upgrading](https://help.ubuntu.com/community/Grub2/Upgrading)

Regards.

---

### Post by lliseil on 2016-06-11
Thanks you guys for the skilled advices.
> **oldfred said:**
> Are you trying to use same /boot partition in all your installs? That will not work.
...
But grub2 can even directly boot into LVM.
Here the BootInfo summary report for this machine: [https://ptpb.pw/4PNH](https://ptpb.pw/4PNH)

You're right about *not* using a separate /boot partition for multiple GNU/Linux distros or versions, oldfred. That's what my last two attempts with dual or multi-booting with Ubuntu teach me clearly (and longingly, but this way I'll more probably remember it!).
First one was with Ubuntu Grub2 installed along side of Mageia grub, sharing a /boot partition.
This one with Ubuntus Grub2 on LVM all sharing a /boot partition (there's no grub in this case, Slitaz's is installed in its own partition).
On a side note the mixing (of kernels, root partitions and distros) is so dense it looks like it was deliberately created for that purpose. We used such a scheme with no issue back in the old grub time and that's another time I'll regret its simplicity and modularity.

How do you guys suggest moving /boot to each version's root partition?
I'll try booting each one starting with the oldest, unmount /boot (mounting it as /mnt/boot) and reinstall GRUB. I can't see it'll take any more fuss than chrooting into one after another.

---

### Post by oldfred on 2016-06-11
Back in 2009/2010, I hated grub2 as I chainloaded my grub legacy installs. But grub2 did not like installing to partitions.
But now I only use grub2.
I do not know LVM, but thought its main advantage was larger drives and using it for the entire drive. Then you can easily resize a partition. More appropriate for servers that may have several system folders as separate partitions. 
Some specific reason for your use of LVM? 
I have seen posts where some systems that default to LVM, the users suggested if multiple booting better to just use ext4.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)

I also converted to gpt partitioning to avoid primary, logical & extended partitions. Ubuntu can boot in BIOS or UEFI mode from gpt. Windows only boots in UEFI boot mode.
        
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT) 

I do boot multiple installs, most Ubuntu flavors. But once I get more than one or two installs, I turn off os-prober and maintain my own grub.cfg.
And I convert to booting the partition. With Debian based (not  sure about others), there is a link in / to the most current kernel. So double updates to get most recent menu kernel in main install are not required.
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Back when I still had grub legacy, I did move /boot from inside my install to a separate partition and updated fstab. That lasted all of a day or less, as then I realized I wanted a grub legacy only partition, so I move /boot back. I think I just used cp -a?
Now I just keep one main working install, and add my own entries into 40_custom to boot other installs. I also then have my own description which makes more sense than what os-prober creates.

Not sure I answered anything?

---

### Post by yoshii on 2016-06-11
If it gets way too messed up, and if you don't mind erasing some or most of the distros, you can use a LiveDVD of gParted or bootable USB drive of gParted.  Use gParted to erase every partition/distro you don't want to use anymore.  Then use a LiveCD of Puppy Linux to install GRUB4DOS (from the control panel) so that you can have whatever distro is left over booting.  

After you boot into that remaining distro, you can do a "sudo install-grub" to get back the normal Ubuntu grub2 instead of GRUB4DOS.    Then reboot.  Then you can (sudo) delete the menu.lst created by GRUB4DOS in your root area.  

I know it's kind of a complex procedure an it's a pain to have to create a boot drive.  But I was able to do all this stuff recently to fix up my hard drive for similar reasons.  

uNetBootIn is a good tool for creating bootable USB drives in case your CD/DVD-ROM drive doesn't work.  You have to edit your computer's BIOS boot order to allow for booting from other devices before the hard drive though.  And on some HP computers, you have to manually select the USB drive during boot.  

But on the plus side, Puppy Linux boots into root and there are some Ubuntu-compatible versions of Puppy Linux that have gParted and other tools on them.  Also, GRUB4DOS might look wierd, but it's menu is easier to edit for custom kernel commands even though it is pretty much the old grub.  Luckily the old grub within GRUB4DOS is sophisticated enough to be able to find the linux boot image and make a menu entry for that.  

It's kind of risky doing all this, but it can work if done right as long as you don't delete all of your working distros.  

And like I said, to get rid of GRUB4DOS, you do "sudo install-grub", let it finish completely, and then reboot.  Install-grub can't list what no longer exists so you'll be left with only the remaining distro entries hopefully.

---

### Post by lliseil on 2016-06-11
@grahammechanical please note that on my last post I wanted to multi-quote but quotes were lost upon clicking 'Go Advanced' and my message appeared below oldfred's first answer. 

OK I've moved all /boot "inside" the four / partitions., set /etc/grub.d/40_custom as wanted, ran `grub-install --root-directory=/ /dev/sda` then `update-grub2` from Xenial Xerius.
Yes oldfred you answered most of the stuff. Yet what'll happen when updating a kernel on, say, Trusty: Looks I'll have to edit 40_custom any time that happen, is it correct?
Hmm that's addressed in the links #4 you provided: a nice maintenance free chainloading same as in the good ol grub era (as well as turning off 30_os-prober), thank you for that!

> Some specific reason for your use of LVM? 

Yeap, laziness to foresee the unforeseeable ;) lvm2 allows us to start working on the OSes knowing I can shrink/enlarge partition on the fly any time needed. On the two distinguished boxes (from the pentium3 / Athlon XP and first dual core CPUs eras) we're testing the OSes we're going to both demo and set up on the other machines we'll sell at the local DIY (building up a digital workshop there).
That's also why I'm using msdos partitions tables: fits well with antique hardware --on which only XP can run in case they want to keep that old shi* software.

---

