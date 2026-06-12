---
title: "Grub problems with 10.10 install"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by docit on 2010-10-24
I've attempted a clean install of 10.10 64 bit on my desktop that has been running 10.04 without any problems. The install appears to go ok, but when it comes to the restart I'm not presented with a grub menu and it just appears to hang. I can boot into the live CD ok and have run dsck and all seems ok.  After a couple of attempts without success I did a complete reformat of the disk and attempted to install 10.04 which produced the same result. I'm presuming that my MBR has been corrupted.  From within the live CD boot I did a grub-install to reinstall GRUB2 to the MBR, but that made no difference.  I ran bootinfoscript (output attached).  The only issue I can see with this is that it reports "Unknown BootLoader on sda2".

Any suggestions would be very much appreciated.

---

### Post by oldfred on 2010-10-24
You will not get a menu if you only have one system installed. You can hold down shift from BIOS until menu appears. Can you then get menu. And can you boot from recovery mode?

They moved the start from 63 to 2048, so some old data may be on the drive in the area that boot loader would exist in a partition. Grub does not normally install to a partition and the script is just saying it sees some data in the boot area. You can ignore that.

Often issue seem to be video related. my system would just start to boot and then the monitor would go to sleep (but it was still loading). I had to edit boot line in grub menu. What video card do you have?

From liveCD, if you cannot boot:
Check your chipset with:
lspci -nn|grep VGA

---

### Post by docit on 2010-10-24
Hi,

Holding down shift from the BIOS had no effect (I have an ASUS P5Q Delux motherboard)

My video card is an nVidia G96 (GeForce 9500 GT).  It works fine with the live CD and worked fine with previous versions of Ubuntu.  If the issue was just the video card then I would have expect the Ubuntu 10.04 install to work ok... but it now has the same problem. Hence clearly something has broken.

---

### Post by lindsay7 on 2010-10-25
i would try reinstalling grub, see this

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

doing so will not hurt anything

---

### Post by docit on 2010-10-25
I tried reinstalling Grub using the approach given in your link.  Unfortunately it didn't have any effect.

---

### Post by oldfred on 2010-10-25
If the two line version of reinstalling does not work then you should try the full chroot version:

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by docit on 2010-10-25
I tried grub uninstall and reinstall. Unfortunately it didn't have any effect.

---

### Post by drs305 on 2010-10-25
Because you aren't getting a Grub error message and have reinstalled Grub several times I don't think you can rule out a video issue - even if the Live CD works. Additionally, if the changes below do not take effect it could be an indication that the Grub files are *not* loading.

If holding down SHIFT during boot doesn't display the Grub menu, you might try booting the LiveCD, mounting sda1 and then manually editing /boot/grub/grub.cfg to add the "nomodeset" kernel option. Save the file and reboot (don't try to udpate grub). 

Since we will be editing the file, we might as well try to force the Grub menu to display as well.

From the LiveCD:
```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/grub.cfg
```

Try to force the menu display by adding this:
> function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
[COLOR="Red"]# Added to force menu display
recordfail=1[/COLOR]
}


In the first menuentry, replace this:
> ### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 4a2dd348-84db-43ed-859c-97d954a1eeec
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4a2dd348-84db-43ed-859c-97d954a1eeec ro   [COLOR="Red"]quiet splash[/COLOR]
	initrd	/boot/initrd.img-2.6.35-22-generic
}
With this:
> ### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 4a2dd348-84db-43ed-859c-97d954a1eeec
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4a2dd348-84db-43ed-859c-97d954a1eeec ro   [COLOR="Red"][COLOR="Red"]nomodeset[/COLOR][/COLOR]
	initrd	/boot/initrd.img-2.6.35-22-generic
}

If it does now boot, add your video drivers, update grub and see if it will now boot. Updating grub will remove the "recordfail" force of the menu display.

---

### Post by docit on 2010-10-26
I made the changes as suggested. It starts to boot, displaying progress on the screen. But when it reaches "Setting sensors limits" it hangs.

---

### Post by oldfred on 2010-10-26
Since it is Nvidia:

