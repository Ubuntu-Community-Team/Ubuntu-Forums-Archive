---
title: "What I Wish I'd Known -- Dual-Boot and the Ubuntu Potential User"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by djlerkl on 2006-08-01
First, I should note that this is my first post to your friendly and helpful forum system, and it's rather long.  I’m writing because I’ve spent a few hours over the past days trying to get help for a problem, and then I kept reading to find out what kinds of other users and problems seem to be showing up rather consistently.  One thread that recently caught my attention (and the responses to it) prompted this post; I apologize to the moderators if it’s in the wrong forum, but this one seemed most likely.  If I’m wrong, please feel free to move or delete it.  I’m writing this because I think that the number of questions about fundamental install/upgrade problems raises both philosophical questions as well as pragmatic (i.e. software) ones.  I've got a bit of both here.

Here’s the thread that got my attention: “ Dual boot XP / Ubuntu: What somebody should've told me.”  ([http://www.ubuntuforums.org/showthread.php?t=202904](http://www.ubuntuforums.org/showthread.php?t=202904)) Since a dual-boot problem is what got me rather frantic on Friday, I read it with interest.  The author was very polite, but also showed a sense of frustration that I shared after my recent update attempt.  Please forgive a digression here, because based on my admittedly limited experience and understanding, I think it's relevant to the entire Ubuntu/Linux system (using that term in the global sense as an alternative to the mainstream computing monopoly).

I'm guessing that there are a lot of people out there like me -- familiar enough with computers to look for alternatives to the dominant system, but not expert in programming commands and syntax or anything more than the basics of computer architecture.  We're very supportive of Linux-based OS's and are interested in switching, in large part out of principle: we’ll support anything that offers an alternative to the dominant monopolies.  It's the same reason why we use Open-Office in Windows, etc.  But until all of the applications that we need are available in non-Windows platforms, we'll have to keep a reluctant foot in both worlds. From what I read on the Ubuntu home page, people like me are the current target audience for recruiting new users.  

I'm lucky to have a colleague who uses Ubuntu, so when I got a new laptop in January he set me up with a dual-boot system.  There were some glitches that I didn't have time to investigate, so I have been primarily using the Windows section until this summer.  Then on Friday I decided to update my Ubuntu installation from Breezy to Dapper (great names, by the way)and followed the instructions.  Since I first had to update the Update program, I never got to do the full system update (I ran out of time), but enough software was updated that when the machine rebooted, the initial OS selector (GRUB) had been reconfigured, and my Windows installation was no longer available as a boot option. 

Okay, I'm finally getting to the reason why I include this post in this section.  "What I wish I’d known" is that an update (for some reason) eliminates the Windows section of the boot options in Grub, although  _every Ubuntu version_  shows up.  (If this happened in reverse, where a Windows upgrade would result in every non-Microsoft program getting "lost," I'd be rather suspicious; for those of you who have the ears of the Ubuntu developers, I think it would be worthwhile passing on a message about the way this little quirk can be perceived.)  Now it may well be true that somewhere, in some "Docs" section this tidbit of information is included; it's also true that for the real Ubuntu diehard the dual-boot option might not be needed, or you've all gone through the drill so many times that you can make the necessary changes blindfolded and in your sleep.

But if Ubuntu is only aiming at people who have no problem doing the quick code edit that will fix the problem, then Ubuntu will never grow the way I'd like it to grow.  If even someone like Jere (the author of the other post on dual-boot problems), who seems to know a fair bit (perhaps too much?) about computers has trouble with a dual-boot installation, then the Ubuntu OS will always remain something that's just for high-end elite users.  If that's the intention, then great.  People like me will keep trying to work with it, and helpful people on these forums will help me fix up all my screw-ups until I either become an adept Ubuntu user or I reach the terminal patience point and reluctantly go back to the monopoly.  But if Ubuntu and the other Linux-based systems are really looking to grow, there will have to be a way to avoid some of the potentially catastrophic problems (at least from a newbie's very limited point of view) that can crop up on an install or an update.  (By the way, I see similar versions of my basic philosophical question being debated in other parts of the forum community, and it seems that the most experienced users tend to have a hard time understanding people like me: in many ways we are Ubuntu’s ideal target audience, since we’re philosophically _predisposed to try anything that doesn’t support the monopoly_ .  But we’re not experts.)

