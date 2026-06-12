---
title: "Can't install kubuntu on new samsung"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2014-01-29
There is a new Samsung computer. I'm trying to install kubuntu from disc on it.  Since I was just getting blank screen, I searched internet and decided to disable fast bios etc.  Eventually, accidentally I can get to a point where I'm shown an option to "install kubuntu". I click on it. I'm shown a few options which come from Bios. Some of them allow me to continue installing. I'm asked location etc... A some point I'm asked network. This doesn't make any sense at all. First let me install it. .. I continue one way or another, for example I'm asked user pw (is it the same as encryption pw; it doesn't say)... What happens at the end: A blue page with a white strip. I can type characters there, or click enter to turn the page into white color. But nothing happens. What can I do: nothing. Everything dead.  ... This is extremely shameful thing. Previously I was able to install kuuntu with a few clicks , and in minutes. Now, new computers are intentionally(?) built as problematic devices; so only most expert people can install  linux, and others have to use windows. ... And windows doesn't work either.   Even if you don'tknow how to fix thisproblem, maybe you can explain why are things done so badly, incompatibly at this age. Intentionall or accidentally? What is the agenda. Why ask IP, to send pw's on network.  Being angry doesn't fix the problem. Probably your answers won't ither. You will say technical things I can't understand. But pls ty to do your best.

---

### Post by bjngchn on 2014-01-29
Boot options are not understandable at all. I modify things, nothing works. Boot options should be like this: 1. hd 2. cd 3. usb,.  in the past it was like this. Now, click something click enter to modify something; what happens, what does it mean? no info. I don't see good intentions in this. I'm not blaming linux community of course. But it looks like linux is being killed by computer manufacturers, and people can't sue them. .. This is like I buy a shoe and walk on the street. And one day new shoes are created. I wear them, and can't walk with them. Why is it done this way. No explanation. Are we all slaves, and have nothing to say.

---

### Post by oldos2er on 2014-01-29
Can you please describe your computer's hardware specs, and whether it's using UEFI and Secure Boot?

---

### Post by bjngchn on 2014-01-29
I don't know how to check specs.. Currently I can only view bios info. Sysinfo: SATAPort1 ST500...Sataport2: TSSTCorp CDDVDW..  CPU Vendor: Intel (R) CPU type: Core (TM) i-53230M Speed:2.6 ghz  CPU VT (vt-x): Supported Memory: 8gb  Bios version: P04ABE MICOM version : same..  ==========================ADVANCED: CPU power saving mode:enabled  hyperthreading :disabled EDB: Execute disable bit): Disabled  Fast Bios : Disabled (was enabled)  AHCI Mode Control: Auto  Battery life extension: Disabled USB s3 wake up: disabled   Security: Superviser/user/hdd pw" clear.  ============================ BOOT: Boot Device Priority:  Bootoption 1: Disabled in BBS order Boot option2: [P4 :TSSTcorp CDDCDW]  Hard Drive BBS priorities: Bot option 1: disabled CD/DVD Rom Drive BB Priorities: Boot Option 1: Disabled  Secure Boot : Disabled OS Mode selection: [CSM OS] (modified this a few times)  Internal LAN: enabled PXE OPROM: Disabled  ================ EXIT:   Boot Override  Dsiabled in BBS Order P4: TSSTcorp ...  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ These all make zero sense to me.   ================= UEFI: Yes it appear somewhere in Boot, but I modified it. It is under OS mode selection: UEFI OS, CSM OS, UEFI and Legacy OS ; are selections. I heard UEFI is bad, so I switch to CSM OS.  .............................

---

### Post by bjngchn on 2014-01-30
After I get to "install kubuntu" and click enter and a few easy steps, I'm asked to add network info (which doesn't make any sense). I choose ETH-dhcp  thing. it tries, and it doesn't work. Choosing "not configure at this time" doesn't work either. Only thing I can do is to click ESC button.  .. Now I'm o installer menu page.  Here are options: Choose language (done), Configure keyboard (done), Detect and mount CD-ROM (maybe done maybe not); Load debconf preconfig file (no idea), Load instaler components from CD (no idea); Detect network hardware (no idea), Configure the network (tried and failed); . NOW THE NEXT THING IS HIGHLIGHTED IN RED COLOR: Set up users and passwords: I don't know if I will be ever asked encryption pw. User and encryption pw should be different right? Or not (please answer this). In previous attempts, after i choose username/pw; screen turns into blue page with a white strip at the bottom, where I could type characters and turn the page more white and less blue. And nothing else can be done after this point. No errors, just it doesn't work. Esc doesn't work either..... So maybe I should skip this option and try others? :   Configure the clokc, Detect disks, partition disks, install the base system, configure the package manager, select and install software, install GRUB boot loader on a hard disk, Continue without boot loader, finish the instalation, check debconf priority, check CD-ROM integrity, save debug logs, execute a shell, eject a cd from the drive, abort the installation. ==========================NO IDEA if all these have to be done  all step by step, or  whether some of these can be skipped, or done in different order. Previously everythign was trivial. Click next,click ok, clikc yes. Noone really knows why things are done this way? Why noone is complaining. Why aren't we protesting all these on streets. ............Maybe we should buy very old computers  only and install kubuntu there, because new computers are all evil.

---

### Post by RadicaX on 2014-01-30
@OP.

You can also tell the the number that should be on the front of it. like my computer is a compaq SR5250NX. This allows one to check the specs. Sometimes it takes a moment for people to post too, so give it a bit of time, sorry though, it is a bummer when something like this is happening.

---

### Post by oldfred on 2014-01-30
If you have Windows in UEFI boot mode, you do need to install Ubuntu in UEFI boot mode.
You must have fast boot or always on hibernation off, better to have secure boot off.

 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)



 How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

### Post by bjngchn on 2014-02-07
[http://ubuntuforums.org/showthread.php?t=2204172](http://ubuntuforums.org/showthread.php?t=2204172)  Now, can install it, but can't make it work...

---

