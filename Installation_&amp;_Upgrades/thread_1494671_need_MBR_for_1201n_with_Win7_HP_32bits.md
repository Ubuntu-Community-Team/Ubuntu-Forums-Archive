---
title: "need MBR for 1201n with Win7 HP 32bits"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by gawryl77 on 2010-05-27
Hi all,

I've got problem to recovery my Windows 7 Home Premium 32 bits after installing Ubuntu 10.04 on my 1201n netbook. Recovery mode (F9 key when system is booting) doesn't work (I mean doesn't boot at all) but I can still enter and boot from the rescue partition via grub. BUT afeter booting windows rescue (or whathewer calls it) I can choose one from: Recovery or Exit - after selecting Recovery system reboots and... grub welcomes me again, and gives me option to start Ubuntu 10.04 or Windows Resce. Of course I choose Windows Rescue (to complete the rescue process) but what I can see is only windows in recovery mode with two choises: Recovery or Exit - not the continue of allready started recovery mode... 

I am thinking that I need "fresh" MBR (i mean first 446 bytes of it) and put it on my 1201n. Can anybody send me it? 

You might ask me: MBR? WHAT FOR?! After changing my MBR to the fresh one I need to reinstall grub to /dev/sda3 and set the boot flag to that partition -and i hope it could work ;) Am i wrong? Any others ideas? How's gonna send me 446 bytes of his MBR?

one more thing: I've run [darkod]("http://ubuntuforums.org/member.php?u=946366")'s script (boot_info_script055.sh) and I saw a lots of garbages/strange things - here is full script's result [http://gawryl.pl/RESULTS.txt](http://gawryl.pl/RESULTS.txt))

---

### Post by darkod on 2010-05-27
First of all, I don't want it to sound like I am taking credit for someone else work. :) The wonderful script is not 'mine', it's meierfra's. :)

Just putting generic or windows MBR will not help you. The boot flag is important for the windows boot process, but a generic MBR can't call grub2 from a partition even if you put the boot flag on it.

Your results are very strange. You have some serious errors with /dev/sda5. It is reported in fdisk as Linux partition, but it is also reported as ntfs with errors on it. You could run testdisk to see what it detects and maybe it can update the partition table to make it correct.

As for running the recovery partition, it should usually have boot files to start it off. It seems /dev/sda3 is your recovery partition. If you don't have any data to recover from your computer, and if you want to run the restore process, you could try using Gparted from the live mode to set the boot flag on /dev/sda3 (remove it from /dev/sda2), and put generic MBR on /dev/sda with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore the warnings it will give you. That will install generic mbr which will just invoke the boot flag and should start off /dev/sda3.

However, usually the restore process wipes your hdd completely and creates the factory setup. If this is what you want to do, you might try the above.

---

### Post by gawryl77 on 2010-05-27
> **darkod said:**
> First of all, I don't want it to sound like I am taking credit for someone else work. :) The wonderful script is not 'mine', it's meierfra's. :)

upps, sorry for transfering copy rights to you - i am noob...but i am gonna be more patient next time ;)

> **darkod said:**
> 
Your results are very strange. You have some serious errors with /dev/sda5. 
hopefully for me i have no important data on my hdd, except recovery partition (/dev/sda3) and Ubuntu 10.04 (/dev/sda6). So i can do (almost) everything 

> **darkod said:**
> 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
is it the same as runnig (cleaning) the bootstrap via  [FONT=monospace]
[/FONT]```
dd if=/dev/zero of=/dev/hdX bs=446 count=1
```or somethings more?

> **darkod said:**
> 
However, usually the restore process wipes your hdd completely and creates the factory setup. If this is what you want to do, you might try the above.
I ve checked it by calling Asus Support Center - they told me that Windows Recovery will gives me a CHOISE to install on a first partition, or install on all hdd removing existig partition (strange!) - seems be nice in theory, but anybody had use it?

---

### Post by darkod on 2010-05-27
I'm not sure what the dd command you specified does, it looks like it's writing zeros in the MBR. Anyway, using lilo can install generic MBR on your disk.

It's good if you have option to install in the first partition, but in your setup it also depends what the first partition is. In your setup /dev/sda1 is actually extended partition holding the logical ones inside.
And then /dev/sda2 and /devsda3 are behind it on the disk. Plus, the first 40GB on the disk seem unused with no partition on them.

