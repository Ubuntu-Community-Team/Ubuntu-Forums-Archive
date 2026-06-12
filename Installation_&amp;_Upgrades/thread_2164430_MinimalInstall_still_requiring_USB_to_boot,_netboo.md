---
title: "MinimalInstall still requiring USB to boot, netbook booting issue"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by xAWdhW8 on 2013-07-31
So a couple weeks back, I used a bootable USB to get Lubuntu (I believe it was 12.04) on my Asus Eee PC 1015pe netbook. I erased the windows XP that was on there. It worked for a couple days, then went corrupt (or so I have deduced, perhaps incorrectly), and starting giving me this upon booting up:

Reboot and select proper boot device or insert Boot media in selected boot device and press a key.

I attempted to reinstall Lubuntu the same way I had before, but now all of a sudden I was getting partitioning errors during the installation, which led to system crashes. I should note that booting a live version of lubuntu 13.04 works just fine. But installation was throwing one issue after a the next at me. I have also tried different distros, and each was giving me flack.

Finally I tried the MinimalInstall last night. I followed all the instructions on this tutorial page:  [https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

I downloaded the 32 bit mini.iso (Found in "Downloading" section)

Then I hooked up my ethernet and followed the instructions found in the "Method" section. Steps 1-10 worked fine.

Then I followed the command lines in the "Installation" section "For the full desktop installation use:"
Note: Commands 1-4 worked fine. The following command did nothing: 

rm /var/cache/apt/archives/*.deb

Then I rebooted, and Lubuntu seemed to be working just fine (!)

The USB was still plugged in, so I turned off the netbook. Unplugged the USB, and turned it back on only to find that the same message had appeared: 

Reboot and select proper boot device or insert Boot media in selected boot device and press a key.

I plugged the USB back in, got back to my desktop, opened the terminal, and followed the commands in the "For the Lubuntu core installation use:" section, which spit back some language suggesting that these steps had already been covered and a core was already installed. 

Long story short, my netbook will not let me use lubuntu unless my USB is plugged in. It's as if it installed lubuntu to the USB and not my netbooks harddrive. When it boots up (with USB in) it doesn't give me the usual installation screen of a bootable USB (try lubuntu live, check cd for errors, install lubuntu). It just starts the os and goes about things as if it's business as usual. Obviously its running crazy slow because it's using the usb though.

Can anyone help?

Also, I should mention that at some point during the grub installation, it told me that I could remove the usb and continue on with the process, except when I removed the USB, the installation stopped until I plugged it back in. I wish I could be more specific about which step during the installation process this happened, but I didn't document it.

---

### Post by oldfred on 2013-07-31
I have not installed minimal.

But is the issue where did grub install its boot loader? Default installs always install to sda, but some BIOS/systems make the USB drive sda which then causes issues as it installs to the wrong drive.

Or is your internal drive having issues?

You normally do not remove install device until it is done and sometimes the writing is slower than the screen, so best to make sure it is done.

       sudo parted /dev/sda unit s print

      
 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in advanced  edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

If system can run Boot-Repair you can also run it. Its BootInfo report includes the bootinfoscript plus additional information.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

