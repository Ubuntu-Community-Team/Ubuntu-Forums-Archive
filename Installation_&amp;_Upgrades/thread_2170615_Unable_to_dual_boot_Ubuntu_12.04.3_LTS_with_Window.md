---
title: "Unable to dual boot Ubuntu 12.04.3 LTS with Windows 8"
date: 2013-08-26
forum: Installation &amp; Upgrades
---

### Post by eric18 on 2013-08-26
I just purchased an Acer E1-571-6837 laptop that came with Windows 8 pre-installed.  I would like to have a dual boot system with Ubuntu 12.04.3.  However, after installing Ubuntu with the LiveCD, the laptop goes straight to Windows without the option of loading Ubuntu.  

I tried fixing this twice using boot-loader on the LiveCD, but I still can't load Ubuntu.  The first time I tried boot-loader the BIOS were set to UEFI  with secure boot enabled.  The Boot-Loader output can be found here:  [http://paste.ubuntu.com/6026783](http://paste.ubuntu.com/6026783).  The second time BIOS were set to Legacy mode with secure boot disabled and boot-loader asked me to paste a few commands into the terminial, which I did.  The boot-loader output from this session can be found here: [http://paste.ubuntu.com/6026850](http://paste.ubuntu.com/6026850).  

The BIOS version I am running is v2.11.  I installed Ubuntu with the BIOS in UEFI mode.

I am not sure if my partitioning scheme is causing any problems or not.  I can provide that information if needed.  Also, I could try Ubuntu 13.04 if someone thinks that would help.  

Any suggestions you can give me would be great.  Thanks so much!

---

### Post by oldfred on 2013-08-26
Your first install had the Microsoft signed grub shim file and Linux kernels. From UEFI menu you just had to choose to boot the ubuntu entry.
Your second install is in UEFI mode, but does not have signed files. It also should boot from UEFI menu ubuntu entry, but you have to have secure boot off. With secure boot on only signed systems will boot.

Should be something like these others posted.

---

### Post by eric18 on 2013-08-27
Thank you oldfred for the information.  I think I am better understanding the problem.

Just to clarify, I only installed Ubuntu once.  It sounds like you think I installed it twice.  However, I did run boot-repair twice.  The first time was in UEFI mode and the second was in Legacy mode.  Or maybe I am misunderstanding you.  

So if I understand your answer correctly, the only thing I had to do after running boot-repair the first time (under UEFI) was change the boot priority order so Ubuntu would load first?

For additional information, when looking at the BIOS, it doesn't appear that I can turn secure boot off while keeping UEFI on.  The secure boot option is grayed out.  The only way I can see to turn secure boot off is to change from UEFI to Legacy mode.  Then secure boot becomes disabled.  However, in Legacy mode it doesn't recognize either Windows 8 or Ubuntu, in which case I have to boot to the LiveCD.  I have included pictures at the end of this post of the current state of the Security and Boot tabs of the BIOS.

So to try and fix my problem, I went into the BIOS, which I changed back to UEFI after my initial post because UEFI is the only way Windows 8 will load and I wanted something to load.  I then moved the Ubuntu option to the top of the boot priority list and restarted.  Upon restarting I got a blue box that said Ubuntu was blocked.  I hit "ok" and then another window came up that said HDD was also blocked.  I then went back into the BIOS and changed back to Legacy mode, which disables secure boot.  Upon restarting no OS was recongnized to boot from.  I then went back into the BIOS and put it in UEFI mode with secure boot.  I then booted into Ubuntu from the the LiveCD where I proceeded to run boot-repair again, whose output can be found here:  [http://paste.ubuntu.com/6026850](http://paste.ubuntu.com/6026850). 

Upon restarting I got the blue box again that said "HDD: has been blocked by the current security policy".  I clicked "ok", the messsage came up again, I again clicked "ok", and then Windows 8 booted.  I then went back into the BIOS and noticed the boot priority list no longer has Ubuntu in it (hence it is missing in the picture below).

I am wondering if reinstalling Ubuntu in UEFI mode (with secure boot on) and then putting Ubuntu at the top of the boot priority order will solve my problem.  Or, if I have messed things up so much, I could put the laptop back to its factory state using the Windows 8 recovery partition and essentially start over.

Again, your suggestions are very appreciated.  Thanks!



PS. Don't be fooled by the picture.  Secure Boot is grayed out.

---

### Post by oldfred on 2013-08-27
To get Boot-Repair to update Ubuntu with the secure boot versions of grub & kernel you have to boot it in secure boot mode.

       One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

Many systems have three options, UEFI with secure boot, UEFI, and CSM. But some like yours seem to only have secure boot on or off. Most of those will boot Ubuntu in UEFI mode and should also boot Windows in UEFI mode, but will also default to a BIOS/CSM boot if no efi files found.
But it sounds like yours may be one of the few that only boot Windows with secure boot on.
Microsoft requires vendors to let user turn off secure boot, but is not clear if then you can still boot Windows. Some systems do and others do not.
Have you updated to vendor's newest UEFI/BIOS? Sometimes that fixes other issues also.

You can attach screenshots from advanced editor and paperclip icon in top edit panel. Files need to be smaller or screenshots.

See line 254 in boot script which does not say signed. Then in 338 & 339 you show both unsigned & signed kernels already on your system. So it should just be an update to grub menu?

---

### Post by darinsson on 2013-10-08
For me it was about the same with an acer. I hade to boot with UEFI but secure boot off. 
Even if the installation of Ubuntu went well bit both enabled. So I had to disable Secure Boot and then run boot repair to have a proper dual boot installation with Ubuntu and Windows 8. But the other machine I had, I  had to make a password in BIOS before I could disable Secure Boot and still get UEFI installation.

---