---

### Post by gawryl77 on 2010-05-27
> **darkod said:**
> 
It's good if you have option to install in the first partition, but in your setup it also depends what the first partition is.
thanks for pointing me that ;) i''ll be carefull -  first i am gonna run gparted and rearranged disks.

---

### Post by gawryl77 on 2010-05-27
ok, i've done some gpated stuff and Win7 RescueDisk (running from usb stick) and thinks look nice (see [http://gawryl.pl/newRESULTS.txt](http://gawryl.pl/newRESULTS.txt)).

Question:
is it a good idea to have grub installed in the particular partition (plus boot flag set to that partition) not on the MBR of /dev/sda ? IMO because window's installer will erase it every time it runs, so... am i thinking correct?

---

### Post by dino99 on 2010-05-27
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by darkod on 2010-05-27
I always prefer having grub2 on the MBR. Windows installer will overwrite it only when running windows installation, how often do you do that? Besides, it's very easy to reinstall grub2 back to the MBR.

If you put it on a partition you have to use EasyBCD or similar to add it to the windows bootloader because it can't see linux. Further more, you have to search for EasyBCD 2 which is not on the EasyBCD website (latest version there is 1.7.2) because only version 2 can 'see' grub2 and work correctly with it.
In my opinion, too much hassle to make windows bootloader see linux since it can't by default.

In your latest results file I still can't see a win7 installation, at least one that is recognized by the script. Did you reinstall win7 or not?

---

### Post by srs5694 on 2010-05-27
Putting GRUB on the boot partition's boot sector can protect it from Windows' tendency to think it has the right to do whatever it likes with the boot section of the MBR; however, this approach also requires that the boot loader in the MBR be able to redirect the boot process to the Linux partition. In the case of the disk partition reported by gawryl77, all the Linux partitions are logical partitions, and I don't believe the standard Windows boot loader can redirect the boot process to logical partitions, so you'll need to either put GRUB in the MBR or put GRUB in the linux partition and use some other boot loader that can redirect the boot process to a logical partition. I have no specific recommendations for products to use for the latter scenario. I know such tools did exist ten years ago or so, but I haven't kept up with them, so I don't know what might do the job today. IMHO, it's better to put GRUB in the MBR in this specific case.

My suggestion to get Windows booting is to try adding a GRUB entry to boot Windows via its boot partition rather than its recovery partition. The update-grub utility might do this automatically, but I'm not sure of that. If it doesn't, try adding the following to /boot/grub/grub.cfg:

```

menuentry "Windows Vista (on /dev/sda2)" {
      set root=(hd0,2)
      chainloader +1
}

```

Place those lines at the very end of the /boot/grub/grub.cfg file. You should see a new entry for Windows when you reboot, at the end of the list. If this works but update-grub didn't, you should copy those lines into your /etc/grub.d/40_custom file so that they'll persist the next time the system runs update-grub (as it does when you install a new kernel from the Ubuntu repositories, for instance). Note that I can make no guarantees that this will work. Resizing Windows partitions so that their start points change is risky at best, especially if you did the resizing with a Linux tool. It's conceivable that you'll have to re-install Windows to get it working again, sad to say.

It appears that you resized your Windows partition up, leaving room at the start of the disk; but some of the space freed in that way hasn't been overwritten, leaving old data in some unallocated parts of the disk. I believe this is causing at least some of the warning messages produced by the boot info script. If I'm right, this situation isn't actually an error; it's just that the script is trying too hard to find filesystems and is getting confused. OTOH, it could be I'm misinterpreting something. Other problems, such as the failure to read the last sector on /dev/sda4, may indicate filesystem corruption. Certainly /dev/sda4, at least, should be checked for errors with dosfsck in Linux or CHKDSK in Windows.

---

### Post by gawryl77 on 2010-05-27
> **darkod said:**
> I always prefer having grub2 on the MBR...
In my opinion, too much hassle to make windows bootloader see linux since it can't by default.
thanks for opinion. i have to think about it.

> **darkod said:**
> In your latest results file I still can't see a win7 installation, at least one that is recognized by the script. Did you reinstall win7 or not?
yes, it was to quick - i've still got  a problem with my partitions :(

