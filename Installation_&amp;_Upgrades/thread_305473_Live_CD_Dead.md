---
title: "Live CD Dead"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by jim-c-logger on 2006-11-23
Folks,

I imagine I am screwing up something very basic and am hoping someone can point me in the right direction.  I have read a bunch of other posts and cannot find anyone with exactly the same problem...

I have downloaded both 6.06.1 and 6.10 and have exactly the same issue: when I try to start using the CD I created, I get the first menu screen (1.  Start or install, 2... etc.) and no matter what I attempt to do, I get the following:

- A pop-up window saying I have an I/O Error
- A message at the top of the screen saying "Loading ISOlinux: Disk error 20: AX=4200 drive=EF"

I have downloaded both the 6.06.1 version (twice) and 6.10 versions.  I have pressed three disks: all three give exactly the same error.  

One other note: none of the hash checks match.  I downloaded the recommended hash checker and disk writer.  Both appear to be operating properly.  For all three downloads, the Hash numbers do not match any of the hash totals on the CD Build instructions.

I am running a 2GHZ AMD Athlon 2400, 512MB of RAM (64 of which is used for video memory).  I have had no issues with the burner.  The img loader gives good return codes, the disk verifies fine, etc., etc.

If anyone has any ideas, would appreciate the tip.  I have been a unix guy for a long time: this is my first trip to linux.

Thanks,

Jim

---

### Post by drphilngood on 2006-11-23
I´m no expert and some of the others may have better/easier suggestions but this always works for me.

Since it seems that you´re having trouble downloading the image, you could install the [DownThemAll]("https://addons.mozilla.org/firefox/201/") extension for Firefox.  It breaks the download up into pieces and checks the MD5 sum when it joins them.  This should insure that you start with a good Iso image to burn.
After you download it, check the MD5 sum again, just to make sure.  Then burn it on the lowest supported setting that you can and don´t use your computer at all while burning.  Some say that if you use burnproof that you don´t have to worry about this but I don´t agree.
Now, check the CD again or you can boot from it and use the built-in checker.

Hope this helps.  Good luck.

---

### Post by Bartender on 2006-11-23
drphilngood, that's an interesting extension for Firefox!

jim-c-logger, I'm not sure I'm following what you're saying about your md5's.  The download should be one big file, and one resulting md5.  If the resulting md5 doesn't match up with the one that you got off the download website, there's no point in proceeding with burning CD's.  The download has to be perfect.  

I second the dr., don't do anything else with your PC during the download or during the burn.  Use good quality media, burn it as slowly as you can.  This is more important if you've got an older PC.  My P4 3 GHz can burn at 8X reliably (have burned about a dozen .iso's) but probly couldn't get away with 8X with a 1GHz CPU.

---

### Post by wpshooter on 2006-11-23
Clean your CD drive.

Make sure your CD drive has the latest & greatest firmware installed.

Make sure nothing else is running while downloading ISO image.

Burn the image to a good name brand CD-RW (that has been completely erased) at preferably 4X or below.

Make sure the first thing you do when getting to the initial Ubuntu boot screen menu is to run the CD integrity check found on that menu.

Good luck.

---

### Post by jim-c-logger on 2006-11-23
Thanks to both of you.  I am going to download again and stay totally off the PC while I do it.  

I had not considered the burn speed, and I believe it was set to max...  I will slow it down to 8x or less and see what kind of results I get.

I will report back...  thx.

---

### Post by jim-c-logger on 2006-11-26
Thanks again to all of you...  

My initial belief that I had done something fundamental turned out to be true.  This PC has a big, honking drive on it capable of handling almost any size file.  Unfortunately, I was not downloading to that drive!  :(   I did a new download, the file size was right, and the hash matched.  Pressed the CD and I am up and running.

I do have another issue: I cannot seem to save any files, config data, etc.  I will put in another post for that.  

Thanks again.  I appreciate help from "veterans"...

Regards,

Jim

---

### Post by drphilngood on 2006-11-26
wpshooter is one of the "veterans", not me.  However, I am very happy to have been of some service and wish you luck in solving any other problems you may have.

---

