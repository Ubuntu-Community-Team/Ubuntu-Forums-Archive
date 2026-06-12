---
title: "Unable to install - Hangs after language choice, very slow..."
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by jaa1180 on 2006-06-13
Installing on Dell Inspirion 1100, 256 MB memory, 1.3Ghz Celeron. (I am doing from memory, not quite sure about CPU speed. It is close)

I currently have XP home installed on the laptop. (I have to because of my camera software)
So I did have Ubuntu 5.10 on the laptop and wiped it clean and put XP with plans to dual boot with 6.06. However, when I input the CD, starts booting.. it is very slow and the resolution is only 640x480... not 1024x768. 
Once on the desktop I start the install. It has taken about 15 minutes to get to this point. 
After about five more minutes, the first screen comes up asking for language selection. The "Forward" button is below the screen so I hit "Enter". It freezes at this point.

I let it set for a few hours... nothing. :-( 
Is there an option for the old text install? :confused: 
I kinda liked it better in this respect.

Any ideas??

---

### Post by jaa1180 on 2006-06-13
Anybody???

---

### Post by The Cosmic Hobo on 2006-06-14
I've had the same problem with installation (Toshiba Satellite A10 Pro laptop, 2GHz Celeron, 25MB DDR RAM, 20GB HD) - though my resolution is fine, it seems to take ages to even get into Gnome, and the install just died after the language choice screen. I had to power down the laptop and reboot it, and tried checking the CD from the Ubuntu menu, but that froze too.
I'm re-downloading the .iso and will thoroughly check it this time - I literally just learned about Md5sums - before burning. If that doesn't work, I'll have to try the alternate CD and see if that works any better.

If it's not simply a bad CD, and the alternate CD's installer doesn't help, I might have to find some more RAM and see if that alleviates the problem.

Can anyone more technical chime in on this and help us out?

**Quick Update:** I've burned a new CD, the Md5 hash is okay, but the CD still hangs when checked. Oh well, I'll see if the install works any better...

---

### Post by mafitzpatrick on 2006-06-14
**jaa1180: **  I have the same laptop setup (is it the Dell special offer one from a year back?)

Short answer is I've got Dapper installed just fine - although I didn't appear to have the display problems that you are reporting.  You are right though that the installation is **very** slow to the point where sometimes it does appear to have hung completely.  If the CD's spinning it aint dead (yet).

My solution was to go and watch tv between clicks.  The installation took over 4hrs, but mostly due to Bargain Hunt.

I also found that sometimes it does not register clicks from the mouse when you click the Next button.  The solution is to click off the Next button before re-clicking to the Next page.

In the languages page specifically you need to click the language for install (i.e. click English even if English is already selected) and then click Next. This had me going for the whole of Scrapheap Challenge.

Good luck! Rest assured it's a lot better installed - I'm a very happy Ubuntu user.

---

### Post by The Cosmic Hobo on 2006-06-14
Well, I finally got the install to work properly, and here's how:
As I said above, I re-downloaded the .iso and checked its Md5sum hash - the [Ubuntu how-to burn page]("https://wiki.ubuntu.com/BurningIsoHowto") links to instructions [here]("http://www.openoffice.org/dev_docs/using_md5sums.html") (written for OpenOffice .iso files, but it still works the same) - note I had to use the second method, digestIT with GUI. It didn't work quite as expected, but by selecting "hash file" from the right-click menu, a number was generated, and I compared it with the appropriate line from the MD5SUMS file by pasting one under the other in Notepad.

Anyhow, if you think your CD might be bad (as I did), that's a good first step. The newly burned CD, which I wrote as slowly as possible (the OEM copy of Nero I was using wouldn't go any slower than 8x), actually seemed to work a little better and was definitely faster, though maybe that's because I was using a decent quality CD, rated for a higher speed.
My first install attempt with this disk also hung (or at least I think it did - as **mafitzpatrick** notes, it could just be very slow, though I'm sure my optical drive actually stopped running). I rebooted and selected "safe mode graphics" from the boot menu, and would you believe it, the install ran just fine! Took an hour to do, but it was faster than previous attempts, and much smoother than I expected.

Unfortunately I'm now at work, where I'm restricted to the not-particularly-good Win95 machine at the sales desk - it's a POS, in more ways than one! ;) - so I can't test my new Ubuntu laptop til I get home tonight. But I hope my experiences can help solve your problem, **jaa1180**!
Good luck!

---

### Post by jaa1180 on 2006-06-14
I know the CD is good, I used it to install on my server.
I have the server and desktop versions of the CDs. 

I noticed the server version is a text install. I am not sure about the differences between the two. 

[QUOTE=mafitzpatrick]In the languages page specifically you need to click the language for install[/QUOTE]
I would like to, but the screen is below what I can see. Literally it is larger that what I can see. And when I hit the Enter button, it hangs....

I let it sit for a couple of hours and it did not go past this screen. 
I think Ubuntu has forgotten about the little PCs. :sad: 

There should be a boot option for the text install if desired.

---

### Post by mafitzpatrick on 2006-06-17
I believe there is an "alternate" install CD which includes a the option to perform a text-based install? See how you get on with that & report back...

As for the click-before-whatever thing, I'm not sure if it'll take notice of hitting Return if it thinks it's not selected but who knows! All very weird behaviour. If you do have a mouse pointer visible try clicking on the language list then hitting Return.

Also, there is [this in the Wiki Documentation]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell?highlight=%281100%29") where it suggests upgrading to the latest BIOS from Dell before install (along with some other tips).

---

### Post by jaa1180 on 2006-06-20
well, I installed Breezy and then upgraded to Dapper. It was the only way to get it to work. 

The text based CD is the server... it does not install much by default.
It seems that dapper is lacking in a few areas again.... at least it is working.

---

