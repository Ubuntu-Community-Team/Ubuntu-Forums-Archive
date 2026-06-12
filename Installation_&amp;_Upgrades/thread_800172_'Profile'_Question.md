---
title: "'Profile' Question"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by smith_fan on 2008-05-19
I have an installation of Ubuntu 7.10 on a laptop which my ignorant messings screwed-up MAJORLY.  My linux-using brother-in-law saved my bacon and got a GUI back by installing a bunch of modules and then re-configuring X.  My problem with it is that I can not update to Hardy Heron.  Also, OOo launches with a '2.3.0' splash screen so I know that it's not just the OS that won't update, but everything, apparently.

I believe that just using an 8.04 disc to install once I've got all the partitioning figured-out and finished is probably the easiest sure way to eliminate the various behavioral abnormalities and get a “default” installation back.  If I just paste copies of the current contents of my Home folder into that same location in the Hardy Heron installation, will all of my customizations and changed settings be transferred?

I've got Acronis Disk Director Suite 10 and True Image 11 and I'm trying to get XP Pro and Ubuntu to happily boot alongside the Vista Home Basic joke that this thing came with.  And I'd really like to accomplish that without a catastrophic loss of data.

Thanks for your help!,
~D~

---

### Post by EXCiD3 on 2008-05-20
If you backup your /home and paste them into your new /home after a fresh install your settings will be saved. You will need to reinstall your software but the settings for anything you had will still be there. I would recommend doing a fresh install since 7.10 is already kind of messed up and i can almost guarantee you upgrading will do even more harm as almost everyone who has upgraded has experienced loss of wifi and/or graphics drivers, not to mention many other problems. Its always safer to go with a fresh install. If you do a fresh install, create a separate partition for /home so you dont have to back it up every time you reinstall, you can just mount the partition as /home instead! :) Its so much easier that way.

Info on triple booting vista, xp and linux: [http://lifehacker.com/software/ubuntu/hack-attack-how-to-triple+boot-windows-xp-vista-and-ubuntu-193474.php](http://lifehacker.com/software/ubuntu/hack-attack-how-to-triple+boot-windows-xp-vista-and-ubuntu-193474.php)

---

### Post by smith_fan on 2008-05-20
EXCiD3,

That is just fantastic, THANK YOU!!!  I have already tried to update it—it just doesn't do it right.  I've just screwed things up bad enough that I believe a fresh install is probably the easiest path to normalcy.  It's great to hear that saving things is as simple as moving a folder; oh what Microsoft could learn...!

Yeah, I had planned on doing a dedicated Home partition the next time around.  I'm just not sure how big it should be.  This Toshiba has an 80 gig drive (well, 74.53 GB).  The pre-installed Vista and it's data are currently using 32.83 GB of it.  I want to install and use XP as my primary Win-32 platform.  But I'd like to use Windows as little as possible and I don't want to run myself out of room.  Do you have any thoughts on this?

Also, I get a 'PCI BIOS Bug [#89435000]' message upon booting Ubuntu and until I went through several gyrations involving ALSA drivers this thing had no sound.  I'm sure it'll do the same thing with a fresh install of Hardy.  Or will it?  Your thoughts would be appreciated.

Thanks again!,
~D~

---

### Post by EXCiD3 on 2008-05-20
If a post was helpful you can click the Thanks button (blue medal) so that other users can find the answers to their questions easier. ;)

If you have sata hard drives like mine does you will need to make a custom XP disc slipstreaming the sata drivers in it so that it can detect them, otherwise you will need to put IDE compatibility mode on in the BIOS. Since Vista is taking up so much room your are somewhat limited in what you can do. XP is going to require 10gb or so and you might want it to have some more room, maybe 20gb. A 10gb partition is plenty for Ubuntu (mine is only using 4gb so you could do even less), and then you can partition off the rest of the free space for /home.

I'm not sure about the bios bug, i know that mine used to display a couple. You can try updating the bios in Windows with the tools from the manufacturers website. That might help a bit.

Hardy has changed audio from using ALSA mainly to a new Pulse Audio sound system. It might work just fine out of the box, just depends on your hardware. Did you have trouble before or after trying the upgrade?

---

