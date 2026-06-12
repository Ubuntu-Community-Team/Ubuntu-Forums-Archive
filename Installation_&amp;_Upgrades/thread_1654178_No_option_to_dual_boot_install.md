---
title: "No option to dual boot install"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by aly625 on 2010-12-28
Alright, so first of all, I'm pretty new at this, so go easy on me. I want to install Ubuntu alongside my Windows 7, which I upgraded from Windows Vista pretty recently. I managed to get Ubuntu onto a USB drive and am able to boot it up and run it. When I try to install, though, I only see the options to erase everything and start over with Ubuntu (no.) and the option to partition stuff (which might be what I should end up choosing, but I wouldn't know what I was doing and would probably end up erasing something). But there is no option to install alongside current operating system, as the website says there should be.

From browsing this forum a little bit and going into the terminal in Ubuntu and playing around I am pretty positive that my problem is that I have no free partition space; it looks like I have 5 (which from what I've read, there is a maximum of 4, so I have no idea how the heck that happened). I took a picture of the output it gave me:
(yes, I know it was silly of me to take a picture, and I'm sorry for the glare, but I hadn't gotten internet yet in Ubuntu and I needed to get the output into Windows so I could post it here...whatever, the point is, here's a picture.)
[http://img.photobucket.com/albums/v686/lurvely_layouts_xanga/IMG_20101227_233438.jpg](http://img.photobucket.com/albums/v686/lurvely_layouts_xanga/IMG_20101227_233438.jpg)

So yeah, I'm pretty sure that's my problem, I just have no idea how to fix it. Any help would be greatly appreciated!
Also, if it helps, I'm mainly using the C drive although my D drive is being used for Recovery (well, that's what the computer says, at least. I don't know, I've never touched my D drive but there's stuff there so I have no idea if it's essential or important or just Windows being dumb and sticking stuff everywhere.)

Thanks, and let me know if you need any more information!

---

### Post by Quackers on 2010-12-28
From within Windows can you please post a screenshot of your disk management screen? I suspect we will find that your partitions have been changed to dynamic, which is not good news :-(

---

### Post by aly625 on 2010-12-28
Of course! I was actually just looking at that...

[http://img.photobucket.com/albums/v686/lurvely_layouts_xanga/stuff.jpg](http://img.photobucket.com/albums/v686/lurvely_layouts_xanga/stuff.jpg)

Again, unfortunately, no idea what any of that means.

---

### Post by Quackers on 2010-12-28
Well, that's good :-)
Only 4 partitions! All primary. Where did the other one come from in the previous picture?
What is in the unlabelled 250GB partition? It looks like it's empty. Is it an unused data partition?

---

### Post by aly625 on 2010-12-28
I have absolutely no idea where the 5th one came from! And I've been looking around, and I can't find any evidence that the 2.5 GB one has anything on it. When I right click on it, the only option I'm given is to "Delete Volume". Since there doesn't seem to be anything on it, my instinct would be that deleting it would be okay, but I just want to check...

So if deleting that one is the correct option, would that open up a partition for me to use for Ubuntu? Although I know that at least 2.6 GB disk space is recommended, and that's only 2.5, so is there any way to maybe take a bit from the D or the C drive and use it for that empty space? There are options on the C and D and the other random one to "shrink volume", which I assume means that if I delete the 2.5 one and shrink the volume of the C one by, like, .5 or 1 GB, that there will be a 3 or 3.5 GB size free space that could be used for Ubuntu. Is my logic correct in thinking this?

---

### Post by Quackers on 2010-12-28
oops, I cleaned my glasses. I now see that it's 2.5GB :-)
Yes, if you are happy that the partition is empty you can delete it. It is a strange size though. I have no idea why it would be there.
Anyway, if you delete that partition, then shrink the C: partition you will have some free space for Ubuntu to use. I would give Ubuntu more space myself. 6GB minimum, and don't forget 2 things. You will probably need a swap partition; and secondly you may like Ubuntu and want to extend it :-)

But firstly, I would recommend that you defrag Windows, at least once, and preferrably twice, before shrinking C:. I would also recommend that you boot back into Windows a couple of times after shrinking the C: drive, just to make sure Windows is happy about it.

And one final recommendation. You don't say which version of Ubuntu you intend to install. If it's 10.10, I recommend that you DON'T use the "install alongside" option! This has been known to over-write Windows!!!
I would recommend that you select "specify manually" in the partitioning stage of the installer, and make your own partitions. Scary, I know, but safer!
People here will help, if you need it.

---

### Post by garvinrick4 on 2010-12-28
Quackers take a look at the jpeg link in post 1. His fdisk -l

---

### Post by aly625 on 2010-12-28
> **garvinrick4 said:**
> Quackers take a look at the jpeg link in post 1. His fdisk -l

...?

---

### Post by Quackers on 2010-12-28
> **garvinrick4 said:**
> Quackers take a look at the jpeg link in post 1. His fdisk -l

I did that garvinrick4, but we can't seem to find where that other partition came from. Windows doesn't report a 5th partition and it's existing partitions have not been changed to dynamic, so we are attempting to press on.
It may be that during the deletion and shrinking of the existing partitions will throw up an error. If that happens we will need to address it then. But it's hard to address something that doesn't show up as a problem yet :o

---

### Post by wilee-nilee on 2010-12-28
in a whisper dell data safe.

---

### Post by Rubi1200 on 2010-12-28
@Quackers: ask the OP to run ```
sudo parted -l
``` from the LiveCD before moving ahead with anything.

And, if wilee-nilee is right, this could be a problem!
See here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

---

### Post by Quackers on 2010-12-28
> **wilee-nilee said:**
> in a whisper dell data safe.

aly265, can you wait before proceeding please?

So Dell data safe is on sda5 (which is within sda4 extended)? Is that the 2.5GB partition that appears empty to the OP? Does it normally appear empty?
Can it be deleted without problem?
Thanks for clearing up the extra partition :-)

---

### Post by aly625 on 2010-12-28
I believe I subscribed to the basic, free package of Dell Data Safe when I got my computer, however, I have never actually used it. I have an external hard drive that I use. I just finished defragmenting my disk and JUST deleted the 2.5 GB partition (oops). It told me that it was a partition not created by Windows and was possibly being used by another OS; but since I don't actually have any other OS apart from my live version of Ubuntu I figured that wouldn't be a problem. I will boot into Linux now and try the parted thing; no idea if that still applies since I deleted the extra partition, but I'm thinking that if that was, in fact, something created by Dell Data Safe, it shouldn't cause any problems since I've never used Dell Data Safe?

---

### Post by Quackers on 2010-12-28
> **Rubi1200 said:**
> @Quackers: ask the OP to run ```
sudo parted -l
``` from the LiveCD before moving ahead with anything.

And, if wilee-nilee is right, this could be a problem!
See here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

Thanks Rubi1200, I was aware that it writes to the mbr after every boot. I just don't know whether it's safe to delete it :o Or whether other steps will be necessary

---

### Post by Quackers on 2010-12-28
aly625, it may be better to wait for clarification - even if you have deleted it!

---

### Post by wilee-nilee on 2010-12-28
Here is a link on the data safe it needs to be removed from the computer.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

Carry on you all.:)

Most of the time the dual boot has been done; and removing this as described and resetting the boot works.

---

### Post by Quackers on 2010-12-28
> **wilee-nilee said:**
> Here is a link on the data safe it needs to be removed from the computer.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

Carry on you all.:)

Thanks willee-nillee :-)
So it appears that uninstalling Dell data safe will be ok.
aly625, will you try that from the Control Panel > Programs, please and tell us what happens? Thanks.