fdisk results with:
```

root@eee1201n:/home/gawryl# fdisk -l

Dysk /dev/sda: 250.1 GB, bajtów: 250059350016
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 30401
Jednostka = cylindrów, czyli 16065 * 512 = 8225280 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512
Rozmiar we/wy (minimalny/optymalny) w bajtach: 512 / 512
Identyfikator dysku: 0x7f3fb23e

Urz&#261;dzenie Rozruch   Pocz&#261;tek      Koniec   Bloków   ID  System
/dev/sda1               1        5466    43905613+   7  HPFS/NTFS
/dev/sda2            5467       11083    45118522    5  Rozszerzona
/dev/sda3           11084       16183    40960000    7  HPFS/NTFS
/dev/sda4   *       29094       30400    10485760    b  W95 FAT32
/dev/sda5           30400       30401       16064+   b  W95 FAT32
/dev/sda6            8079       10690    20980858+  83  Linux
/dev/sda7           10691       11083     3156741   82  Linux swap / Solaris

Wpisy w tablicy partycji nie s&#261; w tej kolejno&#347;ci, co na dysku

```(sorry for my nativ language in the message below - how to switch to english for a moment?), anyway -  please focus on starting/ending partition 
```

 device        boot  start          end           blocks   ID  System
/dev/sda1               1        5466    43905613+   7  HPFS/NTFS
/dev/sda2            5467       11083    45118522    5  Rozszerzona
/dev/sda3           11084       16183    40960000    7  HPFS/NTFS
/dev/sda4   *       29094       30400    10485760    b  W95 FAT32
/dev/sda5           30400       30401       16064+   b  W95 FAT32
/dev/sda6            8079       10690    20980858+  83  Linux
/dev/sda7           10691       11083     3156741   82  Linux swap / Solaris

```and whats worry me a lot is extendend partition - it ends at 11083 but logical drives are outside it! i dont know how this happened, but i run Windows in a Rescue Mode and i choose Repair Problem :P after that everything looks nice, but i wasnt too patitent :P

now, gpartet won't coroperate with me, showng: my hdd is free of partitions, whole space is unalocated space! wow! 

any ideas how to fix it? i will try testdisk from ubuntu-livecd and see whats happen.

---

### Post by gawryl77 on 2010-05-27
ok,

Without waiting for any sugesstions i've decide to do Rescue Windows from my usb-stick (i've created it few days before, putting into it all the data from rescue partition that was on my brand new eeepc 1201n - and - of course - making it bootable). 

Actually, i was trying that before, but every time after chooing Recovery system reboots and end up with nothing. BUT this time it wasnt this scenario - i saw text console (cmd line) with running *ImageX Tool for Windows version 6.1.7600.16385 *.After 15 minutes  of waiting system reboots and...

success wasnt 100% because grub apears after reboot. Grub with messages:
```

error: unknown filesystem
grub rescue >

```so i run my system from (another) usb-stick with Ubuntu 10.04 to see whats happen with partition table - here is my new RESULTS.txt :  [http://gawryl.pl/new-new-RESULTS.txt](http://gawryl.pl/new-new-RESULTS.txt)).

I (succesfully) run gparted and saw nice results - 
/dev/sda1         is NTFS and Win7 (that is what i wanted)
/dev/sda2         is extended partition with 20GB of unallocated space (i will do NTFS for Windows data), and 
/dev/sda5    is my Ubuntu 10.04 (i hope its not modyfied by the Win Rescue process)
/dev/sda3         is primary partition with NTFS - i am gonna delete it and merge with 98GB of unallocated block - next, i will do extendend partition for more logical disks
/dev/sda4         is my Rescue Partition that i am gonna save
(and finnaly - there is 15.69MB of unallocated space - not important for me)

but now i am thinking what to do with grub - because i cant boot ANY OS from my netbook :P
awaiting for suggestions (and i will promise do nothing till you tell me what to do ;) )

---

### Post by darkod on 2010-05-27
OK, looks much better. :)

You will have to reinstall grub2 from live mode but at the same time update the grub.cfg because previously ubuntu was /dev/sda6 and now it's /dev/sda5, so the current grub menu will not boot anything I guess.

So you need additional commands for updating grub.cfg from live mode:

sudo mount /dev/sda5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys

sudo grub-install --root-directory=/mnt/ /dev/sda
sudo chroot /mnt update-grub

sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc

Hopefully that should get you up and running.

---

