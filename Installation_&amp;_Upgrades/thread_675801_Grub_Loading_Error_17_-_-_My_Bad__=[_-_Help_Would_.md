---
title: "Grub Loading Error 17 - - My Bad  =[ - Help Would Be Appreciated!"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by push_harder on 2008-01-23
Hi, i installed ubuntu a week ago, and was very impressed with the look and feel of it.

I've recently decided to start burning home made video from my camera and i thought i'd use windows to do this seeing as it's easier.

I have an acer extensa 5220.
Factory, the laptop came with an 80Gig HDD partitioned into 3, one was a hidden partition with acer recovery, One was C: and the other one was a a blank partition ready for storage.

I decided to install ubuntu and format the blank partition, keep windows and the recovery partition.

Everything went fine with a few hardware issues here and there.

Now, seeing as i only have 5 Gig left on C:, NTI won't let me burn big video files because it requires at least 20 Gig of space (stupid)
So i went into vista's HDD management and reformatted the ubuntu installation so that there was Vista, Recovery and the storage partitions left.
I shut down the computer that nit and went to sleep.
I awoke to turn the laptop on and it said GRUB Error 17.

I'm guessing that's because i uninstalled ubuntu the lazy way and didn't change the boot file in windows.

My question is, what do i do from here?

Sorry for the loooooong topic, just yeh :P

Cheers, Matt

---

### Post by jeffus_il on 2008-01-23
Boot from your windows CD, go into the repair mode console and ```
fixmbr
``` (don't remember exactly but it's a command that rewrites the Master Boot Record.

---

### Post by push_harder on 2008-01-23
Ah, trouble is, Acer don't hand out copies of windows with new laptops.
Even though that all PC manufactures are supposed to by law.

I have an XP disk though...

---

### Post by push_harder on 2008-01-23
Oh no, i'm quite worried now.
I try to do the recovery with XP disk and it says setup could not find any disk drives :S

---

### Post by push_harder on 2008-01-23
Please anyone with any ideas at all i would greatly appreciate.
I have very very important work on that drive and windows disk won't even recognise it's there.

I used the ubuntu live cd and had a  look at the drive Vista's on and it had a very bad looking exclamation mark next to it =[

cheers For the help.

---

### Post by Herman on 2008-01-23
:) Hello push_harder,
I have some Acer computers here too and I know what you mean about the lack of a proper Windows installation disc.

If all you did was delete Ubuntu then you should have nothing at all to worry about, there are lots of ways to make your MBR point to your Windows boot loader again, I have a whole list of them right here in this link, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm").

Those have all been tested with Acer computers, some of my MBRs have been wiitten and overwritten so many times I would be rich by now if I had a dollar for each time. As you will see by the rest of my website, I have tested just about every decent boot loader there is. :)
You'll be fine.

Regards, Herman :)

---

### Post by Herman on 2008-01-23
>  I used the ubuntu live cd and had a  look at the drive Vista's on and it had a very bad looking exclamation mark next to it =[Oh, well I don't understand what that could possibly have to do with deleting Ubuntu, but it seems like your NTFS drive needs a file system check then. :)

You'll need a Windows Installation CD to do that. Boot into a [Windows XP 'Recovery Console' method]("http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console") and run CHKDSK c: /F

Here's a link to explain, [http://www.easydos.com/chkdsk.html](http://www.easydos.com/chkdsk.html)

Regards, Herman :)

---

### Post by push_harder on 2008-01-23
Cheers for the reply.
Nice to here from an Aussie.
I didn't mention anythin g about a lack of Disk ?
What i did was, from Vista, i deleted the ubuntu partition.

And when i use my windows disk to recover, it explains that it could not find any hard drives installed :O

I'm quite fuzzled by this, but i'll have a scour through the link you supplied

Thanks mate, Matt. (from vic)

---

### Post by push_harder on 2008-01-23
I had a quick look on the site and can't seem to find the answer.

I get GRUB load error 17 at start up.
I'll try installing ubuntu again and then removeing it the propper way.

Are you from alice springs at all?

Just cause my dad was mates with a guy named herman from alice.

Cheers, Matt

---

### Post by Herman on 2008-01-23
:) Well installing Ubuntu again is the best way to fix error 17.