### Post by smith_fan on 2008-05-21
It's the weirdest thing—some sources (mainly the Toshiba *'Documentation'*) indicate that a SATA lives in there, but yet diagnostics like SiS Sandra and Everest Home Edition just show a plain ole IDE.  [SIZE="1"]I can't remember what Device Manager thinks it is.[/SIZE]  Thanks for the heads-up, though!  I wasn't able to locate any SATA drivers when I made my XP disc.  I should probably do another one now that SP3 is officially out, just in case there are differences between Release Candidate 1 and the full-fledged Service Pack 3...

I believe that quite a bit of that space Vista has used is just garbage and wasted space and I want to re-do Vista as well, so I'll probably just use the MS Easy Transfer Wizard to temporarily store it on an NAS box.  Then I can just format the whole drive and put XP where Vista is right now.  Is your /Home partition at the end of your disc?  Thanks for giving me an idea of how big it should be, I really had no clue.  How much and where did you put your swap space?  I was thinking of giving it a 2 GB partition since this machine has 1 GB of RAM and I've seen it recommended to be sized at twice the host's memory.  But I dunno where it should be located, ideally.:confused:

No, I had no sound right after the initial installation.  My upgrade snafu didn't play into that, at all.  Some helpful folks on the forums managed to help me get it working.  I'm glad to hear that they changed the audio portion.  Maybe it actually *will* work outta the box... :) I've already updated to the latest BIOS I could find.  I guess that's really not a major hindrance, though, if I do still get that BIOS bug message.

Thanks, so much, for helping me get through this, man!  I feel **very** close to being able to tell Microsoft where they can shove it...!:guitar:

~D~

---

### Post by EXCiD3 on 2008-05-21
Don't get the tech support line people pissed off at you when you call them to tell them that! The poor guys had to get a job somewhere...im sure thats not their dream job, they would rather work as tech support for a linux company but they couldnt compete with ubuntu forums ;)

I know that my laptop has sata drives yet the controller can mimic them being IDE drives so that you can install XP or an older OS on it without needing SATA drivers. I have to turn on IDE mode and that reduces performance. If you do have a sata drive, check this out for slipstreaming into xp: [http://paparadit.blogspot.com/2007/06/installing-sata-hard-drive-with-windows.html](http://paparadit.blogspot.com/2007/06/installing-sata-hard-drive-with-windows.html)

SpaceMonger is a great tool for Windows that shows the files/folders that are taking up lots of space on your Win installation. You probably will have a pagefile and a hibernate file that are taking up at least 1gb of space a piece. I think you can safely delete the hibernate file, but im not sure about the pagefile, its basically the "swap" for windows. Just google about deleting them and see what you get. 

Here is my hard drive configuration:
sda:
60gb vista
rest of drive (like 13gb) Ubuntu

sdb:
4gb swap
70gb /home for ubuntu

I have 2gb of ram but my swap partition is NEVER used no matter what. I have compiz running and gnome and even allocating 512mb of ram for a virtual machine never goes over 768mb of ram, so you may consider not even using a swap partition, unless you want to use hibernate. Hibernate basically saves your ram to the swap partition, therefore you need it to be AT LEAST the size of ram and possibly twice the size just to be safe. It doesnt really matter what order you put the partitions in.

If the bios bug isnt causing any problems (that you know of) then i wouldn't worry about it too much. Hopefully your audio will work fine in Hardy, if not im sure just a bit of tweaking will get it working just like it did before.

---

### Post by smith_fan on 2008-05-22
You guys certainly are tough to beat!;)  No--I've had too many tech support jobs myself to want to give 'em any grief unnecessarily.

I will hafta keep at it to see whether or not it is SATA.  Thanks for relaying the info about yours—I'd not ever heard of that mode.  I'll check it out.  I also hadn't ever heard of SpaceMonger before and am eager to try it, too.

So, I take it that you are triple-booting, too, sir? (my apologies if you're female).

Thanks for the information!,
~D~

---

### Post by EXCiD3 on 2008-05-22
I'm only dual booting at the moment. Ive had triple and quad boots before though! ;)

I guess if you really wanted to see if your drives were sata you could open up the hard drive cover and unplug the drive to see what type of connection it is. If you have documentation on your laptop it might say somewhere what type the drive is.

I'm male, haha. I'm going to be going into sophmore year at college as a computer science major. :)

---

