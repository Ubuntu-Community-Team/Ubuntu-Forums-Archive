---
title: "Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1"
date: 2014-12-09
forum: Installation &amp; Upgrades
---

### Post by adrian_patch on 2014-12-09
Hello, 

I have been using ubuntu for about 4 years, I am not a coder or developer - I can run terminal commands/access BIOS etc, but need to be guided!

I  created a boot USB for Ubuntu 14 LTS (64 bit) and installed said release  on my new Acer Aspire ES1-512 in UEFI (erasing Windows 8.1) - the computer  won't boot without the USB in ('No Bootable Device') and when it has booted from USB it won't  close down properly, just hangs part way through. Quick start and Secure  boot were disabled in Window and BIOS/UEFI (though showing secure boot as 'disabled' BIOS still shows Secure boot as  'Standard!). I think I may have had the secure boot enabled when I installed ubuntu (I was going round in circles late last night so can't be 100% sure!), but have since disabled it.

I tried boot repair and it gave me the following web address to email: [http://paste.ubuntu.com/9432795/](http://paste.ubuntu.com/9432795/)

this is mostly gobbledegook to me! ... right at the end it says:

"Boot successfully repaired.
You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!"

I have no idea how to do the last bit!!

Any help (spellled out) would be gratefully received!

(another post I saw after extensive searching suggested a fresh install with secure boot disabled might work, but am hoping someone here can give me a clear and definite steer)

Thanks
Adrian

---

### Post by oldfred on 2014-12-09
Another user with similar Acer:
[http://ubuntuforums.org/showthread.php?t=2256026](http://ubuntuforums.org/showthread.php?t=2256026)

Your install seems ok, Boot-Repair may be just telling too much. In UEFI you may only see ubuntu.

this was a list of all the entries in UEFI:
```
 BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 2001,2002,2003
Boot0000* Unknown Device:     HD(1,800,100000,7dcc3c77-1d3f-4221-8590-65982a0f320a)File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])RC
Boot0001* USB HDD: TDK    ACPI(a0341d0,0)PCI(14,0)USB(0,0)HD(1,3e,774d8a,000920d8)RC
Boot0002* [COLOR=#ff0000]ubuntu[/COLOR]    HD(1,800,100000,7dcc3c77-1d3f-4221-8590-65982a0f320a)File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC


```

Not sure why you have an unknown device?
But can you choose the ubuntu entry in UEFI boot choices, or from one time boot key often f10 or f12 but varies by vendor.

Some vendors also modify UEFI to only boot an entry that says Windows. 

If you cannot boot ubuntu or set it as a default we rename it to "Windows" and system will happily boot Windows.

You may have a supervisory  password as discussed with this Acer?
[http://ubuntuforums.org/showthread.php?t=2176273&p=12800489#post12800489](http://ubuntuforums.org/showthread.php?t=2176273&p=12800489#post12800489)

If you need to rename grub or shim to Windows see d: in this list of work arounds for systems that only boot Windows.
       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
[/URL]
 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

You can also use grubx64.efi instead of shim.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\grubx64.efi"

More details on what efibootmgr can do:
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by adrian_patch on 2014-12-11
Thanks oldfred,

although some of your advice went a little over my head (!) enough sank in as I did manage to select ubutu in UEFI and it did boot - unfortunately it froze when shutting down. I had to power button shut-down, and although it would sometimes boot, sometimes freeze on boot, it would always freeze on closedown - I was using the power button to close down a little too often. I did another boot-repair but to no avail. 

Rather then keep going round in circles I decided to go into legacy mode BIOS and USB-live install 12.04LTS - this appeared to work, but then boot was slow and sometimes froze. So, I did a boot-repair. It reported that the grub or boot (?) may be too far from the start of the disk, and suggested maybe making a new partition at the fron of the disk and moving it there - sorry if this sounds vague, but the address for the boot-repair report (I wrote the number down) said that it couldn't be found!

Anyway, I started googling the bit about moving grub closer to the start disk and found this guide:
[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

I have worked my way through, but now the boot-repair seems stuck at step 6 while executing:

'Purge kernels then reinstall last kernel sda1 (ins). This may take some minutes' .... well 2 hours later and it is still going at it. I am going to have to stop this boot-repair as it appears to be stuck - and hope that doesn't have adverse implications for the computer!


Where am I now: having spent many hours studying forums and other websites looking for a clue as to how to sort this out; I am frustrated - all the while my girlfriend is saying "maybe we should just have windows"! I would rather not, of course, regardless of the fact that I doubt I could re-install it anyway!

so, I will take a deep breath and look for a clean-start way to get ubuntu working on my new laptop - something I naiively thought would be acheivable with an hour or two's work.

If anyone has had any success doing this on an ACER ASPIRE ES1-512 pre-loaded with Windows 8.1 (now erased) I would love to hear how it is done (not on a Dell, Asus, HP or whatever, thanks!) - this is, apparently a common laptop, so I am hoping someone has had some success that they can share...

thanks all

---

### Post by Gordonbp531 on 2014-12-11
Hi, I have an Acer Aspire E3 that came with Windows 8.1. Although (obviously!) not the same model, it may have the same BIOS.
Is your BIOS InsydeH20 rev 5.0?

if it is, then this is what happened with me.
I created unallocated disk space in Windows and re-booted from the USB stick containing Ubuntu 14.04
the install went correctly, and I re-started after it finished.
No sign of Ubuntu AT ALL, it booted straight into Windows, although the Ubuntu partition had all the files on!
What I discovered eventually, is that I had to tell the BIOS thast Ubuntu was a "trusted UEFI file"
Once I'd done that and re-booted, the GRUB menu appeared and all is well.

To do this, you have to go into the BIOS, and on the Security Tab you have to enter a Supervisor password.
This gives you access to the  "select an UEFI file as trusted for executing" where you can add the Ubuntu file as trusted.
NB - you have to install GRUB to the EFI partition to enable this in the first place.
Here's a picture:
[https://uk.owncube.com/public.php?service=files&t=18c647c338c71d2fe8bb3839902bfbea]("https://uk.owncube.com/public.php?service=files&t=18c647c338c71d2fe8bb3839902bfbea")

Hope that is of some help!

---

### Post by oldfred on 2014-12-11
Do not create the /boot partition. That advice is for some older BIOS or external drives. I have yet to see a newer UEFI based system where that is an issue. And a /boot partition makes some repairs more difficult. But if using BIOS mode to boot and gpt partitioning you do need a bios_grub partition.

       [URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot
[/URL]
 Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

Some possibly similar systems:
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html](http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html)




[URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]
[/URL]

---

### Post by adrian_patch on 2014-12-24
Update: 

I had to walk away from this as it was getting me down - then an outage of a week by my internet provder provided another cooling off!

I have now got 14 LTS running in legacy mode - almost there: start-up is slow, and it freezes at shutdown (the screen with the dots) I gather from web search that this may be due to MBR versus GPT partitions on my disk, but it is too technical for me at this stage to discover how to see how mine are partitioned or remedy it.

Thanks guys for responding - 

Gordon - as I mentioned at the top, I deleted Windows so no working with that; also, had managed to set trusted in UEFI - it was going round in circles that led me to try legacy BIOS.

Oldfred - I already created that partition before I read your post!

I will continue searching for a full solution. If i get there I will post a guide suitable for non-techies like me - I find that almost all informtion that gets posted here and elsewhere assumes far too much previous knowledge for the average joe who wants to buy a basic spec laptop and install ubuntu over windows (which is surprising to me, since if this were not the case then many more would be switching to ubuntu - my two-pennies-worth)

Cheers

---

### Post by oldfred on 2014-12-24
Screen issue should have nothing to do with MBR(msdos) or gpt. That is just partitioning and partitioning is related to whether booting in BIOS or UEFI.

Usually screen issues are related to video card or chip.

If Intel chip, then nomodeset does not usually work, but you add a different boot option the same way. If Intel see ubfan1's post on several options. Usually one of them works.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    
If you only have Ubuntu installed you probably do not normally see grub menu as it just defaults to boot.
If in BIOS mode you hold shift key from BIOS screen until menu appears. If in UEFI mode then you press escape key often several times while UEFI screen is loading.

---

### Post by adrian_patch on 2015-01-02
Thanks for your patience with this oldfred.

The ubuntu installation has been getting progressively more unstable - to the extent that the computer locks-up/freezes regularly - with no cursor and no response from the keyboard - I can't get a terminal window when this happens.

This is in addition to the following problems:
- screen freezes at shutdown 90% of the time (despite various attempted fixes from web) - neccesitating power-button shutdowns (Probably causing some system damage);
- arrow keys often dont work (sometimes they open rhythmbox!)

Given I made the /boot partition before I saw your advice not to, I have probably done something that I shouldn't - I tried copying the gparted screen-print picture of the partitions here but not sure if I have done so correctly: [IMG]/home/adrian/Pictures/gparted Screenshot from 2015-01-02 22:03:07.png[/IMG] - it may now be attached below!

(oh, and I always get the grub sceen on startup, with various options, but always let it boot into option 1).

I am considering another fresh install, probably going back to 12.04 LTS, and then working methodically through any issues that arise - but want to make sure that I have the disk formatted and partitioned correctly first -- what would you (or anyone else!) recommend for this? 

Thank you.[ATTACH=CONFIG]258963[/ATTACH]

---

### Post by balbkubrox on 2015-01-04
Sorry to hear you are struggling with your laptop. i am writing this from a successful installation of Mint 17.1. on the same model.
I followed a guide on the Mint forum and successfully partitioned and installed Mint, booting from the uEFI. It works. I also had to blacklist some drivers to stop the hanging shutdown problem I was having [it was worse than that - it affected the boot process too]. This may be the info you need to cure your hanging problem. The only trouble I have noticed since is that the trackpad occasionally freezes when booting up. A reboot is all I can do to cure it, but it always works second time...
You can read my progress at[URL="http://forums.linuxmint.com/viewtopic.php?f=42&t=163126&start=20#p961212"]
http://forums.linuxmint.com/viewtopic.php?f=42&t=163126&start=20#p961212[/URL]
Go to the top of the thread for the full details of the EFI installation. Mint shows as ubuntu on the efi partition so I imagine much if not all of the info on that thread will be useful to you.

---

### Post by adrian_patch on 2015-01-06
Hi balbkubrox -and thanks for your input.

Funilly enough, I had been looking around at other distros and settled on trying Mint, initially alongside the ubuntu, leaving the latter as a 'project' while having a stable system that I can use - i feel comfortable with ubuntu after a few years use so would like to remain acquainted if possible (i also just installed peppermint on an older Acer Aspire One that had been running Ubuntu ok for several years since purchse but just 'died' after getting a load of updates - and other niggly little problems over the last 12 months).

Anyway, I have created a bootable USB with Mint Mate edition, but cannot get the main machine (Acer Aspire ES1) to live boot; got further with a Startup Disk-created stick than with one created with unetbootin, but not all the way. This is in legacy bios, so may next try in UEFI, and 17.1 Cinnemon (the range of Mint versions/distros is a little overwhelming at the moment).

I will have a look at the thread you posted and see how I get on - it would be good if the driver-blacklisting (whatever that is!) also works with ubuntu, but I'm also now intrigued about trying Mint as well.

Cheers!

---

### Post by buhuhu on 2015-01-07
Hello, 
Don't know if it is still useful, i bought a Acer Aspire ES1-512-C39M and spent more than 3 hours trying to install xubuntu 14.04.1 / 64 (several usb instalation atempts by trying all combination of bios settings, finally i was able to run xubuntu in try mode and install the system from x - but no way to boot in after restart). After allot of fun browsing again the few bios settings (if you check uefi - the secure boot is already enable and no way to disable it), i find a notice about how to disable secure boot (few words lost nowhere on acer site) - you have to create a supervisor password from security (all from bios settings - by F2), confirm the password and the secure boot (from boot menu) will be active. Also the secure boot mode options from security menu will be active. In this last one at: select an uefi file as trusted for executing - select HDD0 - then <EFI> - then <ubuntu> and finally enable the 3 efi files inside (shimx64.efi, grubx64.efi and mokmanager.efi) - be sure to type exactly Yes (not yes) for confirmation for all 3 files (nice homework for a user). Well after all this funny staff i was able to boot the xubuntu from hdd, half tired and half astonished that all this fun is hapend on my manny payd for this system.
Finally the system works quite nice, i write this only to save the several hours for others in the same situation.
Have fun. ;)

---

### Post by buhuhu on 2015-01-07
Hello, 

Don't know if it is still useful, i bought a Acer Aspire ES1-512-C39M  and spent more than 3 hours trying to install xubuntu 14.04.1 / 64  (several usb instalation atempts by trying all combination of bios  settings, finally i was able to run xubuntu in try mode and install the  system from x - but no way to boot in after restart). 

After allot of fun  browsing again the few bios settings (if you check uefi - the secure  boot is already enable and no way to disable it), i find a notice about  how to disable secure boot (few words lost nowhere on acer site) - you  have to create a supervisor password from security (all from bios  settings - by F2), confirm the password and the secure boot (from boot  menu) will be active. Also the secure boot mode options from security  menu will be active. In this last one at: select an uefi file as trusted  for executing - select HDD0 - then <EFI> - then <ubuntu>  and finally enable the 3 efi files inside (shimx64.efi, grubx64.efi and  mokmanager.efi) - be sure to type exactly Yes (not yes) for confirmation  for all 3 files (nice homework for a user). Press F10 to save bios settings and restart.

Well after all this funny  staff i was able to boot the xubuntu from hdd, half tired and half  astonished that all this fun is hapend on my manny payd for this system.
Finally the system works quite nice, i write this only to save the several hours for others in the same situation.
Have fun. :wink:

---

### Post by buhuhu on 2015-01-07
Hello, 

Don't know if it is still useful, i bought a Acer Aspire ES1-512-C39M  and spent more than 3 hours trying to install xubuntu 14.04.1 / 64  (several usb instalation atempts by trying all combination of bios  settings, finally i was able to run xubuntu in try mode and install the  system from x - but no way to boot in after restart). 

After allot of fun  browsing again the few bios settings (if you check uefi - the secure  boot is already enable and no way to disable it), i find a notice about  how to disable secure boot (few words lost nowhere on acer site) - you  have to create a supervisor password from security (all from bios  settings - by F2), confirm the password and the secure boot (from boot  menu) will be active. Also the secure boot mode options from security  menu will be active. In this last one at: select an uefi file as trusted  for executing - select HDD0 - then <EFI> - then <ubuntu>  and finally enable the 3 efi files inside (shimx64.efi, grubx64.efi and  mokmanager.efi) - be sure to type exactly Yes (not yes) for confirmation  for all 3 files (nice homework for a user). Press F10 to save bios settings.

Well after all this funny  staff i was able to boot the xubuntu from hdd, half tired and half  astonished that all this fun is hapend on my manny payd for this system.
Finally the system works quite nice, i write this only to save the several hours for others in the same situation.
Have fun. :wink:

---

### Post by oldfred on 2015-01-08
Thanks buhuhu.

That is more detail than most have posted on the issues of how to correctly enable password & settings.

---

### Post by lugeperez on 2015-01-08
Hello!
I have the same model, and I am experimenting some troubles too,  since I Installed several times ubuntu and lately linux mint 17.1. 
Once I used the legacy mode from the BIOS, I was able to install the linux based operating systems, but most of the times,
when I tried to shutdown it hangs, and I need to use the power button to finish it.
I have tried diferent suggestions from the web, but didn't work for me.
I haven't tried solutions propossed on this thread yet, but at least I'm glad to hear that I'm not alone in the research for this problem, adrian_patch :)
With the good will of you, people, maybe we'll find a solution soon.
):P

---

