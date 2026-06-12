---
title: "Windows 8/Ubuntu 12.10 dual install--boot repair issues"
date: 2013-03-29
forum: Installation &amp; Upgrades
---

### Post by munnster on 2013-03-29
My apologies if this has been addressed. If so please point me to the correct posts. I have been reading until I am cross-eyed.

I just got a Dell Inspiron 660s and wanted to dual boot with ubuntu. First go round, I ended up erasing windows and had to ask Dell for the recovery media disk (thankfully it worked to reinstall windows). After a few failed attempts to get both Windows and Ubuntu installed, I believe I have them in place after following this post as closely as possible [http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450) , Note: when I first restarted, I saw GRUB with both ubuntu and windows listed and following what this post said, I booted to windows. I haven't seen the GRUB screen since (and it now only boots to windows). I have used the boot repair utility and first it told me that the boot files are far from the start of the disk and I may want to create  a /boot partition (ext 4 >200MB, start of disk) so I did that even after getting a warning about moving the start sector of windows (no issues with booting into windows after that) This is a picture of Gparted's screen: (I do not know why they all say /boot now unless it has something to do with boot repair.)
[ATTACH=CONFIG]240689[/ATTACH]

Now the boot repair utility is giving me messages and I don't know what to do...
 
It first tells me that EFI is detected and to check my options. So clicking on advanced options this is what I get:
  [ATTACH=CONFIG]240685[/ATTACH][ATTACH=CONFIG]240686[/ATTACH][ATTACH=CONFIG]240688[/ATTACH]
I see that "secure boot" is checked in the third picture, but when I  uncheck (I do not want secure boot, correct?) it it has a "edit grub  configuration file" button and I don't know what I should change in there  (if I should be messing with any of it).

Please note that when I created the /boot partition it was in sda5 and I was sure it said efi as well, however now of course it does not say that. When I click apply (with settings as shown), I get this:
[ATTACH=CONFIG]240687[/ATTACH] 
After running this script in terminal, it tells me "Grub is still present. Please try again."  If I change the boot partition to sda5, I get a message: GPT detected. Please creat a BIOS-Boot partition (>1MB, unformated file system, bios_grub flag). This can be performed via tools such as Gparted. Then try again. Alternatively, you can retry after activatiing the [Separate /boot/efi partition:] option. 

I also read this morning that the efi should be fat32 (which it is in sda1), so should I combine sda5 with sda1 so it's big enough (as I was instructed to make it bigger than 200MB)? At this point, I know I am going in circles, so any direction would be GREATLY appreciated.

---

### Post by oldfred on 2013-03-29
Not sure you need the separate /boot. We used to see the issue a lot with BIOS boot, large drives, and older versions of grub. I always thought it was a BIOS issue, but it may have been a grub bug. One grub bug was fixed on very large >500GB root drives. Boot-Repair still flags it as an issue, but only if you cannot boot and get grub errors usually grub rescue> in BIOS boot is it then needed. Not sure if we have ever needed it with UEFI boot or not? But now that you have it, it should not matter.
But if you moved NTFS partition, it should have run chkdsk on reboot? It always has to run repairs after any change to size.

You (and all of us) have issues on whether in BIOS mode or UEFI mode and they are a lot different.
In UEFI mode, you only boot from efi partition. In gpt partitioning, the efi partition is the only partition with the boot flag. Gparted used boot flag to mean the efi partition in gpt, and it really means a lot different thing in MBR(msdos) partitioning.
If booting Ubuntu in BIOS mode you need the bios_grub partition. I only have BIOS but use gpt and have 1MB unformatted partition with the bios_grub flag. But you do not need a bios_grub partition if in UEFI boot mode.

So use gparted to remove boot flag from your sda5. Did you reinstall or move boot files to sda5? Not sure if Boot-Repair would have done that for you or not?

New UEFI systems sometimes just work, some have issues, and some just about do not want to work.
The ones that work will install Ubuntu and boot both Windows & Ubuntu with secure boot on or off.
Many only boot Windows with secure boot on, and with grub'2 shim file that has the Microsoft secure boot key Ubuntu will also boot.
But some have modified UEFI to only boot the Windows efi file in secure boot mode. In those cases Boot-Repair renames grub2's shim to the Windows file name and you actually boot into grub. Grub then chains back to Windows to boot. These usually need secure boot on. 

More info on file renaming:
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