### Post by gawryl77 on 2010-05-27
> **darkod said:**
> You will have to reinstall grub2 from live mode but at the same time update the grub.cfg because previously ubuntu was /dev/sda6 and now it's /dev/sda5, so the current grub menu will not boot anything I guess.
its not clear for me - do i have to edit grub.cfg mannualy and REPLACE every /dev/sda6 to /dev/sda5 OR after all commands that you have written it will be done automaticly?

---

### Post by darkod on 2010-05-27
It's done automatically with the sudo chroot /mnt update-grub command. Just execute them one by one and I think it should be fine.

---

### Post by gawryl77 on 2010-05-27
@darkod
thanks for help, but still i've got not 100% success...

after your suggestions my netbook starts with grub and I can run Ubuntu 10.04 (actually i am writing from my eee 1201n) BUT when i am trying to run Win7 i've got:
```

Windows failed to start

File: Boot\BCF
Info: The Windows Boot Configuration Data file does not contain walid OS entry

```i can mount my Win7 partition to see what's inside Boot directory
```

gawryl@eee1201n:/media/06780C59780C4A3F/Boot$ ls
BCD       BOOTSTAT.DAT  el-GR  Fonts  ja-JP        nl-NL  ru-RU  zh-HK
BCD.LOG   cs-CZ         en-US  fr-FR  ko-KR        pl-PL  sv-SE  zh-TW
BCD.LOG1  da-DK         es-ES  hu-HU  memtest.exe  pt-BR  tr-TR
BCD.LOG2  de-DE         fi-FI  it-IT  nb-NO        pt-PT  zh-CN

```and file BCD* results with
```

gawryl@eee1201n:/media/06780C59780C4A3F/Boot$ file BCD*
BCD:      MS Windows registry file, NT/2000 or above
BCD.LOG:  MS Windows registry file, NT/2000 or above
BCD.LOG1: empty
BCD.LOG2: empty

```i am afraid that now it's Windows related problem, so probably nobody can help me :P 

but... maybe any ideas? maybe somebody can send me his BCD? (if one has 1201n with Win7 Home Premium 32 bits)

---

### Post by darkod on 2010-05-27
You can download win7 repair cd image here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

It's small and can fit on a cd, no need to waste dvd. With that cd you can boot and make small repairs, but not a full install. You can use it to repair the win7 boot files which seem wrong or missing.

Instructions for that are here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Note in the vista/win7 section there are two commands. You should be OK if you do just the /fixboot because if you also do /fixmbr it will overwrite grub2 on the MBR so you need to reinstall it again.
You only need to fix the boot files, not the mbr.

PS. I hope it works. If it doesn't there are still few more complicated things to try but I don't have too much experience with that. This is typical windows, you just restored it, and already the boot files are not working. :)

---

### Post by gawryl77 on 2010-05-27
> **darkod said:**
> You can download win7 repair cd image here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

yes, i've already found that page and that iso - so i create (another) usb-stick to boot from this and... it mades a lot of BAD THINGS - newRESULTS.txt was created - another thing is that i've used Repair mode, some machine, not the cmd line....
> **darkod said:**
> 
Note in the vista/win7 section there are two commands. You should be OK if you do just the /fixboot because if you also do /fixmbr it will overwrite grub2 on the MBR so you need to reinstall it again.
You only need to fix the boot files, not the mbr.

ok, i am gonna do this but i am not sure about Windows installer - maybe it hasn't finish? i mean... after purchasing eeepc i've installed Windows in two steps: first i've installed first/main part (?) and after reboot i've chosen language. This time was only one step. Maybe installation process doesnt finsih? How to check it?

> **darkod said:**
> 
PS. I hope it works. If it doesn't there are still few more complicated things to try but I don't have too much experience with that. This is typical windows, you just restored it, and already the boot files are not working. :)
ok, i will ask for more help if other fails

---

### Post by darkod on 2010-05-27
Maybe the win7 repair process got confused if the boot flag was not set correctly. Windows depends very much on the boot flag, and right now in your latest results, it is correctly set on /dev/sda1, your new win7 partition.

Try the repair from the cmd, hopefully it should work out OK.

---

### Post by gawryl77 on 2010-05-28
finnally, 99% success !
BIG thanks to darkod ;)

i've got both Win7 and Linux - and what's funny - grub wasn't rewriten from MBR after installing Win7. BTW: to complete the installation process i had to choose boot once from rescue partition, and two (or three) times from new Win7 partition. now everything is perfect.

