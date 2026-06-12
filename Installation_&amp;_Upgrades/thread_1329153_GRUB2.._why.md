---
title: "GRUB2.. why?"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by It-Alien on 2009-11-17
Hi,

I hope this post will not sound harsh, as I'm simply curious about the reasons for which Ubuntu community has decided to adopt GRUB2 as standard boot manager, which does not seem the best choice to me, as of now.

I understand that GRUB2 comes with new features and structure which will let developers create better utilities, but I think that Ubuntu is aimed at ease of use, and currently making a simple dual boot scheme in GRUB2 is terribly difficult if compared to GRUB. If you put yourself into the shoes of a newbie who wants to perform a Windows-Ubuntu dual boot, you will easily found yourself dispaired. I'm not a newbie myself, still I find myself unable to find the will to start working with this, so this is the main reason for which I installed version 9.04 instead of 9.10 lately and will do so until soemthing like a GUI-driven application for GRUB2 will be released.

---

### Post by presence1960 on 2009-11-17
whenever change rolls around a lot of us fall into the human condition of resisting it. GRUB 2 is different than GRUB legacy and it will take some getting used to and some studying. I have Jaunty, Karmic, Masonux 9.04 & XP on a multi-boot setup and GRUB 2 is working perfectly. Of course I had to do some reading when I added an OS but all went well. If you don't want GRUB 2 you can remove it and install Legacy GRUB. See [here]("http://ubuntuforums.org/showpost.php?p=8071880&postcount=18")

---

### Post by It-Alien on 2009-11-17
thanks for your reply, but I don't think you have answered my actual question: I'm not questioning the fact that there have been many good reasons for creating GRUB2 in the first place; what I wonder is if it was really advisable to put GRUB2 into an user-friendly-oriented distro such as Ubuntu. It is already not 100% straightforward to create a dual-boot with legacy GRUB, will it be better with GRUB2? I don't think it will.

so, if you can get rid of GRUB2 if you don't want it (thanks for the link by the way), wouldn't be better to provide GRUB2 as an alternate option to GRUB in Ubuntu, instead of the viceversa?


NOTE: I have edited the thread title from "GRUB2.. why?" to "GRUB2 in Ubuntu.. why?". I hope this will make my question more clear

---

### Post by wkulecz on 2009-11-17
Different is not better, better is better.  

What exactly does Grub2 bring to the party?  Enough to justify all the pain caused already?  Nothing that I see so far.  

Maybe someday when/if it supports booting from RAID5 etc. but for the average Ubuntu user, I just don't see an upside beyond trying to force folks to be Guinea pigs with ext4 installs.

The pain might have ben minimized if the installer would have warned about using Grub2 and if its docs and howtos were on the CD with their locations specified in the installer notification.

Maybe next time.

--wally.

---

### Post by decoherence on 2009-11-17
This is a pretty common type of question. Why did they include crappy Intel/ATI drivers? Why did they include PulseAudio? Why did they include NetworkManager?

Ubuntu tries to balance cutting-edge software with usability which is a very hard thing to do and I applaud the effort.

What I'm not so thrilled about is the "Linux for Human Beings" slogan. The philosophy of including new, relatively untested software is completely at odds with that.

That said, Ubuntu users are a great test-base and, as a result of Ubuntu's popularity, most things get fixed pretty darn quickly. I haven't had to worry about NetworkManager in a year, though it was completely unusable for me at first.

So I guess the simple answer to your question of "Why GRUB2" is "because this isn't an LTS release."

---

### Post by It-Alien on 2009-11-17
thanks for all the answers. I see your point decoherence, and I hope that your vision is right, but this would mean that I expect to see, in next LTS version, GRUB2 turned into something which a "human being" can actually use without getting a degree in computer science, but I'm dubious it will happen: although it would be somehow easy to create a GUI-driven dual-boot configuration application which simply wants to know the /dev of your Windows installation and creates a GRUB2 menu, it was even more easy to do this with GRUB, but this has never been done (as far as I know).

about the other big changes you mentioned, it has to be noted that all of them gave extremely better user experience, so they got introduced at an expense at first, but gave great bonus after a while

---

### Post by oldfred on 2009-11-17
I am coming around on liking Grub2. The osprober solves most of the issues with finding other operating system. Separate files for editing eliminated the problem where you screw up menu.lst and cannot boot. You can still manually add entries its just now in 40_custom not at the end of menu.lst.
I also think it has long term implications. Grub legacy was built on MBR type partitions. Old grub has not really been updated, but some fixes were bandaid added. Also MBR has a max of 2TB and you now can buy 2TB drives. The next update to  drive size will not work with MBR, so if the next release of Ubuntu is long term it needs a boot loader that will correctly handle large drives with GPT partitioning like Apple currently has. So I think Ubuntu needed the fixes to grub2 before the next long term release.

---

### Post by slakkie on 2009-11-17
> **It-Alien said:**
> Hi,

I hope this post will not sound harsh, as I'm simply curious about the reasons for which Ubuntu community has decided to adopt GRUB2 as standard boot manager, which does not seem the best choice to me, as of now.


It is the best choice, since grub-legacy is not supported anymore and there is no active development. Grub 2 on the other hand is supported and has active development. Simple.

