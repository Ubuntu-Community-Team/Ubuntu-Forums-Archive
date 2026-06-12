---
title: "Install Ubuntu [Errno 5] input/output error"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by weblizzer on 2008-03-13
Hi, just downloaded a Desktop 64Bit UBUNTU Installer, when i install i got this error

[IMG]http://img174.imageshack.us/img174/5166/errorkf6.png[/IMG]

My specs:

1 40gb Barracuda
AMD64 X2 3800+ Processor
2GB 667mHz Memory

Actually i about to dual boot for my XP and this Ubuntu

my 25gb is used for XP 

and the 15 is for Ubuntu

I'm very much newbie to this, and hoping to install this successfully,

I hope you can help me. thanks!!!!

---

### Post by scragar on 2008-03-13
I can only say read what it say's really, it's proberly down to a bad/dirty disk, but you can quickly check that using the CD check option from the liveCDs boot menu(can't remember exact text, but it say's something about checking disk for errors).

---

### Post by weblizzer on 2008-03-13
Ah i see. okay i will try that, but do you think that is the only problem?... well anyway hopefully that will solves my error

---

### Post by scragar on 2008-03-13
it's just saying that it was unable to copy the files to the hard disk, so the only explination I can see is a bad disk(either dirty, burned with errors or scratched).

15GB is more than enough space, and ubuntu gives more specific warnings regarding that, your ram is more than enough to run the liveCD...

---

### Post by weblizzer on 2008-03-13
thanks for your reply dude! i was also thinking as it says in the error maybe because of the LIVE CD i burned after i download. as i burned it by 32x using Nero.. Do you think this might be possible?

---

### Post by scragar on 2008-03-14
firslt thing to do is use the liveCDs option to check for errors, and see if it reports any, if it does then before wasting a second CD check you iso file for errors: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) <-- guide to checking for errors on iso(they match = no errors).

---

### Post by weblizzer on 2008-03-14
Hi dude, thank you for your tips, well i follow the instructions there and after i download this version in ubuntu:

ubuntu-7.10-desktop-amd64.iso 

I got md5 hash: edace4cb97f43c5a37614974a03cecd9

but on the ubuntu hash list here is:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

61c87943a92bc7bf519da4e2555d6e86 - ubuntu-7.10-desktop-amd64.iso


So does it mean that i need to download once again? or what shall i do to the iso image?

---

### Post by alberto ferreira on 2008-03-15
Hi, I'm having the same problem ( input/output error) during install, the laptop is brand new and works fine with vista. I have checked the live cd disk for errors and none was found, then i booted the disk for install and this error appeared. Any suggestions?

Thanks

---

### Post by weblizzer on 2008-03-15
Just checking the md5sum on the first i download. but seems that the checksum are not the same so i download it back again... and it match now... i burn it to nero at 8x speed but i didn't tried it yet. i will try to install it again by tomorrow. hope it will.

---

### Post by scragar on 2008-03-15
that's why it's recomended to download from a torrent, since torrents run the MD5 sum over each chunk to check it and redownload only small parts in the event of an error.

if the MD5 sum's match then it should be ok once it's burnt.



@ alberto ferreira - same error? Where do you get the error(during install or boot)? Are you sure that the disk is the right disk for your PC(eg: 64bit edition for a 32 bit PC).

---

### Post by Porta-Chaves on 2008-04-08
I get the same error, did the cd check and no errors were found. Also my HDD isn't damaged since i run WinXp perfectly on it.

Any solutions for this problem?

ty

---

### Post by weblizzer on 2008-04-08
hi dude,, just try to check your md5checksum if they match here, it might the file has been corrupted... i've encountered it already, but when i download it again an install to my pc no problem occurs, so just kindly check it.

---

### Post by Porta-Chaves on 2008-04-08
The CD I use is an official CD which I ordered through the internet.

---

### Post by weblizzer on 2008-04-08
ah i see, okay,

first try to run the live CD since you can work on it. 

second, if you follow the 2 types of format that you need to create in your hard disk... can't remember bu t there should be two... 

lastly just try to look the compatibily of your pc if you are running the latest one they try the 64bit version... 

anyway i'm just trying to figure out the possible outcomes for that, but i'm not a very much knowledgeable about that so i'm just trying to help just based on what i encountered before.
;) :popcorn::popcorn::popcorn::popcorn:

---

### Post by Porta-Chaves on 2008-04-08
the file types you're talking about is (if i'm not mistaken) ext3 and swap. My PC is x86 and the CD version is x86 as well (not the 64bit but the other one).

---

### Post by weblizzer on 2008-04-09
okay.. well hope there someone can help you in here... :)

---

### Post by Porta-Chaves on 2008-04-10
does anyone know how to fix this?

---

### Post by Psyphre on 2008-04-17
Your not the only one im afraid.

Heres a thread on it:
[http://ubuntuforums.org/showthread.php?t=600126](http://ubuntuforums.org/showthread.php?t=600126)

---

