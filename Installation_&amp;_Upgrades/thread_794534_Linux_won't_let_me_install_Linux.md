---
title: "Linux won't let me install Linux"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by webcoded612 on 2008-05-14
I'm desperate to get away from Windows XP. I downloaded the Ubuntu 8.04 Alternate CD (Ubuntu installer doesn't play nice with my video card, I guess) and burned it (at slow speeds since Ubuntu doesn't install from a disc burnt at 40x).  

When I pop it in an reboot, I get a black screen with a blinking cursor:  _

It sits.  I went to smoke, read a little, made a few phone calls...came back twenty minutes later and it's still sitting there. 

What do I do?  

I'm running an e-Machines W3502...Windows XP Home...2Ghz AMD64 CPU with 1600Mhz FSB...1.5GB DDR RAM...80Gb HDD...ATI Radeon X1300 PCI-E vid card 256Mb.  

My system is plenty fast enough to run Linux, and I've been able to install 8.04 before...I just can't remember how.  Nothing has changed with the hardware in the PC, and Windows loads and runs everything fine (I'm using Win XP now) so it's not broken hardware.  

Bad disc maybe?  I only have one blank one left, and I hate to waste it on Ubuntu if it's not going to work.  :(

Any constructive help would be greatly appreciated.  

Thanks!

P.S.  I also burned Linux Mint and tried to install it.  I know it's a derivative of Ubuntu, and it did the exact same thing.  The odds of burning two bad discs are a lot greater than burning one bad one, and since they both use the Ubuntu structure, I'm thinking program issue here.  Thought I'd toss that in in case it ruled out the "bad disc" theory.

---

### Post by webcoded612 on 2008-05-14
Nobody knows?

---

### Post by Xappe on 2008-05-14
Make sure you didn't burn the disc as a data disc with the iso on it. You have to use the "Burn image" (or similar) option in the burning software that you use.

If you pop in the disc in windows, what do you see when you browse the contents?

---

### Post by webcoded612 on 2008-05-14
I burned it as "Disc from Image".  It's not just a data disk.  

As for what I get when I browse in Windows...it freezes explorer lol.

What are the odds of two disks being burned badly?  I'll try the instructions I found on burning disks...if that doesn't work I guess it's not meant for me to run Linux.  

Thanks for pointing out the obvious lol!

---

### Post by Xappe on 2008-05-14
If you don't get your discs up and running you could try this application I stumbled upon yesterday:

[URL="http://unetbootin.sourceforge.net/"]
http://unetbootin.sourceforge.net/[/URL]

Haven't tried it myself yet, but it sure looks like a nice little tool.

---

### Post by spectrevk on 2008-05-14
I had a similar problem trying to install Ubuntu on my laptop. The solution I found was to burn the iso normally, but to use a DVD instead of a CD. 

I can't tell you why, but the damn thing worked immediately.

---

### Post by wpshooter on 2008-05-14
1) Have you check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

2) Suggest that you get yourself a few CD-RW media, so that you can write and erase them over & over & over again.

3) Have you tried booting in the Safe video mode ?

P. S. - Are you burning the CDs at 4X or less ?

Good luck.

---

### Post by webcoded612 on 2008-05-14
Lowest the burning program I'm using goes is 16x.  I can't check integrity or boot in safe video mode because it doesn't get that far.  I get the gian "e" for emachines, then black screen with blinking cursor.  

CD-RW media is a good idea, but it doesn't help me tonight (wife has only car at work), and I want to get this done tonight.  It irks me that the .iso is so touchy it won't run when burned under normal burning conditions.  Grr.

I found a page on the forums here with burn instructions and a program to use, but I can't find it again.  

Thanks!

---

### Post by wpshooter on 2008-05-14
Are you downloading and burning from a Windows machine or from a another Ubuntu/Linux machine ?

P. S. - If you have access to a Ubuntu machine, I would use the k3b program to burn the ISO image.

---

### Post by webcoded612 on 2008-05-14
Windows XP

---

