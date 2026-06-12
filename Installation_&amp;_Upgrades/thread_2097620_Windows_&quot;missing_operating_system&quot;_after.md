---
title: "Windows &quot;missing operating system&quot; after Ubuntu 12.10 instal?"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by jp1016 on 2012-12-23
Hi, I used rEFIt to install Ubuntu 12.10 on my macbook pro, which also had windows 7 on it. Now when I try to use the windows partition, it displays the message "missing operating system" on a black screen. If there's any other information needed I'll post more. 

Any help is appreciated! Thanks!

---

### Post by fdrake on 2012-12-23
> **jp1016 said:**
> Hi, I used rEFIt to install Ubuntu 12.10 on my macbook pro, which also had windows 7 on it. Now when I try to use the windows partition, it displays the message "missing operating system" on a black screen. If there's any other information needed I'll post more. 

Any help is appreciated! Thanks!
 you have to fix the win partition with a windows cd. select the part that says repair windows or something like that..

---

### Post by jp1016 on 2012-12-23
Now if I have lost that cd, is there anything I can do :confused:

---

### Post by Bucky Ball on 2012-12-23
*Thread moved to** Installation & Upgrades***


Try Boot Repair ...

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I don't know what rEFIT is but that may negate Boot Repair working.

Are you positive you haven't wiped Windows in the process of installing? If you can boot from the LiveCD, open Gparted and post a screen shot of your hard drive partitioning.

You can also open a terminal and post the output of:
```

sudo blkid
```

---

### Post by jp1016 on 2012-12-23
I can see all my windows files from my mac osx finder. Do I use that terminal code in OSX or Ubuntu?

---

### Post by jp1016 on 2012-12-23
I also created a recovery disk using a different laptop? Will it work? and how do I boot into the cd on my mac?

---

### Post by Bucky Ball on 2012-12-23
Have you tried Boot Repair??? Create a bootable disk or run it from the Ubuntu liveCD (it will install to that from Software Centre).

You run that code in a terminal in Ubuntu. Who knows, could work in the terminal in Mac, too ...

---

### Post by fdrake on 2012-12-23
> **jp1016 said:**
> I also created a recovery disk using a different laptop? Will it work? 

NO recover cd are configurated only for that spec hardware

> and how do I boot into the cd on my mac?

in order to boot from cd/usb you have to select the boot device from the bios. I do not have a mac but if you google around i am sure you'll find a way.

---

### Post by jp1016 on 2012-12-24
Well I tried Boot Repair, and it uninstalled grub, and I reinstalled it onto the same linux partition. Was I supposed to continue without installing it again? What should I do now.

---

### Post by Bucky Ball on 2012-12-24
Boot Repair shouldn't uninstall grub unless you ask it. Sure it didn't just install it somewhere else? In Linux lingo, in a straightforward setup, it should be on the beginning of sda, first drive.

Boot Repair should rewrite your grub with any OSs it detects then write it to the correct place ...

---

### Post by jp1016 on 2012-12-24
Well I clicked the recommended step that said it would fix most problems, and well the message is stil being displayed. What should I do now?

---

### Post by jp1016 on 2012-12-24
Please help :o!

---

### Post by Bucky Ball on 2012-12-24
If anyone could help I'm sure they would. Realise that it is now xmas day in many parts of the world and people will be in and out or absent for the next 24/48 hours.

I understand your frustration ...

---

### Post by jp1016 on 2012-12-25
> **Bucky Ball said:**
> If anyone could help I'm sure they would. Realise that it is now xmas day in many parts of the world and people will be in and out or absent for the next 24/48 hours.

I understand your frustration ...

