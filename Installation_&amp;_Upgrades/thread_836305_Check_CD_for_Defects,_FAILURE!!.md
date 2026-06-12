---
title: "Check CD for Defects, FAILURE!!"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by mtantawy on 2008-06-21
hi, i downloaded the ubuntu 8.04 DVD and burnt it on a BENQ DVD and when i checked it for defects it kept giving me different errors some were input/output error, and some related to logical.... couldn't read it because it went fast

i couldn't also wait till the check ends because it was checking every single file and giving error with every single file

i burnt it using a SONY DVD device at 4x speed and it was the only working program, so everything should be okay

i tried the cd check on 3 computers"2 laptops+1 PC(using the SONY DVD Device)",,all gave those errors..

so now what should i do??
also, how can i check for the md5 check sum or whatever it is called??
what program is the best??also, please provide steps , and is it normal that such programs go NOT RESPONDING while checking and take long time??"may be because it is a DVD"

and what should i check, the iso??the burnt cd??or what!!!

one last thing, i had Ubuntu CD burnt and gave errors too!!HINT::burnt using another device

mmmmm, dont think i have more questions!!

oh, ofcourse am talking about Ubuntu Hardy Heron 8.04 in both the DVD&CD

so, Thanks in advance

Mahmoud Tantawy

---

### Post by avtolle on 2008-06-21
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) will help you concerning your md5sum question.

Wondering if you have a hardware problem with your burner? First, however, does your device have the latest and greatest firmware upgrades?

EDIT: Not trying to be stupid here, but you did burn it as an iso image, and not as, e.g., a data file?

---

### Post by mtantawy on 2008-06-21
> **avtolle said:**
> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) will help you concerning your md5sum question.

Wondering if you have a hardware problem with your burner? First, however, does your device have the latest and greatest firmware upgrades?

EDIT: Not trying to be stupid here, but you did burn it as an iso image, and not as, e.g., a data file?
ofcourse i burnt it as ISO , by the way, i used power iso, is it good??i also have magic iso&nero, which is better??anyother suggestions!!!

the SONY DVD Device is okay, infact i used it alot and it gives no errors with other movies DVDs or even windows CDs & DVDs or data CDs & DVDs so it is okay...

the page &the program provided on it check only the ISO file, and it is correct, i want a program to check the DVD??and if available compare it with the ISO!!

Mahmoud Tantawy

---

### Post by Pumalite on 2008-06-21
Try ImgBurn (by the legendary maker of DVD Decrypter):
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install
Go to Mode>ISO>Burn. Select speed as 4x.
Clean the lens in your burner, just in case.

---

### Post by Dale61 on 2008-06-23
It's also been suggested that you burn at SLOWEST speed possible.

---

### Post by shlonsky on 2008-08-02
Hello :)

I also have a very weird CD burning problem:

I downloaded Ubuntu Hardy Heron for the AMD64 Turion processor.

I checked the iso checksum, the iso is definitely NOT corrupted :S

I tried to burn the iso with Poweriso on win xp: no luck (5 CDs trashed)

I then tried to burn it on Mac OS X with:
> The Disk Utility
> Toaster

Both caused me some trouble: the CD files checksum are all correct EXCEPT:

> filesystem.squashfs
> initrd.gz
> vmlinuz

Which all give, when I checksum them from the CD:

> Input / output error

Now, I have tried the slowest possible burning (1x speed on Toaster, which averaged 7x speed during the actual burning)

I have used Poweriso on an Acer Aspire 5050, and Disk Utility and Toaster on a Macbook Pro running Mac OS X Leopard.

If I'm not sure of the former's performances, the MBP should be pretty much guaranteed... right? Never had burning problems with it...

Oh, am using Samsung CD-R 52x CDs.

Can anyone guide my steps? Besides preparing a USB with Ubuntu installer on it, how can I guarantee a clean CD burn from my Mac to use on the Acer?

Thanks a bunch,
.w.

---

### Post by Pumalite on 2008-08-02
Clean the lens in your burner (disk or compressed air)and check CD integrity before install. Are you doing md5sum on the iso before burn?

---

### Post by shlonsky on 2008-08-03
Well, my MBP is relatively new (a couple of months old), I doubt the superdrive's lens is the problem, furthermore, the same problem hapened on 2 different computers (the Acer is a pretty old 2nd hand machine I bought to use as a server)...

As for the integrity check, I do it on the downloaded ISO before I burn it, and it checks out to be correct.

Then I check each file in the burnt CD against the md5 listed for every file in a txt file on the CD... All come out correct EXCEPT 3 files in folder 'Casper': filesystem.squashfs, initrd.gz and vmlinuz; 

when I check those files in the terminal, I get the "Input / output error" error as a result...

Downloading Debian and Mandriva now to test them...

---

### Post by shlonsky on 2008-08-03
Mandriva boot CD hanged for some time; Debian etch is currently installing, no problem until now.

Might it be a bad iso build? at least for the amd64 version?

---

### Post by wpshooter on 2008-08-03
[QUOTE=
Might it be a bad iso build? at least for the amd64 version?[/QUOTE]

Yes, might want to try downloading from a different source/server !!!

---

### Post by shlonsky on 2008-08-03
> **wpshooter said:**
> Yes, might want to try downloading from a different source/server !!!

I don't think that would do... The iso itself is totally healthy, with matching md5, and the 'incriminated directories' (those that cause the i/o error when on the CD) behave more than correctly, returning the right checksum, allowing copies of themselves etc...

But when it came to transfer this completely sane package to a CD-R, those folders were tranferred in an (incomplete?) way on the CD.

With the same hardware, I was able to burn the Debian cdinst (160MB), and get the rest off the internet...

Maybe Ubuntu's "690" MB is too edgy for 700MB mediums??

---

### Post by TenPlus1 on 2008-08-03
I tend to downloda my .iso files using Deluge, then afterwards FORE a re-check to make sure the file is 100% before burning it at low-speed in Brasero...

---