---

### Post by aly625 on 2010-12-28
Alright, before I saw the whole wait-for-clarification-thing, I went ahead and went back into Linux and did the parted -l thing. This is what it gave me, if it helps.
[http://img.photobucket.com/albums/v686/lurvely_layouts_xanga/IMG_20101228_010410.jpg](http://img.photobucket.com/albums/v686/lurvely_layouts_xanga/IMG_20101228_010410.jpg)

Then I rebooted back into Windows, don't see any problems yet. Went into my Control Panel to uninstall Dell Data Safe; but it's not there. I subscribed to it (I think, I'm not even 100% sure I subscribed but it's ringing major bells) about 2 years ago, back when I had Windows Vista, before I upgraded to Windows 7 and then later did a clean install of Windows 7. Also searched through all my programs and did a quick scan of things from my start menu; no record of Dell Data Safe anywhere. So I dunno what that's about.

---

### Post by Quackers on 2010-12-28
Hmm, I wonder if it was ever installed? Obviously the partition was there for it, or so it seems.
Your parted -l still refers to an extended partition.
Can you post another screenshot of your disk management screen please? Is there still a 4th partition listed there?

---

### Post by aly625 on 2010-12-28
[http://img.photobucket.com/albums/v686/lurvely_layouts_xanga/stuff2.jpg](http://img.photobucket.com/albums/v686/lurvely_layouts_xanga/stuff2.jpg)
There you are!

I'm not sure if this is how it works; but the software may have been deleted when I did my clean install of Windows 7 but the partition for it remained. No idea if it works like that, but that might be what happened.

The disk management screen looks fine to me, but y'all know more about this than I do. 

And, by the way, thank you all so much for your help!

---

### Post by Quackers on 2010-12-28
Now I understand some of it.
Your screenshot shows "free space" but I suspect if you right-click on it you will get the option to delete it, as it is certainly an extended partition. You have deleted the partition which lived there, but not the partiton that held the 2.5GB partition. 
I don't understand why Windows just reported it as a primary partition. I would have expected it to report it as an extended, but it didn't. Only Linux reported the extended.
If you delete the green partiton :-) you will then be left with a black line which will be listed as "unallocated space", which is good.
You can then shrink your C: partition, as you have defragged, I believe.

---

### Post by aly625 on 2010-12-28
You're right--that option is there. Clicked it, it warned me that it is an extended partition and that if I delete it it's lost. Just deleted it, and yes I defragged (is it just me, or does that sound dirty?) both my C and my D drives and am going to go ahead and try and shrink my C partition. 

Okay...it's querying volume for available shrink space...okay it said I can shrink up to around 31 GB, I told it to shrink around 7.8 GB, and now, just for fun, I've got this:
[http://img.photobucket.com/albums/v686/lurvely_layouts_xanga/stuff3.jpg](http://img.photobucket.com/albums/v686/lurvely_layouts_xanga/stuff3.jpg)

Look good? Look okay to try the whole Ubuntu thing again? I've been googling and I kind of semi think I might maybe understand the whole manual partition thing, but I wanted to check this first.

---

### Post by abanta11 on 2010-12-28
SO, I currently have this exact same problem- no option to install alongside another OS

I have Win7 Starter on this new netbook and need to install Ubuntu 10.10 netbook addition.

Are you guys saying you can shrink partitions manually with the "Change" button, and then add a new Partition Table with that button? Windows only shows me 2 partitions, also, but Ubuntu shows 4 so I have no idea what the last 2 are used for.

I would gladly install the 10.10 to my D: drive which seems to be SDA2, the 131GB partition. Does a Swap partition have to be created along with the OS partition? Am I completely wrong so far?

This is a life saver, thanks for your help!

---

### Post by Quackers on 2010-12-28
Yes it does sound a bit dodgy - defragging :-)
Your screenshot looks luvverly :-)
Any questions during installation will receive prompt assistance, I'm sure :-)
Good luck!

