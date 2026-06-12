---
title: "Cannot dual boot with win 7 after 16.04 install."
date: 2016-04-20
forum: Installation &amp; Upgrades
---

### Post by keith54 on 2016-04-20
I last used Ubuntu Hardy Heron god knows how long ago.

thought that I would give the new 16.04 a try.

Loaded a 64 .iso onto a pendrive and started in trial mode.

After a few tries I decided to install after shrinking my win7 install (using Easeus) leaving an unallocated partion on the end of the SSD of around 55 gbytes.

I aborted my first few tries at installing when i came up against some very ominous warnings about dual boot and UFEI.

On the last try I clicked go back again at this page and let it just sit there for a minute or so whilst i thought about what to do next.

It backed out and an install page appeared and I eventually chose the "something else" option and told it to install to the unallocated space on the end of the drive.

After choosing root, home and swap it installed ok and after a restart I was presented with a grub 2.02 beta 36 ubuntu 3 page with no win7 option.

Clicking the ubuntu option starts up ubuntu ok and I have updated a few programmes so Ubuntu install looks ok.

But no win7.

I loaded up the pendrive install again and was able to check that all the windows partitions and files were still there.

but no win7 boot option.

My computer is an Asus Z97-pro which boasts a UEFI bios.

I have tried the advice given in a similar post below but the advice fails at the first hurdle.

After typing in l /sys/firmware -l (from memory) it comes back no sys/firmware file found.

Any help would be much appreciated

Keith

---

### Post by oldfred on 2016-04-20
I have an Asus Z97-AR which I had to change a lot of settings in UEFI to get it to boot in UEFI mode from flash drive. I also just updated my UEFI to newest version and that reset everything and it again gave me issues on trying to boot a UEFI bootable flash drive.

Are both Windows & Ubuntu in UEFI boot mode?
Ubuntu on gpt partitioned drive can be either UEFI or BIOS.

       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Some other threads, I have posted my UEFI screens, if that would help. I can probably find them, but oldfred has 'several' posts on issue.

---

### Post by yancek on 2016-04-20
You would have saved yourself a lot of problems if you had come acrosse the Ubuntu page dealing with UEFI below.  If windows 7, is installed using UEFI/GPT, then you must also install Ubuntu or any Linux using UEFI/GPT.  If you are using MBR, then Ubuntu must also be installed MBR.  While booted into Ubuntu, copy and paste the command below which will tell you which is being used:

```
[LEFT][COLOR=#333333][FONT=monospace][ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"[/FONT][/COLOR][/LEFT]
```

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you used UEFI, you should have a FAT32 partition at the beginning of the drive with both windows and Ubuntu files in it.  Most likely scenario is that windows 7 was installed MBR and you booted and installed Ubuntu using UEFI.  If you can't resolve this, go to the site below while booted into Ubuntu and follow the instructions to get the boot repair script and run it but make sure you select only the opiton to "Create BootInfo Summary" and do not try to make any changes.  You can post a link to the output here and someone should be able to advise you.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by keith54 on 2016-04-20
Hi Yancek,

pasting your string comes back with 

"Legacy boot on HDD"
EFI boot on HDD

Hi Oldfred

following the link you posted and copying the code lines that they give into terminal gives (on the second command)

sudo apt-get install -y boot-info && boot-info
Reading package lists... Done
Building dependency tree       
Reading state information... Done
boot-info is already the newest version (4ppa35).
0 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
/usr/share/boot-sav/gui-g2slaunch.sh: line 33: hash: gksudo: not found
/usr/share/boot-sav/gui-g2slaunch.sh: line 35: hash: gksu: not found
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ Traceback (most recent call last):
  File "/usr/bin/glade2script", line 48, in <module>
    import gi
ImportError: No module named gi


Regards

Keith

---

### Post by keith54 on 2016-04-20
Hi Yancek,

I should have added that following the link to boot-repair that you gave seems to install it on my system but when i try to start it from the terminal by typing boot-repair I get the same result.

i.e Import error: No module named gi

Keith

---

### Post by oldfred on 2016-04-20
I just ran Boot-Repair on my 16.04 install. I do not have a live installer to test with.
Live installer does not include gksudo or gksu anymore.

While Report ran ok, it did show an error on terminal after I closed it. Some version issue.

```
/usr/bin/glade2script:4800: PyGIWarning: Notify was imported without specifying a version first. Use gi.require_version('Notify', '0.7') before import to ensure that the right version gets loaded.
  from gi.repository import Notify
/usr/bin/glade2script:4804: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3 as appindicator

```

---

### Post by keith54 on 2016-04-20
Problem has resolved itself with a daily system update.

Had me worried for a good few hours even though I had backed up all my data before trying an install.

Thank you all for your help

Keith

---

