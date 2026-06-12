---
title: "Grub does not behave normally after upgrade to 10.10"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by Alver on 2011-03-13
Hi all, some days ago I upgraded my 10.04 Ubuntu to 10.10. Upgrading took quite some time as I had already witnessed in previous upgrades. Everything seems to work fine after this operation but for the Grub. I can no longer set the timer! It means I have to manually push "Enter" to start booting. I also noted that I cannot change the font size of the Grub any longer. I have not seen such behaviour during previous upgrades (I started upgrading with U 9.04). It is of course not a big problem but if any of the learned members of this forum could offer an explanation or remedy it would be most welcome.

Alver

Toshiba L505-10M with dual boot W7/U 10.10  500 GB HD & 6 GB RAM

---

### Post by tommcd on 2011-03-13
> **Alver said:**
> 
Upgrading took quite some time as I had already witnessed in previous upgrades. ...
 I have not seen such behaviour during previous upgrades (I started upgrading with U 9.04). It is of course not a big problem but if any of the learned members of this forum could offer an explanation or remedy it would be most welcome.

Ubuntu 9.04 still used grub-legacy, while Ubuntu 9.10 and after used grub2. Are you sure you have completely upgraded to grub2? [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
That would be one thing to check. Also read that entire tutorial, since the configuration of grub2 is very different from grub-legacy.

I always do clean installs of Ubuntu. I never do dist-upgrades. Since you noted that "*Upgrading took quite some time as I had already witnessed in previous upgrades*..." Please be aware that clean installs are fast and dead simple. Plus you start with a clean slate, which eliminates essentially all of the problems associated with dist-upgrades. See the sticky in this section of the forums about upgrading Ubuntu for more info about problems with upgrades.

---

### Post by Alver on 2011-03-13
> **tommcd said:**
> Ubuntu 9.04 still used grub-legacy, while Ubuntu 9.10 and after used grub2. Are you sure you have completely upgraded to grub2? [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
That would be one thing to check. Also read that entire tutorial, since the configuration of grub2 is very different from grub-legacy.

I always do clean installs of Ubuntu. I never do dist-upgrades. Since you noted that "*Upgrading took quite some time as I had already witnessed in previous upgrades*..." Please be aware that clean installs are fast and dead simple. Plus you start with a clean slate, which eliminates essentially all of the problems associated with dist-upgrades. See the sticky in this section of the forums about upgrading Ubuntu for more info about problems with upgrades.

My Grub is (GRUB) 1.98+20100804-5ubuntu3. Isn't this the right one?

---

### Post by kagerato on 2011-03-13
> **Alver said:**
> My Grub is (GRUB) 1.98+20100804-5ubuntu3. Isn't this the right one?

It's extraordinarily confusing, but 1.98 is, in fact, Grub 2.

What happened here is that the old grub was still on 0 for the major number, so a major version bump incremented it to one.  Yet this was the second major version of Grub and everyone naturally started calling it Grub 2.  >_<

---

### Post by Alver on 2011-03-13
> **kagerato said:**
> It's extraordinarily confusing, but 1.98 is, in fact, Grub 2.

What happened here is that the old grub was still on 0 for the major number, so a major version bump incremented it to one.  Yet this was the second major version of Grub and everyone naturally started calling it Grub 2.  >_<
Since I, most probably,  do have the right version of Grub, where do I go from here?

---

### Post by kagerato on 2011-03-13
> **Alver said:**
> Since I, most probably,  do have the right version of Grub, where do I go from here?

The timeout, graphics mode, and several other general Grub 2 options are controlled by the text configuration file /etc/default/grub (for Ubuntu and Debian, at least).

Whenever you make changes to the Grub config there, or to grub scripts in /etc/grub.d/ , you must issue the command `update-grub` in order to apply them to the real conglomerated grub config (stored at /boot/grub/grub.cfg ).

This information is a short summary of things you can learn at:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by kansasnoob on 2011-03-13
It would help to see the output of a couple of commands, please copy-n-paste because the first one is actually a few commands combined:

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

```
ls /boot/grub
```

Please post the output in code tags using the # symbol at the top of this reply box. It makes things much easier to read :)

---

### Post by Alver on 2011-03-14
> **kansasnoob said:**
> It would help to see the output of a couple of commands, please copy-n-paste because the first one is actually a few commands combined:

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

```
ls /boot/grub
```

Please post the output in code tags using the # symbol at the top of this reply box. It makes things much easier to read :)
Thank you very much for your advice and instructions. Can you be somewhat more detailed on the different steps? I am an absolute novice as far as command line instruction go, so please be patient.

Alver

---

### Post by tommcd on 2011-03-14
> **Alver said:**
> Can you be somewhat more detailed on the different steps? 
Open a terminal and copy and paste the first command Kansasnoob posted into the terminal:
```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```
Post the output of that command here.
Then copy and paste the second command into the terminal: ```
ls /boot/grub
```
And post the output of that command here as well.

---

### Post by Alver on 2011-03-14
1)This is the answer to the first (series) of commands:
"alver@alver-laptop:~$ sudo grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
[sudo] password for alver: 
grub-install (GRUB) 1.98+20100804-5ubuntu3
Pakket: grub
Staat: niet geïnstalleerd (=not installed)
Pakket: grub-pc
Staat: geïnstalleerd (=installed)
Pakket: grub-common
Staat: geïnstalleerd
Pakket: os-prober
Staat: geïnstalleerd"
I'm running a dutch language version!

2) This is the answer to the second command:
"915resolution.mod	     gcry_serpent.mod	 parttool.lst
acpi.mod		     gcry_sha1.mod	 parttool.mod
affs.mod		     gcry_sha256.mod	 password.mod
afs_be.mod		     gcry_sha512.mod	 password_pbkdf2.mod
afs.mod			     gcry_tiger.mod	 pbkdf2.mod
aout.mod		     gcry_twofish.mod	 pci.mod
ata.mod			     gcry_whirlpool.mod  play.mod
ata_pthru.mod		     gettext.mod	 png.mod
at_keyboard.mod		     gfxmenu.mod	 probe.mod
befs_be.mod		     gfxterm.mod	 pxeboot.img
befs.mod		     gptsync.mod	 pxecmd.mod
biosdisk.mod		     grldr.img		 pxe.mod
bitmap.mod		     grub.cfg		 raid5rec.mod
bitmap_scale.mod	     grubenv		 raid6rec.mod
blocklist.mod		     gzio.mod		 raid.mod
boot.img		     halt.mod		 read.mod
boot.mod		     handler.lst	 reboot.mod
bsd.mod			     hashsum.mod	 regexp.mod
bufio.mod		     hdparm.mod		 reiserfs.mod
cat.mod			     hello.mod		 relocator.mod
cdboot.img		     help.mod		 scsi.mod
chain.mod		     hexdump.mod	 search_fs_file.mod
cmostest.mod		     hfs.mod		 search_fs_uuid.mod
cmp.mod			     hfsplus.mod	 search_label.mod
command.lst		     iorw.mod		 search.mod
configfile.mod		     iso9660.mod	 serial.mod
core.img		     jfs.mod		 setjmp.mod
cpio.mod		     jpeg.mod		 setpci.mod
cpuid.mod		     kernel.img		 sfs.mod
crc.mod			     keystatus.mod	 sleep.mod
crypto.lst		     linux16.mod	 splashimages
crypto.mod		     linux.mod		 tar.mod
cs5536.mod		     lnxboot.img	 terminal.lst
datehook.mod		     loadenv.mod	 terminal.mod
date.mod		     locale		 terminfo.mod
datetime.mod		     loopback.mod	 test.mod
diskboot.img		     lsmmap.mod		 tga.mod
dm_nv.mod		     ls.mod		 trig.mod
drivemap.mod		     lspci.mod		 true.mod
echo.mod		     lvm.mod		 udf.mod
efiemu32.o		     mdraid.mod		 ufs1.mod
efiemu64.o		     memdisk.mod	 ufs2.mod
efiemu.mod		     memrw.mod		 uhci.mod
elf.mod			     minicmd.mod	 unicode.pf2
example_functional_test.mod  minix.mod		 usb_keyboard.mod
ext2.mod		     mmap.mod		 usb.mod
extcmd.mod		     moddep.lst		 usbms.mod
fat.mod			     msdospart.mod	 usbtest.mod
font.mod		     multiboot2.mod	 vbeinfo.mod
fshelp.mod		     multiboot.mod	 vbe.mod
fs.lst			     nilfs2.mod		 vbetest.mod
functional_test.mod	     normal.mod		 vga.mod
gcry_arcfour.mod	     ntfscomp.mod	 vga_text.mod
gcry_blowfish.mod	     ntfs.mod		 video_bochs.mod
gcry_camellia.mod	     ohci.mod		 video_cirrus.mod
gcry_cast5.mod		     part_acorn.mod	 video_fb.mod
gcry_crc.mod		     part_amiga.mod	 video.lst
gcry_des.mod		     part_apple.mod	 video.mod
gcry_md4.mod		     part_bsd.mod	 videotest.mod
gcry_md5.mod		     part_gpt.mod	 xfs.mod
gcry_rfc2268.mod	     partmap.lst	 xnu.mod
gcry_rijndael.mod	     part_msdos.mod	 xnu_uuid.mod
gcry_rmd160.mod		     part_sun.mod	 zfsinfo.mod
gcry_seed.mod		     part_sunpc.mod	 zfs.mod"