---

### Post by Quackers on 2010-12-28
abanta11, you would be better off with your own thread. Just copy/paste what you've written into a new post. Can you include a screenshot of your disk management window in Windows please?

---

### Post by wilee-nilee on 2010-12-28
> **abanta11 said:**
> SO, I currently have this exact same problem- no option to install alongside another OS

I have Win7 Starter on this new netbook and need to install Ubuntu 10.10 netbook addition.

Are you guys saying you can shrink partitions manually with the "Change" button, and then add a new Partition Table with that button? Windows only shows me 2 partitions, also, but Ubuntu shows 4 so I have no idea what the last 2 are used for.

I would gladly install the 10.10 to my D: drive which seems to be SDA2, the 131GB partition. Does a Swap partition have to be created along with the OS partition? Am I completely wrong so far?

This is a life saver, thanks for your help!

We will help you but it would be easiest in your own thread. So hit the report button and turn yourself into the mods.:) watch out their real mean, actually they will be glad to make your post into a thread. If you have 4 partitions stop the install so we can look at your set up.

---

### Post by aly625 on 2010-12-28
Have I mentioned that you are all the most wonderful, amazing people in the world?

I installed it without a hitch and it's up and running beautifully! Well, except I can't get internet because the wireless is somehow messed up, but for now all I want to do is play with my beautiful new terminal and be able to write code in vi so I'll worry about that later.

Again, thank you all!

---

### Post by Quackers on 2010-12-28
For my part, you're welcome :-)
I'd also like to thank garvinrick4, wilee-nilee and Rubi1200 for trying to stop me make a fool of myself :-)

By the way, aly265, if Ubuntu booted directly you may want to open a terminal and run ```
sudo update-grub
```
and watch to see whether the Windows Loader is picked up - and try it at some time, to make sure Windows still boots ok.
For your wireless problem try running System > Admin > Additional drivers to see if any graphics or wireless drivers are available for your machine.
You will need to connect via ethernet cable first though :-)

---

### Post by garvinrick4 on 2010-12-28
> **aly625 said:**
> Have I mentioned that you are all the most wonderful, amazing people in the world?

I installed it without a hitch and it's up and running beautifully! Well, except I can't get internet because the wireless is somehow messed up, but for now all I want to do is play with my beautiful new terminal and be able to write code in vi so I'll worry about that later.

Again, thank you all!```
sudo lshw -C network
```
Run that code in a terminal and will tell you your network cards and most likely broadcom
and they have drivers you can install in ubuntu. Make a post about broadcom network card needs driver. You will get quick help. Post the cards also will make it easy.

---