### Post by wpshooter on 2008-05-14
Are you certain that there is no way in your burning program to manually choose a speed lower the 16X.  I really feel that that is your problem, CD is being burned at too high of a speed.

---

### Post by Joeb454 on 2008-05-14
Check out Imgburn, it's *never* failed me yet :) [http://www.imgburn.com](http://www.imgburn.com)

---

### Post by webcoded612 on 2008-05-14
> **wpshooter said:**
> Are you downloading and burning from a Windows machine or from a another Ubuntu/Linux machine ?

P. S. - If you have access to a Ubuntu machine, I would use the k3b program to burn the ISO image.

Nope only machine I have is the one I'm on:  Windows XP Home.  There was an article on the forums here, but I can't find it again.  It was how to burn the ISO or something.  

Can't remember....

---

### Post by dasunst3r on 2008-05-14
I would suspect your CD/DVD burner.  So here's what I think the game plan should be:
[list=1]
[*]Check the .iso's image MD5 sum and compare them to what is here: [http://cdimage.ubuntu.com/ports/releases/8.04/release/MD5SUMS](http://cdimage.ubuntu.com/ports/releases/8.04/release/MD5SUMS) .  You can get a program to check MD5 checksums for Windows here: [http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum) .  If they don't match, you have a bad CD image and should re-download it.
[*]When you burn the image, have the program verify what it wrote.  If that fails, then your CD/DVD burner is defective.  I remember going through a stack of 10 DVD+Rs and pulling my hair out because my DVD burner was bad.
[/list]

---

### Post by ugm6hr on 2008-05-14
> **webcoded612 said:**
> I'm running an e-Machines W3502...Windows XP Home...2Ghz AMD64 CPU with 1600Mhz FSB...1.5GB DDR RAM...80Gb HDD...ATI Radeon X1300 PCI-E vid card 256Mb.  

My system is plenty fast enough to run Linux, and I've been able to install 8.04 before...I just can't remember how.  Nothing has changed with the hardware in the PC, and Windows loads and runs everything fine (I'm using Win XP now) so it's not broken hardware.  


If you've had it installed before, it clearly is a CD burn issue.  Perhaps poor quality CD-Rs, although incorrect download is more likely than bad burn if you burned it twice.

Make sure you check md5.

This is a good link: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

PS: Fast burn speeds often an issue for some, but actually I've never had a problem at 24x writes myself.

---

### Post by webcoded612 on 2008-05-14
Well I burned the disc using ImgBurn and it went through alright, but failed verification.  I rebooted and loaded the Ubuntu installer and did the "CD Integrity" check, and it failed that, too.  

I'm starting to think it might just be a bad file download, though that doesn't explain why Linux Mint gave me the same problems.  I'm ruling out CD burner issues because I only have problems with Linux ISO's.  Everything else I burn works fine.

But I'm out of CD's now, and no wheels til the wife gets home.  One last question, I guess, and then I'll just fix my Windows install and keep going with that:  I don't have any more CD-R's, but I'm pretty sure I've got some DVD+RW's around here.  My CD burner is also a DVD burner, and it supports DVD+RW as well...would it be possible to take the .iso file and burn it using those DVD+RW's?  

That's about my only option.  I'm not rich enough to keep throwing CD's at Linux :(

P.S.  I really, *really* want to install Linux, and will try whatever I can within my means.  If I have to I'll go buy another pack of CD-R's, but I wasn't kidding when I said I didn't have the $$$ to keep throwing CD's at Linux.  So ANY ideas here are welcome.  I HATE Windows.  I'm also going to re-download the .iso file right now, while I'm waiting.  :)

Thanks for all the help guys.  :)

---

### Post by webcoded612 on 2008-05-14
Little bump here...is it possible to burn the .iso to a DVD+RW and install it that way?

Thanks!

---

### Post by spectrevk on 2008-05-14
> **webcoded612 said:**
> Little bump here...is it possible to burn the .iso to a DVD+RW and install it that way?

Thanks!

Uh, like I said before...I had a similar problem, I burned the .iso to a DVD+R and the thing worked fine.