Q1: 
how to remove 'start from Recovery Win partition' from the grub menu during the boot time? because i am not the only person who's gonna use that netbook and i am afraid of mistakes - i dont wonna go through install process one more time ;P

Q2:
i've sad that i am 99% sattisfied because... i cant enlarge my extendend partition OR create new one (is it possible to have 2 extendend partitions?). Ive got a lot of unused space that i cant allocate :P gparteg claims that he can create _only_ primary partition, but i need 2 logical drives (one for gentoo OS and another one for my /home stuff). fdisk says: ''no free sectors avaible". So, what to do? use PartitionMagic from Windows (because is better than gparted??) ? or other soft (what, if any)?

here is my RESULTS.txt ([http://gawryl.pl/okRESULTS.txt](http://gawryl.pl/okRESULTS.txt))

awaiting for suggestions

---

### Post by darkod on 2010-05-28
Q1:
If you don't wanna risk starting the restore partition which is /dev/sda4, you can do this:
Open the file /boot/grub/grub.cfg and copy your win7 entry, all of it like

menuentry win7 {
some lines
}

and then open /etc/grub.d/40_custom and paste it there. You can also delete the current entry for vista in 40_custom because it's wrong anyway.

You put your manual entries in 40_custom.

After that you need to disable 30_os-prober from searching for OS, you do that with

sudo chmod -x /etc/grub.d/30_os-prober

Then to create updated grub.cfg run

sudo update-grub

That should leave only your manual win7 entry.

Q2:
For partitioning question it helps better if you post attachment of Gparted screenshot because it visually shows partition. It's harder to read the sectors and calculate what is where from fdisk results. But anyway, if you want to use the space I guess what you could do is:

You will have to expand /dev/sda2 first, the extended partition holding the logicals inside. Right now the unallocated space in after /dev/sda2 but it's not inside it to create another logical partition in it.
So, first expand /dev/sda2 to include the unallocated space, and after that Gparted will be able to create new logical partition from that space without any problems.

Be careful with Gparted, you just got the computer sorted out, it would be waste to mess up the partitioning. :)

---

### Post by gawryl77 on 2010-05-28
> **darkod said:**
> Q1:
If you don't wanna risk starting the restore partition which is /dev/sda4, you can do this:
Open the file /boot/grub/grub.cfg and copy your win7 entry, all of it like

menuentry win7 {
some lines
}

and then open /etc/grub.d/40_custom and paste it there. You can also delete the current entry for vista in 40_custom because it's wrong anyway.

You put your manual entries in 40_custom.

After that you need to disable 30_os-prober from searching for OS, you do that with

sudo chmod -x /etc/grub.d/30_os-prober

Then to create updated grub.cfg run

sudo update-grub

That should leave only your manual win7 entry.

omg, it's really complicated! i mean - gentoo distro has got ONLY ONE config file (/boot/gentoo.conf) and this is enough - since Ubuntu has got few config files :P anyway - if i understand you correctly, after removing 30_os-prober i want be able to find my next OS - gentoo - which i am gonna install in a not so long future... so every time i am gonna use update-grub i will have to add gentoo manualy? or write it to 40_custom?  swear God  its  crazy :P

> **darkod said:**
> 
Q2:
For partitioning question it helps better if you post attachment of Gparted screenshot because it visually shows partition.
thanks for suggestion with taking a screen shot - when i was doing it i focused on small *key* *icon*  next to /dev/sda2 and realized, that it means *lock partition* - so that was the reson why i coudnt extend this partition. Solution was simple - i run Ubuntu from live-cd (pendrive, no matter) and do resizing process - successfully, of course (this *key icon* wasnt there, because ive start from pen drv). So everything is perfect now ;) thanks man!

---

### Post by darkod on 2010-05-28
Yes, after disabling 30_os-prober ubuntu will not be able to automatically detect any OS installed later.
You can add menuentry for gentoo manually in 40_custom if you know the exact syntax.
Or, you can enable 30_os-prober again just temporarily, let it detect gentoo, and then copy the gentoo entry in 40_custom so you are sure that the syntax is correct.
After that to disable 30_os-prober again.

Yes, it does sound complicated. :) But if you let automatic detection to work, it also detects your restore partition boot files. If you turn it off, you have to make manual entries yourself. :)

---

