---
title: "(U)EFI issues again, again"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by mirmos192 on 2014-12-08
Everything that follows is 64 bit...
I successfully replaced Windows 8.xx on a new Toshiba with Ubuntu 14.04 LTS by installing from live USB stick created on that machine. In creating the original live USB stick the software seemed to recognise that the live version was to be run on an EFI machine, so problems in installing from the stick to the machine itself were relatively minor. 
Subsequently, I was able to fully install an efi compatible Ubuntu 14.04 OS onto another USB stick using this machine plus the original live stick and the new USB stick. 
So far so good. I now have a dual boot capability on this (U)EFI machine, with the USB stick as a boot option. There are BIOS/Grub-type complications on the USB stick each time the linux version updates, but they are easily overcome using Boot-Repair. Grub eventually recognises everything (until the next Linux update). I'm now successfully running Ubuntu 14.10 on the machine and also via the USB stick, having upgraded both. 
The USB stick will also dual boot with an older non-efi machine running Windows 7, after a bit of inconsequential complaining and pressing S for skip.
So far... so, err, good.
Here is my problem.
I thought I'd give Pinguy 14.04 a trial on my USB stick - because it's pretty (don't ask...). Pinguy is Ubuntu-based via Mint.
What I have found it that the live version of Pinguy is not recognised for booting by my efi machine. Not nohow. Thus I was forced to install live Pinguy onto a USB stick via my non-efi Windows 7 machine. That worked fine and I was then able to fully intall Pinguy 14.04 onto another USB stick via this older non-efi machine. 
But I'd like to run this fully installed Pinguy OS from its USB stick on my efi machine and I cannot work out a way of getting a working efi-boot capability onto this Pinguy stick.
Does any genius out there know what I need to do to the Pinguy stick (currently all EXT4 format), containing a Boot partition, a Root partition and a Home partition - (no point in Swap). I'm guessing I need to create a new (FAT32?) partition on it with an efi boot-loader. But there doesn't seem to be a way of doing this via Boot-Repair and/or GParted.
If someone ):P  knows what-the-hell I'm talking about and could take me through it step by (pretty-newbie) step, I'd be very grateful. (Phew...)
David

---

### Post by oldfred on 2014-12-08
I am not sure you (or me) can convert a system that is BIOS boot only to UEFI boot. If it was UEFI compatible then yes.

You should still be able to boot on UEFI system, but have to boot in BIOS/CSM/Legacy boot mode.

That said I was able to create a UEFI boot flash drive with no system, just by copying efi files & folders. I use it to loop mount with grub ISO files directly for installing or repairing. So one flash drive can have multiple ISO.

I did not compile a new grubx64.efi or shimx64.efi which probably is the correct way. And it turns out the grubx64.efi has built into it paths to some of the files, so the version on my Ubuntu flash drive is different than the version on my installed Ubuntu.

If you want to experiment.

Is flash drive gpt partitioned? You need to have flash partitioned with gpt and have first partition with the FAT32 efi partition. To have it boot in BIOS mode on older systems you need the 1 or 2MB unformatted partition with the bios_grub flag.
       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

For my flash drive I just copied all the files from my /boot/efi/EFI/ubuntu folder to an /EFI/Boot folder in my efi partition. I renamed shim(probable should have just renamed grub as it will not be secure boot anyway) to bootx64.efi. The /EFI/Boot/bootx64.efi is what UEFI systems expect to see for devices particularly external devices. I then edited grub.cfg to chain to my grub.cfg in my /boot folder. Since I had no install I then in the efi partition created a /boot/grub folder. I did have to copy /fonts & /x86_64.efi folders into the /boot/grub from my install. And I put my grub to oot ISO in /boot/grub. If you have an install you may have those already. But that was what I found was different with installer as font & .mods were in different path. After a few errors as BIOS/UEFI reports to grub the boot drive as hd0 and fixing paths so correct files could be found, it did work.

---

### Post by mirmos192 on 2014-12-08
oldfed
You are so helpful. And alsways were. Thank you so much.
It's just that there is clearly far too much work involved for me to even begin to understand you - so much above my level it is, it is. I might well get there in the end if I were prepared to do my homework over a period of some days but I've got Eric Hobsbawm's autobiography to plough through (what an appalling writer he is) plus a 1950s copy of The Einstein Theory of Relativity by Lieber & Lieber (She the math professor, he the artist-illustrator) a sheer delight taking you from high-school algebra through to tensor calculus and which, aged 16, having got it from my local library and managed to understand it then, and 10 years ago managed to find again via ABE Books, it sits on my bedside table glowering at me and daring me to start again when I find I have forgotten my highschool algebra. It's a tough choice. Do I do my homework on Hobsbawm, The Einstein Theory of Relativity (math version) Special and General, or play with my USB stick? 
Retirement is tough for us baby-boomers, no?

---

### Post by oldfred on 2014-12-08
Einstein or flash drive? Not even a question for me.
Not even sure how I passed advanced differential equations, I was going to specialize in Fluid Mechanics, but could not see myself manually solving all those equations. If I knew we would have computers I might have stayed with it. 

I did see somewhere they were going to put online Einstein's papers.

---

### Post by mirmos192 on 2014-12-08
Yes - Einstein's papers - link here...

[http://www.preposterousuniverse.com/blog/2014/12/05/einsteins-papers-online/](http://www.preposterousuniverse.com/blog/2014/12/05/einsteins-papers-online/)

Unfortunately math too advanced for me (though allegedly Einstein was stretching himself a bit - his wife was the better mathemetician...)

But thanks again.

Best
David

---

### Post by grahammechanical on 2014-12-08
I once read a book by Einstein about his theories of Relativity. It was a small book and written in English. Yes, I am sure it was written in English but could I understand a word he was writing? And it did not have much mathematics in it, either :)

I also read a post on this forum the other week where someone installed Pinguy and Grub did not recognise the existence of Pinguy. I do not think that Pinguy uses Grub or maybe it is because the Pinguy developers do not follow standard procedures regarding boot files.

Regards

---

### Post by mirmos192 on 2014-12-08
Pinguy uses grub, grahammechanical.The issue is its compatibility with the newer UEFI system Microsoft has insisted manufacturers use for their computers (instead of BIOS) if they are to be allowed to ship with Windows nowadays. Recent versions of Ubuntu recognise this and install accordingly. Evidently, despite being based on Ubuntu 14.04 Pinguy does not.Regarding Einstein he is alleged once to have said "This world is a strange madhouse. Currently, every coachman and every waiter is debating whether relativity theory is correct. Belief in this matter depends on political affiliation". He was too polite to mention which kind of political persuasion allowed for a belief that his Relativity Theories were correct. Nevertheless, research continues to vindicate them. However, Einstein's 'theology/political persuasion' did not allow him to trust Quantum Theory as per his famous 'God does not play dice' quote (as well no doubt as its fundamental (so far) apparent conflict with Relativity).BestDavid

---