All those ways of getting the MBR to point to Windows worked for me in WIndows XP, but I don't have Vista, so I can't test them, but I think it's still the same as XP.
>  I didn't mention anythin g about a lack of Disk ? Yes, you did mention you don't have a Windows XP installation CD, but then you said something about using a disc to recover, so I thought you meant you found one from somewhere, (borrowed from a neighbor maybe), or maybe not, did you mean yourAcer 'Recovery' disk? Don't do that, that will wipe everything!

I've never been to Alice, I've been to Darwin and Port MacArthur in the 'Territory' though. I used to drive road trains up there. Now I live about half way between Townsville and Mt Isa.

Regards, Herman :)

---

### Post by push_harder on 2008-01-23
Yes well i'll give it a shot, thanks sooo much for the help mate.

I ment that acer are to tight to give you a disk with a new laptop, but i have an old xp pro disk. and theres a hidden partition with acer's recovery ****.

---

### Post by Herman on 2008-01-23
An old XP Pro disk should still have the same CHKDSK program in it as what you'd need for Vista, but if it's your partition table then I think TestDIsk is the best thing to use, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html"). But it's best to practice a bit with it on an old hard disk first, to get used to it. 

Regards, Herman :)

---

### Post by push_harder on 2008-01-23
Right, so i used TestDisk and it went rather well, i changed Vista to Primary and fixed the boot file.
Now i get error 15.

I'm about to do some reasearch on this error and also try to enter console through XP Installation disk.

Cheers Herman.

---

### Post by push_harder on 2008-01-23
After some reasearch, i found nothing, except people with the same problem.

some of them completly reformatted their HDD and were left with "GRUB_"
Which leads me to belive, maybe GRUB implements iteslf into the BIOS?

Is this possable?

cheers

---

### Post by bwtranch on 2008-01-23
Good day,

You guys would probably like Texas. But, the people talk kinda funny here, too. 

I have an Acer and used to have vista on it. That didn't last long. I have the AMD64 processor. Ubuntu 7.10 has all you really need to get it running. You really don't need vista. There is nothing in the computer world that can't be done in Linux. Absolutely nothing. Windows can never even attempt to equal this OS. Once you get to know it, you realize how limited Windows is. Mail me if you have any questions..

---

### Post by push_harder on 2008-01-23
> **bwtranch said:**
> Good day,

You guys would probably like Texas. But, the people talk kinda funny here, too. 

I have an Acer and used to have vista on it. That didn't last long. I have the AMD64 processor. Ubuntu 7.10 has all you really need to get it running. You really don't need vista. There is nothing in the computer world that can't be done in Linux. Absolutely nothing. Windows can never even attempt to equal this OS. Once you get to know it, you realize how limited Windows is. Mail me if you have any questions..

First off, i dont want this becomming another Windows vs Linux brawl.
Who cares which OS is better, I'm what matters, just like every other computer user matters.
It's anyone's choice what OS they use, and as much as i like ubuntu with the amazing desktop effects and the ability to code things they way you want.

Windows is probably the most stable and well maintained OS there is. and Linux/Mac is right behind it.
Linux just can't provide what i want to do as easy as windows can.

And that's that.
Go take you're bickering elsewhere, because i genuinely need help and you're not helping much.

Reguards, Matt. It's funny, i'm only 16 and i'd say you're around 25?

---

### Post by push_harder on 2008-01-23
Anyone??

---

### Post by jeffus_il on 2008-01-23
You could boot the Ubuntu livecd, open a terminal and reinstall grub, using grub-install and grub can pick up your windows installation, Grub is just another program and as you know can boot windows, you could leave grub permanently, instead of the Windows MBR, with of course no effect on the running OS.

---

### Post by jeffus_il on 2008-01-23
Another easy solution is to download this Windows Vista repair cd iso, specially for people like you who paid for their OS and did not get a cd:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Hows that? Two workable solutions for you!

---

### Post by push_harder on 2008-01-23
That's not a bad idea, could you take a look at the other Thread i just wrote? and tell me what you think?
Problem is, i don't have ubuntu at all anymore, but if it's not neccacery, what commands would i use off the LiveCD?

Cheers mate!

---

### Post by jeffus_il on 2008-01-23
You could open a terminal and run ```
grub-install
``` the parameters depend on your hard disk setup, if you decide to go that way, I will help you, maybe the windows disk will be more attractive to you. ADDED: It will always be a useful tool in your top drawer!

---

### Post by push_harder on 2008-01-23
Thanks mate =]

