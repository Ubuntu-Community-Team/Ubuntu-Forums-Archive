---
title: "Problem with HP Pavilion zv600"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by Wybiral on 2006-10-16
Hello. Well, I successfully installed ubuntu on my e-machine and I love everything about it! :mrgreen:

But, I've been trying to install it on my Hp Pavilion zv600 laptop...

Here is some info on it...

Ram: 512mb
Processor: 1.8 AMD64 3200+
Hard drive: 80gb
DVD Drive: Matshita UJ-840D DVD
Display: ATI MOBILITY RADEON Xpress 200 series
Current OS: Windows XP home edition

The problem is that it refuses to boot the live cd.
I burnt the ubuntu-6.06.1-desktop-amd64.iso
And yes, I tried setting the boot order to CDrom first.
I even tried dissabling the hard-drive from the boot order and it just sat there with a blank screen.

I had zero problems with my other computer, but this one is being stubborn. ](*,) 

No matter what I do it simply boots my old OS as if the disk were not in the drive.

If anyone can help me out I would be very grateful. Thanks for your time!

-Davy

---

### Post by foxmulder881 on 2006-10-16
As you've already mentioned, you have the correct settings in BIOS.

I suggest and error with your optical drive. Does it boot a Windows install dics? Try it.

---

### Post by K.Mandla on 2006-10-16
Hi Davy, and welcome. I've worked with those zv6000's, and to be honest, they were the only machines I had to admit failure, and it was because of that video card. For some people it works, but for me and the Xpress 200 in the zv6000, it just wasn't going to cooperate.

You will probably have better luck installing if you use the alternate (install) CD, rather than the desktop (live) CD version. Installing will most likely work fine, and a dual boot is a fun thing, but video acceleration might disappoint. 

If you're willing to live without pure 3D, it will work great -- even the wireless works with the fwcutter method. If you're willing to fight the good fight and try to get the ATI proprietary drivers working, I'd be more than happy to lend some advice. :)

---

### Post by Wybiral on 2006-10-16
:-k

I popped in the windows recovery disk and it booted up just fine :confused:

Anything else it could be?

btw, I burned the disk using ubuntu, I just put in a fresh cd and it popped up... Then I dragged the iso into it and burnt the image. Everything seemed normal...

Edit:

Ok, I'm currently downloading the alternate install iso... I will probably need some help with this eventually (especially if it doesnt work) but also because I am still pretty new to linux, so dont forget me :-D 
And yeah... I'm more than willing to do what it takes to get that ATI working.

---

### Post by Wybiral on 2006-10-16
:( Well... No luck. I downloaded the alternate iso and tried it, same thing, even when I changed the boot order and it still just jumps right over to windows. And once again, when I removed the hard drive from the boot order, it just sat there with a blank screen. I'm all out of ideas.

It does fine booting a windows recovery cd though. If anyone has ANY ideas, please, I would appreciate them. Btw, thanks guys for your quick responses, I doubt I could have got support like that on any other forums. Hopefully I'll get this sorted out, I absolutely love ubuntu and would really love to have it on my laptop.

Anyway, thanks again guys and if you run across anything that might help, I would be very glad to see it.

-Davy

---

### Post by K.Mandla on 2006-10-16
> **Wybiral said:**
> I burned the disk using ubuntu, I just put in a fresh cd and it popped up... Then I dragged the iso into it and burnt the image. Everything seemed normal...
At risk of oversimplifying things, make sure you're burning the ISO to the disc, and not just burning a data disc that has the ISO on there as a file. ...

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Sorry if I'm underestimating your expertise; you'd be surprised how many people haven't burned an ISO before and need help with it. ;) 

Post again if that still doesn't do the trick, or PM me if you want more help. Cheers!

---

### Post by Wybiral on 2006-10-16
No, I understand, you always have to cover the basics. I dont feel underestimated in any way... But, yeah, I burned it as an image. In fact, I burned it as an image in Ubuntu, as a Data CD in Ubuntu, AND as an iso using nero in windows (the same way I burnt my first install). And the disk's are good... The laptop will boot a recovery disk... And I do know how to change the boot order. I wish I were overlooking something really simple... But I think I've covered all the basics I can think of :( Do you have any other ideas to try, is there any more info I can get you that might help or something? Once again, I do appreciate your time, you guys on these forums are great at quick responses. I just hope that there actually is a way to get ubuntu on the laptop... Is there a way to copy it to the hard drive and mount a partition like it's a CD? (I have no idea if thats possible... I'm just out of logical ideas)

---

### Post by K.Mandla on 2006-10-16
Actually, there is. If you can copy the ISO onto a partition on the drive, I know you can set up Grub to boot that partition.

[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)

Those are some serious acrobatics, though. It might be hard to tell if it's the ISO that's just not working, or if the entire procedure is faulty. But that's the link to get you started.

Alternatively, you could pull the hard drive, install on another machine, then move it back and reconfigure. Ugly, but it would work.

And you have the option of downloading, burning and installing an earlier version of Ubuntu, then upgrading to the latest one. That's something people do all the time, and would probably work fine.

To be honest, I would wait to install from an ISO until after you've tried to upgrade from an earlier version. That would be far easier, in my opinion.

---

### Post by Wybiral on 2006-10-16
](*,) 