press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by Square³ on 2010-10-27
Any update on this? I had the same problem when I installed Mav with all updates, though it worked flawlessly after installing it without updating anything and now I don't have the guts to update, because I fear it will happen again :|

---

### Post by crazyjpeters on 2010-10-30
> **Square³ said:**
> Any update on this? I had the same problem when I installed Mav with all updates, though it worked flawlessly after installing it without updating anything and now I don't have the guts to update, because I fear it will happen again :|

I have been running 10.10 for a week.  I also have held off running updates because I had run into trouble with several of my installs because of the updater.

Stupidly, I just ran the updater, and now it won't boot 10.10, or recovery mode.  Luckily I have a liveCD and a spare install of 10.04.  But I'd like to know why I shouldn't be able to update my software without crippling my system.

---

### Post by Square³ on 2010-10-30
Bah, sounds like I still have to keep the updates back on my Desktop system :( ..would be nice to know which package is faulty here, at least. Could it be the updated Kernel image? The running system has the following updates pending...when I apply them, the problem with hanging at "setting sensors limits" will appear (which I know because of the first installation, where I installed all updates and ****ed it up ;)):

```

Die folgenden Pakete werden aktualisiert (Upgrade):
  app-install-data-partner compiz compiz-core compiz-gnome compiz-plugins cups-bsd cups-client cups-common
  empathy empathy-common evolution-common evolution-data-server evolution-data-server-common evolution-plugins
  firefox firefox-branding firefox-gnome-support gcalctool gconf-defaults-service gconf2 gconf2-common
  gdm-guest-session gnome-settings-daemon indicator-sound jockey-common jockey-gtk libcamel1.2-14 libcups2
  libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdecoration0 libebackend1.2-0
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-7 libedataserver1.2-13 libedataserverui1.2-8
  libegroupwise1.2-13 libevolution libgconf2-4 libgdata-google1.2-1 libgdata1.2-1 libgpod-common libgpod4
  libgudev-1.0-0 libldap-2.4-2 libnss3-1d libpam-modules libpam-runtime libpam0g libpoppler-glib5 libpoppler7
  libpulse-browse0 libpulse-mainloop-glib0 libpulse0 libudev0 libutouch-grail1 libvte-common libvte9
  libwebkit-1.0-2 libwebkit-1.0-common linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
  linux-image-2.6.35-22-generic linux-libc-dev nautilus-dropbox nautilus-sendto-empathy pitivi poppler-utils
  pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python-papyon python-vte simple-scan software-center thunderbird ubuntu-sso-client udev
  update-manager update-manager-core xulrunner-1.9.2

```

---

### Post by Square³ on 2010-11-05
Strangely, the problem didn't occur anymore when I updated, while it definitely was there when updating during the installation. Of course it could be that there has been another update of the "faulty" package by now...

---

### Post by foxsick on 2010-11-05
Can you help me>?

---

### Post by drs305 on 2010-11-05
> **foxsick said:**
> Can you help me>?

It appears your Ubuntu installation is on sdg2. Grub2  was at one time installed to the partition instead of the drive, which is not recommended.

You can get Grub2 installed in the sdg MBR and pointing to sdg2 with the following. Boot the LiveCD, then open a terminal via Applications, Accessories, Terminal.

```
sudo mount /dev/sdg2 /mnt
sudo grub-install --root-directory=/mnt /dev/sdg
```
Note that in the second command you do NOT include the partition number.

sdg needs to be the drive that boots first - you may need to change the BIOS. Normally you enter the BIOS during boot by pressing the DEL key or one of the F keys. You may be told which key to press on the first screen you see during boot.

---

### Post by foxsick on 2010-11-05
Thank you for your response!
I have this:
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sdg
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
/usr/sbin/grub-setup: warn: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

