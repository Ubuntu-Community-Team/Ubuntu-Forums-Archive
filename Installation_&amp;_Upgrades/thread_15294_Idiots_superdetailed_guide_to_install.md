---
title: "Idiots superdetailed guide to install"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by Sharphedin Olsen on 2005-02-13
Does such a thing as what indicated in the title exist? It seems I am in need of one.  ](*,)

---

### Post by DJ_Max on 2005-02-13
[QUOTE=Sharphedin Olsen]Does such a thing as what indicated in the title exist? It seems I am in need of one.  ](*,)[/QUOTE]
 Currently no, as if you need one, I wouldn't suggest using Linux, or any OS for that matter.

What problem(s) are you having?

---

### Post by milovoo on 2005-02-13
>  Currently no, as if you need one, I wouldn't suggest using Linux, or any OS for that matter.

Isn't this exactly the right forum for someone to look if they need help?

I would say that you should be able to handle installing this software just fine.  It's one of the easier distros to install.  You can look [here](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/20040801ubuntu20/doc/manual/en/index.html)  for a detailed install guide, if you have any questions beyond that you should post the specifics and maybe we can figure it out.

---

### Post by Sharphedin Olsen on 2005-02-13
[QUOTE=DJ_Max]Currently no, as if you need one, I wouldn't suggest using Linux, or any OS for that matter.[/QUOTE]

Beautiful. Just the kind of answer I was looking for after reading about ubuntu. I sincerly hope that your persona serves you well. 

Thanks for the tip milovoo; already been skimming those pages a bit.

My problem is that after having downloaded and burned the cd it doesn`t boot from it. I went into bios and set it to boot from cd-rom. The result is a screen where A: is waiting for some king of command.  Above it it says "Current options available" and then starts with "MUX something" next option being "BL=16" There are 4 or 5 of these options.
I don`t get it all.
So I punched in "dir" and got up "wwbu"as an exe-file in A:, and I decided to try to run that one. I was not preparred for a german meny, but excited enough to go ahead anyway. After a while I decided it was not a good idea, canseled whatever I has been doing and rebooted. Then I discovered my new boot-menu is in german. No problem, can get w2k to run from there. But when I tried to further into the german menus to try to install somehow - I discovered that only one of my hd was detected, and it was not the one I had preparred a partition on.

I hope I have made some idiotic mistake and that this is supposed to be much simpler. If anyone (excluding, of course, DJ Max) can give me some tips to get back on track I would be deeply grateful.

---

### Post by kanem on 2005-02-13
Yes, it is supposed to be much more simple than that. Something has definitely gone wrong with your install. I think what DJ_Max was implying is that if things go right there is no need for an idiot's guide, and since you hadn't mentioned that you were actually having problems with the installation yet, it sounded like you were asking for something unnecessary. Under most circumstances you would have had no problem installing.

As for your problem; After booting from cd it should have gone directly into the Ubuntu installation with a big Ubuntu splash screen and then a semi-graphical installer. None of that stuff you mentioned should be there. 

I'm no expert, but here's some things more experienced folks will probably want to know before they can help:
have you checked the md5sum of the installation disk image?
are you able to boot from other cd's?
what kind of motherboard do you have?
what happens when you tell your computer to boot from cd but don't put cd in? Maybe your computer just didn't see the cd at all.

---

### Post by tkiesel on 2005-02-13
Hi Sharphedin,

I'm a total Ubuntu newcomer. I had a few issues with improperly burned CDs making my attempts to install frustrating.

It might be the case, from what you said, that you burned the ubuntu image as a bootable cd with some kind of Floppy disk emulation. I saw some options to that effect when I was trying to burn my copy with Nero in Windows XP.

Does that sound familiar at all to how you burned your CD? Turns out you don't need to use any floppy emulation, and in fact you don't need to set any special boot options in Nero. You just tell it to burn the .iso, which is already bootable.

Don't give up. I got the CD burned correctly several days ago, and have been quite hapy with Ubuntu since then!

Good luck!
tkiesel

---

### Post by Sharphedin Olsen on 2005-02-13
tKiesel: Yes, that makes kind of sense. So I burned the iso once again. But when I try to boot from the cd, the wwbmu-meny (in german, sic) that I managed to install in my first attempt, comes up. And it makes no sense to me. Maybe if someone out there could explain how I can get rid of it so I can try anew?

---

### Post by KiwiNZ on 2005-02-13
[QUOTE=DJ_Max]Currently no, as if you need one, I wouldn't suggest using Linux, or any OS for that matter.
 
 What problem(s) are you having?[/QUOTE]
 
 Play nice please[img]http://www.ubuntuforums.org/images/smilies/eusa_naughty.gif[/img]

---

### Post by Gary Powers on 2005-02-13
Sharphedan, it would be a very good idea to check MD5SUM on your downloads before burning them.  I've wasted quite a few disks before I wised up.  If you are working in Windows, you can download the check program from winmd5sum.solidblue.biz or google it.

BTW, with rare exception, this is one of the nicest and most helpful groups of folks in computerdom.  Once you get your system up and running, read through these forums as time permits and you will find answers to most of your problems.  When you don't, just hollar!

Gary

---

### Post by piedamaro on 2005-02-13
FYI there is an installation guide on the ubuntu wiki, DJMax.

---

### Post by tkiesel on 2005-02-13
Sharphedin,

I don't know for sure that your current OS is Windows, but if it is, here are a few helpful programs.

