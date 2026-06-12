---
title: "Can not mount dev loop0..."
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by quethefux on 2011-01-17
Hello!

As  you can probably tell, I'm a noob to Ubuntu! I hope I'm not being stupid and nooby for asking this, but I think I'm making a silly mistake! The trouble I'm having is that when I load a bootable USB/CD of 64bit 10.10, I always get an error that looks a little like:

"(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error.

Can not mount /dev/loop0 (cdrom/casperfilesystem.squashfs) on //filesystem.squashfs."

I've done some googling and I've noticed people have had the same problem. They say the alternate downloads could be the problem, or the CD, and that I should use the UNetbootin application.

I guess I should start with describing my build:

Custom built
Core i7 920 @ 2.66ghz
Caviar Green 1TB HDD (I know, don't laugh)
ASUS P6T SE mobo
GTS 250 1GB
8gb DDR3 1333mhz
Dual monitor setup
uh, think that's about it. (I ran x64 M$ Pro before I wiped my HDD, if that's at all relevant.)

I've tried:
1. Going to the DL page, DLing 64bit 10.10, and mounting the image to create a bootable CD (by the procedure offered on the DL page).
2. Using Unetbootin to create a bootable USB (this I did multiple tmes, with different versions: 10.10 64bit desktop, 10.04 64 bit desktop, and I'm about to try another DL except I forgot which one I'm using, but I'll find out in a bit :P).

I'm not sure if it's that my hardware is just flat-out incompatible, or what? That would suck SO hard. (I was snooping around the hardware compatibility section and didn't find it very helpful--I'm a huge hardware freak, and still found it difficult to navigate... I think the list is a little lacking, imo!)

And, yes, I did change the boot priority depending on where I wanted to boot from--first thing I did! :p

Just to clarify, I do see the Ubuntu splash screen, and then after a little bit of waiting, I get that jankity error. :( Any insight would be helpful!

Thanks!

PS I'd really hate to go back to M$ without even getting to try Ubuntu. PLX HALP! xD

---

### Post by Rubi1200 on 2011-01-17
Hi and welcome to the forums :)

Start by checking the integrity of the iso before burning:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by quethefux on 2011-01-17
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Start by checking the integrity of the iso before burning:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Thanks!
Yeah, I saw this, too. I'll post my results once I've done it.

...The reason I didn't wanna do this earlier was because it looks like a lot of info, and I'm very intimidated of it all. =p

---

### Post by quethefux on 2011-01-17
Okay, so I've found out that the Check Sums are different.

This means that the iso is corrupted, right?
How can I fix this? Another DL?

I've downloaded it a few times, so it makes me wonder why it happens repeatedly, with both 64bit versions of 10.10 and 10.04. Am I doing something wrong?

---

### Post by Rubi1200 on 2011-01-17
If the checksums don't match then, yes, this is the likely cause of the errors.

I am not sure what to tell you; perhaps try downloading from another mirror?

---

### Post by quethefux on 2011-01-17
Hm! It seems it is. I guess I'll have to give the alternate downloads another shot, because doing it from the drop-down list is not working for me.

Do you suppose other sites might have the downloads? I'd feel more comfortable doing it from the official Ubuntu site, but if the check sums aren't matching up on both the first DL page and the alternate DL page, I'll have to go elsewhere.

...Or order a CD. Except I REALLY don't want to do that. :(

And, of course, thanks so much for your help!

---

### Post by Rubi1200 on 2011-01-17
I suppose you could try one of the torrent downloads from the official site.
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)

---

### Post by quethefux on 2011-01-17
> **Rubi1200 said:**
> I suppose you could try one of the torrent downloads from the official site.
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)

Yeah, I've tried the torrent DLs, all applicable versions at least twice. I never get a matching checksum.
I also tried from linuxtracker.org. No luck. Gonna try on a dif comp. I don't see what difference it'll make, but it's worth a shot.

---

### Post by Rubi1200 on 2011-01-17
Yes, definitely a bit odd. Usually if the checksums don't match the first time downloading again resolves it.

---

### Post by quethefux on 2011-01-17
And this is unrelated, so I hope it's okay to ask, but I just wanted to know if going for 10.04 is a good choice, as opposed to 10.10. I love getting the latest and greatest, but the longevity of 10.10 pales in comparison to 10.04, and I've heard that it's also more buggy.
I have no experience with either, and though I'm sure there are a lot of factors involved in making this decision, which should I go for?
I'm just trying to get a matching checksum, but after at LEAST 10 downloads from three different sources, I'm considering just buying a CD. So it made me think a little... 10.10 or 10.04?

EDIT: I'll keep working on the checksum. It's weird that I've tried multiple downloads on multiple computers from multiple sources and had no luck. I have to wonder if I'm doing something wrong...

---

### Post by Rubi1200 on 2011-01-17
It's really a personal choice and you will hear a 100 different viewpoints on this one.

Here is mine:
to be honest, there is not a huge difference between the 2 versions; a few packages removed, a few updated/upgraded, some minor GUI changes etc.

If you prefer stability, go for 10.04. 

I have 10.04 as my main stable working environment and am very pleased with it.

---

### Post by quethefux on 2011-01-17
I see, I see. Yeah, I was leaning towards 10.04, anyway.
Thanks again.

---

### Post by jdieter on 2011-01-18
downloaded 3 times. burned on 6 different cd's, 1 dvd and every single freaking one starts running, gives the menu, then after choosing install, you get the cannot mount dev loop0 squash ... CRAP!!! I've downloaded burned and installed ubuntu a hundred times before! this has been 6 freaking days!!!! WHAT IS THE FIX!!!

---

### Post by jdieter on 2011-01-18
md5sums match. tried two different cd drives. one dvd, one cd. what the heck is going on?

---

### Post by quethefux on 2011-01-18
I have NO idea. I'm not getting any matching sums, no lie. DL after DL after DL, on different comps, from different places, from the main site... Not a single match.

I just gave up and am now wrestling with the persistent thoughts of purchasing a disc.
I'm seriously annoyed with M$ and feel like there are so few options out there. I can't say I'm not a lil disappointed with all this!

And I never even get far enough to reach the main menu, nor am I given the option to select anything. It just loads splash screen and gives me that jank error.

---

