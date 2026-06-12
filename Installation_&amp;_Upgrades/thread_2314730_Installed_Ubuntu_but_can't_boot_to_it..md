---
title: "Installed Ubuntu but can't boot to it."
date: 2016-02-23
forum: Installation &amp; Upgrades
---

### Post by jdkcarlson on 2016-02-23
I bought a new Windows computer and immediately backed up Windows, changed the partition sizes, installed Ubuntu from a stick onto the big partition, and failed to change the boot order. Now I can boot Ubuntu only off the stick and can't get to the other partition. 

After fiddling with the BIOS F2 boot order to no avail (it starts with Windows boot manager no matter what I pick), I figured out how to enable the F12 boot menu to let me boot off the stick, then I tried Boot Repair.

This was the preliminary report:
[http://paste.ubuntu.com/15176854/](http://paste.ubuntu.com/15176854/)

After that, I ran boot-repair, but it told me there was an error because of Secure Boot:
[http://paste.ubuntu.com/15176884](http://paste.ubuntu.com/15176884)

So I disabled that and tried again:
[http://paste.ubuntu.com/15177060/](http://paste.ubuntu.com/15177060/)

There's still an error, but I don't know enough to know what. The computer boots to the internal hard drive automatically, which is good, but then I'm looking at Windows Boot Manager again. I've already fiddled with the boot priority order in BIOS with no success, so I don't know what to do next. I also tried to run the Windows command line command recommended, but was told I lack privileges. My password won't let me run cmd as administator, so I don't know what to do here either.

I am not going to use a Windows laptop again, so right now this computer is almost useless to me. Any advice you have would be appreciated.

---

### Post by oldfred on 2016-02-23
I saw mention of Acer?

Boot-Repair was supposedly updated to add a mention on Acer systems that Supervisory password & setting "trust" on Ubuntu/grub's efi boot files.

       Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)

---

### Post by spencer2 on 2016-02-25
I'm not sure if this is the right place but it seems like a good place: 
i just got a new laptop with Win10 on it; i downloaded iso file directly from ubuntu website, ran disc, partitioned and installed but when booting up laptop I'm not getting the option for which OS I want to boot into. I do have an acer aspire F15. I don't know if that matters. I've seen a couple different post about terminal codes to run and programs to download in the Ubuntu OS, but I can't get to that OS. I only seem to be able to get into Windows.
Any tips on getting to my Ubuntu when booting up please?

---

### Post by oldfred on 2016-02-25
@spencer2
Generally better to start your own thread as boot issues while often similar, also need different commands. 
But in your case it does sound identical and solution is in post #2 above. 

If not, start a new thread and post link to Summary Report from Boot-Repair.

---

### Post by spencer2 on 2016-02-25
@oldfred: i saw this original post was also an acer so i did piggyback the post. Thank you for the tip towards answer #2. i will give it a shot and if I have any further issues i'll start a new thread. thank you again for the assistance.

---

### Post by jdkcarlson on 2016-03-07
Hi! Thanks!

I understood from your comments that I should upgrade my BIOS and try again. I did that without especial success. The version I updated to is this one:

[http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_1.05_A_A.zip?acerid=635841043247305739&Step1=NOTEBOOK&Step2=ASPIRE&Step3=ASPIRE%20R5-471T&OS=ALL&LC=en&BC=ACER&SC=PA_6](http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_1.05_A_A.zip?acerid=635841043247305739&Step1=NOTEBOOK&Step2=ASPIRE&Step3=ASPIRE%20R5-471T&OS=ALL&LC=en&BC=ACER&SC=PA_6)

My first attempt failed because redoing the BIOS set Secure Boot again and I had to get rid of it. So I tried again, and got another error message. Here is the report:

[http://pastebin.ubuntu.com/15325780/](http://pastebin.ubuntu.com/15325780/)

My expertise level is too low to make too much of it, but I can see it doesn't seem particularly sanguine.

---

### Post by oldfred on 2016-03-08
I have to change many settings back in old BIOS and even more in UEFI. And new UEFI or BIOS resets everything back to defaults. With BIOS I had to take photos. My new UEFI allows screen shots and lists changes before I save those changes.

Did you enable Supervisory password in UEFI and set trust on Ubuntu/grub's files as posted above?

---

### Post by jdkcarlson on 2016-03-08
All I did was install this newest BIOS, set the supervisor password, turn off Secure Boot, which Boot Repair asks me to do, unset the supervisor password, and unfreeze the HDD password. 

I don't know what UEFI is or how to get to it, and somehow didn't realize there was another step to the process that applied to my computer. I'll try to read through those and let you know how that goes.

Okay, I followed one of the links and now it boots to GRUB automatically. Is there a way to make it boot to Ubuntu instead?

---

### Post by oldfred on 2016-03-09
When you say boots to grub, to you mean grub menu or an error like grub rescue>

I just change timeout to 3 seconds from normal 10 second to boot Ubuntu. Then I still have time to press a key can choose something else to boot. 
In /etc/default/grub
#GRUB_TIMEOUT=10
GRUB_TIMEOUT=3

---

### Post by jdkcarlson on 2016-03-09
The Grub menu. It autoboots to Ubuntu after several seconds, but I have the option to do something else in the interim.

I would like it to just automatically boot to Ubuntu without any such intermission, and to be able to bring back that menu if need be by holding down a button on startup. Is that sort of thing feasible?

---

### Post by oldfred on 2016-03-10
If you change timeout to zero, then you do not have anytime to press a key. 
That was why my compromise is change from 10 sec to 3 sec.

 sudo nano /etc/default/grub 

And edit timeout as I posted above.

Other grub customization.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by jdkcarlson on 2016-03-11
I see. I did that. Thanks!

If I were to change it to zero, I could get it back if I needed just by changing this number to something positive again?

---

### Post by oldfred on 2016-03-11
But if system is not working, you cannot get into it to change the 0 back to 3 or 10.
You end up need to chroot from live installer or run Boot-Repair, or Supergrub. I actually have repair flash drives with all those plus a few other tools.
Grub will present menu on abnormal shutdown so you can possibly use recovery mode.

---