May be best to just post the BootInfo report from Boot repair. It should just give a link to post.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by munnster on 2013-03-29
Thank you oldfred for responding so quickly.  

I honestly don't think windows ran Chkdsk on it's own. I had run it JUST previous to creating the sda5 boot file (moving windows partition) because there was some issue when I reinstalled windows again. (Perhaps when I shrunk the windows partition, but I honestly can't remember). I have started windows numerous times and AFAIK a scan has not been run (but I will say, I don't usually sit in front of my computer while it warms up either.)

I removed the boot flag from sda5...I installed the boot files (or perhaps thought I did) when I was making the partition. (You see I only know enough to be "dangerous"; I am still learning.  :sad: ) 

In boot-repair, I unchecked "secure boot" and left "backup and rename EFI files" checked. That (supposedly) fixed the boot menu(!!). and I was able to get into Ubuntu. YAY! I did get a message that said "Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file" How do I do that? I did not see any listing of sda1 in my BIOS, just 1st boot being my optical disk, second being (now UEFI ubuntu). Is that what they are talking about? I then went into BIOS and changed it to secureboot and I got this error: "Secure boot violation Invalid signature detected. check secure boot policy in setup" Should I install ubuntu secure remix 64bit as stated near the end of this post: [http://askubuntu.com/questions/206950/12-10-uefi-secure-boot-install?](http://askubuntu.com/questions/206950/12-10-uefi-secure-boot-install?) or can I leave secure boot unchecked and off in BIOS?

---

### Post by munnster on 2013-03-29
Obviously something in your directions was to KEEP the GRUB menu showing up because now that I've restarted and picked windows, I no longer see the grub menu again. *sigh* Sorry to be so slow...

---

### Post by munnster on 2013-03-29
I have both a boot repair info page from last night (still broken) [http://paste.ubuntu.com/5656647/](http://paste.ubuntu.com/5656647/) and a fixed info page [http://paste.ubuntu.com/5659020](http://paste.ubuntu.com/5659020) I'm not sure if either one of those will help you help me at all...

---

### Post by oldfred on 2013-03-29
Something wrong with links. 
One is BIOS two drive system, the other one drive UEFI boot?

---

### Post by munnster on 2013-03-30
Hmm...Well, by "drive" you mean hard drive, right? I had my external drive hooked up at one point while messing with all of this, but I don't know how it would have been a BIOS and the other UEFI. 
I am going to go over your post from yesterday and see what happens. I probably missed something.

---

### Post by munnster on 2013-03-30
I did notice something while in BIOS yesterday. I have a setting "Load Legacy OPROM" and it is enabled. I thought I remember reading about Legacy somewhere, but perhaps that was a different topic?...

---

### Post by oldfred on 2013-03-30
Post the link to another BootInfo report. Do not run repairs, just report. 
One of your previous links is in Polish? and the other English.

---

### Post by munnster on 2013-03-30
That is very strange because I have no issues with Polish(?) when I click on either one. Here is the report today. Mind you, I didn't restart after running boot-repair this morning, so GRUB actually came up. Not sure if that is going to make a difference in this report.
[http://paste.ubuntu.com/5662455/](http://paste.ubuntu.com/5662455/)
Hopefully it's in English this time! :)

Here is one after it would not boot into ubuntu (using live CD) (and after disabling BIOS Load Legacy OPROM [http://paste.ubuntu.com/5662580/](http://paste.ubuntu.com/5662580/)   Hoping it would make a difference, but it didn't.

---

### Post by oldfred on 2013-03-30
Boot-Repair says it is offering to install the signed versions. I would be sure to run that. 
Then with secure boot on see it it boots?

---

### Post by munnster on 2013-03-30
I see it on the boot info file--Recommended repair, but I don't know how to run that?  Can you tell me what steps to take? (I am not sure what setting it is talking about.) And that means I would have to disable the Load Legacy OPROM again, correct?

---

### Post by oldfred on 2013-03-30
Yes on Load Legacy off, so you are in UEFI mode. Not sure, but I think you need secure boot on. Ubuntu should still boot, but on some systems it may not. 
But after update then you may need secure boot on to boot Windows.

More info on Boot-Repair:
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by munnster on 2013-03-30
Ok, so this is the readout I got after running boot-repair with legacy off paste.ubuntu.com/5662827 and if I'm reading it correctly it supposedly moved grub back to sda4...(it says on line 671 that there is an error...) 

When I changed back to secure boot in BIOS, I got the "secure boot violation Invalid signature detected. Check secure boot policy in setup" message as usual (when I try to change that back).

---

### Post by oldfred on 2013-03-30
It does not look like you have the signed version installed of grub.efi and kernels. You do have shimx64.efi which is the signed grub, but systems need signed kernels also like this:
       /boot/vmlinuz-3.5.0-26-generic.efi.signed 

It looks like Boot-Repair just updated not installing the signed version. Did you tick off secure boot in Boot-Repair?

---

### Post by munnster on 2013-03-30
I unmarked the secure boot in the grub options. (Purge grub before reinstalling it is also unchecked.) Do you want me to run it with secure boot checked then? even though secure boot is off in BIOS?

---

### Post by oldfred on 2013-03-30
Try that, then turn secure boot on in UEFI/BIOS.

---

### Post by munnster on 2013-03-30
when I run it that way I get a message to open terminal and type (copy/paste) commands the commands I mentioned in my first post (sudo dpkg--configure-a etc) I copy and paste those and click the forward button and get "Grub is still present. Please try again."
Scratch that. I put them in one at a time and it seemed to work...now to check.

---

### Post by munnster on 2013-03-30
paste.ubuntu.com/5662907/ on line 656 is a message about typing something (I assume into terminal?)...Do I stay on this screen or do you want me to try something else before trying to reboot?

---

### Post by oldfred on 2013-03-30
It looks like that command is to install grub signed version.

---

### Post by munnster on 2013-03-30
I pasted it into terminal and it said "dpkg: error: unknown option -n

---

### Post by oldfred on 2013-03-30
Never used that so I do not know. If you copy & pasted it should be ok. Often when retyped a space or other error creeps in.
You showed it as one line. It looks like it should be 3? if one line commands have && to add or separate them together.

 sudo dpkg --configure -an
sudo apt-get install -fyn
sudo apt-get purge -y --force-yes grub*-common shim-signed linux-signed*

---

### Post by munnster on 2013-03-30
I was wondering about that! Thanks. (It was shown as all one line). I put in the first part and it still gives me the same error message (unknown option -n)
Here is the full readout:

leanne@leanne:~$ sudo dpkg --configure -an
[sudo] password for leanne: 
dpkg: error: unknown option -n

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by oldfred on 2013-03-30
My notes on my running of dpkg do not have the n.

       dpkg --configure -a

and sudo apt-get install normally has a package name after it. Not sure of options or it that is just setting some that needs before it runs the next command? Fount it, leave off the n on that. -f is fix and -y is yes, so that is just to fix & auto answer yes if needed.

so use this:
sudo apt-get install -fy

It seems like it converted a /n type entry to n? or corrupted a line ending? Which then would have made it multiple lines.

---

### Post by munnster on 2013-03-30
Ok, I got a long readout and I don't know how to make it so it doesn't take up a lot of space on the page. the second line didn't install or remove anything and the third line gave me a bunch of these: 
Note, selecting 'linux-signed-image-3.5.0-22-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.5.0-17-generic' for regex 'linux-signed*' with all different numbers and then a bunch of these:
Package 'linux-signed-image-3.5.0-18-generic' is not installed, so not removed  with different numbers and then a bunch of grub entries were removed.

The more I am reading this terminal, the more confused I get. It doesn't look like it installed anything(?) I have this line in the readout as well: 

The following packages will be REMOVED:
  grub-common* grub-efi-amd64* grub-efi-amd64-bin* grub-efi-amd64-signed*
  grub2-common* linux-signed-generic* linux-signed-image-3.5.0-26-generic*
  linux-signed-image-generic* shim-signed*
0 upgraded, 0 newly installed, 9 to remove and 317 not upgraded.
After this operation, 17.0 MB disk space will be freed.

---

### Post by oldfred on 2013-03-30
Is it just uninstalling old versions and you still have new version? 

Usually this just works. I do not understand why you are having these issues.

---

### Post by munnster on 2013-03-30
Probably because I only half understand what I'm doing. Sorry!

It looks like most of the versions (17, 18,19, 21, 22, 23, 24, 25, 26) were selected "for regex" but then it says versions (17, 18, 19, 21, 22, 23, 24, 25) were not installed "so not removed"

---

### Post by oldfred on 2013-03-30
I think the command was general and it looked for all possible versions. Since you did not have them, then there was nothing to uninstall. All that should be ok.
But we want to be sure we installed at least the newest and the newest that is the signed version.

---