I hope this makes sense to you. Thank you for your guidance.

Alver

---

### Post by kansasnoob on 2011-03-15
The latter command output is very hard to read, not because of language, but because it's not in "code" tags. Just as an example here's the output of "ls /boot/grub" from my machine with and without code tags:

```
lance@lance-desktop:~$ ls /boot/grub
915resolution.mod            gcry_serpent.mod         part_sunpc.mod
acpi.mod                     gcry_sha1.mod            parttool.lst
affs.mod                     gcry_sha256.mod          parttool.mod
afs_be.mod                   gcry_sha512.mod          password.mod
afs.mod                      gcry_tiger.mod           password_pbkdf2.mod
aout.mod                     gcry_twofish.mod         pbkdf2.mod
ata.mod                      gcry_whirlpool.mod       pci.mod
ata_pthru.mod                gettext.mod              play.mod
at_keyboard.mod              gfxmenu.mod              png.mod
befs_be.mod                  gfxterm.mod              probe.mod
befs.mod                     gptsync.mod              pxeboot.img
biosdisk.mod                 grldr.img                pxecmd.mod
bitmap.mod                   grub.cfg                 pxe.mod
bitmap_scale.mod             grubenv                  raid5rec.mod
blocklist.mod                gzio.mod                 raid6rec.mod
boot.img                     halt.mod                 raid.mod
boot.mod                     handler.lst              read.mod
bsd.mod                      hashsum.mod              reboot.mod
bufio.mod                    hdparm.mod               regexp.mod
cat.mod                      hello.mod                reiserfs.mod
cdboot.img                   help.mod                 relocator.mod
chain.mod                    hexdump.mod              scsi.mod
cmostest.mod                 hfs.mod                  search_fs_file.mod
cmp.mod                      hfsplus.mod              search_fs_uuid.mod
command.lst                  iorw.mod                 search_label.mod
configfile.mod               iso9660.mod              search.mod
core.img                     jfs.mod                  serial.mod
cpio.mod                     jpeg.mod                 setjmp.mod
cpuid.mod                    kernel.img               setpci.mod
crc.mod                      keystatus.mod            sfs.mod
crypto.lst                   linux16.mod              sleep.mod
crypto.mod                   linux.mod                tar.mod
cs5536.mod                   lnxboot.img              terminal.lst
datehook.mod                 loadenv.mod              terminal.mod
date.mod                     locale                   terminfo.mod
datetime.mod                 loopback.mod             test.mod
diskboot.img                 lsmmap.mod               tga.mod
dm_nv.mod                    ls.mod                   trig.mod
drivemap.mod                 lspci.mod                true.mod
echo.mod                     lvm.mod                  udf.mod
efiemu32.o                   mdraid.mod               ufs1.mod
efiemu64.o                   memdisk.mod              ufs2.mod
efiemu.mod                   memrw.mod                uhci.mod
elf.mod                      minicmd.mod              unicode.pf2
example_functional_test.mod  minix.mod                usb_keyboard.mod
ext2.mod                     mmap.mod                 usb.mod
extcmd.mod                   moddep.lst               usbms.mod
fat.mod                      moreblue-orbit-grub.png  usbtest.mod
font.mod                     msdospart.mod            vbeinfo.mod
fshelp.mod                   multiboot2.mod           vbe.mod
fs.lst                       multiboot.mod            vbetest.mod
functional_test.mod          nilfs2.mod               vga.mod
gcry_arcfour.mod             normal.mod               vga_text.mod
gcry_blowfish.mod            ntfscomp.mod             video_bochs.mod
gcry_camellia.mod            ntfs.mod                 video_cirrus.mod
gcry_cast5.mod               ohci.mod                 video_fb.mod
gcry_crc.mod                 part_acorn.mod           video.lst
gcry_des.mod                 part_amiga.mod           video.mod
gcry_md4.mod                 part_apple.mod           videotest.mod
gcry_md5.mod                 part_bsd.mod             xfs.mod
gcry_rfc2268.mod             part_gpt.mod             xnu.mod
gcry_rijndael.mod            partmap.lst              xnu_uuid.mod
gcry_rmd160.mod              part_msdos.mod           zfsinfo.mod
gcry_seed.mod                part_sun.mod             zfs.mod

```