Another reason could be that Debian also switched to grub2 (and also migrates grub to grub2 for you).

---

### Post by Dedoimedo on 2009-11-17
I think the problem is that a beta version was included in a production release of the OS. That's not typical for Ubuntu. And since bootloader is such a critical part of the OS, it seems a little irresponsible.

As to functionality, there are some ups and downs. The big down is that you need far more expertise to manage grub2 than legacy.

I've written a long tutorial that shows everything, I'm gonna post it soon, so you may like it, dual boot, triple boot, legacy and grub2 mix, windows, troubleshooting, fixes, errors, etc.

Dedoimedo

---

### Post by xzero1 on 2009-11-17
I sympathize with the original poster. It seems Ubuntu want to put everything on "automatic" i.e. "it just works". The problem with this is if it doesn't work it is typically much harder to find the problem and fix it because it is no longer "user oriented" by design. If you've ever used windows you know what I mean.
The biggest problem with all of this is the general lack of good documentation, especially with new "features".

---

### Post by Rink on 2009-11-18
> **xzero1 said:**
> I sympathize with the original poster. It seems Ubuntu want to put everything on "automatic" i.e. "it just works". The problem with this is if it doesn't work it is typically much harder to find the problem and fix it because it is no longer "user oriented" by design. If you've ever used windows you know what I mean.
The biggest problem with all of this is the general lack of good documentation, especially with new "features".

Well I'm not sure I agree with this.

Firstly, the Bootloader is, of necessity a highly individual configuration. Some run just one OS, some have multile OSs with multiple configuration options for each.

Some people want their default to be Ubuntu, others want another OS to be default.

Clearly, the Ubuntu installer is unlikely to guess the desired boot options correctly every time.

So, obviously, there is bound to be a requirement from the user to reconfigure his boot loader.

The problem is that Karmic has added another layer of obfuscation to make this configuration more difficult, even for experienced users; heaven knows what newbies make of it.

Now one can not longer just edit 'menu.lst', (which has been removed from the installation in a measure surely deliberately designed to frustrate anyone who thought he had some idea).

All I want to is change the names of the operating systems from "Linux Generic Kernel blah blah blah on blah blah blah" to simply "Linux" or "Ubuntu" and similarly the Windows title.

I want to remove the erroneous reference to the hidden windows partition so that Grub does not try to boot this if the user picks it by mistake.

I want to change the default so that it boots into Windows rather than Ubuntu (It's a work machine).

And lastly I want to add my Slax installation which the Ubuntu install has either ignored or didn't see.

None of these has any chance of being delivered "automatically".

The problem is that the Karmic team has seen fit to remove the easy option of simply editing the menu.lst file and replace it with something infinitely more problematic.

That said, Karmic is a wonderful release and (this little rant aside) I think the team have done a brilliant job. Thank you.

---

### Post by oldfred on 2009-11-18
Ok just editing some entries is not easy but in menu.lst if it was in the automagic area it was rewritten anyway.
Grub 2 Title Tweaks Thread
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

I have had more trouble trying to explain to new users to put windows above the automagic area which looks like a lot of comments, to get windows first. I think it is easier to create 06_custom and copy windows into that. The osprober solves many of the issues of adding other systems.

You still edit 40_custom just like you edited the bottom of menu.lst. ok it now has {} and a slightly different format, not the end of the world once you know.

You can turn off osprober so then it does not find any other operating system except your manual entries in 06_custom or 40_custom. You can add as many custom file you want (ok 99 less the few automatic) and turn executable on or off to get any configuration you want.

It does seem more difficult to reinstall grub and I like to install to a partition. Why are blocklists so bad or what is the way to chainboot?

---

### Post by Rink on 2009-11-18
Thanks, Oldfred.

I'll take note of those.

I'm sure there are very valid reasons for incorporating Grub2; maybe they should have thrown together a tcl/tk front end or something, maybe even a webmin module.

---

### Post by It-Alien on 2009-11-18
> **oldfred said:**
> I also think it has long term implications. Grub legacy was built on MBR type partitions. Old grub has not really been updated, but some fixes were bandaid added. Also MBR has a max of 2TB and you now can buy 2TB drives. The next update to  drive size will not work with MBR.

thanks, I think you have some very good points. yesterday night I thought that maybe they could have released GRUB2 only in Server Edition, but by reading this probably I am now convinced, although the point of allowing more user friendlyness is still valid: Ubuntu is now quite a mature project, so I think it would be time for improvements like a GUI for some technical aspects like this, which instead seem to become more complex with time..

---

### Post by Rink on 2009-11-19
Nah.

Enough mucking about wasting time on this.

fdisk /MBR here we come...

It's not that I'm resistant to change as a lot of posters are suggesting, it's just that it's way too complicated.

There are simpler ways of doing this.

---

### Post by phaedr_os on 2010-01-01
Don't u just hate when someone responds to a thread about A by saying never mind A what about B?
 
So what about extlinux?
 
There must be cases when the only thing u care abount is that the linux disk which intercepts the boot process boots up quickly and simply.
 
And extlinux, how clean simple and direct: mbr code, extlinux.sys then up with vmlinuz and initrd. Voila. By comparison, lilo and grub are temperemental monstrosities.

---