I used [MD5sums for Windows](http://www.pc-tools.net/win32/md5sums/) to check my ISO file. Just drag the ISO file onto the MD5sums icon and it will spend several seconds calculating the MD5 hash of the ISO file.  Then you check that it matches the corresponding MD5 sum at the [Ubuntu Releases archive](http://releases.ubuntu.com/warty/MD5SUMS) .

Take your currently burned CD-R, rip it to an ISO image, perform an MD5 sum on the image and compare that sum to the official one. If they are different, your burned media has errors.

I was lucky enough to see that both strings of text were exactly matched, meaning that my download was good. My problem, therefore, was with my CD burner.

I used a small, free program called [burnatonce](http://www.burnatonce.com/) to burn the ISO. I had to purchase new CD-R media (I hadn't known that the data on a CD-R is carried by a photosensitive dye. My previous discs had been sitting out in the living room for more than a year. Ooops) and burn at 2x to get a good image. Once I had burned the image, I immediately ripped it to a new ISO on my harddrive using burnatonce, and ran MD5sums on that image.  When it matched the official sum, I knew I'd burned a perfect image to CD.  My install was problem-free after I took those measures.

If your current OS isn't Windows, the program links are useless, but the methodology can help to produce a error-free CD. If you can verify that yoru burned image has the correct MD5, you can eliminate the CD as the source of your trouble. It was the source of mine.

take care,
tkiesel

---

### Post by hashimoto on 2005-02-14
Made a quick google on WWBMU. It seems to be a boot manager and _all_ of the links were in german. Doesn't sound Ubuntu stuff at all!  Anybody??

BR
Hashimoto

---

### Post by DJ_Max on 2005-02-14
> Yes, it is supposed to be much more simple than that. Something has definitely gone wrong with your install. I think what DJ_Max was implying is that if things go right there is no need for an idiot's guide, and since you hadn't mentioned that you were actually having problems with the installation yet, it sounded like you were asking for something unnecessary. Under most circumstances you would have had no problem installing. 
It was moreless a joke, but some people take comments the wrong way.  :? 
I would have helped, as I asked if he had any problems, but he didn't mention any. 

>  If anyone (excluding, of course, DJ Max) can give me some tips to get back on track I would be deeply grateful. 
No problem

---

### Post by KiwiNZ on 2005-02-14
Thats cool DJ . the misunderstanding is accepted and understood We will all move on . 
 
 Just remember folks the cold enviroment of a forum means that a light hearted or joke  post can be misunderstood because you dont have the live person to person interaction . Remember to use smileys etc they do help .
 
 Cheers

---

### Post by Sharphedin Olsen on 2005-02-15
[QUOTE=DJ_Max]It was moreless a joke, but some people take comments the wrong way.  :? 
I would have helped, as I asked if he had any problems, but he didn't mention any. 

 
No problem[/QUOTE]


I`m at fault here too, as I should have been able to consider that he may have meant it in a different way. Let me apologize for that DJ_Max, and let me regret not wanting your help as I`m grateful for any I can get. Ok?   :grin: 

I have now found the german developers uninstall page, but as I have a very limited understanding of german maybe someone out there (including, of course, DJ_Max  :p  ) could help me understand it. Babelfish hasn`t been to helpful in figuring it out.

I decided that I should get rid of this bootloader in a foreign language before I move on.

tKielsel &kanem: You were right, the MD5sums where indeed different. An imporatant lesson to be learned there; I will be doing it every time from now on!
I will also burn a new image slowly to see if it`ll help, though before I move from there I will have to get rid of wwbmu.

Edit: url of german uninstall-page should not have been forgotten: [http://toolsandmore.biz/Central/Helpdesk/FAQs/Deinstallation/](http://toolsandmore.biz/Central/Helpdesk/FAQs/Deinstallation/)

---

### Post by hashimoto on 2005-02-15
With my (poor) german: It basically tells you to uninstall the boot manager using the standard windows tool for removing software. Also warns that the software must not be active and that entry in the start-up menu must be remioved before uninstall. Go figure if it really is that easy...

---

### Post by Sharphedin Olsen on 2005-02-15
While checking out different distros I also downloaded suse, but I didn`t install it. Now, it seems to me that I might have put in a suse-iso beliving it was ubuntu; no wonder no suggestions haven`t turned up here. I`m still going to install ubuntu, but I`ll have a shot over at some suse forums as to the removal of wwbmu.

---

### Post by DJ_Max on 2005-02-15
[QUOTE=Sharphedin Olsen]I`m at fault here too, as I should have been able to consider that he may have meant it in a different way. Let me apologize for that DJ_Max, and let me regret not wanting your help as I`m grateful for any I can get. Ok?   :grin: 
[/QUOTE]
It's all good, sorry if I came off a little "rugged"(can't think of a good word to use).
[QUOTE=Sharphedin Olsen]
tKielsel &kanem: You were right, the MD5sums where indeed different. An imporatant lesson to be learned there; I will be doing it every time from now on!
I will also burn a new image slowly to see if it`ll help, though before I move from there I will have to get rid of wwbmu.
[/QUOTE]
Thats a common problem when burning at a fast speed. Sometimes you won't get a "clean" burn, plus, it's a lot of other factors, like the speed of your HD Bus, etc..

Removing wwbmu should be as simple as overwriting it with GRUB and/or reformatting that parition when going through the Ubuntu install.

---