lance@lance-desktop:~$ ls /boot/grub
915resolution.mod            gcry_serpent.mod         part_sunpc.mod
acpi.mod                     gcry_sha1.mod            parttool.lst
affs.mod                     gcry_sha256.mod          parttool.mod
afs_be.mod                   gcry_sha512.mod          password.mod
afs.mod                      gcry_tiger.mod           password_pbkdf2.mod
aout.mod                     gcry_twofish.mod         pbkdf2.mod
ata.mod                      gcry_whirlpool.mod       pci.mod
ata_pthru.mod                gettext.mod              play.mod
at_keyboard.mod              gfxmenu.mod              png.mod
befs_be.mod                  gfxterm.mod              probe.mod
befs.mod                     gptsync.mod              pxeboot.img
biosdisk.mod                 grldr.img                pxecmd.mod
bitmap.mod                   grub.cfg                 pxe.mod
bitmap_scale.mod             grubenv                  raid5rec.mod
blocklist.mod                gzio.mod                 raid6rec.mod
boot.img                     halt.mod                 raid.mod
boot.mod                     handler.lst              read.mod
bsd.mod                      hashsum.mod              reboot.mod
bufio.mod                    hdparm.mod               regexp.mod
cat.mod                      hello.mod                reiserfs.mod
cdboot.img                   help.mod                 relocator.mod
chain.mod                    hexdump.mod              scsi.mod
cmostest.mod                 hfs.mod                  search_fs_file.mod
cmp.mod                      hfsplus.mod              search_fs_uuid.mod
command.lst                  iorw.mod                 search_label.mod
configfile.mod               iso9660.mod              search.mod
core.img                     jfs.mod                  serial.mod
cpio.mod                     jpeg.mod                 setjmp.mod
cpuid.mod                    kernel.img               setpci.mod
crc.mod                      keystatus.mod            sfs.mod
crypto.lst                   linux16.mod              sleep.mod
crypto.mod                   linux.mod                tar.mod
cs5536.mod                   lnxboot.img              terminal.lst
datehook.mod                 loadenv.mod              terminal.mod
date.mod                     locale                   terminfo.mod
datetime.mod                 loopback.mod             test.mod
diskboot.img                 lsmmap.mod               tga.mod
dm_nv.mod                    ls.mod                   trig.mod
drivemap.mod                 lspci.mod                true.mod
echo.mod                     lvm.mod                  udf.mod
efiemu32.o                   mdraid.mod               ufs1.mod
efiemu64.o                   memdisk.mod              ufs2.mod
efiemu.mod                   memrw.mod                uhci.mod
elf.mod                      minicmd.mod              unicode.pf2
example_functional_test.mod  minix.mod                usb_keyboard.mod
ext2.mod                     mmap.mod                 usb.mod
extcmd.mod                   moddep.lst               usbms.mod
fat.mod                      moreblue-orbit-grub.png  usbtest.mod
font.mod                     msdospart.mod            vbeinfo.mod
fshelp.mod                   multiboot2.mod           vbe.mod
fs.lst                       multiboot.mod            vbetest.mod
functional_test.mod          nilfs2.mod               vga.mod
gcry_arcfour.mod             normal.mod               vga_text.mod
gcry_blowfish.mod            ntfscomp.mod             video_bochs.mod
gcry_camellia.mod            ntfs.mod                 video_cirrus.mod
gcry_cast5.mod               ohci.mod                 video_fb.mod
gcry_crc.mod                 part_acorn.mod           video.lst
gcry_des.mod                 part_amiga.mod           video.mod
gcry_md4.mod                 part_apple.mod           videotest.mod
gcry_md5.mod                 part_bsd.mod             xfs.mod
gcry_rfc2268.mod             part_gpt.mod             xnu.mod
gcry_rijndael.mod            partmap.lst              xnu_uuid.mod
gcry_rmd160.mod              part_msdos.mod           zfsinfo.mod
gcry_seed.mod                part_sun.mod             zfs.mod