Did sorta forget about that :(

Well I've now tried booting from a recovery disk made on a different computer, which as previously mentioned, did not work. Also retried the boot repair with the same results. I uninstalled rEFIt.

---

### Post by oldfred on 2012-12-25
I do not know Macs, but there are some threads with good & not so good results.

[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

See posts by trogdor1138 (you may want to search for others)
[http://ubuntuforums.org/showpost.php?p=12390285&postcount=6](http://ubuntuforums.org/showpost.php?p=12390285&postcount=6)

---

### Post by YannBuntu on 2012-12-26
Hello
> **jp1016 said:**
> Well I tried Boot Repair, and it uninstalled grub, and I reinstalled it onto the same linux partition. Was I supposed to continue without installing it again? What should I do now.

Please run the Recommended Repair then indicate the URL that will appear.

---

### Post by jp1016 on 2013-01-01
The link given was:

[http://paste2.org/p/2677514](http://paste2.org/p/2677514)

---

### Post by YannBuntu on 2013-01-01
> **jp1016 said:**
> The link given was:

[http://paste2.org/p/2677514](http://paste2.org/p/2677514)

GRUB recognized your ext4 partition as ext2, which is strange. I reported the bug here: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1095142](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1095142)

However, GRUB seems to be in your PBR, so rEFIt (or rEFInd) should be able to chainload to it.

Please install rEFInd, and tell us what you observe.

---

### Post by jp1016 on 2013-01-03
After reinstalling rEFIt what should I try?

---

### Post by YannBuntu on 2013-01-03
After reinstalling refit, just reboot and check if you can access the GRUB menu.
If you can't, try with Refind instead of Refit.

---

### Post by jp1016 on 2013-01-03
I tried with both rEFIt and rEFInd, and I cannot access the grub loader menu. It says something about it being missing?

---

### Post by YannBuntu on 2013-01-03
ok.
Please run Boot-Repair --> Advanced options --> "GRUB location" tab --> select "Place GRUB into: sda" --> Apply.
Tell me the new URL that will appear.
Then reboot and tell what you observe.

---

### Post by jp1016 on 2013-01-03
I tried that an I got the message:

"GPT detected. Please create a BIOS-boot partition (>1mb unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted."

---

### Post by YannBuntu on 2013-01-04
via Gparted, reduce your sda4 partition in order to make 1MB free space between sda3 and sda4.
Then in this space, create a 1MB unformatted partition with bios_grub flag.
Then run Boot-Repair --> Place GRUB into sda.

---

### Post by jp1016 on 2013-01-05
Actually, I tried booting into Ubuntu via rEFInd and could find the GRUB menu, I just couldn't boot into my mac osx partition or windows partition from that menu...

---

### Post by YannBuntu on 2013-01-05
Can you boot MacOS and WIndows from Refind?

---

### Post by jp1016 on 2013-01-05
Mac os yes, windows no. I can't boot into windows from any bootloader, they all say its missing the os.

---

### Post by YannBuntu on 2013-01-06
Where you able to boot Windows before installing Ubuntu? if yes, how?

---

### Post by jp1016 on 2013-01-06
I did by holding down option, using the bootcamp bootloader, and choosing windows.

---

### Post by YannBuntu on 2013-01-06
Then you should reinstall Bootcamp and check if you can still access WIndows from it.

---

### Post by jp1016 on 2013-01-06
Do you mean reinstall windows? I tried using a repair disk and nothing happened..

---

### Post by oldfred on 2013-01-07
Windows needs to be in the first four partitions, so it is MBR in hybrid partition configurations used by Macs to boot Windows.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by jp1016 on 2013-01-07
> **oldfred said:**
> Windows needs to be in the first four partitions, so it is MBR in hybrid partition configurations used by Macs to boot Windows.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

I'm a bit confused about this, but in specific what makes them "flaky and dangerous"? Will creating a hybrid MBR allow me to boot all three os?

---

### Post by oldfred on 2013-01-07
I think the issue is each does not know about the other. 

Most partition tools then do not know that you have to keep them in sync, so it is up to the user to know what he is doing and not use anything that can get the two out of sync.

---

### Post by jp1016 on 2013-01-09
So in the case of the user not knowing what he is doing (me), how do I fix it...:(

---

### Post by jp1016 on 2013-01-11
bump?

---

### Post by oldfred on 2013-01-11
I do not know Macs.

But I thought the whole idea of hybrid was so you could install Windows in MBR mode as that seems to be the only way it works with Macs. And Ubuntu will boot from a gpt drive so it does not have to be MBR or can be beyond the first 4 partitions.. And hybrid only syncs the first 4 partitions so Windows has to be in sda1 thru sda4 or the primary in MBR.

You need to reverse the locations on the drive of Windows & Ubuntu. How did you get Windows out of the primary partitions? I do not know if somehow you renumbered them, if so reverse that. Otherwise it looks like a lot of reinstall?

---

### Post by jp1016 on 2013-01-11
I typed the command diskutil list, and here's what I got:

/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *250.1 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            192.4 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
   4:       Microsoft Basic Data                         10.0 GB    disk0s4
   5:                 Linux Swap                         1.1 GB     disk0s5
   6:       Microsoft Basic Data BOOTCAMP                45.7 GB    disk0s6
/dev/disk2
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     Apple_partition_scheme                        *17.3 MB    disk2
   1:        Apple_partition_map                         32.3 KB    disk2s1
   2:                  Apple_HFS Flash Player            17.3 MB    disk2s2

Did I mess something up?

---

### Post by oldfred on 2013-01-11
Afraid I do not know more than what I have posted. And I do not know your Mac tools on how to fix anything. I only read on hybrid configurations as I was trying to understand gpt partitions from the rodbooks site.

---

### Post by jp1016 on 2013-01-12
Has no one else had this happen to them? I'm a bit confused as to why this happened in the first place.

---

### Post by oldfred on 2013-01-12
I probably should have moved you to the Apple sub-forum initially. May be best just to end this thread and start a new one there. Then users familiar with Macs should respond. 

You can also search forum or review posts in Apple sub-forum.

       Just append site:ubuntuforums.org to your search term
OR:
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by jp1016 on 2013-01-14
Well I made a new thread there, but its been two days and no responses :o

---

### Post by Bucky Ball on 2013-01-15
Bump the thread. All good after twenty four hours and quite acceptable. Simply type:

bump

... which will get it back to the top of the list. ;)

---

