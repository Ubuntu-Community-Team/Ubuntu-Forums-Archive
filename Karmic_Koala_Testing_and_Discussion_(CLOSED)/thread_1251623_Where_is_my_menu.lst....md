---
title: "Where is my menu.lst?..."
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by beastrace91 on 2009-08-27
So I just did a fresh install of 9.10 64bit and the first thing I went to do was customize the entries in my menu.lst how ever I do not have one in my /boot/grub folder as is typically found... ```
jeff@sager-lintop:~$ ls /boot/grub
915resolution.mod  at_keyboard.mod  chain.mod       device.map    fat.mod      halt.mod     jpeg.mod      lvm.mod        ntfs.mod      pxeboot.img   serial.mod    udf.mod           vga_text.mod
acorn.mod          befs.mod         cmp.mod         diskboot.img  font.mod     handler.lst  kernel.img    mdraid.mod     ohci.mod      pxecmd.mod    setjmp.mod    ufs.mod           video.mod
acpi.mod           biosdisk.mod     command.lst     dm_nv.mod     fs_file.mod  handler.mod  linux16.mod   memdisk.mod    partmap.lst   pxe.mod       sfs.mod       uhci.mod          videotest.mod
affs.mod           bitmap.mod       configfile.mod  drivemap.mod  fshelp.mod   hdparm.mod   linux.mod     memrw.mod      parttool.lst  raid5rec.mod  sh.mod        usb_keyboard.mod  xfs.mod
afs.mod            blocklist.mod    core.img        echo.mod      fs.lst       hello.mod    lnxboot.img   minicmd.mod    parttool.mod  raid6rec.mod  sleep.mod     usb.mod           xnu.mod
amiga.mod          boot.img         cpio.mod        efiemu32.o    fs_uuid.mod  help.mod     loadenv.mod   minix.mod      pci.mod       raid.mod      sun.mod       usbms.mod         xnu_uuid.mod
aout.mod           boot.mod         cpuid.mod       efiemu64.o    gfxterm.mod  hexdump.mod  loopback.mod  mmap.mod       pc.mod        read.mod      tar.mod       usbtest.mod       zfs.mod
apple.mod          bsd.mod          crc.mod         efiemu.mod    gpt.mod      hfs.mod      lsmmap.mod    moddep.lst     pcpart.mod    reboot.mod    terminfo.mod  vbeinfo.mod
ascii.pf2          bufio.mod        datehook.mod    elf.mod       gptsync.mod  hfsplus.mod  ls.mod        multiboot.mod  play.mod      reiserfs.mod  test.mod      vbe.mod
ata.mod            cat.mod          date.mod        ext2.mod      grub.cfg     iso9660.mod  lspci.mod     normal.mod     png.mod       scsi.mod      tga.mod       vbetest.mod
ata_pthru.mod      cdboot.img       datetime.mod    extcmd.mod    gzio.mod     jfs.mod      lua.mod       ntfscomp.mod   probe.mod     search.mod    true.mod      vga.mod

```

Any ideas where I can find/edit the grub menu? The 9.10 install auto detected my 9.04, how ever it failed to add my Fedora11 to boot list and I would kinda like to use it.

Thanks,
~Jeff

---

### Post by Cenotaph on 2009-08-27
i believe its grub.cfg now

---

### Post by tuxxy on 2009-08-27
It's called /boot/grub/grub.cfg now that it is GRUB 2, you are able to edit GRUB now the GUI :D

---