I may have figured it out... Sortof... My laptop isn't wanting to read any burnt disk's... At all... Its fine with dvd's and the windows recovery disk and everything. But, I was going to rip that iso from one of the disk's I burnt it on using windows, and then try to manually install it from that link you gave me, but it wouldnt recognize the disk. Any of my burnt disk's. I assume no one here can help with something like that... So, I guess I am going to try to download it from the laptop and then try those instructions. I dont get why it would be fine reading other stuff (dvd's/software) but not burnt stuff. But, I'll let you know how this goes.

---

### Post by Wybiral on 2006-10-17
Oh no... I can't partition my laptop because every partitioning program I find requires you to burn it or copy it to a floppy! Does anyone know any partitioner that will work with windows xp? I know windows isn't your thing... But, its required for me to get ubuntu on my laptop. Thanks in advance.

---

### Post by foxmulder881 on 2006-10-17
I always use and recommend GParted. Although, to use with Windows you have to use the GParted Live CD which involves burning to disc and then booting from that. As far as I know there is no Windows installer version of GParted.

---

### Post by K.Mandla on 2006-10-18
> **Wybiral said:**
> Oh no... I can't partition my laptop because every partitioning program I find requires you to burn it or copy it to a floppy! Does anyone know any partitioner that will work with windows xp? 
There's PartitionMagic, which costs like $70 or something. (Sheesh!)

I think those zv's might boot from USB. Would that help at all? I think there was a exceptionally simple partitioner that ran from a DOS boot environment ... Ranish Boot Manager or something like that?

---

### Post by foxmulder881 on 2006-10-18
> **K.Mandla said:**
> Ranish Boot Manager or something like that?

Oohhhh, I was hoping that nobody suggested Ranish! Please don't even bother with it. Trust me, from experience of using it myself.

Partition Magic was what I used to use when I used Windows until I migrated to Ubuntu and now use Gparted. PM is worth the money as it's a very good quality program. But only fork out the cash if your willing to make use of it. It's not worth the 80 bucks just for one time use.

---

### Post by Wybiral on 2006-10-18
Ok... To update. My windows recovery disk actually had a partitioner in it, so I was able to create a second partition. I followed the instructions on the "Install Ubuntu Linux without burning a cd" and I was able to get it up and ready to install... I even got it to a command line... But I can't install because it wont connect to my network! Is there a way I can download the ISO and maybe mount the "C:" drive in order to download it from there? And if so, does anyone know the commands to use?

Oh yeah... I have a 256mb USB card. Would it be possible to manually move files from the ISO into via the USB card onto the laptop and then install from that (using the SHELL that I get from the almost install of linux I just did)

---

### Post by K.Mandla on 2006-10-19
If Windows is working, you might download it to there, put it on a FAT32 partition, then move it into the Ubuntu environment. Would that work for you?

As far as installing via a folder ... whew! I've never heard of that. You'd need to poke around quite a bit to get the answer to that one.

By the way, you win a prize for tenacity. Most folks would have given up by now. :KS

And to think: You haven't even gotten close to configuring the wireless card or video card! :rolleyes:

---

### Post by Wybiral on 2006-10-19
:mrgreen: lol. I have ubuntu on my PC... And I love it. My favorite OS so far (and I've tried my share of them). I just really want to see how it runs on my laptop and to... Well... Have it on my laptop. I want to get rid of my old OS for good (you know... That one OS... The really annoying one... You know who I'm talking about...)

Anyway... The partitioning program on this OS recovery disk is just for NTFS, unfortunately (but I was able to create an unallocated partition). I might just have to wait until I get my disk drive fixed (or replaced) which is kindof sad. But, I'll keep researching.

As far as the wireless and graphics... I've already had to get the wireless working on the computer I'm on right now. It wasn't bad, just took alot of research. And I can live without graphics acceleration for a while. My computers are mostly for programming (ASM:twisted:, C/C++, BASH + web scripting) and the internet.

---

### Post by foxmulder881 on 2006-10-19
Don't remove Windows until you're absolutely 100% sure that you're happy with Ubuntu or any Linux as a matter of fact.

You don't know how many people I have heard say they love Ubuntu and then later on down the track they find there's one thing in particular they use or need Windows for. And before they know it, it's too late and they've removed the partition.

---

