---
title: "ubuntu 12.10 &amp; Windows 8 oem"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by Dendo on 2012-12-02
Hello, 

I tried to intall ubuntu 12.10 64bit (usb) on my new Sony T series. I disabled secure boot and followed instuctions from: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
I can boot to ubuntu but windows 8 will not boot and I just get the Invalid EFI file path" error. (I think Bug #1024383) As the instructions said I booted to live usb again and ran disk-repair (paste.ubuntu/1406514).  However it is still giving me the same error.  So I used the windows recovery to repair boot and i can now boot into windows 8 and it works fine.  I now have a raw partition where i had installed ubuntu originally. Any help would be much appriciated. Thank you.

---

### Post by oldfred on 2012-12-02
Clickable BootInfo 
[http://paste.ubuntu.com/1406514/](http://paste.ubuntu.com/1406514/)

It looks like Boot-Repair made fixes. It did add the correct UEFI chain entry. The 30_osprober versions are the old BIOS Windows chain load entries and do not work with efi.
       Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
    
Two others with Sony, not sure how similar they may be.
       Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)

       Sony Vaio dual UEFI boot with manual copy of files to efi partition
[http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/)

Is this an Intel SRT system?
That has some sort of RAID that causes issues.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
   > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by Dendo on 2012-12-02
Thank you so much,

I do have Intel SRT system. HDD 350GB and SSD 32Gb. I will read all the links you posted.  Again thank you.  Im very lost with this UEFI/GPT things this is very good learning experience.

---

### Post by oldfred on 2012-12-03
I think most of the Intel SRT systems were not the very new Windows 8, gpt partitions and UEFI.

But the issue with Intel seems to be that some how it uses RAID. I do not understand RAID, but thought it really only worked with drives of the same size. But this is some sort of exception.

It seems that you have to turn off the SRT to get Ubuntu to install, but then can turn it back on. Not sure if then the Ubuntu RAID drivers that you can install will let you see the Windows or not. 