### Post by beastrace91 on 2009-08-27
Where do I find this grub GUI editor? :( I wanna get my displayed menus how I like them lol

~Jeff

---

### Post by beastrace91 on 2009-08-27
Did some reading on grub2... I've since reverted the grub back to legacy - I like having full control over my entries...

~Jeff

---

### Post by dino99 on 2009-08-28
you'd better to stay with grub2 as Karmic only use it: grub legacy is the old story & will be dropped for ever.

---

### Post by jocko on 2009-08-28
> **beastrace91 said:**
> Did some reading on grub2... I've since reverted the grub back to legacy - I like having full control over my entries...

~Jeff
You can still have full control over your entries, and the process is pretty much the same as before. It's just that the settings update-grub looks for when it generates the boot menu have been moved from menu.lst to /etc/default/grub and a few scripts in /etc/grub.d

So just edit the file /etc/default/grub and perhaps some of the scripts in /etc/grub.d, and then run update-grub to update the grub.cfg file to your liking.

---

### Post by beastrace91 on 2009-08-28
Yes, I read all the docs on grub2... it just seems like alot more work to get the same effect :( 

Anyone know the reasoning behind such a drastic change?

~Jeff

---

### Post by jocko on 2009-08-28
> **beastrace91 said:**
> Yes, I read all the docs on grub2... it just seems like alot more work to get the same effect :( 

Anyone know the reasoning behind such a drastic change?

~Jeff
Why do you think it's so much more work?
The "correct" process in legacy grub to change settings for the boot options:
Edit the "debian automagic kernels list" section of menu.lst, then run update-grub.
Corresponding process in grub 2:
Edit the file /etc/default/grub, then run update-grub.

No more work there, just a different file name (and the options may not look exactly the same).
And in legacy grub there was no way (that I know of) to re-check for other OSes and update the "Other OS" part of the menu, now the script /etc/grub.d/30_os-prober will do this every time update-grub is invoked and update any changes.
So as I see it, it's not more work to do the same things, there's just more things you can do (if you want to).

---

### Post by VMC on 2009-08-28
> **beastrace91 said:**
> Yes, I read all the docs on grub2... it just seems like alot more work to get the same effect :( 

Anyone know the reasoning behind such a drastic change?

~Jeff

I agree, it is a lot more work, especially if you want the menu single entry. Also grub2 fails to pick up initrd on Fedora. I have to edit by hand.

I'm using grub2 but as you stated I don't know the reasoning behind it. Future use of newer hardware perhaps. there's a ton to learn regarding the scripts now.

All I want out of my boot manager is to boot my OS's. And to boot them right now. I don't need to look at pretty pictures. I want to get at my work, period.

If you take the time to learn the scripts you will be able to accomplish this , I suppose. I know all about the numbered files in "grub.d". It does seem like a lot of extra work though.

---

### Post by beastrace91 on 2009-08-28
> **VMC said:**
> All I want out of my boot manager is to boot my OS's. 

Agreed. 

> Why do you think it's so much more work?

In legacy grub adding a menu entry was as simple as editing the menu.lst and rebooting and then BAM! It was in the list. In grub2 I have to create a separate file with information in it and then run a command for it to process it... Thats two steps VS one step - twice as much work. Not to mention I now have to do the same for removing menu entries? Before all I had to do was open a file and comment out the lines I didn't need. (I like my boot manager to look clean and not display 800 kernels when I have multiple distros/kernels on the system) 

All in all I can see where some of the changes in grub2 are good for new people but to the power user it kinda takes away some of the control I feel.

~Jeff

---

### Post by jocko on 2009-08-28
> **beastrace91 said:**
> Agreed. 



In legacy grub adding a menu entry was as simple as editing the menu.lst and rebooting and then BAM! It was in the list. In grub2 I have to create a separate file with information in it and then run a command for it to process it... Thats two steps VS one step - twice as much work. Not to mention I now have to do the same for removing menu entries? Before all I had to do was open a file and comment out the lines I didn't need. (I like my boot manager to look clean and not display 800 kernels when I have multiple distros/kernels on the system) 

All in all I can see where some of the changes in grub2 are good for new people but to the power user it kinda takes away some of the control I feel.

~Jeff
You can still edit the grub.cfg directly and have the changes take effect immediately, it's just not the best way to do it, just as it was not the best way to do it with legacy grub.
If you just edit the actual boot menu part in menu.lst (or grub.cfg), next time you get a kernel update (or any other update which will trigger update-grub) you'll loose the changes you made. To make the changes permanent and carried along to the next kernel update, you have to make it by editing the settings for update-grub, and then run update-grub to apply the changes to the boot menu. This used to be in menu.lst (the "debian automagic kernel list" section), and now it's in /etc/default/grub. It's still just one file to edit, to access the same things. You can ignore the files in /etc/grub.d completely if you don't want to do anything that you couldn't do in legacy grub.

It may be new and different to what you are used to, but it's not more work and not any more difficult, it's just not done in exactly the same way.

---

### Post by Seventh Reign on 2009-08-28
It is actually LESS work with grub2.  With grub2 if you edit the correct files (ie adding boot commands in the correct places) you only need to do it ONCE ever.  Every new kernel that is installed will automatically take those commands into effect.

With Grub1 you have to manually edit your menu.lst every single time you add a new kernel.

I have to add the pci=nomsi command or my system doesnt boot.  With grub1 everytime I get a kernel upgrade I have to go to /boot/grub/menu.lst and re-add it to the new kernel.

With Grub2 I simply add that line to /etc/default/grub one time and every kernel upgrade after that instantly has it enabled.

Just remember to 'sudo update-grub' after you make any changes.

---

### Post by taavikko on 2009-08-28
> **Seventh Reign said:**
> It is actually LESS work with grub2.  With grub2 if you edit the correct files (ie adding boot commands in the correct places) you only need to do it ONCE ever.  Every new kernel that is installed will automatically take those commands into effect.

With Grub1 you have to manually edit your menu.lst every single time you add a new kernel.

I have to add the pci=nomsi command or my system doesnt boot.  With grub1 everytime I get a kernel upgrade I have to go to /boot/grub/menu.lst and re-add it to the new kernel.

With Grub2 I simply add that line to /etc/default/grub one time and every kernel upgrade after that instantly has it enabled.

Just remember to 'sudo update-grub' after you make any changes.

Actually, it works in grub0.96 also, One would set the desired options in 
#defoptions= quiet splash pci=nomsi <etc> 
and running update-grub. Instead of adding boot-options in every kernel.

---

### Post by jocko on 2009-08-28
> **taavikko said:**
> Actually, it works in grub0.96 also, One would set the desired options in 
#defoptions= quiet splash pci=nomsi <etc> 
and running update-grub. Instead of adding boot-options in every kernel.
Yup. It works exactly the same in grub 2 as in grub 1, just a different file to edit...

---

### Post by beastrace91 on 2009-08-28
> **jocko said:**
> Yup. It works exactly the same in grub 2 as in grub 1, just a different file to edit...

If it works exactly the same I guess my real question is why reinvent the wheel if it already rolls quiet well xD

~Jeff

---

### Post by taavikko on 2009-08-28
> **beastrace91 said:**
> If it works exactly the same I guess my real question is why reinvent the wheel if it already rolls quiet well xD

~Jeff

they didn't reinvent the wheel, just added suspension and chassis to it;)
Grub2 offers much more than grub1 so isn't it good to finally we migrate to it...

---

### Post by VMC on 2009-08-28
I know I had issue using grub with Ext4. The patched grub made that work. So I guess for one thing, grub2 is better suited for future file systems coming down the pike.

---

