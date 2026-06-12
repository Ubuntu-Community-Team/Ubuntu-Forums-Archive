---
title: "downloaded the alternate CD what now?"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by gejufan on 2008-09-02
i have downloaded the alternate CD and have also downloaded Cygwin as the guide adviced in order to check the OS download went ok however i have no idea what to do next. how do i check the OS file?
i have the nero express program on my computer can i burn the OS with it if i chose Date, should i chose Data or some else?

i work with Win XP.

could someone please help me out. i'm totaly new to linux and though i know my way around a computer i am quickly getting confused.

Thanks
Maya

---

### Post by lisati on 2008-09-02
When it comes to burning the disk, assuming it's an "ISO" file you downloaded, you need to burn it as a disk image, not as a data file. The versions of Nero I've used have an option suitable for this.
Then you boot from the CD.

Note: with the "Alternate" disk, you won't normally be able to try things out before installation.....

---

### Post by Jordanwb on 2008-09-02
> **lisati said:**
> you need to burn it as a disk image, not as a data file.

Someone did that at the Fedora forum a while ago.

> **lisati said:**
> Note: with the "Alternate" disk, you won't normally be able to try things out before installation.....

That's correct. I prefer it. It's been suggested to burn the ISO at a low speed: 1X, 2X etc. Personally I don't know why, maybe if someone could explain.

---

### Post by gejufan on 2008-09-03
> **lisati said:**
> When it comes to burning the disk, assuming it's an "ISO" file you downloaded, you need to burn it as a disk image, not as a data file. The versions of Nero I've used have an option suitable for this.
Then you boot from the CD.

Note: with the "Alternate" disk, you won't normally be able to try things out before installation.....

at the momant the Os is as a Winrar file. what should i do?
do i need to open it and extrect the files from it unto a folder on my desktop before i burn or should i burn it as a winrar file?

---

### Post by Partyboi2 on 2008-09-03
> **Jordanwb said:**
>  Personally I don't know why, maybe if someone could explain.
Basically to avoid data corruption.

---

### Post by Partyboi2 on 2008-09-03
> **gejufan said:**
> at the momant the Os is as a Winrar file. what should i do?
do i need to open it and extrect the files from it unto a folder on my desktop before i burn or should i burn it as a winrar file?
Extract the winrar to a folder. What are the contents of the winrar?

---

### Post by confused57 on 2008-09-03
> **gejufan said:**
> at the momant the Os is as a Winrar file. what should i do?
do i need to open it and extrect the files from it unto a folder on my desktop before i burn or should i burn it as a winrar file?
Don't extract the iso file before burning it, Windows just associates the iso file as a winrar filetype.

---

### Post by gejufan on 2008-09-04
ok wait i'm confused one person tells me to extrect everything and the other tells me not to extrect the ISO file.
first of all i have no idea where the ISO file is inside the winrar file.
secondly i'm confused do i need to extrect everything except for the ISO file or all of the files?

---

### Post by Partyboi2 on 2008-09-04
follow what confused57 said

---

### Post by ashmew2 on 2008-09-04
Gejufan ...Ok U have Nero Installed..

Now Open Nero , Insert a blank CD into your CD ROm.
Goto the top tab : "COPY AND BACKUP"
Click Burn Image to Disc..
Look at the image :

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=84026&stc=1&d=1220534571[/IMG]

Once it opens , Just select the ISO file for Xubuntu that you had downloaded. Make sure the speed is 8x !!!

---

### Post by gejufan on 2008-09-05
ok when i open the winrar file on the address list this is the file name i get:
"ubuntu-8.04.1-alternate-i386.iso - ISO9660 archive, unpacked size 726,108,284 bytes"

do does that mean that the entire winrar file is an iso file and that is the file i need to burn?
i'm asking because inside the winrar file there's a folder called isolinux.
do i need to burn the entire file i downloaded or first extract everything and then burn it?

Maya
who is still a little bit confused.

---

### Post by Sef on 2008-09-05
Read [How to write an iso to cd]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm").

If you want, download [isorecorder]("http://isorecorder.alexfeinman.com/isorecorder.htm") to burn the iso to a cd.

---

### Post by Ryadt on 2008-09-05
You don't unpack the iso. Follow this link:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by ashmew2 on 2008-09-05
You need to burn this one : ubuntu-8.04.1-alternate-i386.iso

Just goto Nero >Burn Image to Disc and select "ubuntu-8.04.1-alternate-i386.iso" and burn it at 8x.

---

### Post by gejufan on 2008-09-06
> **ashmew2 said:**
> You need to burn this one : ubuntu-8.04.1-alternate-i386.iso

Just goto Nero >Burn Image to Disc and select "ubuntu-8.04.1-alternate-i386.iso" and burn it at 8x.

ok i finally realized what i need to burn.
i still haven't figured out what i need to do with the program called: Cygwin.
on the "ButningIsoHowto" link it says:
"MD5 Sums
Before burning a CD, it is highly recommended that you verify the md5 sum (hash) of the .iso file. For instructions, please see HowToMD5SUM. For the current list of Official Ubuntu MD5 hashes, see the MD5SUMS file for the release you're using under [http://releases.ubuntu.com](http://releases.ubuntu.com) (and optionally the PGP signatures in the MD5SUMS.gpg file), or see UbuntuHashes. This ensures that the file was not damaged during the download process and is 100% intact." 

in this link: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
on the Windows section it says to downloaded a program called Cygwin in order to check that the file is not corrupt. i downloaded the program but i have no idea how to check the file with it. do i really need to check the file?

---

### Post by Partyboi2 on 2008-09-06
Checking the md5sum is recommend as it checks that you have no errors in the downloaded file.

I have personally found that  [winMD5Sum]("http://www.nullriver.com/index/products/winmd5sum") is easy to use, it even gives instructions on the link you are using.
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Once you have installed it all you need to do is right click on the ubuntu-8.04.1-alternate-i386.iso and send to winMD5Sum and then make sure the number that winMD5Sum gives matches  with the number listed at [[COLOR=Blue]ubuntuhashes[/COLOR]]("https://help.ubuntu.com/community/UbuntuHashes#8.04%20LTS")

---