I have always suggested a separate NTFS shared data partition & with Windows 8, it is even more important. 

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Dendo on 2012-12-03
Ok I double checked and my fast-start up was disabled but my secure boot was back on I guess after i used windows to recover it turned it back on.  So i tried again after double checking fast-start was off and disabling secure boot.  I still get the same error. [http://paste.ubuntu.com/1407197/](http://paste.ubuntu.com/1407197/)
I will try and use the method described in the link: Sony Vaio dual UEFI boot with manual copy of files to efi partition
       Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/]("http://ubuntuforums.org/showthread.php?p=11842855")
    just for more info I used the ubuntu installer (as advised by [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)   to format partions.  i dint use oter setting to try and do it manually.

---

### Post by Dendo on 2012-12-03
Ok I tried [http://www.hackourlife.com/sony-vaio...-04-dual-boot/](http://www.hackourlife.com/sony-vaio...-04-dual-boot/) but it didnt work. I could boo into ubuntu but the couldent boot into the windows loader or the windows i added to custom_40 the error is error file: /EFI/boot/mootmgfw.efi.old not found and for the windows loader (sda3 and sda5) the error was cant find command drivemap and invalid efi file path.  
I now cant boot into recovery to even repair to get windows back. I ran boot-repair and now i see options for windows UEFI recover, Windows boot UEFI bootx64.ef.bkp revovery, but even after i run it and runs the sony vaio care and fixes it still takes me back to the grub and still cant et into windows.  after i did the boot-repair here is the [http://paste.ubuntu.com/1407304](http://paste.ubuntu.com/1407304). any help would be greatly appriciated.

Update: I was able to use differnt option in Vaio Care and now I'm trying to do a system restore through windows 8.

---

### Post by YannBuntu on 2012-12-03
> [http://paste.ubuntu.com/1406514/](http://paste.ubuntu.com/1406514/)

Boot-Repair didn't detect your ESP. I will fix it ASAP. Please update and retry Boot-Repair in [~4hours]("https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages").

---

### Post by oldfred on 2012-12-03
I corrected the link to your manual repairs but those changes are just what Boot-Repair does.
I think some if not most of the remaining issue is the Intel SRT. Last pastebin BootInfo report still shows you not being able to 'see' the SRT partitions.

Most with the Intel SRT seem to say to go into the Intel SRT manage screen and turn it off, install Ubuntu then reinstate the SRT. Others just totally turn it off and Install Ubuntu to the SSD.

---

### Post by Dendo on 2012-12-03
Thank You, So I restored everything and am back to square one except partition that i had made for ubuntu was still there.  
Just to clarify I will do:

1. Backup 
2. Turn off fast-boot / use Inter SRT management to turn off and double check windows fast boot setting
3. disable secure-boot 
4. use ubuntu64bit iso or remix 
5. install using auto method 
6. reboot into live mode and run boot-repair

---

### Post by YannBuntu on 2012-12-03
Before doing step 2, please wait for all packages to be ready on [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages) , then retry the Recommended Repair of Boot-Repair.

If still not good, continue to step 2.

---

### Post by Dendo on 2012-12-04
OK I think it works I can boot into both Ubuntu and windows 8 (through the UEFI Windows selection on grub2) after selecting UEFI windows in grub 2 it takes me to a Windows Advance startup page where i can select start windows, repair etc.  

I thought it would load directly to windows8 but I am satisfied with this as long as it works. Thank you so much oldfred and YannBuntu.  I will mark thread as solved and also write my exact cumputer model and hardware and the eact steps i took to get it working so people with the same computer and issue can just follow.  

Also I think it may have worked on an earlier try but like an idiot i never tried to hit the start windows from that second windows page that you go to from grub.  Since i purchased a Japanese computer (and i CANT read Japanese I just ignored it on the earlier attempts) I live in Japan so and it was cheaper for me to buy here and my wife gets discount so that is reason I have JP computer.  

Again Thank you so much!

---

### Post by Dendo on 2012-12-04
VAIO T Series 13 inch (Only Japan has 13 model I believe)&#12288;&#12288;
SVT1312AJ
Windows 8 64 Bit (oem)
Hybred HDD 320GB(+SSD 32GB&#65289;-Intel SRT
Core i3-3217U&#65288;1.80GHz&#65289; 
4GB Memory&#65288;4GB×1&#65289;
Insyde H20 UEFI 

So just to make it clear on what I did to get dual boot with a brand new VAIO T Series with a OEM install of Windows 8 64bit.
(I'm sure ther are more efficient ways such as using the ubuntu remix iso so you dont have to install boot-repair each time but as i didnt want to download again and put on USB I just used my regular Ubuntu64bit ISO)

1. In windows went to power management and turned off fast-start 
2. went to advance start up and choose UEFI settings 
3. In the UEFI BIOS settings I Disabled secure boot and Intel AT service (I wont use anti theft) Saved and Exit
4. booted USB ubuntu64 ISO into live mode
5. connected to wireless Internet
6. Ran the install Ubuntu and used the Install Ubuntu alongside Windows option Not the Manual install.
7. adusted partitions through installer and installed normally
8. after install rebooted and grub appeared showing sda3 and 5 for windows and windows recovery tried both but both were error [bug# 1024383]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383") 
9. rebooted into ubuntu live mode, connect internet and added [boot-repair repositry and installed boot-repar]("https://help.ubuntu.com/community/Boot-Repair")
10. ran boot-repar with reccomended setting.
11. rebooted and voila UEFI WIndows entry added to grub. 
12. choose UEFI Windows entry which took me to Windows advance starup screen (blue one) choose start windows and done. 

So basically just same as instructed on the [ubuntu UEFI documentation]("https://help.ubuntu.com/community/UEFI") just with the making sure the  fast-start is off Havent tried to turn back on Inter SRt yet.  

Hope this helps

---

### Post by Dendo on 2012-12-04
OK back again.  After rebooting from Windows 8 I no longer get the grub menu and it boots straight into Windows.  I believe i read somewhere that Windows 8 overwrites something on reboot, I was hoping that didnt apply to me so I will do some searching and try and find a resolution.  Again any help would be appreciated in the mean time.  I guess I jumped the gun there when I marked thread as SOLVED.

Update: (hopefully last one) I rebooted into USB ubuntu live mode and re-ran boot-repair [http://paste.ubuntu.com/1410345](http://paste.ubuntu.com/1410345)
and rebooted and grub menu was back.  I was then able to boot into Windows through the UEFI Windows Loader entry. I then restarted and shutdown in windows 8 to see if grub would return.  Grub returned and all is good.  I think the last time i ran boot-repair the package [https://launchain](https://launchain) thanks to Ypad.net/~yannubuntu/+archive/boot-repair/+packages was not published yet. Again thank you Yannubuntu and oldfred for advice.

---

### Post by oldfred on 2012-12-04
Thanks for update and glad you got it working. :)

Those that search forum may find you explanation very helpful.

I will also link to this thread for others with Window 8 & Intel SRT issues.

---

### Post by YannBuntu on 2012-12-04
**@Fred:** the last days PPA versions of Boot-Repair (3.195~ppa19 to 22 i think) had bugs which prevented the creation of Windows UEFI entries, and that corresponded with what Dendo observed, so this case may not be related to SRT.

**@Dendo:** please could you re-activate SRT and tell us if that stops access to Windows?
- if no, then perfect, leave it like this.
- if yes, please run the Recommended Repair and tell us the new URL, then deactivate SRT, and tell us if the problem persists.

---

### Post by Dendo on 2012-12-04
@oldfred thank you again 

@YannBuntu Ok you got it, I will try and turn on the SRT and report back.

---

### Post by alexskw on 2013-04-11
Hello,
I have no experience with UEFI and need to buy new laptop. How is your progress and experience in using your vaio? If you did successfully install Ubuntu, do you have any issues with drivers?
Im attempting to buy Sony Vaio ultrabook SVT 1312V1ES:
Proc: i5 - 3317U 1,7G (2,6G Max)
Graphics: INTEL HD 4000
128 GB SSD
4 GB RAM
Just not sure if I will be able to use Linux properly. I dont care Win 8, dual boot is ok but without Windows is also fine!
Would you recommend to install Linux on UEFI or legacy mode?
Thanks!
Alex

---

