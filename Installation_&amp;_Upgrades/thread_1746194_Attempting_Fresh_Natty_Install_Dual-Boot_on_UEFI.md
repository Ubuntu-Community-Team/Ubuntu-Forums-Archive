---
title: "Attempting Fresh Natty Install Dual-Boot on UEFI"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by manders2600 on 2011-05-01
**[COLOR="DarkRed"]WARNING[/COLOR]**:  **Lengthy Post**

I appreciate anyone who will take the time to read this and offer some help.  My system specs are in my sig, and the crux of the problem is a listed here at the top.

[B][COLOR="blue"]Goal:[/COLOR] Dual-Boot Windows 7 x64 SP1 and Ubuntu 11.04 (Natty) on GPT HD with UEFI
[COLOR="blue"]Problem:[/COLOR] Cannot get GRUB to properly install, Ubuntu Freezes on shutdown/restart.[/B]

Okay, so I got my fresh, new system up and running with a Windows install, as I new I wanted to dual-boot.  On previous builds/installs, the process has been pretty straight-forward (install Windows while creating a partition for Ubuntu and a shared storage partition, then install Ubuntu/Kubuntu and allow GRUB to over-write the Windows bootloader).  However, this time around I have ecountered a number of errors, and I am hoping someone more knowledgeable than myself will be able to help me out.  Thank you in advance, whoever you are.

The first problem I ran into was regarding the fact that my Motherboard uses UEFI and my installation HD was set up in MBR.  Windows installed fine to my MBR, but Ubuntu (by default) attempted to install EFI GRUB, which caused a boot problem.  There is a way to fix this by installing grub-pc, but I figured, "What the hell, I'll just reinitialize the HD as GPT and set up Windows and Linux in UEFI."

**Setting Up Windows/Partitions Rd 1**
After setting up the HD as GPT, and booting into the Windows 7 Ultimate x64 SP1 install disk UEFI mode, I set up the partitions on my 2 TB Hitachi 7K300 HD thusly (translated for linux-speak): sda1=100MB (EFS) sda2=128MB (MSR) sda3=151GB ntfs(windows install) sda4=90GB ntfs(linux future install) sda5=1.58TB ntfs (storage)

Windows installed into the sda3 partition correctly, and everything went smoothly.  When I checked my EFI BIOS settings, the first boot device was Windows Boot Manager in UEFI mode, and booting into this worked perfectly.

**Creating Ubuntu LiveCD USB**
Next, I used the Natty Beta 2 install I have going on my recently created File Server to download the Ubuntu Desktop AMD64 iso and create a Start-Up disk on a 4 GB USB stick.  I booted my desktop system into the EFI/BIOS settings, and told it to boot from the USB stick in UEFI mode.  This also worked just fine.

**Installing Ubuntu Rd 1/Partitions Rd 2**
Now, I went to the installer (making sure to leave the boxes for downloading updates and installing third-party software blank) and chose to make further partitions of the 90 GB ntfs partition I made when installing Windows.  I created swap, root (ext4), and home (ext4), and told the installer to put the bootloader on sda.  The installer seemed to work fine, there were no errors, and after setting up my location, user accounts etc, told me that the installation was successful, and that I needed to restart.  I clicked the button to restart, was told to remove the installation media and press enter, did so, and then got a freeze (text apeared as though it were shutting down/restarting, saying that various services were terminating and shutting down).

**Where is Ubuntu?**
I did not think much of the freeze, waited a while in case the system was just "thinking", and did a manual reset.  After resetting, I pressed "delete" to enter into the EFI/BIOS settings and make sure that GRUB would be booting instead of Windows Boot Manager.  Unfortunately, GRUB was nowhere to be found, and so I ended up trying to boot directly into the HD, and then into Windows Boot Manager.  I tried this a couple of times, but no matter what I did, I could not get GRUB to appear.

I then booted into the Live USB and checked, and it certainly seemed that all of the necessary files and folders had been created during the install, I just had no way to boot into it.

Next, I re-did the install, this time telling the installer to put the bootloader on sda1 (the 100MB FAT32 EFS partition Windows created initially).  This had the exact same effect, including the freeze at the end of the installation.

**Where is Windows/GRUB?**
After this, I did the install yet again, this time selecting the 100MB partition as the EFI partition.  This got me slightly closer, although I still got that freeze at the end of the install.

This time, when checking the EFI settings, there were UEFI entries for both Windows Boot Manager and ubuntu.  Ubuntu successfully booted, however I did not get GRUB; it simply booted to Ubuntu.  I attempted to restart the system, and got the same freeze.

After manually resetting, I found that not only could I not boot into Windows via GRUB, but the UEFI WIndows Boot Manager entry would not let me boot into Windows, either.  I tried installing all available updates in Ubuntu, as well as updating my Motherboard EFI/BIOS to the latest version, and none of this helped.

