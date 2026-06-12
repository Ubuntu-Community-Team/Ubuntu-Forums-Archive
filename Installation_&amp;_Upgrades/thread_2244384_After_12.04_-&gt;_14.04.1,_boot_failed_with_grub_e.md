---
title: "After 12.04 -&gt; 14.04.1, boot failed with grub error"
date: 2014-09-16
forum: Installation &amp; Upgrades
---

### Post by neoxeon2 on 2014-09-16
Hello,

I executed do-release-upgrade to update my laptop's ubuntu 12.04 to 14.04.1 yesterday.
Upgrade seems smooth, however, after I reboot my laptop, it suddently enters grub rescue mode with message:
```
error: file not found
```

I tried googling this issue. Serveral threads I found suggest live-cd & boot-repair to fix this problem. Then I boot with 
live-cd 14.04.1, followed the procedure on ubuntu wiki to install boot-repair, ran boot-repair. Some error happend, and
boot-repair gave me url with log :
[http://paste.ubuntu.com/8352816/](http://paste.ubuntu.com/8352816/)
At the end of log, it says :
```
Unrecognized option `-y'
```

I guest the error maybe come from grub 2.0.2 instead of grub 1.99. So I tried to create a fake update-grub to ignore all
parameter for a 'workaround' :
```
#!/bin/sh
update-grub.original
#"update-grub.original" is the renamed update-grub.
```

Ran boot-repair again, "Unrecognized option" error disappears, but some error remain :
[http://paste.ubuntu.com/8352925/](http://paste.ubuntu.com/8352925/)
I can't found obvious clue this time.....

Also tried to use grub rescue command to boot, but failed when
```
insmod normal
```
with undefined symbol grub_divmod64.

Is there anything I can do to fix this problem? Thanks in advance for any suggestion.

**My laptop** :
Sony S15V
Insyde H2O bios (boot mode: **UEFI**)

---

### Post by neoxeon2 on 2014-09-18
Hello,

Googling, testing, and rebooting for 2 days, I have found a 'fix' for my problem.

1. In order to avoid the "file not found" error, I copied all files under /boot/grub/x86_64-efi to /boot/grub
```
cd MOUNTED_PATH_TO_ROOT/boot/grub
for f in x86_64-efi/*; do ln "$f" `basename $f`; done 
```
"file not found" fixed, but "undefined symbol grub_divmod64" remains.

2. Copy all .efi files in ubuntu directory of EFI partition to Microsoft/Boot
```
cd MOUNTED_PATH_TO_EFI/EFI/ubuntu
cp *.efi ../Microsoft/Boot
cd ../Microsoft/Boot
cp grubx64.efi bootmgfw.efi
```
Finally my laptop can boot into ubuntu.

There are still so many questions that I don't fully figure out:
* I am not sure if step 1 is really needed after step 2 is done.
* "Windows 7" does not come back yet.
* ... ... questions that I don't even remember ... ...
I feel exhausted and have no passion to find out answers recently.

At last but not least, thanks the key-word "sony buggy uefi", and thanks oldfred's info in
[http://ubuntuforums.org/archive/index.php/t-2200818.html](http://ubuntuforums.org/archive/index.php/t-2200818.html)

[-o

---