Here's my own concrete example:  the first time I started my computer after my update, the Windows boot option did not show up in Grub.  Okay, I didn't panic.  I first tried to edit within Grub, but I didn't know the proper syntax, couldn't figure out how to get a directory, etc.  I did remember enough old DOS words to see a list of possible commands, etc., but that was still not enough to do anything.  So I booted to Ubuntu and started to search.  I first went back through all the upgrade instructions -- Nothing.  Then I went to the Ubuntu website and found the forums.  I searched through multiple threads looking for info on dual-boot problems. Many of them were rather sophisticated, and the help suggestions were too detailed and assumed at least a medium-level familiarity with Ubuntu applications and editing techniques.  (Some very helpful respondents may have a hard time even imagining that someone would be trying to fix an install without having a clue what "sudo" or "gedit" refer to; I even had to poke around for a while to figure out what all the references to "Terminal" meant.  Finally I came across someone’s reply (sorry, I can’t find that reply today or I’d give credit to the poster) where the instructions were very detailed and moved step by step.  I opened the file, removed the “#” symbols that had hidden my Windows boot option, and was back in business.  Net time spent trying to find a solution that took 2 minutes to implement: 3 hours.  Not the end of the world, but something that could surely have been anticipated by anyone who knows how Grub works after an update.  

Of course, the bigger question is WHY Grub nulls the other OS boots on an update; that’s the fundamental part that should be fixed, and from my naive perspective it seems like it should be rather simple. But the secondary issue here (and the more basic one, as far as the issue of making the Linux-based world more attractive as an alternative) is that the issue only arises because the Ubuntu system seems intended either for the very sophisticated new user, or for those who are already part of the Linux world.  For the many people like me, who support the Linux world in principle and would also like to support it in practice, its details like these that could too easily make the switch seem impossible, or at least not worth the bother.  I would like to see some pre-emptive instructions about the most commonly occurring issues for upgrades and new installs; these could even include links to the solutions already posted.  In my case, if the upgrade instructions had told me that an update would reconfigure my dual-boot file and told me in advance how to fix it, I’d have been very grateful.  (Sorry, I can't do it myself because I don't remember the commands.:) )

Cheers,
Don

---

### Post by teasum on 2006-08-01
First of all, you're trying out Ubuntu, which is great.  The transition goes smoothly for most, while for others, there are issues.  

More importantly, MS Windows does not play nice with linux, and will basically install itself as the only OS (which is why it's always a good idea to install Ubuntu last on a dual-boot system).  On the other hand, if the Windows option disappeared from GRUB after an update, I don't think that's the normal behaviour (it's never happened on my end).  

Bottom-line: what's great about Ubuntu? 1) It plays nice with other operating systems, including Windows, even if in this case there was a glitch. 2) If you need help, you can always ask around here on the forums.  If you're up to it, you can search yourself, but if you need more immediate help, you can simply post your problem.  This is MUCH better than having to call some tech-support person, in my opinion.

Let us know if you have any other issues--most of us on these forums are more than glad to help.

Good luck.

---

### Post by WolfLust on 2006-08-01
teasum I agree with everything you said, but I have an urgent problem posted in the same part of the forum and I need help with it, if you can take a look at it i would be grateful.

Thanks in advance.

---