---

### Post by push_harder on 2008-01-23
I don't quite know what to do.
I type grub-install and get a list of commands that i don't quite underatand
such as this: --root-directory=DIR
So i type, 'grub-install --root-directory VISTA'
And is gives back: More than one install device?

I'm quite fuzzled :S

cheers.

---

### Post by jeffus_il on 2008-01-23
It's usually something like /dev/sda1 or /dev/hda1 depending on the partition

---

### Post by Battie on 2008-01-23
Hello.

I'm reading this quickly at work, so forgive me if I've misunderstood.

You just want to get back into Windows, right?  Have you tried the Super Grub Disk? [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

It has an option to automatically restore GRUB to point to whatever operating system you want.  I'm pretty sure it will let you boot Windows.  You'll end up with the Grub boot loader, but that will work fine and at least you can get to your stuff.

I hope that helps!

---

### Post by jeffus_il on 2008-01-23
Hey!, that's great, I'll burn one for my toolbox, thanks!

---

### Post by Herman on 2008-01-23
push_harder sent me a PM to say he's got it fixed, he's just getting some sleep now. 
Thanks everyone, for all your help.

> Good day,
You guys would probably like Texas. But, the people talk kinda funny here, too.
I have an Acer and used to have vista on it. That didn't last long. I have the AMD64 processor. Ubuntu 7.10 has all you really need to get it running. You really don't need vista. There is nothing in the computer world that can't be done in Linux. Absolutely nothing. Windows can never even attempt to equal this OS. Once you get to know it, you realize how limited Windows is. Mail me if you have any questions.. Hello bwtranch,
I agree with you, I've never been to Texas but I've been to Rolleston. (We have a town called Texas in Queensland). 
Not all of Australia is the same, but around where I live most people wear cowboy hats and listen to country music.  At least with people of my generation. We have our own country music, and American country music is very popular too.
Yes, we do talk funny, I try to pick my words when I'm typing in to Ubuntu Web Forums so that anyone who speaks English can understand what I'm trying to say as clearly as possible.
We all speak 'English' here in Australia, sort of, but quite a few words can be used in such a way as to mean something completely different to another Australian than English speakers from most other countries might expect.
Sometimes that can lead to some humorous situations. :)
I'm originally from Canada, I've lived here since I was a kid, but I know what it's like to travel around and have fun with language differences. :) 
Yes, I think our countries have a lot more in common culturally than differences. 

I agree with you about Ubuntu too. I believe that it's only a matter of time before Linux operating systems become dominant. Things have come a long way just in the past couple of years. Maybe not everybody is ready to switch yet, but it's hard to give up Ubuntu and Linux once people get a taste for it. 

Regards, Herman :)

---

### Post by Harisankar on 2008-07-06
Hello,
My ubuntu got erased when I tried to re-install WinXphome from acer recovery discs. Now it shows same grub loading error 17 and windows or ubuntu both not booting. Please help me to install windows and ubuntu both.
Thanks in advance,
Hari.

> **Herman said:**
> :) Well installing Ubuntu again is the best way to fix error 17.

All those ways of getting the MBR to point to Windows worked for me in WIndows XP, but I don't have Vista, so I can't test them, but I think it's still the same as XP.
 Yes, you did mention you don't have a Windows XP installation CD, but then you said something about using a disc to recover, so I thought you meant you found one from somewhere, (borrowed from a neighbor maybe), or maybe not, did you mean yourAcer 'Recovery' disk? Don't do that, that will wipe everything!

I've never been to Alice, I've been to Darwin and Port MacArthur in the 'Territory' though. I used to drive road trains up there. Now I live about half way between Townsville and Mt Isa.

Regards, Herman :)

---

### Post by Herman on 2008-07-06
```
My ubuntu got erased when I tried to re-install WinXphome from acer recovery discs. Now it shows same grub loading error 17 and windows or ubuntu both not booting. Please help me to install windows and ubuntu both.
```:) Hello Harisankar, 
I know how you feel, the Acer 'Recovery' discs I have with a couple of my computers do that too, they wipe everything else off the hard disk and return it to it's 'factory shipped' state. It's great for the average computer user. I hope you had your data backed up.
I'm surprised it didn't restore your MBR too though.

The easiest thing to do would be to just install the latest Ubuntu next and that will fix everything, the Windows boot included.

Regards, Herman :)

---

