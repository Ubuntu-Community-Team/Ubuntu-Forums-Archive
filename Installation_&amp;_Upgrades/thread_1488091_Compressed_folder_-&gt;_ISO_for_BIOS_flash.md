---
title: "Compressed folder -&gt; ISO for BIOS flash???"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2010-05-19
Is there a step-by-step anywhere?

Every link I find seems to refer me to another link, and it sure isn't like burning an install disk...

I got the files extracted, but how to create the bootable CD?

---

### Post by Moozillaaa on 2010-05-22
Any help here?

I'm stuck with with 3 files from board manufacturer site, and I don't know how to make a CD boot disk with them...

---

### Post by lisati on 2010-05-22
If it's an ISO file that you've downloaded, you probably don't need to decompress it. Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Moozillaaa on 2010-05-23
> **lisati said:**
> If it's an ISO file that you've downloaded, you probably don't need to decompress it. Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Thanks.

Well, it's NOT an ISO that I've downloaded; that's what I was trying to say when I said "it sure isn't like burning an install disk...." (which is an ISO)

Anybody know how to make an ISO of these BIOS update files? One is .ROM, another is .exe, and the third is .bat.

---

### Post by cryptotheslow on 2010-05-23
Are you sure you need to make it bootable?

It depends on the board manufacturer of course, but with mine (Asus) all I have to do is burn the bios image file to a basic data cd then boot up with it in the drive. The board recognises the file and automatically flashes it to BIOS. I have a feeling this is just Asus's smart recovery mechanism though.

---

### Post by MartyBuntu on 2010-05-23
What are the specs of the system you're trying to flash?

---

### Post by Moozillaaa on 2010-05-24
> **Moozillaaa said:**
> Thanks.

Well, it's NOT an ISO that I've downloaded; that's what I was trying to say when I said "it sure isn't like burning an install disk...." (which is an ISO)

Anybody know how to make an ISO of these BIOS update files? One is .ROM, another is .exe, and the third is .bat.

Anybody know how to help me compile this ISO?

---

### Post by dino99 on 2010-05-24
> **Moozillaaa said:**
> Anybody know how to help me compile this ISO?

give some details about what you really want/need to do with which hardware manufacturer (i guess there is a howto provided)

---

### Post by Moozillaaa on 2010-05-24
Yes; there is a how-to at the manufacturer web site. It says download the files, and burn them to a bootable disk.

I have the files downloaded>  ME
 
One is .ROM, another is .exe, and the third is .bat.And now I need to create a bootable disk, with those files added.

Anybody?

---

### Post by Moozillaaa on 2010-05-25
Can anybody help here?

---

### Post by oldfred on 2010-05-25
They are talking about a DOS bootable floppy. If you can boot with USB that may be a better choice.

Dos Boot CD
[http://www.hiren.info/pages/bootablecd](http://www.hiren.info/pages/bootablecd)

[http://wiki.fdos.org/Installation/BootDiskCreateUSB](http://wiki.fdos.org/Installation/BootDiskCreateUSB)
[http://en.gentoo-wiki.com/wiki/FreeDOS_Flash_Drive](http://en.gentoo-wiki.com/wiki/FreeDOS_Flash_Drive)
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by Moozillaaa on 2010-05-25
> **oldfred said:**
> They are talking about a DOS bootable floppy. If you can boot with USB that may be a better choice.

Dos Boot CD
[http://www.hiren.info/pages/bootablecd](http://www.hiren.info/pages/bootablecd)

[http://wiki.fdos.org/Installation/BootDiskCreateUSB](http://wiki.fdos.org/Installation/BootDiskCreateUSB)
[http://en.gentoo-wiki.com/wiki/FreeDOS_Flash_Drive](http://en.gentoo-wiki.com/wiki/FreeDOS_Flash_Drive)
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Who's talking about bootable floppy? I'm focusing ONLY on bootable CD creation. My mobo manufacture website lists bootable CD creation details, although rather poor details.

Yes, lots of alternatives, but none practical in my situation.

The first link is good, but editing batch files (to add multiple BIOS update files to the burn image) is beyond my capability. Even then, I'm not knowing which, or if all of the previously mentioned files need to be part of the compilation.

If it were OS files, I wouldn't be afraid to trial and error. BIOS editing however, seems to not be so forgiving of errors...

Thanks anyway - I think the live flash from Windows environment might be the safest way - that utility is referred to on the site also, so cross yer fingers...

---

### Post by MartyBuntu on 2010-05-29
What are you trying to flash?

---

### Post by Moozillaaa on 2010-06-03
>  		What are you trying to flash? 	
[I][B]
:confused:

[/B][/I][
I don't understand your question. Isn't that answered by the title? 'BIOS' ? 

>  (Title)
Re: Compressed folder -> ISO for BIOS flash???

---

### Post by MartyBuntu on 2010-06-03
> **Moozillaaa said:**
> [I][B]
:confused:

[/B][/I][
I don't understand your question. Isn't that answered by the title? 'BIOS' ?

I meant what is the make and model of the piece of hardware you are trying to flash.

---

### Post by Moozillaaa on 2010-06-03
> **MartyBuntu said:**
> I meant what is the make and model of the piece of hardware you are trying to flash.

A**HA**! That makes the question a little easier to understand.

The mobo is FoxConn A7DA-S.

But still I don't understand what difference ***that*** makes? I need to know how to add files to an ISO compilation.

Does anyone know how to add files to an ISO compilation, such that it still burns as an ISO?

---

### Post by cryptotheslow on 2010-06-03
Ahh I see what you mean now.

I had this problem years ago on a now long dead PC. I was using Win2K at  the time and the Nero CD burning software I used at the time had the  option to create a bootable CDRom - but you had to supply it with what was essentially a boot sector in a file that it would then put in the right place on the CD.

I seem to remember having to use some utility along with a DOS boot disk to extract the boot sector information into a file of the right format.

There was no need to create an ISO file though - just dump the data files on as data files then point the burning app at the boot sector image in the options somewhere.

I'll see if I can find any more info on how I did it, it is a long time ago though.

---

### Post by cryptotheslow on 2010-06-03
OK.... I have just run through this process and it worked perfectly for me.

1. Download the MS-DOS 6.22 ISO image from here. [http://www.bootdisks.us/ms-dos/5/ms-dos-bootable-cd-images.html](http://www.bootdisks.us/ms-dos/5/ms-dos-bootable-cd-images.html)

2. Install isomaster using Synaptic.

3. You will then find ISO Master in your Applications > Sound & Video menu.
Use this to open the downloaded ISO file and add your 3 files to it. You then have to use File > Save As to save the revised ISO with a different name (no idea why you can't just save it in place).

Then use your favourite CD burning app to burn your new ISO to CD. Et Voila a bootable DOS CD including the 3 files you need to carry out your BIOS flash.

Good Luck.

---

### Post by DavePlummer on 2010-06-03
Another approach is to put the two BIOS flash files onto a FAT16 or FAT32 formatted USB flash drive. Download a FreeDOS ISO file, and burn it to CD. You can then boot the CD with the USB flash drive inserted. FreeDOS will assign the flash drive a drive letter. You can then change to that drive and run the executable file to flash the BIOS.

---

### Post by Moozillaaa on 2010-06-03
Yeah - there's about 20 approaches. 19 are not practical for what I've got going. I really tried to make that clear every post, just asking if anyone knows how to add files to an ISO compilation.

I think crypto hit the solution here - thanks!

---

