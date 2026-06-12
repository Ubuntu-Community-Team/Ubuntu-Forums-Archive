---
title: "Multi boot with multiple windows operating systems"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by trademark91 on 2010-05-30
I recently re worked my OS configuration, and installed Windows 7 and Ubuntu 10.04. (x64 for both)

i really liked that setup, however, i could not play some of my games on either windows 7 or ubuntu, so i elected to install a third OS, windows xp. (x86)

i loaded up gparted, shaved about 10gb off of my shared partition, and made a new part for XP.
after installing xp, i had to reinstall grub, which i expected, however i had an extra effect i was not anticipating: whenever i chose windows 7, it would boot to XP.

after a little work, i got Windows 7 to boot when i chose it, however, now when i choose XP,  it boots windows 7 as well.

this has left me very frustrated and confused, as i am used to fixing most problems of this nature myself (ive been using linux since debian etch, and only just switched to ubuntu as of 10.04)

ive heard that some people get success by using windows 7 to load the windows bootloader, which lets them choose between 7 and xp, but when i try to get that to work, 7 says "no other OS detected"
Plus id much rather just have them all start from grub, because that extra bootloader feels kind of sloppy.

has anyone had any success in this field, and if so, how did you do it?

---

### Post by bcbc on 2010-05-30
[www.multibooters.co.uk/multiboot.html](www.multibooters.co.uk/multiboot.html)

This site has some good info. Windows works when you install a later version after the earlier.

---

### Post by darkod on 2010-05-30
When installing two versions windows is designed to combine the boot files. It should still work for you though, but that means you will have only one windows entry in grub menu, and if you select it then you get the windows bootloader menu to select from the two versions.

Without knowing your exact partition setup, I can only speculate, but in general the process would be:

1. Windows depends on the boot flag, and it puts its boot files where ever the boot flag is.

2. Install windows ver1 to the partition you want it.

3. Use Gparted and create the other partition for ver2. Remove the boot flag from first partition, put it on second partition. Install windows ver2 which will put its boot files separately.

This way grub2 can detect both sets of boot files and allows booting both versions of windows from the grub menu.

Because you already have the systems installed, what you could try:

1. Set the boot flag on winXP partition. Use the install cd and the boot files restore command (/fixboot) to create new set of boot files.

2. Move the boot flag to win7 partition. Use the manual commands for /fixboot also.

3. Because you are not also running /fixmbr in the above procedures, grub2 should remain on the MBR so you wouldn't need to reinstall it. Boot ubuntu and do the update-grub to detect both windows.

More detailed instructions about the bootloaders restore:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

NOTE: The above can work only if both your windows partition are primary. The boot files have to be on primary partition so if one part is logical, you have no choice but to keep the boot files mixed on the other windows part.

---

### Post by trademark91 on 2010-05-31
neither of those solutions worked...
darkod, since you mentioned it, here is my partition configuration
[IMG]http://img20.imageshack.us/img20/9471/screenshottou.png[/IMG]

and i have ntldr in my xp partition,

[img]http://img412.imageshack.us/img412/6007/screenshot1gy.png[/img]

and here is my 7 partition

[img]http://img706.imageshack.us/img706/9533/screenshot2jd.png[/img]


for some reason, whether i tell grub to boot to /dev/sda1 or /dev/sda3, it always opens up the "starting windows" screen and then proceeds to boot into windows 7.

anyone??

ive tried switching the boot flag, installing when 7 is hidden, darkods idea, nothing...

when i install xp, regardless of whether 7 is hidden or not, it boots xp straight. then, when i clear the MBR for grub, 7 takes over for any ntfs partition...

---

### Post by trademark91 on 2010-05-31
ok, i got it. the problem was with my grub configuration.

i have custom grub menu entries
so in my 40_custom
i had the following for xp:
insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9c14ecf814ecd5f4
    chainloader +1

when i needed this:
insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 9c14ecf814ecd5f4
    drivemap -s (hd0) ${root}
    chainloader +1


re-enabling os-prober and checking my grub.cfg cleared that up. thanks for your help everyone :P

---

### Post by drdos2006 on 2010-06-01
I have also found that when dual-booting XP and Ubuntu, XP does not take control of all the HDDS, but Windows 7 does. 
My installation procedure for multi-booting is now: XP first, Windows 7 second, and Ubuntu third. Booting into Windows would give me the option of XP or Windows 7, booting into Ubuntu gives me the option of Ubuntu or Windows. ( I got rid of XP so that is no longer an issue )

regards

---

### Post by darkod on 2010-06-01
Glad you got things sorted.
Just to notice that your 7 partition also has /boot.ini /ntldr and ntdetect.com. Those boot files are used in XP but not in vista/7.
So I guess somehow you still had the boot files combined which added to the confusion. If it works now, fine, but I just wanted to point out. If the boot files are totally split and independent, you should have like:

for XP: /boot.ini, /ntldr and ntdetect.com

for vista/7: /bootmgr, /boot/BCD and windows/system32/winload.exe

---

### Post by trademark91 on 2010-06-01
thanks for noticing that darko, i guess when i tried to fixboot with xp i had the 7 partition marked as boot still. got rid of those, didnt make it run any better or worse, but saved me a little space on the 'ol hdd :)

---