In order to use code tags simply copy the text you wish to paste, then click on the **[COLOR="Red"]#[/COLOR]** at the top of this reply box. Then you'll notice the cursor blinking between the code tags so just place the mouse pointer at the blinking cursor, right-click, and select paste.

Regardless I'm thinking the problem must be in /etc/default/grub so please post the output of:

```
cat /etc/default/grub
```

And if you post the output of:

```
ls /boot/grub
```

in code tags I can properly compare both for discrepancies :)

---

### Post by Alver on 2011-03-16
Hello kansasnoob,

I'm very sorry to have caused you some hard reading times, I'm afraid it only highlights my relative ignorance in these matters. Let's try again and do better this time.

1)```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="6"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=force"
#GRUB_CMDLINE_LINUX=" vga=791"
GRUB_CMDLINE_LINUX="gfxpayload=true gfxpayload=1024x768x24,1024x768 splash"


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768x24

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

2)```
915resolution.mod            gcry_serpent.mod    parttool.lst
acpi.mod                     gcry_sha1.mod       parttool.mod
affs.mod                     gcry_sha256.mod     password.mod
afs_be.mod                   gcry_sha512.mod     password_pbkdf2.mod
afs.mod                      gcry_tiger.mod      pbkdf2.mod
aout.mod                     gcry_twofish.mod    pci.mod
ata.mod                      gcry_whirlpool.mod  play.mod
ata_pthru.mod                gettext.mod         png.mod
at_keyboard.mod              gfxmenu.mod         probe.mod
befs_be.mod                  gfxterm.mod         pxeboot.img
befs.mod                     gptsync.mod         pxecmd.mod
biosdisk.mod                 grldr.img           pxe.mod
bitmap.mod                   grub.cfg            raid5rec.mod
bitmap_scale.mod             grubenv             raid6rec.mod
blocklist.mod                gzio.mod            raid.mod
boot.img                     halt.mod            read.mod
boot.mod                     handler.lst         reboot.mod
bsd.mod                      hashsum.mod         regexp.mod
bufio.mod                    hdparm.mod          reiserfs.mod
cat.mod                      hello.mod           relocator.mod
cdboot.img                   help.mod            scsi.mod
chain.mod                    hexdump.mod         search_fs_file.mod
cmostest.mod                 hfs.mod             search_fs_uuid.mod
cmp.mod                      hfsplus.mod         search_label.mod
command.lst                  iorw.mod            search.mod
configfile.mod               iso9660.mod         serial.mod
core.img                     jfs.mod             setjmp.mod
cpio.mod                     jpeg.mod            setpci.mod
cpuid.mod                    kernel.img          sfs.mod
crc.mod                      keystatus.mod       sleep.mod
crypto.lst                   linux16.mod         splashimages
crypto.mod                   linux.mod           tar.mod
cs5536.mod                   lnxboot.img         terminal.lst
datehook.mod                 loadenv.mod         terminal.mod
date.mod                     locale              terminfo.mod
datetime.mod                 loopback.mod        test.mod
diskboot.img                 lsmmap.mod          tga.mod
dm_nv.mod                    ls.mod              trig.mod
drivemap.mod                 lspci.mod           true.mod
echo.mod                     lvm.mod             udf.mod
efiemu32.o                   mdraid.mod          ufs1.mod
efiemu64.o                   memdisk.mod         ufs2.mod
efiemu.mod                   memrw.mod           uhci.mod
elf.mod                      minicmd.mod         unicode.pf2
example_functional_test.mod  minix.mod           usb_keyboard.mod
ext2.mod                     mmap.mod            usb.mod
extcmd.mod                   moddep.lst          usbms.mod
fat.mod                      msdospart.mod       usbtest.mod
font.mod                     multiboot2.mod      vbeinfo.mod
fshelp.mod                   multiboot.mod       vbe.mod
fs.lst                       nilfs2.mod          vbetest.mod
functional_test.mod          normal.mod          vga.mod
gcry_arcfour.mod             ntfscomp.mod        vga_text.mod
gcry_blowfish.mod            ntfs.mod            video_bochs.mod
gcry_camellia.mod            ohci.mod            video_cirrus.mod
gcry_cast5.mod               part_acorn.mod      video_fb.mod
gcry_crc.mod                 part_amiga.mod      video.lst
gcry_des.mod                 part_apple.mod      video.mod
gcry_md4.mod                 part_bsd.mod        videotest.mod
gcry_md5.mod                 part_gpt.mod        xfs.mod
gcry_rfc2268.mod             partmap.lst         xnu.mod
gcry_rijndael.mod            part_msdos.mod      xnu_uuid.mod
gcry_rmd160.mod              part_sun.mod        zfsinfo.mod
gcry_seed.mod                part_sunpc.mod      zfs.mod

