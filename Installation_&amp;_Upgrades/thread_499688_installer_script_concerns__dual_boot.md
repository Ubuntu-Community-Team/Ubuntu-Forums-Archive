---
title: "installer script concerns / dual boot"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by maxwellhouse on 2007-07-12
Hi, 

I am not exactly new to linux, however I am trying to make sure that my installation will go right.  I have the latest ubuntu desktop version on cdrom, and I have a laptop that is currently a dual boot between Fedora and windows.  Sadly, due to media players, licensing, and lawyers, I am forced to keep the windows around so I can play my cbtnuggets cbt (a vendor I highly recommend NOT buying from).  Also I have plenty of data on the windows box and I cannot lose it, priceless stuff like baby pictures etc.  

I want to blow away all of the ext3 partitions and I am eager to get ubuntu since it is, in my mind, a superior distribution than fedora 7.  I started to go through the installer and wipe out all of the ext3, but there is also some kinda tool (forgot the name) which ubuntu's installer has, which detects that you have a windows install on there and wants to help migrate  you to ubuntu.  

Not being a clueless windows-only user, or someone new to the OS scene, I need ubuntu to be a bit less meddly in my business.  :)  I *JUST* need it to just install and blow away the other linux but DO NOT overwrite my windoze for now.  I may have to just dd the whole windows partition and put it on another drive, but then I am not sure if I can get the win2k to boot off of a usb drive (something tells me that might be YAWG yet another windows gotcha).  

When I attempted to go through the install I didn't see a way to tell the installer script to not import your windows stuff.  Even if I find that (check box or whatever), I am not convinced that I won't wind up at the end, with a laptop that has nothing but ubuntu on it.  THAT would be really bad at this point.  

Does anyone have any suggestions on how to handle this?  Ordinarily if I had a problem, I would just reinstall the windoze, but thanks to cbt nuggets' super-restrictive licensing on me, a paying customer, I only have a couple of tries before I have to go back to them and re-pay them yet again for the right to use their software.  Although this is annoying, I want to keep the win2k around long enough to do this cbt which is going to be awhile.  All of this problem is mainly because of restrictive licensing terms, by the way ---not a linux or necessarily even a windows problem per se.    Add one more reason to support open source software to the already long list...  

Any suggestions are appreciated

Thanks

---

### Post by Herman on 2007-07-12
Hello maxwellhouse, :)
> Also I have plenty of data on the windows box and I cannot lose it, priceless stuff like baby pictures etc.   You should back up all your important files to some other media before using any disk partitioning software. You should have all your important data backed up even if you aren't planning to use any disk partitioning software. A good time to do it is right now. A hard disk can just fail out of the blue. If you only have data on a hard disk then really, consider it already gone. You have no data unless you have it backed up on some other media.
> I started to go through the installer and wipe out all of the ext3, but there is also some kinda tool (forgot the name) which ubuntu's installer has, which detects that you have a windows install on there and wants to help migrate you to ubuntu. Not being a clueless windows-only user, or someone new to the OS scene, I need ubuntu to be a bit less meddly in my business.  :)  I *JUST* need it to just install and blow away the other linux but DO NOT overwrite my windoze for now. I wouldn't worry about that too much,  Ubuntu doesn't write to the Windows parttiion, it just might copy some useful files from it, that's all. It saves you doing a little work. My wife's computer has her Acer desktop background like she had in Windows, I forget what else got copied, but anyway it's nothing to lose any sleep over. I would just go ahead and get on with the installation. :)
If you are really concerned about that you could use the 'Alternate CD', but really I wouldn't think that would be necessary.

The main thing is to make sure you have a good backup of all your important files, then you really can't go too far wrong, but I really can't stress that enough!

Regards, Herman :)

---

### Post by maxwellhouse on 2007-07-12
Ok, that is reassuring to know that the ubuntu installer doesn't do anything too weird with the windows data.  I realize that hard drives are mechanical and I have seen many fail so you are right about all of that.    I think that is all the reassurance that I need, I have worked a lot with other distros but am pretty new to the ubuntu utilities.  

Thanks  for the backup suggestions.  I do have many pictures on DVD already.   And the data (documents etc) I can easily move off of there.  However my real gripe (exacerbated by licensing stuff) is that I am unable to reinstall my windoze should anything go slightly wrong.   I have this licensed software which now limits my freedom - I don't own it, despite paying for it.  I will be glad to get fully switched over to ubuntu.  

Regards
Marc

---

### Post by Herman on 2007-07-13
> However my real gripe (exacerbated by licensing stuff) is that I am unable to reinstall my windoze should anything go slightly wrong. I have this licensed software which now limits my freedom - I don't own it, despite paying for it. I will be glad to get fully switched over to ubuntu.:) Well, actually I'm pretty sure if you read all the fine print in the Windows licensing stuff you will see somewhere that you are allowed to re-install Windows alright as long as it's on the same hard disk and in the same computer. 
Your hard disk and ethernet card's MAC number and some other stuff is traceable by analysing the packets your computer sends over the internet when it connects to a website, like for example Microsoft's Windows Update site. Probably they can see even more than that if they want, so they can check up, but as long as you're sticking to the rules you'll be okay. You're allowed to re-install Windows provided you have your own Windows installation disc and whatever ID or registration numbers and that kind of thing. 

I used to re-install Windows all the time when I used it. Mine had a bad problem with some malware that got into my computer via a nice animated Christmas card a few years ago, and an on-line scan detected it after it had been in there for six months. For six months my antivirus had been re-assuring me that my computer was safe as long as I kept paying for their services and kept it up to date and ran their scans often. I had all the best apps, all up to date and paid for, but still this spyware lurked undetected in my computer for six months, capable of turning my computer into a zombie and giving out all my information to whoever wrote the virus. 
I was able to get rid of the malware easliy once I found out about it, but after that I used to spend all my time scanning and updating stuff and re-installing Windows whether it needed it or not. It does Windows a lot of good to be clean- re-installed. The trick is learning how to back up and re-install your data and settings and stuff without putting the bad stuff back into it again. After that I never trusted Windows again, or the "pay-for-us-and-we'll-protect-you" software racketteers. How could they still keep telling me my computer was safe and protected when they allowed a program like that to remain undetected for so long!  :lolflag:


Then when I found Ubuntu I noticed that if I didn't use Windows on the internet anymore all the anti-spyware and anti-whatever scans started coming up clean. That was a couple of years ago now and I haven't looked back. :)

Ubuntu isn't vulnerable to those type of pests, mainly because of Linux file system ownership and permissions and other inbuilt security strategies. 

Oh yeah, I think that migration thing copies your bookmarks from internet explorer in Windows to your new firefox browser in Ubuntu, which is really handy. :)

At first you might still want to boot into Windows to do certain jobs with apps you're used to. I had a hard time giving up 'Paint', but it didn't take long before I learned GIMP instead, and you may have some games in Windows you like. If you don't need to be on the internet for those then you can save Windows for home use and use Ubuntu for the hard work. Ubuntu is more than tough enough to use on the internet without needing outside apps to protect it, and that way your Windows will stay nice and clean.

My wife and I only use Ubuntu now, we have Windows XP but we don't use it anymore, Ubuntu is better for everything we want our computers for. Some people find Linux a steep learning curve but it's well worht the effort. Besides, it's a lot more user friendly now than it was a couple of years ago or even six months ago. It's getting better and better every day thanks to the hard work of programmers and developers around the world, and if you still have trouble there's lots of help here in Ubuntu Web Forums too.   :)

Welcome to Ubuntu,
Regards, Herman :)

---

