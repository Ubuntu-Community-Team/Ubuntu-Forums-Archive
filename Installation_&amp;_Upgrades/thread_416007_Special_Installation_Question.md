---
title: "Special Installation Question"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Codename Z on 2007-04-20
Hey, so I have an Ubuntu install/bootcd sitting in the cd drive of my other computer. This is the first time I've attempted installing an OS. First, let me explain why I am doing this. I got hacked recently, and so my computer is completely shut down. I was running Windows NT, but unfortunately, I cannot read Chinese well enough to reformat it-my friend recommended NT, so I bought and he installed for me. Well, I'm tired of Windows, anyway. I decided to try linux. Ubuntu was my first choice, as being on a tech forum, I had heard good things about it. However, it seems I cannot install it. I ran the memory test and I passed. However, when I try to start/install.. it goes to booting kernel then gives me a black screen. I tried waiting for 15 minutes, to no avail. I passed the check cd for corruption option, or whatever it was called. One time, I was downstairs and when I went back up to my room it was already back on the home menu. Today, it gave me a black screen that would not go away. I have a 5-7 year old computer, and currently do not have enough money to purchase a new one. I am not allowed to use this, save for homework and fixing my computer. I have 256 RAM, but unfortuntately, due to Windows I only have 1.5 Gigs left (8 gigs total). How can I erase windows?

---

### Post by Codename Z on 2007-04-20
bump?

---

### Post by DarkStarAeon on 2007-04-20
I had an HP that came with Windows pre-loaded, when I tried to install Ubuntu for the first time it didn't work, had similar problems to what you are describing. Even if I reformatted the hard drive, still got the black screen that never died.
So, after looking into it further I found out that no matter what I did, I couldn't remove the pre-loaded files completely, even if it said that the format was wiped clean, deep down, there was still something there, and it prevented me from loading any distro of Linux.

So, I tried installing PC-BSD, which uses a completely different file system/structure than Linux or Windows and it installed just fine.

I bought a second hard drive and installed Ubuntu with no issues what so ever.

I edited my GRUB menu in Ubuntu and now I dual boot Ubuntu and PC-BSD.

So basically, I think you need a new hard drive.

I could be wrong, but since that experience I have met many others who had to do the same thing, so I'm guessing that is the problem. Someone else might have another idea for you.

---

### Post by Codename Z on 2007-04-20
will that kill windows? because that's what i need. i need an OS and windows Gone. i can't buy a second drive either, at the moment. would i need to install DSL (damnsmall linux) and then ubuntu? (this is my first time trying linux)

---

### Post by DarkStarAeon on 2007-04-20
Reformatting the drive WILL kill Windows, but, it leaves behind files that make it tough to install some distributions of Linux.

So, if you can't afford a new hard drive (believe me I understand), and you can't get any version of Linux running, then I would suggest trying PC-BSD. The install is very easy and it will reformat the drive and remove Windows, and most any issue you might have is easily fixable. They have a support forum that is top notch and the people are very helpful. I would check the hardware compatibility list on their site before you try to install, just be sure, but you can also ask on their forums if your hardware is compatible. The hardware compatibility list is not extensive, my computer hardware isn't on their, but all my stuff works.

If this is your first time trying anything non-Windows, you might actually find the transition to PC-BSD easier. It has a slightly similar interface, and you install programs in a similar way. They have a website where you can download all programs available for PC-BSD and once they are on your desktop you just click the file and it runs an installer, then the programs are ready to use. Similar to exe's on Windows.

I prefer Ubuntu, but PC-BSD is very cool, and I use it a lot. (daily)

By the way, if you want a super secure computer, PC-BSD is one of the best. No viruses exist for it.

**NOTE:** PC-BSD 1.3 currently does not support wireless, that is coming in version 1.4 this year. Scanning too. Also, right now it only uses Flash 7 but Adobe just agreed to make a Flash 9 version for PC-BSD.

If you really want to use Ubuntu now, and I don't blame you, maybe wait and see if anyone else answers your post who might know more than I do. But PC-BSD could be a solution for you.

---

### Post by Codename Z on 2007-04-20
"Reformatting the drive WILL kill Windows, but, it leaves behind files that make it tough to install some distributions of Linux."

what kind of files? i considered using [killdisk]("http://www.killdisk.com/") but that seems kinda dodgy. Also, my computer is uh.. I guess you can say "customized". We had two pieces of crap just lying around and we arranged the best pieces ^^;;. I do have wirless internet though.

---

### Post by DarkStarAeon on 2007-04-20
I don't know what they call them, it's just something that Microsoft and companies like HP, Dell, etc. have done that sometimes happens. When I explained my problem to a tech in a local computer shop he knew immediately what I was saying and told me to try PC-BSD. I did, and I am glad I did.
Then I bought that second drive and installed Ubuntu.

I'm not familiar with killdisk, but if it seems dodgy, then it probably is. lol

lol Customized doesn't really matter, as long as the individual pieces of hardware are supported. And if your hardware is older that is actually better, means more likely that your stuff is supported.

Yeah, like I said, Wireless Internet is not yet supported in PC-BSD, but it will be later this year if you can wait. I had wireless and went back to a cable because it's just plain faster, and slightly more secure. 

just go to [http://www.pcbsd.org](http://www.pcbsd.org) and take a look, you can always sign up for the forums and they can help you out before you try installing. My install went smooth as can be, fast too. Once it was installed and I logged in, I had a couple issues that were easily fixed in minutes by help from the people on the forums.

---

### Post by Codename Z on 2007-04-20
Heh. I have no idea what I have installed. My CD Drives are newer and my wireless card was practically brand new. I think everything else is really old.. my floppy drive still has one of those big floppy disk slots.. you know when they were actually floppy... the small one was just coming out XD Cd drives didn't really exist back then.

---

### Post by DarkStarAeon on 2007-04-20
I see...

CD Drives aren't usually a problem.

Wireless doesn't matter since it doesn't work yet, lol

WOW, ok, that's a really really old floppy drive. yikes! Do you even use it? A flash thumb drive would hold more.

Hmm, if you have Windows now, you can always check the hardware profiles and see what's installed.

If you have nothing to lose, all your data backed up, I'd just try PC-BSD. But I'd also have some other distros on hand to try in case that doesn't work.

Damn Small or Puppy Linux may work too, I'd get the ISO's and burn them to disc to have on stand by.

Worse case, nothing works, just reinstall Windows.

---

### Post by Codename Z on 2007-04-20
I can't login to windows. Hacker locked me out. You can only use "netlogon". My jump is only 64 MB i think. none of my data is backed up. i don't really need much of it. a lot was creative works... so i can make more anyhow.

---

### Post by Codename Z on 2007-04-20
bump

---

### Post by DarkStarAeon on 2007-04-20
> **Codename Z said:**
> I can't login to windows. Hacker locked me out. You can only use "netlogon". My jump is only 64 MB i think. none of my data is backed up. i don't really need much of it. a lot was creative works... so i can make more anyhow.

Ah, that's right, sorry I forgot that part.

Well, if you've got nothing to lose, give any distro a try and see what works.

[http://www.distrowatch.com](http://www.distrowatch.com) can give you links to the websites of any linux or bsd distro available.

---

