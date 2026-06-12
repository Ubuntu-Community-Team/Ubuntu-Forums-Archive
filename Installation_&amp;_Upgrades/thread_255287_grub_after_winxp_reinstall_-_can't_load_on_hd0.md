---
title: "grub after winxp reinstall - can't load on hd0"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by pulper on 2006-09-11
i did a reinstall of windows xp on a dual boot system with ubuntu dapper.  i knew that would screw up my mbr so i did some reading beforehand and figured out how to fix the mbr after the reinstall.

i couldn't get it to work.  i tried everything with a live ubuntu cd, and each time i even tried to do a manual grub reinstall, it couldn't find my hard drives.  

therefore, i installed bootmagic on winxp (after creating a fat32 partition which it requires).  it didn't work when i restarted (was close to working right the first time but not after - couldn't find OS).  so i went into winxp recovery mode and did fixmbr.  didn't work.  "cannot find ntldr".  i copied those files (ntdetect.com as well) over to the windows directory and then it gave me "invalid or corrupt boot.ini".  not having a the capacity to create a new boot.ini, i tried ubuntu live cd again.

i finally got grub to see my hard drives.  the instructions that i had didn't say "sudo" grub.  so i:
find /boot/grub/stage1
#returned (hd2,4)
root (hd2,4)
setup (hd0)

then i got about 4 messages saying everything succeeded.  I tried rebooting but again it said "invalid or corrupt boot.ini".  it never gave me the grub screen (delay is set to 10 seconds).

so i went into grub.lst.  i commented out the winxp part, redid the setup (hd0) part above, and restarted.  again, same message (boot.ini).

If grub is loaded to the MBR and windows isn't listed, why would this happen?  At this point i'm stuck but don't want to have to do a complete reinstall of both or either operating systems.

any advice?

Thanks!

Paul

---

### Post by whizbaby on 2006-09-11
Do you have *three* hard drives (hd2 in grub suggests that) ? If not
have you changed the system root before the grub installing stuff (chroot)?
If you didn't do it you would have edited the grub of the live system...

to change system root before doing a grub install boot live cd and open terminal (let's say ubuntuHD is mounted on /media/ubuHD in the live system):

[B]sudo mount --bind /dev /media/ubuHD/dev
sudo mount --bind /proc /media/ubuHD/proc
sudo chroot /media/ubuHD[/B]

now redo your grub install.

---

### Post by pulper on 2006-09-11
whizbaby, thanks for the reply!

i do have three hard drives and ubuntu is on the third one (hd2).

your indication about me changing grub on the "live" system maybe correct.  however, i thought that when i type at the grub prompt:
root (hd2,4)
and then:
setup (hd0)
that the grub installed on (hd2,4), which should be the installed version, will be installed on hd0, which should be the MBR.  is this not correct?  if not, then i have a second question:

after mounting as you suggest, when i type:
sudo chroot /media/ubuHD 
utilizing my hd as ubuhd, when i then type:
"sudo grub", that grub will be the grub of the ubuntu installed version?

Thanks,

Paul

---

### Post by whizbaby on 2006-09-11
> **pulper said:**
> grub will be the grub of the ubuntu installed version?

Yes, then it will be (grub needs information from /proc and /dev, so we pass the proper devices before chroot).

---

### Post by pulper on 2006-09-11
Unfortunately, it didn't seem to work.  Here is what i did after booting up with the ubuntu live CD (hdd5 is my ubuntu installation):

ubuntu@ubuntu:/dev$ sudo mkdir /mnt/temp
ubuntu@ubuntu:/dev$ sudo mount /dev/hdd5 /mnt/temp
ubuntu@ubuntu:/dev$ sudo mount --bind /dev /mnt/temp/dev
ubuntu@ubuntu:/dev$ sudo mount --bind /proc /mnt/temp/proc
ubuntu@ubuntu:/dev$ sudo chroot /mnt/temp
root@ubuntu:/# sudo grub
sudo: unable to lookup ubuntu via gethostbyname()
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory
Probing devices to guess BIOS drives. This may take a long time.

here is what I did @ grub prompt:
find /boot/grub/stage1
# returns (hd2,4)
root (hd2,4)
setup (hd0)

Here is the results from the above:
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p 
(hd2,4)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.


Everything above indicates to me that it worked.  However, when I restart, i get the "boot.ini is invalid" prompt.  afterwards it tries to boot windows from c:\windows and tells me another file is missing.

If i'm not mistaken, after having taken windows out of grub.lst by commenting the lines, a restart should go to a grub screen and only have the ubuntu there.  

i must be doing something wrong but cannot see it.  If anyone has a suggestion, i would love to hear it.  Thanks!

Paul

---

### Post by whizbaby on 2006-09-11
Something went a little wrong. Try the same with adding this line
**mount -t sysfs /sys /media/ubuHD/sys**
Now sudo should stop throwing error messages. If you want to reinstall XP (boot.ini broken) better do this before (otherwise you will do this two times...)

---

### Post by pulper on 2006-09-12
so i decided simply to reinstall windows.  windows xp install went fine.  after install, i decided to go into ubuntu live cd and do the manual grub install again (just like above).

now, when i restart, i get "windows could not start because the following file is missing or corrupt: <Windows Root>\system32\hal.dll.  Please re-install a copy of the above file".

what's interesting is that when i restart and go into the winxp recovery mode, it doesn't identify the windows installation and just gives me a prompt.  when i type in "dir", i get a list of files that are on a different hard drive than the windows installation.  in other words, manaully installing grub as above causes windows to try to boot from a different drive.  this is beyond my level here so i need some more help.

any suggestions?  Thanks,

Paul

---

### Post by pulper on 2006-09-12
i tried using the "super grub disk" utility as i only have a cd rom drive. my results were interesting.

when i went into specific booting, it stated that there is no (hd2,4) partition. so i entered edit mode and changed it a number of times to (hd2,5), (hd2,3), etc. nothing worked, so i did "geometry (hd0)". it listed a number of partitions including an ext extension at (hd0,4). i changed (hd2,4) to (hd0,4), and i was able to get into my installed ubuntu. so, it would seem that linux (or maybe grub???) is installed on (hd0,4).

within ubuntu, i typed "sudo grub" at the terminal, did "find /boot/grub/stage1" and it still indicates (hd2,4).

am i doing something wrong here? doesn't the /boot/grub/stage1 file reside in the partition for grub? what do i do to get grub working on my system again?

any suggestions would be appreciated. Thanks,

Paul

---

### Post by pulper on 2006-09-13
thanks for your help whizbaby.  I ended up using the grub super disk, and after playing around with it, got it to work.  i found the "special booting" to be helpful, especially when you can alter the hd where the mbr looks for the grub file.

paul

---

