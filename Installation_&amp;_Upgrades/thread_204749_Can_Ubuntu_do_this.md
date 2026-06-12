---
title: "Can Ubuntu do this?"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by hkluk on 2006-06-27
Hello everyone,

I have a problem with windows xp (yes i am a windows user, please through only fruit and no sharp objects).

I recently encountered a fatal error that prevents me from starting windows. I cant even use the windows cd to reformat as it doesnt let me get that far. Not even to the recovery section.

the error is ntfs.sys 0x024

Everyone boasts about how knoppix fixed their problem however I downloaded (or i think i did. most links are 404's and i downloaded what i could). knoppix live cd but it doesnt want to run. However I have an ubuntu live cd which does work and can use the live cd.

My question is can I fix the ntfs.sys file like every1 else can on knoppix? If so, how? (dam i wish i knew linux)

[here is a link to the knoppix way of fixing it.]("http://digg.com/software/Fixing_Windows_with_Knoppix")

I hope you can help.

Kind Regards,
HKL-UK

---

### Post by rbalfour on 2006-06-27
no. the ntfs drivers won't let you read back to the disk. Knoppix has this enabled.

---

### Post by ajmoncrief on 2006-06-27
Im curious why knoppix wouldnt boot.  Did you try redownloading the iso, checking the md5, and burning on the same media that you have your ubuntu disc on (may also try slower speed).  I didnt read through the entire article (rather long), so please indicate exactly what it is that you would like to do? (recover data or wipe it all out or what?)

---

### Post by hkluk on 2006-06-27
I would like to replace the corrupt or damaged ntfs.sys file with an undamaged version. So i can atleast reformat the hard drive.

With regards to the downloading knoppix again. Im finding it hard to get the knoppix live cd distro that every1 is talking about. Links are always down.

---

### Post by mips on 2006-06-27
[http://www.retosphere.de/tipsandtricks/ntfserror.php?menu_id=24&](http://www.retosphere.de/tipsandtricks/ntfserror.php?menu_id=24&)

I assumed you burned the iso to disk and did not simply copy the files across. Burn the image at a low speed say x4-x8, things don't always work out that well at highr speeds.

What country are you in to determine closest mirror. There is also bittorrent

---

### Post by hkluk on 2006-06-27
this is the file ive downloaded

KNOPPIX_V5.0.1CD-2006-06-01-EN.iso

and using nero express, make a data cd. i burned at normal rate. So i'll reburn at a slower rate and try.

note: still burning, but thanks for helping guys.

To rbalfour: hajimemashite, yoroshiku^^

---

### Post by mips on 2006-06-27
Also check the integrity of the ISO by comparing the MD5SUM values.

---

### Post by hkluk on 2006-06-27
not sure i know how to do that, sorry:S

---

### Post by mips on 2006-06-27
There is a md5sum procedure in this guide, [http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

The md5sum for your cd is:
653acc801d4059598bd388de8171a20d *KNOPPIX_V5.0.1CD-2006-06-01-EN.iso

---

### Post by hkluk on 2006-06-27
downloading the CDBurnerXP maybe i didnt burn it correctly.

Also do i burn the .md5 file as well as the .iso?

my .md5 file name is KNOPPIX_V5.0.1CD-2006-06-01-EN.iso.md5

and inside it is

653acc801d4059598bd388de8171a20d *KNOPPIX_V5.0.1CD-2006-06-01-EN.iso

then i use the burner to burn the image

---

### Post by mips on 2006-06-27
[QUOTE=hkluk]downloading the CDBurnerXP maybe i didnt burn it correctly.

Also do i burn the .md5 file as well as the .iso?[/QUOTE]

No, only the KNOPPIX_V5.0.1CD-2006-06-01-EN.iso file.

[QUOTE=hkluk]
my .md5 file name is KNOPPIX_V5.0.1CD-2006-06-01-EN.iso.md5

and inside it is

653acc801d4059598bd388de8171a20d *KNOPPIX_V5.0.1CD-2006-06-01-EN.iso
[/QUOTE]

653acc801d4059598bd388de8171a20d is the md5sum value you have to compare with using the utility listed in the guide. Use the md5sum utility to check the KNOPPIX_V5.0.1CD-2006-06-01-EN.iso file and the value should corrospond to the one above.

---

### Post by hkluk on 2006-06-27
burnt cd,

knoppix started up. Followed that guide

rebooted system. still got error.

Do you think my HD has gone?

(trying again)

it says

"Mounting volume... FAILED
Attempting to correct errors..
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT...OK
Processsing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition ... OK
Going to empty journal ($LogFile)... OK
NTFS Volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully."

note: cant i just copy a working ntfs.sys file?

for example, copy the 1 from my laptop(same os) put it on a disc and copy it into the directory on knoppix?

---

### Post by mips on 2006-06-27
[QUOTE=hkluk]
note: cant i just copy a working ntfs.sys file?
[/QUOTE]

Yes it is possible, i read this somewhere else but you can't do it with knoppix as it cant write to ntfs partitions as far as i know. I recall reading that you have to create a bootable cd that will write to ntfs, look up 'rescue cd' I think it was called.

---

### Post by wpshooter on 2006-06-27
If I am understanding correctly and you want to just get rid of everything on the hard drive and then subsequently reinstall M/S windows and possibly Ubuntu, why don't you just get a drive WIPING utility program and wipe the drive clean and then you should be able to install anything you want.

---

### Post by hkluk on 2006-06-27
Is there anyway to wipe my hard drive clean? so i can put windows back on it?

---

### Post by hkluk on 2006-06-27
[QUOTE=wpshooter]If I am understanding correctly and you want to just get rid of everything on the hard drive and then subsequently reinstall M/S windows and possibly Ubuntu, why don't you just get a drive WIPING utility program and wipe the drive clean and then you should be able to install anything you want.[/QUOTE]

You have 1 in mind?

---

### Post by wpshooter on 2006-06-27
Yes, I was trying to find the name for you.

KILLDISK by L soft Technoligies.

[http://www.pcworld.com/downloads/file_description/0%2Cfid%2C22920%2C00.asp](http://www.pcworld.com/downloads/file_description/0%2Cfid%2C22920%2C00.asp)

---

### Post by hkluk on 2006-06-27
ah cool thanks.

1 small problem is that i dont have a floppy drive on my laptop, only on the broken pc:S

ive been using cds to run the linux live cds. these arent iso's :(

edit: just had an idea. ill try and use ubuntu live cd and download it there and put it on a floppy using the broken pc."

---

### Post by wpshooter on 2006-06-27
I don't understand why folks don't put floppy drives on computers anymore, it can still be very important at times.

Try some of the others down the listing.  Maybe the Ultimate boot disk or some of the others will have a CD based wiping utility, but I have not tried any of the others.

---

### Post by hkluk on 2006-06-27
i have 2 machines, a desktop pc and a laptop.

the desktop is broken and the laptop im using to browse the net to look for a solution.

the desktop has the floppy drive. the laptop doesnt. :(

---

### Post by hkluk on 2006-06-27
ok got the kill disk on a flopy put it in an booted windows
got the cmd line
a:\>


so i enter killdisk -killallhdds

it says bad command or file name.:-k

---

### Post by hkluk on 2006-06-27
found this

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

its wiping as im typing this.

---

### Post by spartan777 on 2006-06-27
if you make a "Data Disc" in nero, that is simply copying the data over. that isn't what you want. in nero its called 'burn image' or something like that. it is probably under the 'backup' category. i'd check, but im in linux now.

---

### Post by jrd on 2006-06-27
You don't want to choose "make a data cd". Choose the "burn image to disk" option insted. This is almost certainly your problem.

---

### Post by hkluk on 2006-06-28
i used DBAN to wipe all of it.

took about 8 hours. but its done now. I have installed windows xp and now installing my drivers.

thanks guys for all the help:D

i really appreciate it. I think my problem was just stubborn like me. Otherwise all the easier solutions would have fixed it.

cheers again:D

---

