---
title: "EXT4 install failed, EXT3 worked ... is this common?"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by zcacogp on 2011-06-06
Chaps, 

Not sure what I expect from this thread, 'cos it's not a problem to be solved *per se*, but more a discussion-ish question. 

I upgraded my desktop machine from 10.10 to 11.04 recently, which it had run very nicely for the last 6 months. It has an AMD 64-bit chip, but I was running 32-bit 10.10 and had never tried a 64-bit OS. So, when upgrade time came 'round, I thought I'd give the 64-bit version of Natty a spin. 

I also replaced the HDD for a larger one (320Gb IDE to 1Tb SATA), and thought I'd have a go at the EXT4 file system for the Ubuntu partition, in place of the EXT3 partition I have used previously. 

The install went OK (I put windows in one partition and Natty in another one), but when I came to log into Natty it failed; I could choose my username and put in my password, it would play part of the introduction tune but then stop and show a black screen, from which I couldn't recover.

Cutting a long story short (I'm still a bit of a 'Buntu beginner) I saw the easiest way out as being to re-format the Ubuntu partition as EXT3 and re-install. This worked fine; it installed and logs in just as it should. 

So, from this, is it likely that it was the fact that I was using EXT4 that caused the problem? Or was it more likely that I simply had a bad install? And, if it was the EXT4 filesystem that caused the problems, does this mean that I will never be able to use EXT4? Or not with this motherboard, or not with this hard drive? (i.e. Which part of the system takes offence at the EXT4 filesystem?) 

And another question; what am I going to be missing out on by using EXT3 rather than 4? (I've only ever used EXT3 with Ubuntu, so it's more a question of '*what will I not be gaining*', but there we are.)

Thanks, in advance, for your help. 


Oli.

---

### Post by ghostborg on 2011-06-06
Cutting a long story Short... Too late. Just kidding. 

I have been using EXT4 with an AMD 64 bit 4 core from when they introduced it and have not had any problems installing.

I would only guess that you did a custom partition install and maybe something was not selected correctly, like Format. 

I am only offering you that my experience installing EXT4 on several system in my house has not caused me any problems.

Maybe if you can leave some more info on the steps you used to install, if you can remember, for others to offer you a solution as you might need to install again in the future.

Here is a FAQ Wiki link that might explain EXT3/4.
[https://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions#What_is_the_difference_between_ext2.2C_ext3.2C_and_ext4.3F]("https://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions#What_is_the_difference_between_ext2.2C_ext3.2C_and_ext4.3F")

Good Luck !

---

### Post by zcacogp on 2011-06-06
Ghostborg, 

Thanks for your answer. Perhaps a bad partition is the answer, although I did pretty much the same thing with both installs. I have three primary partitions (Windows - NTFS, Ubuntu - EXT3, and Ubuntu Swap), and an extended partition, with three data partitions within it. When it wouldn't allow me to log in after the first install then I reformatted the Ubuntu partition as an EXT3 (it was EXT4) and re-installed. And that's about it. I did pretty much the same thing the second time 'round and all is well. 

Thanks for the link. From having read it it seems that I am not missing out on much with EXT3 over EXT4, so I'll try not to lose any sleep over it. :)

FWIW, my machine is only a dual-core affair, not a quad - like yours. Although I can't think that that will make a huge difference. 


Oli.

---

### Post by ratcheer on 2011-06-06
I have used Ubuntu for about 3 years and have never used anything except ext4. I have done extensive testing on Alphas and Betas of Lucid, Maverick, and Natty, and I have therefore performed many (certainly well over a hundred) installations to ext4. I have never had any trouble with filesystems except when I was trying to experiment with btrfs.

Tim

---

### Post by zcacogp on 2011-06-06
Tim, 

Well I don't know what btrfs is, so I can only assume that I had a rogue problem that is unlikely to re-assert itself. 

Interesting. I suspect user error somewhere (it usually is in my case!) so I wonder what I did wrong ... 


Oli.

---

### Post by ratcheer on 2011-06-06
btrfs is a newer filesystem design. It will probably become the successor as a default Linux filestem, eventually. Even the designer of ext4 says it (ext4) is just a stopgap until btrfs is ready for prime time.

Tim

---

### Post by ivanovnegro on 2011-06-06
Btrfs is another newer file system for Linux.
I for one experienced problems with the performance of Ext4 but I could install Ubuntu without problems with this file system.
I am using again Ext3 as it performs better under my hardware, dont tell my why. :)

---