### Post by smith_fan on 2008-05-23
Knowing my mechanical aptitude, I'd probably break the damn case!#-o lol It looks like I'll be joining more forums and asking around.  Actually, I just looked at the spec sheet per your idea, and it does say “80 GB (5400 RPM) Serial ATA hard disk drive.”  Now I hafta wrangle an elusive driver.  Guess I could also start downloading SP3 for my slipstreamed disc.

Can I ask how you arranged and configured your partitions, bud?  You probably do things worlds differently than a guy with no formal training.  I'm sure you probably do things the smart way.  I wish that I could always claim that!  Do you use imaging software?  I've got a ton of questions that you could most-likely answer.  But they don't really specifically relate to Ubuntu.

~D~

---

### Post by EXCiD3 on 2008-05-23
I have always used GParted for arranging and creating my partitions straight from the LiveCD. I  experimented a lot without using a /home partition and ultimately came to realize after installing Ubuntu for the 40th time that keeping my settings from the previous installs was what i needed to do instead of backing up my data to usb drives.

If you want to talk about computer stuff or whatever just hit me up on IM or email! I'd love to chat. Its the field im going into and just talking to people about it helps me learn. I started programming back in 7th grade and have been hooked on it as my hobby ever since! :D If i dont get back to you right away its cuz im home for the summer on my parents' dialup... :(

---

### Post by smith_fan on 2008-05-27
Hey, thanks for being so cool about it and accommodating, man!!:)  I really appreciate it!:-D  I'm really not sure just where do I start...

I think that this is probably much further than most people go, but I'd like to install XP into it's own partition and then programs also into a dedicated partition.  That way, when I screw something up messing with things I really don't understand, I can just re-install Windows w/o losing all my info and settings.  Do you use roaming profiles, sir?  I think that is what I need to start doing.  Am I on the right track there?  This idea of linux and it's 'Home' folder seems like an absolute dream when compared to MS's ridiculous complexities!  I'm still not sure I believe it's that simple.

You said the “D-word!”:eek::biggrin:

---

### Post by EXCiD3 on 2008-05-27
No problem, i just am an avid linux user. :D

You sure could install XP, have a separate partition for software, linux, and a separate /home partition. The only thing you will need to know is that every time you install windows after linux windows will overwrite the linux boot loader. Just follow this thread to fix that in under 5 mins ;) ubuntuforums.org/showthread.php?t=224351

You know what you use XP alot of the user settings are stored in the registry and user folders? Well for linux the /home is essentially all of that combined. When you reinstall linux all you have to do is reinstall the software and your settings will automatically be back!

---

### Post by smith_fan on 2008-05-27
I'd sure like to become one of those!  Dunno that I'm cut out to become one, though...  I think I may have just lost too many brain cells to really ever become an avid linux user.  All hope is not lost, however.  Fortunately, I'm quite stubborn and hard to (virtually impossible to) discourage once I've made my mind up to do something.;):D  Maybe that means I'm just destined for a lifetime of frustration. (?) lmao

I hate to hafta ask you for it in a forum, but I've not been able to locate your email address.  And I don't have Pidgin set up yet.  I don't want to ramble on and on in a forum about Ubuntu when it's not specifically-related to Ubuntu.  Got any ideas, man?

Thanks again!,
~D~

---

### Post by EXCiD3 on 2008-05-27
Haha oh i think you could become a good linux user, just give yourself some time, and try lots of new things!

Contact info can be found for each user by clicking their name and clicking View Public Profile and in there somewhere is all the contact info, but ill post it here for you too:

Email: [EMAIL="excid3@gmail.com"]excid3@gmail.com[/EMAIL]
 AIM: [mr20oman]("aim:goim?screenname=mr20oman")
 Yahoo: [mr20oman]("ymsgr:sendIM?mr20oman")
 MSN: [theonemro@hotmail.com]("msnim:chat?contact=theonemro@hotmail.com")
 GTalk: [email]theonemro@gmail.com[/email]
Skype: [excid3]("skype:excid3?call")


I don't usually get on skype anymore since ive got dialup at home, but every time i get online i sign into IM on pidgin.

---

### Post by smith_fan on 2008-05-28
Oh my gosh!:oops:  I can't believe I didn't try that--how embarrassing!:rolleyes::oops:

With _**[SIZE="5"]a lot[/SIZE]**_ of help from folks like you;), I shall free myself from those Redmond devils!:D

Be expecting an email from Yahoo, k?

Thanks,
~D~

---