Where before I had installs of Windows and Ubuntu, with no way of booting into Ubuntu, now I had the same two installs, with no way of booting into Windows.  I still get the same freeze, with the same text (telling me that processes and services are terminating/shutting down).

**Back to Windows**
Finally, I inserted my Windows disk and repaired my Windows start-up (I really like Ubuntu, but I NEED Windows for some things) and it seems I am back to square one.

**I'm Stumped :(**
If anyone has any idea how to fix my situation, I would greatly appreciate it, as I have now spent a huge amount of time on this install, and am nowhere nearer a solution than before.  I would like to have both Windows 7 and Ubuntu 11.04 dual-booting via UEFI on a GPT HD, if possible.

I know this is a bit "verbose" (Linux humor, lol) but I appreciate anyone taking the time to read it, let alone reply.

---

### Post by srs5694 on 2011-05-01
My (U)EFI experience with Ubuntu is limited, and most of that's with a 10.10 install to a Mac Mini; however, based on that experience and posts I've seen here, my impression is that Ubuntu's grub-efi package is badly broken. I recommend you take the time to read and thorougly understand [this page](http://grub.enbug.org/TestingOnUEFI) (which seems to be down at the moment; if you can't get to it, try the [Google cache](http://webcache.googleusercontent.com/search?q=cache:I5elNtsXIvYJ:grub.enbug.org/TestingOnUEFI+testing+on+uefi+site:grub.enbug.org)). This page describes how to build and install GRUB from source code to work on a (U)EFI system. Unfortunately, there's a bit of a chicken-and-egg problem, since to get this procedure to work you'll have to be able to boot first! You may be able to get around the problem by using another computer to build the software, and then install it by copying the files over using the Ubuntu installation disc.

Good luck!

---

### Post by manders2600 on 2011-05-01
> **srs5694 said:**
> My (U)EFI experience with Ubuntu is limited, and most of that's with a 10.10 install to a Mac Mini; however, based on that experience and posts I've seen here, my impression is that Ubuntu's grub-efi package is badly broken. I recommend you take the time to read and thorougly understand [this page](http://grub.enbug.org/TestingOnUEFI) (which seems to be down at the moment; if you can't get to it, try the [Google cache](http://webcache.googleusercontent.com/search?q=cache:I5elNtsXIvYJ:grub.enbug.org/TestingOnUEFI+testing+on+uefi+site:grub.enbug.org)). This page describes how to build and install GRUB from source code to work on a (U)EFI system. Unfortunately, there's a bit of a chicken-and-egg problem, since to get this procedure to work you'll have to be able to boot first! You may be able to get around the problem by using another computer to build the software, and then install it by copying the files over using the Ubuntu installation disc.

Good luck!

Thank you for that link!  I am using the Google Cache version, which I will be printing out tomorrow when I get into work (home printer out of ink, lol).  I will probably have to go over it a few times, and it may take some work, but after a cursory glance it seems very informative.

As an update:

I have gotten both Windows and Ubuntu to boot . . . sort of.  I can now boot either the Windows Boot Manager or Ubuntu via the UEFI.  I have no idea how this happened, because it was not working before, however I have installed Ubuntu and repaired Windows start-up enough times that perhaps something clicked?

I still do not get GRUB, and I still get a freeze at any shut-down/restart of Ubuntu.  I studied the text that usually appears during one of theses freezes a little more closely, and the only thing I could come up with was one line that reads: "BUG: Unable to handle kernel paging request at 00000000df635e60".

Would this possibly be a symptom of GRUB not working properly, or could GRUB not working properly be a symptom of this bug?

---

### Post by Quackers on 2011-05-01
I'm not sure it will have any effect on your system but can you say what happens if you run ```
sudo update-grub
``` in a terminal inside Ubuntu?

---

### Post by manders2600 on 2011-05-01
> **Quackers said:**
> I'm not sure it will have any effect on your system but can you say what happens if you run ```
sudo update-grub
``` in a terminal inside Ubuntu?

I wish that were it, but after doing that, it says that it has found the linux kernel, memtest, etc.  But it does not boot GRUB at all upon restart, and still freezes prior to turning off.

I am curious as to how I would go about investigating this freezing behavior?  The two may be completely unrelated, but both need to be fixed before I can realistically use Ubuntu in this configuration, and I would hate to compile GRUB from source just to find out that it was some hardware incompatibility or something.

---

### Post by srs5694 on 2011-05-02
> **manders2600 said:**
> I have gotten both Windows and Ubuntu to boot . . . sort of.  I can now boot either the Windows Boot Manager or Ubuntu via the UEFI.  I have no idea how this happened, because it was not working before, however I have installed Ubuntu and repaired Windows start-up enough times that perhaps something clicked?

I still do not get GRUB,

Actually, if you're booting Linux, it almost certainly *is* via GRUB. It's probably just got a very short timeout and/or a single boot option, so it boots straight into Ubuntu.

I recommend you back up the contents of the EFI System Partition (ESP) to a USB flash drive or CD-R so that you'll have it ready for restoration should things go south again. The ESP should be mounted at /boot/efi, so copying everything in that directory should do the trick. Normally there'll be an efi or EFI directory with a subdirectory for each OS or boot loader. Each boot loader has a filename that ends in .efi. You might try this:

```

find /boot/efi -iname "*grub*"

```

You might need to do this with "sudo", depending on how Ubuntu mounts /boot/efi. This will find all the files in the ESP with "grub" in their names. If you've got a grub.cfg file in there, it could be that GRUB is using that configuration file rather than the one in /boot/grub. If so, you might need to manually copy /boot/grub/grub.cfg to /boot/efi/{whatever}/ to get any changes you make after update-grub to take effect.

> and I still get a freeze at any shut-down/restart of Ubuntu.  I studied the text that usually appears during one of theses freezes a little more closely, and the only thing I could come up with was one line that reads: "BUG: Unable to handle kernel paging request at 00000000df635e60".

Would this possibly be a symptom of GRUB not working properly, or could GRUB not working properly be a symptom of this bug?

No, GRUB did its job long before this and is out of the picture. This is a kernel issue. It could be a kernel bug, a kernel configuration problem, or an indication of a hardware fault, such as bad RAM. If the latter is the case, it could even explain some of your other problems, since flaky RAM can have all sorts of bizarre symptoms. I recommend running a memory tester, to begin narrowing down possibilities.

If a memory test turns up no problems, you might take a screen shot of the error screen (using a digital camera, presumably) and post it to the forum. I recommend starting a new thread for that, though.

There are some EFI-specific kernel configuration options -- both compile-time options and command-line options. I don't know much about them. I see that there's a /usr/src/linux/Documentation/x86/x86_64/uefi.txt file that describes them, though. Here's the relevant excerpt:

```

Mechanics:
---------
- Build the kernel with the following configuration.
    CONFIG_FB_EFI=y
    CONFIG_FRAMEBUFFER_CONSOLE=y
  If EFI runtime services are expected, the following configuration should
  be selected.
    CONFIG_EFI=y
    CONFIG_EFI_VARS=y or m        # optional
- Create a VFAT partition on the disk
- Copy the following to the VFAT partition:
    elilo bootloader with x86_64 support, elilo configuration file,
    kernel image built in first step and corresponding
    initrd. Instructions on building elilo    and its dependencies
    can be found in the elilo sourceforge project.
- Boot to EFI shell and invoke elilo choosing the kernel image built
  in first step.
- If some or all EFI runtime services don't work, you can try following
  kernel command line parameters to turn off some or all EFI runtime
  services.
    noefi        turn off all EFI runtime services
    reboot_type=k    turn off EFI reboot runtime service
- If the EFI memory map has additional entries not in the E820 map,
  you can include those entries in the kernels memory map of available
  physical RAM by using the following kernel command line parameter.
    add_efi_memmap    include EFI memory map of available physical RAM

```

Based on this, it could be you need to experiment with the noefi or reboot_type=k options. You'd need to set these by manually editing the grub.cfg file.

---

### Post by manders2600 on 2011-05-02
First of all, srs5694, thank you for your help.  I really do appreciate you taking the time.  I will be trying these things as soon as I get home form work (about 8 hours from now).

The one thing I did try was copying the grub config file (yeah, I needed to do it sudo-style) from its normal directory to the efi directory, but this did not seem to have any effect.  I will be posting the contents of the config file, as it does appear to have a timeout of 10 seconds, which should be normal.  The only thing it does not include is the ability to boot into windows, but it should still display the ability to memtest, etc.

I will probably go ahead and compile grub on its own, just to make sure it is solid, and try that.

I wanted to confirm that I had run memtest on each of the sticks of RAM about a week and a half ago, for 7 passes each, when I bought the pieces of this set-up, and I also tested the PSU with a multimeter.  It is certainly possible that the RAM has gotten bad in the interim, but I would tend to think it unlikely.  I did, however, re-seat the sticks last night, just for good measure.

Anyway, more than anything else, I wanted to say, "Thanks" for the willingness to help, and for the ideas.  I am much more hopeful now than I was 24 hours ago, when I had just about gotten to my wits' end.  ;)

---

### Post by alphaamanitin on 2011-05-02
If you have any luck it would be great.  I gave up trying to get a dual boot with Windows 7 and Ubuntu AMD64 on a UEFI board.  Nothing would work.  At first, Ubuntu wouldn't even install, it would fail while trying to install GRUB-efi, now it installes GRUB-efi but when I boot the computer it says there is no operating system on the disk and won't boot.  I gave up and just installed Windows 7 64-bit Ultimate, which worked perfectly with UEFI.  

Good luck.

AlphaA

---

### Post by manders2600 on 2011-05-02
> **alphaamanitin said:**
> If you have any luck it would be great.  I gave up trying to get a dual boot with Windows 7 and Ubuntu AMD64 on a UEFI board.  Nothing would work.  At first, Ubuntu wouldn't even install, it would fail while trying to install GRUB-efi, now it installes GRUB-efi but when I boot the computer it says there is no operating system on the disk and won't boot.  I gave up and just installed Windows 7 64-bit Ultimate, which worked perfectly with UEFI.  

Good luck.

AlphaA

I hope this will work, it seems kind of insane that it would be this much trouble.  Either way, I would think that this HAS to get fixed pretty quickly, as a whole lot of Sandy Bridge boards are being sold, most of them with UEFI, and a whole lot of people dual-boot like myself(either out of necessity or because they still consider themselves new to linux).

Possibly an updated version of EasyBCD or rEFIt (hell, if I could get rEFIt to work on a non-mac, I would never look back)?

---

### Post by srs5694 on 2011-05-02
FWIW, I just did an install of Ubuntu 11.04 using VirtualBox and its UEFI mode. For the most part, it's working now, although I had a couple of video problems:


[list]
[*]The GRUB menu doesn't appear. I suspect GRUB's not setting the video mode correctly or there may be a color problem. (To quote Zaphod Beeblebrox, "it's the weird colour scheme that freaks me. Every time you try to  operate one of these weird black controls, which are labeled in black on  a black background, a small black light lights up black to let you know  you've done it. Hey, what is this, some kind of galactic hyper-hearse?") I've got a UEFI/VirtualBox installation of Fedora 14 working (with a locally-compiled GRUB 2) with a visible GRUB menu, so I know this must be either a configuration file or GRUB version issue.
[*]Ubuntu didn't set up X correctly for the virtual framebuffer driver. The result was that the first boot after installation seemed to hang at "checking battery state", which was a red herring. I eventually tracked down the true cause and got X reconfigured, which was easy enough once I knew the system was actually booting. (For the record, you can switch to a text-mode virtual terminal by using RightAlt+F2, log in, and do "sudo Xorg -configure". The result is a sample Xorg.conf file (Xorg.conf.example or some such) in /root, which you've got to copy to /etc/X11 and rename xorg.conf.)
[/list]


I have *not* attempted a dual-boot installation, in part because the last time I tried installing Windows 7 in UEFI mode under VirtualBox, it didn't work.

Since you're experiencing what may be the same problem as my first one, manders2600, I'll be sure to post back if I solve it.

If rEFIt can run on UEFI systems, that might be a good solution for certain problems, too. I don't know if it will run on such systems, though; rEFIt seems to be pretty Mac-centric. In fact and FWIW, I've toyed with the idea of taking some key bits of GRUB and creating a *much* simpler Linux-only boot loader for (U)EFI, to be used in conjunction with rEFIt or the standard EFI boot loader as a front-end to boot just one Linux kernel. This seems to me to be the best approach to booting Linux on (U)EFI systems. Unfortunately, I lack the time to tackle such a project....

If you care to look into it, though, there is at least one other Linux-capable (U)EFI boot loader: [ELILO.](http://elilo.sourceforge.net/cgi-bin/blosxom) I fiddled with it briefly at one point but couldn't get it working.

---

### Post by srs5694 on 2011-05-03
I've got GRUB working (visible) on my Ubuntu 11.04 install to VirtualBox via UEFI. I can make no promises this will work for you on real hardware, but if you care to give it a try, here's my /boot/grub/grub.cfg file:

```

#
# DO NOT LET AUTOMATIC SCRIPTS OVERWRITE THIS FILE;
# IT WAS MANUALLY CREATED BY A HUMAN WHO'S FAR SMARTER
# THAN ANY STUPID SCRIPT!
#

if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
}

set timeout=5

menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 1a6c575a-0933-44a3-b8ac-638e2e7c0020
    echo    'Loading Ubuntu 11.04 with 2.6.38-8-generic kernel...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1a6c575a-0933-44a3-b8ac-638e2e7c0020 ro
#    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1a6c575a-0933-44a3-b8ac-638e2e7c0020 ro   quiet splash vt.handoff=7
    echo    'Loading initial RAM disk....'
    initrd    /boot/initrd.img-2.6.38-8-generic
    echo    'Initial RAM disk loaded; booting....'
}

menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    load_video
#    set gfxpayload=keep
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 1a6c575a-0933-44a3-b8ac-638e2e7c0020
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1a6c575a-0933-44a3-b8ac-638e2e7c0020 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}

```You'll need to change the UUID references to refer to your root (/) partition (or your /boot partition, if you've got one; and then you'd need to remove the "/boot" part of the references to the kernel and initrd).

Because this is a manually edited GRUB configuration file, you should back it up and be prepared to restore it over the automatically-created file whenever the system runs update-grub. (You may need to manually update your kernel references when this happens, too.) Alternatively, you could probably modify the various GRUB configuration files and scripts in /etc/grub.d and elsewhere, but I can't promise those changes wouldn't be undone by a GRUB update. (This is one of the things I hate about GRUB 2 -- when it works it's convenient, but when it doesn't, the "helpful" features become a royal pain to override!)

A few lines are commented out. The "set gfxpayload=keep" option just caused the framebuffer device to not work for me, so I had to uncomment it. It's conceivable you'll need that line, though, so if you don't get a display when you boot Linux, try uncommenting it. Also, I've got two "linux" lines in the first menu entry, one commented out. The one that's commented out creates the usual graphical boot display; the one that's active produces a more informative (but uglier and scarier to the uninitiated) text-mode display. You should be able to comment out the active one and uncomment the inactive one if you prefer the GUI startup, but I recommend keeping it as-is for the moment, since this might give you better diagnostics if it doesn't work right.

In theory, you should be able to add a Windows reference to the grub.cfg file -- if there's one in your current file, you could try copying it over. I haven't tested this, though, since my VirtualBox installation is Ubuntu-only.

I hope this helps you get it going!

---

### Post by manders2600 on 2011-05-03
You, sir, are the freaking man!!

I cannot tell you how relieved I am, I have finally been able to successfully display grub!

Your config file did just the thing!  Thank you so much!

Now I just need to add memtest and Windows to the grub, and I should be good to go, but those should not be that difficult.

For anyone reading this later, the uuid for your partitions can be found by:
```
sudo blkid
```

Thank you again, and I will be posting again here soon.

---

### Post by srs5694 on 2011-05-03
I'm glad to hear it worked for you!

I'm sure these issues will be resolved better in the future; but for now, I'm afraid that the combination of Ubuntu and UEFI is rather "bleeding edge."

---

### Post by manders2600 on 2011-05-03
> **srs5694 said:**
> I'm glad to hear it worked for you!

I'm sure these issues will be resolved better in the future; but for now, I'm afraid that the combination of Ubuntu and UEFI is rather "bleeding edge."

Who knew I was so ahead of the curve?  LOL.

Again, seriously, thank you so much for this.  Tonight when I get home I will be adding menu entries for Windows 7 and Memtest.  I am assuming I should be able to chain-load the (U)EFI Windows Boot Manager?

One quick question, and I do not know if you or anyone knows the answer, but is there a way to add an option to boot Windows in "Safe Mode" or "Safe Mode with Networking" directly from grub, or would this just need to be done once the Windows Boot Manager has been loaded?

---

### Post by srs5694 on 2011-05-03
In theory, yes, chainloading the .efi file that Windows dropped in the ESP should do the trick. I've never done this myself, though, so I don't know if there will be any pitfalls. (FWIW, I just tried installing Windows on an Intel board I've got that supports UEFI booting, but the UEFI mode in the firmware would drop down to BIOS mode when booting the Windows DVD. VirtualBox's UEFI implementation also doesn't like the Windows DVD. I seem to recall doing it once with UEFI DUET, though....)

FWIW, my UEFI-based Ubuntu installation on this Intel board suffered a kernel panic whenever I tried to reboot, but not when I shut down cleanly. I don't recall any message about kernel paging, and I didn't bother to photograph or write down the messages, but it does seem there's a problem with Ubuntu's shutdown scripts or kernel when it comes to shutting down/rebooting in UEFI mode. (It works fine under VMWare on another machine, though.) I'll probably fiddle around with all this more in the future, but this particular machine is my MythTV box, so I've got to schedule such experiments for times when I have free time *and* when the system isn't recording my TV shows.

I'm afraid I don't know enough about Windows booting to know if there's a way to do what you want from GRUB.

---

### Post by Spudgun79 on 2011-05-03
> **manders2600 said:**
> Who knew I was so ahead of the curve?  LOL.

Again, seriously, thank you so much for this.  Tonight when I get home I will be adding menu entries for Windows 7 and Memtest.  I am assuming I should be able to chain-load the (U)EFI Windows Boot Manager?


If you get this to work let me know since I am trying to do exactly the same thing! I've been playing with custom Grub2 menu entries all evening, but haven't got anything to work so far. Although I'm happy to get my hands dirty with the command line I would still consider myself fairly green so may have missed something obvious!

I have a workaround for the time being which is to set the BIOS of my mobo (Asus P8P67LE) to boot non-UEFI. This brings up Grub with my Ubuntu entries.  If I want to boot Windows 7 I can go into the BIOS and tell it to use the Windows Boot Manager instead as a one-off.  

This obviously isn't ideal and it would be great to have both OS on the one Grub menu.

---

### Post by manders2600 on 2011-05-04
> **Spudgun79 said:**
> If you get this to work let me know since I am trying to do exactly the same thing! I've been playing with custom Grub2 menu entries all evening, but haven't got anything to work so far. Although I'm happy to get my hands dirty with the command line I would still consider myself fairly green so may have missed something obvious!

I have a workaround for the time being which is to set the BIOS of my mobo (Asus P8P67LE) to boot non-UEFI. This brings up Grub with my Ubuntu entries.  If I want to boot Windows 7 I can go into the BIOS and tell it to use the Windows Boot Manager instead as a one-off.  

This obviously isn't ideal and it would be great to have both OS on the one Grub menu.

Yeah, I have Kubuntu now booting successfully with the grub file srs5694 was awesome enough to provide, and he was also right about needing to set the noefi option for the kernel.

To set this option (or the reboot_type=k option) temporarily, before logging into linux, in grub, highlight the kernel you wish to boot into and press "e" to edit it.  When you get to a menu screen, you will see a number of lines, one of which begins with the word "linux" and is followed by the specific kernel version number.  At the end of this line, type either:
```
noefi
```
or
```
reboot_type=k
```
(the first disables all efi runtime services, while the second disables efi reboot runtime services).  After you have done this, press F10 to boot from that configuration.  This, however, will not survive reboot, which is good if you are just testing it out.  If you have found a reboot setting that works for you, and you would like to make this "permanent", do so by editing your grub.cfg file and changing the same lines.

I have not yet tried adding Windows to the grub menu, as work has been a beast and right now I can boot into either Linux or Windows by changing the order in the UEFI menu.  Though, like you said, this is less than ideal, so I will be trying to do this probably tonight.

No worries about being green, I am pretty darn green myself.  It is funny, I am the best person I know "with computers" (and I live in San Francisco), and yet when I am on these forums I feel like a kid, just learning and probably completely out of my depth.  But I suppose that is part of what makes this stuff so interesting: there is always more to learn.  And, of course, there are people like srs5694, who take a bunch of time out of their lives to help someone like myself, who asks a question, and that, in turn, probably helps out a whole lot of people reading this forum thread later.

Good stuff.

---

### Post by srs5694 on 2011-05-04
FWIW, I just finished with another batch of mini-experiments. I tried both the "noefi" and "reboot_type=k" kernel options on my Intel board. The former prevented Ubuntu from booting (or perhaps it did boot, but my screen was blank; I didn't bother to try network access), and the latter had no effect on my kernel panic when rebooting.

I also tried rEFIt. It didn't work on my Intel board, but it did work in VirtualBox, although there are some video glitches in that environment (see screenshot). If you want to try it:


[LIST=1]
[*]Install rEFIt by typing "sudo apt-get install refit".
[*]Copy the main rEFIt files to the ESP: "sudo mkdir -p /boot/efi/EFI/refit && sudo cp -r /usr/lib/refit/refit/* /boot/efi/EFI/refit/". This includes a combination 32- and 64-bit .efi file.
[*]Copy the 64-bit-only .efi file: "sudo cp /usr/lib/refit/x64/refit.efi /boot/efi/EFI/refit/refit64.efi".
[/LIST]


You'll then need to reconfigure your (U)EFI to launch the refit.efi or refit64.efi file. I've specified copying them both, instead of just one, in case one works but the other doesn't work on your hardware. Once you've figured this out, it's probably best to delete one of them to avoid confusion in the future.

---

### Post by manders2600 on 2011-05-04
> **srs5694 said:**
> FWIW, I just finished with another batch of mini-experiments. I tried both the "noefi" and "reboot_type=k" kernel options on my Intel board. The former prevented Ubuntu from booting (or perhaps it did boot, but my screen was blank; I didn't bother to try network access), and the latter had no effect on my kernel panic when rebooting.

I also tried rEFIt. It didn't work on my Intel board, but it did work in VirtualBox, although there are some video glitches in that environment (see screenshot). If you want to try it:


[LIST=1]
[*]Install rEFIt by typing "sudo apt-get install refit".
[*]Copy the main rEFIt files to the ESP: "sudo mkdir -p /boot/efi/EFI/refit && sudo cp -r /usr/lib/refit/refit/* /boot/efi/EFI/refit/". This includes a combination 32- and 64-bit .efi file.
[*]Copy the 64-bit-only .efi file: "sudo cp /usr/lib/refit/x64/refit.efi /boot/efi/EFI/refit/refit64.efi".
[/LIST]


You'll then need to reconfigure your (U)EFI to launch the refit.efi or refit64.efi file. I've specified copying them both, instead of just one, in case one works but the other doesn't work on your hardware. Once you've figured this out, it's probably best to delete one of them to avoid confusion in the future.

Thanks!

The "reboot_type=k" option had no discernible effect on my install, either, although there might have been a change or two described in the boot or reboot text as it was flying by, I could not really tell.  However, the "noefi" option seemed to do the trick, at least for me.  The only thing I do not know is what, if any, effect is occurring on my OS by disabling all efi runtime services.  I do not think it should have any, so long as it boots, but perhaps I am incorrect?

I am hopeful that rEFIt will work for me on my system, but I am assuming that the video glitches only occurred in rEFIt itself, and not when the OS was loaded, correct?

Thanks again!

---

### Post by srs5694 on 2011-05-04
> **manders2600 said:**
> the "noefi" option seemed to do the trick, at least for me.  The only thing I do not know is what, if any, effect is occurring on my OS by disabling all efi runtime services.  I do not think it should have any, so long as it boots, but perhaps I am incorrect?

I'm afraid I don't know the answer to this, since I don't know what those "runtime services" are.

> I am hopeful that rEFIt will work for me on my system, but I am assuming that the video glitches only occurred in rEFIt itself, and not when the OS was loaded, correct?

Correct. In fact, the video glitches go away when I boot rEFIt from GRUB. Of course, that's rather pointless, at least on my VirtualBox installation -- but if you find that rEFIt can boot Windows when GRUB can't, setting it up to boot in that order might make sense, depending on your personal priorities. FWIW, there's also a configuration option to make rEFIt run in text mode. I've not tested that with my Intel board, but it's conceivable that could make it work even when the GUI mode doesn't work.

---

### Post by srs5694 on 2011-05-20
FWIW, and if anybody cares, I recently upgraded my MythTV box from Ubuntu 9.10 to 11.04. This system uses an Intel motherboard with a UEFI boot option, so I've given UEFI a try on this installation. GRUB 2 seems very unreliable -- it successfully boots only about one in four tries. (Some earlier experiments on a scratch disk were much more successful. I suspect it's an issue related to the fact that I'm using an LVM setup this time, but that's just a suspicion.) I've found that ELILO is *much* easier to set up and less trouble-prone on this system. Maybe that's just a quirk of this particular computer, though. I plan to try on a VirtualBox setup and on my Mac Mini, too. I'll post details if ELILO is as superior on these systems as it is on my MythTV box.

---

### Post by manders2600 on 2011-05-20
Well, if ELILO is superior, I will give it a try.  I was able to get my system working well, although there were still some weird issues, which may not have had anything to do with GRUB, but I am not entirely certain.  

However, for issues totally unrelated to this, I had to do a reinstall last weekend (bad HD), and I have not yet reinstalled Ubuntu (just Windows 7 right now), as I have been working on an Ubuntu media server, and I only want one machine to be potentially out-of-commission at a time.

But, this build should be finished sometime this weekend, or perhaps early next week, and I would love to give ELILO a try, if it seems to work better.  I think my trepidation had to do with there seemingly being less documented about it than GRUB, and GRUB is familiar, at least a little bit.

Thanks for all your help on this previously, it was huge!  It would have taken me quite a while to figure that stuff out.

(if you're not busy . . . [http://ubuntuforums.org/showthread.php?t=1763613](http://ubuntuforums.org/showthread.php?t=1763613))

---

### Post by nrundy on 2011-05-20
Hey are these problems with 64-bit ubuntu installs on UEFI specific to dual-boot setups? or do they affect stand alone ubuntu installs as well?

---

### Post by srs5694 on 2011-05-21
I haven't had much luck with ELILO on my VirtualBox or Mac Mini installs, so that dampens my enthusiasm for it. Still, it's superior enough on my MythTV system that I'm planning to keep it on that one. Since that's my only "real" 64-bit UEFI installation, my suspicion is that ELILO will work better on other "real" 64-bit UEFI systems, too. (The ELILO problems on VirtualBox and the Mac Mini seem to have to do with video support, which is weird for both of them.)

ELILO is actually much older than GRUB 2's (U)EFI support. The /usr/share/doc/elilo/elilo.txt.gz file in the Ubuntu package contains documentation. It's not a hand-holding tutorial, but if you take the time to read it and some of the example configurations you should get a pretty good idea of what it's about. Also, the Ubuntu package includes a script called "elilo" that does most of the installation work. (Type "man elilo" to read its documentation.)

FWIW, I'm convinced that part of the reason ELILO works better than GRUB 2 on the one system for which it does work better is that it's much simpler than GRUB 2. GRUB 2 is a mess because it's got so many complex options that if the configuration gets just one of them wrong, it falls down like a house of cards. Because ELILO's got fewer options, there's less opportunity to get it wrong. Here's my complete ELILO configuration file (elilo.conf) from my MythTV box:

```

