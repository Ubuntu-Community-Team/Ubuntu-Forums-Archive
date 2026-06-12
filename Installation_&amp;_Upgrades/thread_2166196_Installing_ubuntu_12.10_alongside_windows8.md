---
title: "Installing ubuntu 12.10 alongside windows8"
date: 2013-08-08
forum: Installation &amp; Upgrades
---

### Post by melchor2 on 2013-08-08
Hi all,

I am writing here because I am really  dissapointed. I bought a laptop a week ago, and I am trying to install ubuntu alongside w8 for a couple of days. I am not able of it.

I have always installed ubuntu with other swindows without having any problem but this UEFI boot system is awful.

Let's go by parts. I have an asus k55vd. When I go to the bios , I disable the secure boot. Then from the setup options I choose 2.0 5.0 for the start, but I have  all this options:

windows manager boot system
UEFI 2.0 5.0
2.0 5.0
Pioner DVD-RW

I choose the third option. Then, I start from my USB with ubuntu, I make he instalation by parts, I assign the /root directory 20GB ext4 extension the /home 400Gb ext4 extension the swap 8GB( my ram memory is 8 GB), the /boot of 300 MB, ext4 extension and the grubbios of 1MB.

Well, all seems to work in a good way, but then when I have to restart the computer, for finish the installation, and I take off the USB the computer is asking me for it. If I put it, and I restart, I return to the installation, if I don't put it and I go to the BIOS boot setup , and I choose windows, obviously, starts on windows, but any other option appears so I don't know how I have to do it for see the GRUB and can choose the starting system.

Maybe I made a mistake an instead o install it form 2.0 5.0 I have to install it from UEFI2.0 5.0 . But before try more things I have prefered to ask, for see if some one can help me.

Thanks in advance

---

### Post by Boab1993 on 2013-08-08
Hi their melchor2,

Saw this problem before actually and got corrected on what it was about.

With UEFI theres actually a whole help page here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If that doesnt work, pretty sure theres a forums moderator who specialises in this and will no doubt help you out.

---

### Post by oldfred on 2013-08-08
If you installed Ubuntu with a bios_grub partition, that is for BIOS boot which with UEFI is called CSM or compatibility support module. Then to boot Ubuntu you have to turn UEFI off or turn CSM on. Then to boot Windows you have to turn UEFI on or CSM off. Not the easiest way to boot.

If both system are installed in UEFI boot mode then you can boot from grub menu to Windows and not have to go into UEFI/BIOS at all. Boot-Repair can also convert a BIOS install to UEFI install by uninstalling grub-pc and installing grub-efi. If booted in secure boot mode you can also update Ubuntu to have signed versions of kernel that will boot with secure boot on. But better for now to work with secure boot off.

Have you turned fast boot off? With some systems that is essential and for most needed to get USB ports to work for booting.

More info in the link in my signature.

Some other models Asus may be similar?
         [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)

            ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

            Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)

---

### Post by melchor2 on 2013-08-12
yes, thanks is solved. The boot repair worked succesfully. Thank you both.

But now after having ubuntu installed for one day more or less, I have entered into windows. Shut down from it, and now ubuntu is not being loaded, I don't know why.

---

### Post by oldfred on 2013-08-12
If Windows ran repairs it may turn fast boot back on or reset UEFI to auto boot Windows. Make sure what changes have been done and check from UEFI which is default boot.

---

### Post by melchor2 on 2013-08-12
everything seems to be ok in bios. fast boot and secure boot disabled, csm enabled and ubuntu boot option as the preferral...I don't know what is happening  I have to check it carefully

---

### Post by oldfred on 2013-08-12
If installed in UEFI mode, you do not want CSM enabled as that is BIOS boot. Windows will not boot with CSM mode at all, and depending on how you install Ubuntu it may boot with CSM, but then you cannot boot Windows from grub menu.

Post link to Boot-Repair's bootinfo report.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by melchor2 on 2013-08-12
for the installation, I select all the option in the way that I have mentiones before. Then I install ubuntu. After it, I use the boot-repair, following all the instructions. Within this instractions was change to an EFI mode. And thne, I went to the bios, I changed the boot order putting first the ubuntu option, and that is, worked fine, ubuntu and also windows8.

I had in the grub menu the otions 

ubuntu
ubuntuadvanced options
UEFI windows 8   - This works as w8
Recovery
windows8 loader (dev/sda)

And also I was working changing the OS, but after almost 24 hours, two hours ago, I tried to start my computer, and the grub is not appearing... I don't know

---

### Post by melchor2 on 2013-08-12
[http://paste.ubuntu.com/5974034/](http://paste.ubuntu.com/5974034/)

---

### Post by oldfred on 2013-08-12
It looks like Boot-Repair installed the UEFI boot version, not you do not have secure boot version. If you want to boot with secure boot on you have to boot Boot-Repair with secure boot on.

You have grub in the protective MBR and still have the bios_grub partition from the CSM/BIOS/Legacy mode install.

Does your Windows boot with secure boot off or only with it on? It will not boot in CSM mode.

---

### Post by melchor2 on 2013-08-13
Well, I am not an expert as you can see. 

I hace CSM on, and windows works properly take it off or not, and with seure boot ro not, and wth fast boot or not, and with any combination of them. But I can't see the grub menu, as I can saw yesteray and the day before yesterdy, so I don't know what have changed from it, I think that I will have to run the boot repair again.

Or you think that is better reinstall ubuntu, I did the installation with partitions, so I don't have to delete the files only format the root partition.

---

### Post by oldfred on 2013-08-13
If you go into UEFI menu do you not have a choice for ubuntu?

---

### Post by melchor2 on 2013-08-14
Yes I have it, but althought I put it as the first boot option, is not responding me. Worked during 24 hours more or less, but after it always starts on windows. This is my actual problem, I can't understand why.

---

### Post by oldfred on 2013-08-14
Afraid I cannot help as UEFI should let you specify which is first and boot that.

As you have said, some systems with CSM on seem to boot UEFI mode if found, and then if that is not found boot then boot CSM (BIOS) mode. So even with CSM on you can boot UEFI but not secure boot?

Boot-Repair says it reinstalled grub to efi partition so it should be correct.

It also has errors on query of UEFI shell which would show the internal UEFI settings. Some systems have the shell enabled and the internal settings can be reviewed. From shell you can also directly change UEFI settings.

       [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it).
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by melchor2 on 2013-08-16
I can fix the problem, using the boot-repair again

paste.ubuntu.com/5992420

the problem seems to be that one of the boot options change efi mode to legacy mode 

I have this boot otion at grub

ubuntu
windows 8 efibootmanager.exe - this seems to work, but maybe in some days change to legacy I don't know
windows8 UEFI boot loader - this enable legacy mode
/boot64/uefi.exe
windows8 loader (/dev/sda4) - this doesn't work

---

### Post by oldfred on 2013-08-16
That the one entry does not work is a bug in grub2's os-prober.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bkpbootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