### Post by Herman on 2006-08-01
> Of course, the bigger question is WHY Grub nulls the other OS boots on an update; that’s the fundamental part that should be fixed, and from my naive perspective it seems like it should be rather simple.Hello, djlerkl,
There is nothing in the software to be fixed. It is because users are not reading the proper documentation or they can't understand it. That is the cause of the problems. 
When Ubuntu is installed, it automatically detects Windows and all other operating systems, and adds them to the operating systems section at the bottom of /grub/boot/menu.lst. Then, new users who are a bit computer savy, who prefer to use Windows as their primary operating system wish to have Windows booted by default. There is a proper way to do that and several wrong ways.
The proper way is described in the [GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html"), which is free and available to anyone. However, it is rather 'dry' reading and a little hard to understand for those who are not familiar with Linux terms. 
Many people turn to other Windows users for help, and are given the advice of cutting the Windows entry from below the divider which is there at the bottom of the automagic kernels list and pasting Windows above Ubuntu at the top of the automagic kernels list. 
This makes Windows the first entry in the list, number 0 in Grub terms, which Grub has been set to boot by defualt.
Placing WIndows first in the automagic kernels list will work for a little while, giving the new user the impression the advice he or she has received was correct, and after a while they forget they have performed this action. Then some time later, a new kernel is installed during an update, and the automagic kernels list does what it is supposed to do and updates itself. Since Windows does not belong in the automagic kernels list, it gets deleted of course. The Windows user is left puzzled and unhappy.
The correct way to edit the menu.lst, explained in the Grub manual, is to replace the number 0, after the word 'default', in menu.lst with the number that represents the Windows entry, perhaps number 4.
If new users read the manual instead of believing other new users and taking shortcuts, everything would be fine.
The automagic kernels list is a great feature of Grub, which means a new Linux kernel given in an update will be automatically added to the menu.lst without the need for the user to manually edit the list. 


> But the secondary issue here (and the more basic one, as far as the issue of making the Linux-based world more attractive as an alternative) is that the issue only arises because the Ubuntu system seems intended either for the very sophisticated new user, or for those who are already part of the Linux world. For the many people like me, who support the Linux world in principle and would also like to support it in practice, its details like these that could too easily make the switch seem impossible, or at least not worth the bother. I would like to see some pre-emptive instructions about the most commonly occurring issues for upgrades and new installs; these could even include links to the solutions already posted. In my case, if the upgrade instructions had told me that an update would reconfigure my dual-boot file and told me in advance how to fix it, I’d have been very grateful.
 I am a new user too, in the same position as yourself, and I have found many of the manuals and instructions difficult to read and understand. I have tried to do something about it. I have made a website for people who are installing Ubuntu for the first time. It is mainly dedicated now to the 'Alternate' Install CD and its use. I have also spent some time reading the manuals and testing things out on my own computers here at home. I have a page that goes into quite a lot of detail explaining how to use Grub, and edit menu.lst. To see an illustrated example of the correct method plus an unorthodox method  for setting the default operating system that will keep keep working,[I] [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")
[/I]I also have another page on how to use GAG Boot Loader if you have trouble with Grub. (To boot windows if it's entry gets deleted or something like that). [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

Here's a link to my index page in case you want it.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Another Ubuntu Forums member ,aysiu, has a great website with lots more information for new users switching from Windows. It has about everything you could want to know explained in an easy to read style.
[COLOR=#3333ff][http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)[/COLOR]
aysiu's website has a page about installing with the new 'Desktop' Live/Install CD. [http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

There is also a great book available in some parts of the world about Ubuntu. It has not yet reached my corner of the globe, but I will buy a copy as soon as I see one for sale somewhere. [http://www.phptr.com/bookstore/product.asp?isbn=0132435942&rl=1](http://www.phptr.com/bookstore/product.asp?isbn=0132435942&rl=1)

There is also the [Official Ubuntu Wiki]("https://wiki.ubuntu.com/"), and lots of other great new [Documentation]("http://help.ubuntu.com/") .            |            [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

Also, of course, don't overlook your help menu, there have been a lot of great improvements made there since the last release.

Lastly, but not least, there is (of course) the Ubuntu Web Forums. I'm sure all advice given here is given with the best of intentions, but please confirm by reading manuals whenever you can. Humans with the best of intentions do make mistakes, most often when we think we know it all. At least that's what keeps happening to me. :D
Regards, Herman :D

---

### Post by Tomosaur on 2006-08-01
It is a real problem, and one which nobody has a real satisfactory fix for. The bottom line in this whole thing is that Ubuntu is advertised as a choice. We get to CHOOSE what we want to do, when we want to do it. I've had problems with Grub before, but I still prefer it to LILO. When something updates, grub changes without my knowledge, until I reboot next (mostly it just adds 2 more menu options, 1 for the new kernel, 1 for a safe mode). Sure, there are ways to fix this, but how the hell is a new user supposed to figure this all out? Do you really expect a brand new linux user to sit around for hours trying to figure out just what grub is playing at? The real problem is this:

Ubuntu installs, user restarts. Grub is all nice and lovely.
Ubuntu updates. New kernel gets added, grub menu changes in the background.
User restarts at some point, grub's different. 'What did I break?' is the first though going through their head, I guarantee it. 

Ubuntu needs a GUI Grub editor. Scripts just aren't going to cut it, no matter how 'useful' they are for a given situation.

---

### Post by Metacarpal on 2006-08-01
> **Tomosaur said:**
> Ubuntu needs a GUI Grub editor. Scripts just aren't going to cut it, no matter how 'useful' they are for a given situation.

Now that sounds like a lovely idea.  As I'm not dual-booting (nothing I need which I can't find in Ubuntu), I've not had the problems described in this post.  However, I do see how having a graphical boot-editor interface would be very useful.  Potentially catastrophic if the wrong changes are made (the same is true for most of the GUI administration tools in the Windows Control Panel, too, of course), but ultimately useful.

---

### Post by Tomosaur on 2006-08-01
don't use, old

---

### Post by teasum on 2006-08-01
There are a couple gui tools for managing GRUB, but they're not included in Ubuntu yet (although perhaps this is on the table for the next release, Edgy Eft?).  One is grubconf: 
[http://grubconf.sourceforge.net/](http://grubconf.sourceforge.net/).  However, this has been discontinued and their website now recommends Gnome System Tools: [http://www.gnome.org/projects/gst/index.html](http://www.gnome.org/projects/gst/index.html).  

I haven't used either of these, however, so I can't vouch for them first-hand.  However,, gui configuration tools are being developed for a variety of purposes.  For instance, there is now a touchpad config tool (gsynaptics) available in Edgy, and hopefully a gui tool of one sort or another for GRUB will be integrated into a future Ubuntu release.

---

### Post by Tomosaur on 2006-08-02
EDIT: don't use this, old

---