### Post by Wybiral on 2006-10-19
No... Im 100% sure. I program, use the internet, and use GIMP & Blender... That's about the extent of my computer use. And Ubuntu has more than enough programs to support those habits. I think alot of people feel comforted by the familiarity of windows, not me. I've always found it to be quite bothersome and annoying (not to mention bulky and unattractive... Oh, and uncustomizable). On my PC right now, I have all of the software I need to fulfill my programming pleasures (3 assemblers, Gcc, Java, and all of the dev resources I'll need).

Now if I can only get it on my laptop...

---

### Post by foxmulder881 on 2006-10-19
Not trying to get you away from Ubuntu, but if you're a serious programmer, I'd use Gentoo. However, if you're happy with Ubuntu, even better.

The more that choose Ubuntu, the better!

---

### Post by Wybiral on 2006-10-20
HEY, I did manage to find a partitioning program for windows (the windows disk manager). So now I have a FAT32 which should help me do this install thing right? Can anyone help me out with steps for downloading the ISO to the FAT32 (I can do that part)... And then installing it FROM the FAT32? It seems like it should work, but I'm pretty new to linux. Thanks.

To foxmulder881: Why would Gentoo be better for a programmer? I mostly just want to assemble and do hardware i/o.

Once again, thanks guys!

---

### Post by foxmulder881 on 2006-10-20
Gentoo is simply more suited and aimed towards programmers. That's Gentoo's intention. But as mentioned, Ubuntu will still exceed your needs.

---

### Post by Wybiral on 2006-10-20
I'm not doubting you, but I did try gentoo's livecd and I thought it was a little too similar to ubuntu. Basically, any programs it comes with to suit programmers, could be installed in ubuntu. It was also a lot more complicated and not very user friendly (just my opinion of course). But regardless, I do appreciate the advice. I've just grown fond of ubuntu, and seeing how it's simple to install GCC, Java, and NASM... It's really all I need. Plus the package manager makes finding dev files and resources really easy. But, you know, everyones boat floats a little differently.

---

### Post by foxmulder881 on 2006-10-21
Yeah, Gentoo is a pretty advanced operating system and not recommended for the newbies of the Linux world. I'm not saying you're a newbie, just a simple statement for others reading this. By the way, I'm a Linux newbie myself. When I get another system up and running, I will be installing Gentoo on it simply for interest and learning sake.

Nevertheless, if you're happy with Ubuntu, that's great. I'm not complaining!

---

### Post by Somniis on 2006-10-21
If you want to try another partition program, try this:
[http://partitionlogic.org.uk/](http://partitionlogic.org.uk/)

You can burn it to a CD and boot it on start-up.  Very nice (and free!)

---

### Post by foxmulder881 on 2006-10-21
> **Somniis said:**
> If you want to try another partition program, try this:
[http://partitionlogic.org.uk/](http://partitionlogic.org.uk/)

You can burn it to a CD and boot it on start-up.  Very nice (and free!)

For all the reasons you mentioned above, that's why I suggested Gparted Live CD.

---

### Post by Somniis on 2006-10-21
> **foxmulder881 said:**
> For all the reasons you mentioned above, that's why I suggested Gparted Live CD.

I realize that. :)  I used PL to reformat my system after a Windows crash, had it lying around, so I thought I'd mention it.

---

### Post by foxmulder881 on 2006-10-21
That's cool. I wasn't flaming you. Cheers! :cool:

---

### Post by Wybiral on 2006-10-21
I use GParted on my PC when I need to mess with the partitions (btw... The tetris game on there really makes moving partitions go by alot quicker). My problem is that the laptops CD drive just recently went out the window. I did create a new partition on it from windows, but it's a FAT32 and I now need to figure out how to get the grub to recognize a hard drive installation.

So you haven't tried Gentoo yet?
I thought it was really nice and everything... But it just didn't seem much different from ubuntu... Alot of the same stuff (and you could manually install anything extra that it offered). But yes... It's alot more complex than ubuntu, the installer had a "simulate" mode... I assume for practicing... Thats pretty intense.

---

### Post by lfloyd on 2006-10-21
in main window press f6 erase those parameters put live acpi=off and it will boot but not sure if it will install, I'm having problems installing

---

### Post by foxmulder881 on 2006-10-21
Wybiral, when I get another machine up and running on my network I will be installing Gentoo on it. Mainly as a learning process. I'm really keen to give it a shot as I have had many others recommend I give it a shot. Still, it will be no replacement for my Ubuntu 64bit system I run as my primary machine. I love it.

---

### Post by Wybiral on 2006-10-23
Cheers to that, Ubuntu is great. So far it has met all of my programming needs. Its been more than easy to find good compilers/assemblers/devfiles/etc... I do think people need to start writing more tutorials and documentation for programming with ubuntu, and I plan to de my share of writing too. Anyway, good luck with gentoo... It personally just didnt do much for me, but like I said... Thats why there ARE different OS's... People are different! Thats what makes me so happy about linux... So much variety.

---

### Post by Wybiral on 2006-10-25
Great news!!! My Dvd drive came in the mail today and I got Ubuntu installed on my laptop!!! It works great. Only one problem... As predicted... The wireless and graphics cards arent working... Any suggestions?

---

### Post by foxmulder881 on 2006-10-29
> **Wybiral said:**
> Great news!!! My Dvd drive came in the mail today and I got Ubuntu installed on my laptop!!! It works great. Only one problem... As predicted... The wireless and graphics cards arent working... Any suggestions?

Need more info on hardware specs?

---