prompt
timeout=50
default=linux

image=vmlinuz-2.6.38-8-generic
        label=linux
        initrd=initrd.img-2.6.38-8-generic
        read-only
        root=/dev/seeker/u1104
        append=""

```

Compare that to the GRUB 2 configuration I posted in post #11. Even considering that this example has just one kernel menu option (vs. two for the GRUB 2 configuration), it's much simpler and easier to understand.

One drawback for a dual-boot configuration with ELILO is that, AFAIK, there's no way to tell ELILO to chainload another OS; once ELILO executes, it's Linux or back to whatever called it. Thus, you'll need to rely on the EFI's boot selector to boot another OS or use another tool, such as rEFIt. I've gotten rEFIt working on all my (U)EFI-based systems, but it's got the video glitch I showed in post #18 on two of them. Using rEFIt in text mode eliminates that problem, but it's less pretty that way.

nrundy, some of the problems in this thread are specific to dual-boot configurations, but many of them apply to Linux-only configurations, too. The problem is that Ubuntu's installer has some half-baked GRUB 2 configuration options for UEFI. It's possible to get around these problems, but you have to either know what you're doing or have access to good advice.

---

### Post by nrundy on 2011-05-21
Is it likely these half baked Grub configs will be improved upon with future ubuntu releases? so it's just a short-term problem with Natty?

---

### Post by srs5694 on 2011-05-21
> **nrundy said:**
> Is it likely these half baked Grub configs will be improved upon with future ubuntu releases? so it's just a short-term problem with Natty?

Of course. UEFI is still a "bleeding-edge" technology, as far as x86-64 distributions are concerned. (AFAIK, all Itanium computers use UEFI, but Ubuntu is mainly an x86/x86-64 distribution, although ports to other platforms -- including Itanium -- are available.) UEFI is on the rise, though, so as more developers get their hands on UEFI-based hardware, the default settings are bound to improve.

---

### Post by Windwoodtrader on 2011-06-18
I think that I have a similar problem installing Natty onto a 500 Gig box with Windows Vista resident. I did the install requesting as installed updates on the fly. The initial install went OK and started OK with some minor housekeeping problems. The next day I got an update screen showing around 140 patches. I did the upgrades, and rebooted. Got to a UNITY screen with icons up the left side and nothing else except a cursor with which I could not cause any action. Had to do a hard kill and reboot- Same thing.
Decided to wipe the whole disk and do a clean install- No more Vista. Everything OK until I followed direction and upgraded- Rebooted and watched my frozen screen again. Once again it took a hard kill.

I re-installed and got up and running but **_[COLOR=Black]did not[/COLOR]_** do the "security Upgrade." So far everything is OK. I'm sure that the upgrade will put me down in flames.

Obviously there is a condition in the install package or the upgrade package that causes mayhem but my little experience precludes my finding it. I have no intention of upgrading unless I can eliminate the problem.

I'm running on an HP Pavilion Slimware box with an AMD Athlon X2 processor (about 4 years old) and a single 500 Gig non-partitioned hard drive.

Anyone got a thought?

---

### Post by oldfred on 2011-06-18
@Windwoodtrader
Welcome to the forums.

But your problem is not at all related to UEFI which is what this thread is all about. Please start a new thread with a good title for your issues.

[FONT=Arial][SIZE=1]**Suggestions on how to get your support questions answered as quickly as possible**[/SIZE][/FONT]
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
[B][FONT=Arial][B]New to Ubuntu? Start here...  
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)
[/B][/FONT][/B]
I am not regularly running Natty, so I have not had an issues.
Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by mr_raider on 2011-08-01
I'm trying to install to an Lenovo x120e in UEFI mode. If I try a live cd, it won't even boot, and the I go back to the boot device selection screen.

With a Live USB, I can boot in to the live environment and go through the install. 

I create a GPT table on the disk, and the default installer will go through and create the fat32 efi partition and the main ext4 partion. However, at the end of the install, the installer tries to install GRUB and says it failed and was unable to install grub to the device. I then fall back to the live USb desktop. Everything seems installed from what I can see, but no GRUB.

Any ideas?

---

### Post by srs5694 on 2011-08-01
Depending on how you do the install, you may need to explicitly flag the EFI System Partition (ESP) as an "EFI boot partition" (I think that's what the Ubuntu installer calls it, but I'm not positive; it's some not-quite-standard term, in any event).

---

### Post by mr_raider on 2011-08-01
> **srs5694 said:**
> Depending on how you do the install, you may need to explicitly flag the EFI System Partition (ESP) as an "EFI boot partition" (I think that's what the Ubuntu installer calls it, but I'm not positive; it's some not-quite-standard term, in any event).

I tried manually partitioning in gparted, and creating a 200MB fat16 partition. Then I flag it as EFI in the installer, and install the bootloader to /dev/sda. Same issue.

I should note I'm using an SSD

---

### Post by vm_boy on 2011-08-17
I'm having pretty much the exact same issue.  I'm very new to Linux and vaguely understand GRUB, etc., but I'm learning.  In fact, this is my first-ever post in these forums.

Manders, could you post your boot.cfg file with the Windows boot options added?

Some other information that I've found is this shell file:
[https://github.com/skodabenz/My_Shell_Scripts/blob/master/grub2/grub2_uefi.sh]("https://github.com/skodabenz/My_Shell_Scripts/blob/master/grub2/grub2_uefi.sh")

And:
[https://help.ubuntu.com/community/UEFIBooting]("https://help.ubuntu.com/community/UEFIBooting")

If you can make heads from tails with that let me know.  I plan on chugging through some of this tonight and I'll let you know what I figure out.

BTW, my system is:
Mobo: ASUS P8P67-Pro
CPU: i5-2500k
GPU: eVGA GeForce 550-Ti
RAM: 4x4GB G.Skill Sniper (1600)

---