---

### Post by ugm6hr on 2008-05-15
> **webcoded612 said:**
> Little bump here...is it possible to burn the .iso to a DVD+RW and install it that way?

Thanks!

Redownload using Torrent - it checks integrity during the download.

I think it is even possible to use the same file as you have already downloaded, and uTorrent will correct it for you as it uploads.

DVD+RW are a lot more expensive than CD-Rs.

Perhaps you want to install without a CD?

Look here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by wpshooter on 2008-05-15
One other thought, have you consider that this might be related to the firmware version of your CD writer ?

Research on the CD writers website and see if you have the latest version installed.

Good luck.

---

### Post by webcoded612 on 2008-05-15
> **ugm6hr said:**
> Redownload using Torrent - it checks integrity during the download.

I think it is even possible to use the same file as you have already downloaded, and uTorrent will correct it for you as it uploads.

DVD+RW are a lot more expensive than CD-Rs.

Perhaps you want to install without a CD?

Look here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Well I already had the DVD+RW's here.  I tried one and it failed.  I burned that same disk a few other times with random data, erasing after each burn, and it worked flawlessly.  

I did remember that when I was downloading the .iso the other day my PC froze on me and I had to force a reboot.  When it came back up, Firefox picked up the download automatically, so I figure this is a file issue.  Doesn't explain why Linux Mint didn't burn, but I tried to burn it at 16x, too, so maybe that's it.

Going today to buy some CD+RW's.  I'll give those a shot, and if they don't work, I'll erase them and just stick with Windows.  :(

Thanks for all the help guys.  I think this is the most help I've ever gotten from the community here.  Normally it's one answer and then a "look for it on the forums" post, which is utterly useless.  If I'd have found it on the forums I wouldn't be asking for help....

Anyhow...thanks again.  I'll let you all know how it went tonight.  :))

---

### Post by wpshooter on 2008-05-15
If what you are about to try does not work, I think I might attempt to go to control panel and uninstall whatever CD burning program that you are using and then reboot the machine and then re-install the burning program.

But before I did that, if you have not already done so, I think I would check to see that the firmware of your CD drive is on the latest and greatest version like I had suggested earlier.

Good luck.

---

### Post by webcoded612 on 2008-05-16
I´m not sure why everybody is complaining about Hardy...this is the first Ubuntu distro EVER to run out-of-the-box on my system.  Once I got the CD burned (which was a Windows problem, I think), Ubuntu went from start to finish with very little input from me.  It picked up my video card (a first for ubuntu for me) and loaded everything perfectly.

Thanks for all the help guys...I know it&#347; hard sometimes to help someone when they know very little about Linux and are frustrated.  Thanks for stickin' with me!

Also it&#347; important to note that I didn´t dual boot:  I got rid of Windows completely.  It is GONE!  

So I guess what I´m saying is that the Ubuntu community has one more member.  :)

Thanks one more time!

---

### Post by ugm6hr on 2008-05-16
> **webcoded612 said:**
> I´m not sure why everybody is complaining about Hardy...this is the first Ubuntu distro EVER to run out-of-the-box on my system.  Once I got the CD burned (which was a Windows problem, I think), Ubuntu went from start to finish with very little input from me.  It picked up my video card (a first for ubuntu for me) and loaded everything perfectly.

It can be difficult when you are first starting...  people often blame Ubuntu for not working, but, as in your case, the issue was with the CD burn.

Glad to hear everything worked out in the end.

And can I say, it was very brave of you to wipe Windows completely!

---

### Post by webcoded612 on 2008-05-27
It's freeing, too.  I've been with Ubuntu for a week or so now, and I honestly can say that I'm already wiping Windows from my mind.  My father called me a few days ago with a Windows problem and I had to Google it because I couldn't remember!  Talk about a happy day!

Thanks again for all the help.  I was affraid that as the OS got better the community would get worse (had a few questions go unanswered...a first on the forums here for me), but at least in some areas everything is still going strong.  :)

Thanks again!

---