```
After update I have the same error.:(

---

### Post by drs305 on 2010-11-05
Grub 2 writes to the MBR and uses a bit of additional space. Unfortunately, some Windows non-booting apps also try to use that space. Apparently FlexNet has already written to the space and won't allow Grub to access it.

Even if you could get G2 installed in the MBR, you may have problems in the future if/when FlexNet tries to overwrite that section.

Your options are to install Grub to a different drive or to remove FlexNet via Windows. Although I am not a Windows user, I believe another option is to use EasyBCD in Windows, which can be set up to boot to the Ubuntu partition.

---

### Post by psusi on 2010-11-05
> **foxsick said:**
> 
After update I have the same error.:(

What error?

---

### Post by foxsick on 2010-11-05
> **psusi said:**
> What error?
Error: no such disk
Grub doesn't load
I have no Windows disk, how can I repair this? :confused:
I'm a full noob, I need step-by-step guide I tried many posts and nothing of them work

---

### Post by foxsick on 2010-11-05
Can you help?

---

### Post by oldfred on 2010-11-06
I had no idea what flexnet is.

[http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2](http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2)

The problem turned out to be Adobe's digital rights management software  [DRM].  Do your own search for "FlexNet," formerly known as "SafeCast."   What I have read is that FlexNet is a viral rootkit that replicates in  multiple locations whenever a CS3 or CS4 product is installed, including  trial versions.  

Once something like this is installed you are trapped. The above link discusses the zero out of everything and reinstall.

---

### Post by foxsick on 2010-11-07
> **oldfred said:**
> I had no idea what flexnet is.

[http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2](http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2)

The problem turned out to be Adobe's digital rights management software  [DRM].  Do your own search for "FlexNet," formerly known as "SafeCast."   What I have read is that FlexNet is a viral rootkit that replicates in  multiple locations whenever a CS3 or CS4 product is installed, including  trial versions.  

Once something like this is installed you are trapped. The above link discusses the zero out of everything and reinstall.
On this disk Adobe Photoshop was installed. But I formatted NTFS to ext4. Completely formatted... How can the program be alive after it?

---

### Post by psusi on 2010-11-07
> **foxsick said:**
> On this disk Adobe Photoshop was installed. But I formatted NTFS to ext4. Completely formatted... How can the program be alive after it?

The area in question is outside of any partition.  That warning does not matter though, you can ignore it.

---

### Post by jabsco on 2010-11-26
Had the same problems with flexnet and my mbr. I used my windows cd to enter the recovery console and used the fixmbr command to rewrite my mbr ( I was warned my mbr was non standard ( not a surprise thanks to flexnet)) . Fdisk will probably let you do the same.

---

### Post by rajeeja on 2010-12-13
I get the same error, here's is what I've done so far:

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda6 /dev/sda

/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it. This software may cause boot or other problems in future. Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

Reboot into the LiveCD and execute:

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
mount: /dev/sda6 already mounted or /mnt busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Simply rebooting without the live CD gets me to grub> prompt. It's because the old grub files are gone and the new one didn't update?

I can access my old system/files from the live CD. Mine is a dual boot with Vista that came with it and later i installed windows. Please let me know..

Many thanks,

---

### Post by newblackgold on 2011-02-01
I wonder.  I've been having problems booting my system after it lost power, although it was not after any updates. It had worked fine for a while.  On mine grub won't appear, and holding shift does not help, just sits at a blinking cursur during boot at "loading operating system."  The system will however boot from a usb stick just fine and all my files are available, it just wont boot from the hard drive.  This is a Ubuntu only machine.
 
I tried repairing grub and although it says the process completed, I get that flexnet error.  This is somewhat silly, Photoshop was installed on that hard drive YEARS ago, heh.  I have no idea if this error is anything related to my booting problem, but it's the only lead I have right now.
 
Ages ago I did a low level format on a hard drive to clean it up after a massive mbr failure.  Luckily I don't have any important files on my linux drive.  I am looking at options for nuking the MBR and rebuiding it and attempting to recover the Ubuntu data, so I will post the results of that.

---

### Post by newblackgold on 2011-02-01
Well, I "fixed" it.  Did a low level format with this free product:  [http://www.killdisk.com/](http://www.killdisk.com/)
 
Made sure to disconnect my RAID just to make sure I didn't accidentally select it!  Heh.  Went smoothly and reinstalled Ubuntu and all is well.  I spent quite a few hours already on this... could not justify spending more when it would take far less time just to reconfigure a fresh system.
 
This is why I never store important data on the same physical as the OS!  Heh  :)

---