```

I hope this is a more civilised answer. 

Alver

---

### Post by tommcd on 2011-03-16
To change the timer for Grub2 edit the *GRUB_TIMEOUT="6"* line for how ever many seconds you want the Grub2 menu to be displayed.
Then run: ```
sudo update-grub
``` to update the */boot/grub/grub.cfg* file.

There is info on fonts and themes for Grub2 here: [https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming)

---

### Post by kansasnoob on 2011-03-16
> **tommcd said:**
> To change the timer for Grub2 edit the *GRUB_TIMEOUT="6"* line for how ever many seconds you want the Grub2 menu to be displayed.
Then run: ```
sudo update-grub
``` to update the */boot/grub/grub.cfg* file.

There is info on fonts and themes for Grub2 here: [https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming)

I think the problem is that the timeout doesn't advance :confused:

From the original post, "I can no longer set the timer! It means I have to manually push "Enter" to start booting. I also noted that I cannot change the font size of the Grub any longer."

Sadly I have to admit I'm puzzled ATM. I don't see anything obviously wrong so far.

@ Alver,

No need to apologize. I chose the moniker "kansasnoob" for a reason when I began here, I really knew less than nothing, and I'm still learning ;)

Right now I need to follow up on a couple of other issues, and also deal with some non-puter issues, but I'm not giving up.

If I space this off for more than 24 hours please either bump the thread or send me a PM. I just don't want to suggest something premature and break your boot altogether.

I am curious though, is Ubuntu the only OS on this machine? 

If so is the grub menu displayed when booting or not?

If it is displayed by default does the "count-down" at the bottom of the screen advance at all?

---

### Post by Alver on 2011-03-16
> **tommcd said:**
> To change the timer for Grub2 edit the *GRUB_TIMEOUT="6"* line for how ever many seconds you want the Grub2 menu to be displayed.
Then run: ```
sudo update-grub
``` to update the */boot/grub/grub.cfg* file.

There is info on fonts and themes for Grub2 here: [https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming)
I've set the time to "6" because that is my previous setting in 10.04 and earlier. Alas, it does not work here!

---

### Post by Alver on 2011-03-16
> **kansasnoob said:**
> I think the problem is that the timeout doesn't advance :confused:

From the original post, "I can no longer set the timer! It means I have to manually push "Enter" to start booting. I also noted that I cannot change the font size of the Grub any longer."

Sadly I have to admit I'm puzzled ATM. I don't see anything obviously wrong so far.

@ Alver,

No need to apologize. I chose the moniker "kansasnoob" for a reason when I began here, I really knew less than nothing, and I'm still learning ;)

Right now I need to follow up on a couple of other issues, and also deal with some non-puter issues, but I'm not giving up.

If I space this off for more than 24 hours please either bump the thread or send me a PM. I just don't want to suggest something premature and break your boot altogether.

I am curious though, is Ubuntu the only OS on this machine? 

If so is the grub menu displayed when booting or not?

If it is displayed by default does the "count-down" at the bottom of the screen advance at all?

Hello, I have dual boot W7/U 10.10 both 64b. Grub appears normally in all its glory but it seems to have a fixed resolution screen of 640x480 AND there is no count down line at the bottom. Other than that everything boots just fine but only after a manual "Enter".

---

### Post by kansasnoob on 2011-03-17
I've been working on something:

[http://ubuntuforums.org/showpost.php?p=10562947&postcount=31](http://ubuntuforums.org/showpost.php?p=10562947&postcount=31)

**[COLOR="Red"]However, don't just jump into that yet![/COLOR]** Specifically, in your case, I see you had to use the "acpi_osi=force" boot parameter (possibly to deal with a fan/cooling issue) so I need to add some warnings about such things :)

You'd be doing me a huge favor if you'd post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I'm also trying to figure out the effects of BURG on this whole thing which means I have to break my own stuff and fix it a few times :D

I personally detest BURG, IMHO it's just a kludge!

---

### Post by Alver on 2011-03-18
> **kansasnoob said:**
> I've been working on something:

[http://ubuntuforums.org/showpost.php?p=10562947&postcount=31](http://ubuntuforums.org/showpost.php?p=10562947&postcount=31)

**[COLOR="Red"]However, don't just jump into that yet![/COLOR]** Specifically, in your case, I see you had to use the "acpi_osi=force" boot parameter (possibly to deal with a fan/cooling issue) so I need to add some warnings about such things :)

You'd be doing me a huge favor if you'd post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I'm also trying to figure out the effects of BURG on this whole thing which means I have to break my own stuff and fix it a few times :D

I personally detest BURG, IMHO it's just a kludge!
Hi Kansasnoob thank you for your continuing interest in this bizarre problem. As requested I have added the results.txt file.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   489,207,807   488,386,560   7 HPFS/NTFS
/dev/sda3         489,207,808   734,957,684   245,749,877   7 HPFS/NTFS
/dev/sda4         734,959,614   976,773,119   241,813,506   5 Extended
/dev/sda5         734,959,616   966,860,799   231,901,184  83 Linux
/dev/sda6         966,862,848   976,773,119     9,910,272  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        D85A356D5A354A10                       ntfs       SYSTEM                        
/dev/sda2        9AF43941F4392145                       ntfs       WINDOWS                       
/dev/sda3        01CB1AE43E0A01E0                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7c5f4260-537f-41d0-a9ad-9dab8ec53279   ext4                                     
/dev/sda6        5ac81bee-e398-44f4-a5b9-e21683565347   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod 
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
set locale_dir=($root)/boot/grub/locale
set lang=nl
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=6
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro splash gfxpayload=true gfxpayload=1024x768x24,1024x768  quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro single splash gfxpayload=true gfxpayload=1024x768x24,1024x768
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro splash gfxpayload=true gfxpayload=1024x768x24,1024x768  quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro single splash gfxpayload=true gfxpayload=1024x768x24,1024x768
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d85a356d5a354a10
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5ac81bee-e398-44f4-a5b9-e21683565347 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 397.9GB: boot/grub/core.img
 413.4GB: boot/grub/grub.cfg
 419.1GB: boot/initrd.img-2.6.32-28-generic
 380.1GB: boot/initrd.img-2.6.32-29-generic
 398.0GB: boot/vmlinuz-2.6.32-28-generic
 398.0GB: boot/vmlinuz-2.6.32-29-generic
 380.1GB: initrd.img.old
 398.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 88 d2 0d 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 88  d2 0d 00 40 97 00 00 00  |...........@....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I hope this makes sense to you! It surpasses my knowledge by many lightyears!

p.s. As to the "acpi_osi=force" thing. I set this variable after reading many posts from Linuxers with problematic Toshiba's AS A PRECAUTION, I'm no longer convinced I really need it. By coincidence I had already gone back to acpi_osi=off and my laptop behaves just fine. Temperature and fan behaviour have not been an issue with this laptop sofar (keep your fingers crossed).

Alver

---

### Post by Alver on 2011-03-23
> **Alver said:**
> Hi Kansasnoob thank you for your continuing interest in this bizarre problem. As requested I have added the results.txt file.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   489,207,807   488,386,560   7 HPFS/NTFS
/dev/sda3         489,207,808   734,957,684   245,749,877   7 HPFS/NTFS
/dev/sda4         734,959,614   976,773,119   241,813,506   5 Extended
/dev/sda5         734,959,616   966,860,799   231,901,184  83 Linux
/dev/sda6         966,862,848   976,773,119     9,910,272  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        D85A356D5A354A10                       ntfs       SYSTEM                        
/dev/sda2        9AF43941F4392145                       ntfs       WINDOWS                       
/dev/sda3        01CB1AE43E0A01E0                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7c5f4260-537f-41d0-a9ad-9dab8ec53279   ext4                                     
/dev/sda6        5ac81bee-e398-44f4-a5b9-e21683565347   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod 
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
set locale_dir=($root)/boot/grub/locale
set lang=nl
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=6
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro splash gfxpayload=true gfxpayload=1024x768x24,1024x768  quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro single splash gfxpayload=true gfxpayload=1024x768x24,1024x768
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro splash gfxpayload=true gfxpayload=1024x768x24,1024x768  quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro single splash gfxpayload=true gfxpayload=1024x768x24,1024x768
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d85a356d5a354a10
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5ac81bee-e398-44f4-a5b9-e21683565347 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 397.9GB: boot/grub/core.img
 413.4GB: boot/grub/grub.cfg
 419.1GB: boot/initrd.img-2.6.32-28-generic
 380.1GB: boot/initrd.img-2.6.32-29-generic
 398.0GB: boot/vmlinuz-2.6.32-28-generic
 398.0GB: boot/vmlinuz-2.6.32-29-generic
 380.1GB: initrd.img.old
 398.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 88 d2 0d 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 88  d2 0d 00 40 97 00 00 00  |...........@....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I hope this makes sense to you! It surpasses my knowledge by many lightyears!

p.s. As to the "acpi_osi=force" thing. I set this variable after reading many posts from Linuxers with problematic Toshiba's AS A PRECAUTION, I'm no longer convinced I really need it. By coincidence I had already gone back to acpi_osi=off and my laptop behaves just fine. Temperature and fan behaviour have not been an issue with this laptop sofar (keep your fingers crossed).

Alver

Hi Kansasnoob, please consider this as a polite bump ;)

Alver

---

### Post by kansasnoob on 2011-03-23
> **Alver said:**
> Hi Kansasnoob thank you for your continuing interest in this bizarre problem. As requested I have added the results.txt file.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       821,247       819,200  27 Hidden HPFS/NTFS
/dev/sda2             821,248   489,207,807   488,386,560   7 HPFS/NTFS
/dev/sda3         489,207,808   734,957,684   245,749,877   7 HPFS/NTFS
/dev/sda4         734,959,614   976,773,119   241,813,506   5 Extended
/dev/sda5         734,959,616   966,860,799   231,901,184  83 Linux
/dev/sda6         966,862,848   976,773,119     9,910,272  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        D85A356D5A354A10                       ntfs       SYSTEM                        
/dev/sda2        9AF43941F4392145                       ntfs       WINDOWS                       
/dev/sda3        01CB1AE43E0A01E0                       ntfs       Data                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7c5f4260-537f-41d0-a9ad-9dab8ec53279   ext4                                     
/dev/sda6        5ac81bee-e398-44f4-a5b9-e21683565347   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod 
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
set locale_dir=($root)/boot/grub/locale
set lang=nl
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=6
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro splash gfxpayload=true gfxpayload=1024x768x24,1024x768  quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro single splash gfxpayload=true gfxpayload=1024x768x24,1024x768
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro splash gfxpayload=true gfxpayload=1024x768x24,1024x768  quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 ro single splash gfxpayload=true gfxpayload=1024x768x24,1024x768
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 7c5f4260-537f-41d0-a9ad-9dab8ec53279
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d85a356d5a354a10
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7c5f4260-537f-41d0-a9ad-9dab8ec53279 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5ac81bee-e398-44f4-a5b9-e21683565347 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 397.9GB: boot/grub/core.img
 413.4GB: boot/grub/grub.cfg
 419.1GB: boot/initrd.img-2.6.32-28-generic
 380.1GB: boot/initrd.img-2.6.32-29-generic
 398.0GB: boot/vmlinuz-2.6.32-28-generic
 398.0GB: boot/vmlinuz-2.6.32-29-generic
 380.1GB: initrd.img.old
 398.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 88 d2 0d 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 88  d2 0d 00 40 97 00 00 00  |...........@....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I hope this makes sense to you! It surpasses my knowledge by many lightyears!

p.s. As to the "acpi_osi=force" thing. I set this variable after reading many posts from Linuxers with problematic Toshiba's AS A PRECAUTION, I'm no longer convinced I really need it. By coincidence I had already gone back to acpi_osi=off and my laptop behaves just fine. Temperature and fan behaviour have not been an issue with this laptop sofar (keep your fingers crossed).

Alver

I'd not seen this post, thanks for the PM. Give me just a bit to review things.

I have a plan, but I don't want to depend on my worn out human memory :)

---

### Post by kansasnoob on 2011-03-23
I'm 99% sure that this procedure is safe and will likely get you back to a virgin grub 2:

[http://ubuntuforums.org/showpost.php?p=10562947&postcount=31](http://ubuntuforums.org/showpost.php?p=10562947&postcount=31)

Just be sure to copy-n-paste commands. Also remember the bit about the "acpi_osi=force" thing. I'd think you'd notice if it's needed or not.

---

