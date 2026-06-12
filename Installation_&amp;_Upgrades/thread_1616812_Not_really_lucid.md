---
title: "Not really lucid"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by kliq on 2010-11-08
I was using 10.04.1 from a live CD but eventually gave in and made room on the HDD for an install because it was so Very clunky, jerky and slow.
But although it is quick-_**err**_ now, the mouse pointer still moves with a quite noticeable jerkiness to it especially when using Firefox.
Also, transfering a 1GB folder to a USB2.0 memory stick proceeded at a steady 2MB/s and did the last 20% @ < that and no other programs were running.
cpu=athlon 2000xp; 1.5GB ram; USB2 ports
So can anyone suggest please, what I can do to make things run more freely?
As well as no floppy operation, it seems Bz2 compression is not catered for either and so I had to go back to Knoppix to unzip a BZ2 file.
Can the the Konsole backround be made fully opaque? [i have tried - honest]
Finally, there is often a thin vertical corruption ot pixels on the display from top to bottom ~ 5mm in from the left hand edge, which if the Konsole is busy with a program, is dynamic/cyclical.[Radeon]

---

### Post by coffeecat on 2010-11-08
> **kliq said:**
> Can the the Konsole backround be made fully opaque? [i have tried - honest]

Konsole is a KDE terminal, yet you have tagged your thread 'Ubuntu'. So, which are you running, Kubuntu or Ubuntu?

> **kliq said:**
> it seems Bz2 compression is not catered for either and so I had to go back to Knoppix to unzip a BZ2 file.

bz2 comes in the box in Ubuntu and I would very, very, very much doubt it has been omitted from Kubuntu. Which, what with some of your other problems, makes me wonder if you installed from a corrupted ISO or a bad burn CD. Did you do a md5sum hash check on the downloaded ISO?

> **kliq said:**
> [Radeon]

Graphics card? Open source or proprietary driver?

---

### Post by kliq on 2010-11-11
Thanks for replying [coffeecat]("http://ubuntuforums.org/member.php?u=129087")
I am running Ubuntu [I'm also a long time KDE user, so Konsole just trips straight off the tongue by default (just as everyone says cellotape instead of sticky tape!)]
so your right, Terminal is, infact what I was refering to.
Just tried again and  BZ2 files still do not unzip.
The discs md5sum does agree with that given on the site, But -, I have not checked the downloaded md5sum file against the GPG signature because despite reading both howtos on checking signatures I still cannot understand how to do it. :-(
Radeon was a reference to my card [SB0090], the driver will be whatever Ubuntu installed itself.

---

### Post by coffeecat on 2010-11-12
> **kliq said:**
> Just tried again and  BZ2 files still do not unzip.

That's very odd. I'm posting from Maverick atm, but I'll reboot into Lucid later today and see what happens when I double-click on a bz2 file.

I'll also hunt out some links for you so that you know how to check the md5sum hashes for downloaded ISOs.

---

### Post by coffeecat on 2010-11-12
> **coffeecat said:**
> I'll reboot into Lucid later today and see what happens when I double-click on a bz2 file.

And it unzips just fine - in Lucid. Double-click - it extracts just  fine. Right-click > Extract Here - ditto. Right-click > Open with  Archive manager - ditto. (Those three are all the same anyway.) And from  a terminal: 'tar xjvf filename.tar.bz2' works just as well. I cannot  explain why your Lucid cannot handle bzip2 files.

As far as the other points are concerned:

If your 'konsole' is the purple gnome terminal then the only way of  making it opaque that I know of is to disable compiz. This might also  solve your sticky mouse. Such issues often revolve around compiz,  particularly if the graphics card is not that able. Your SB0090 is not  the graphics card - that sounds like a Soundblaster sound card.

The slow transfer to USB drive - I don't know. 2MB/s is hopelessly slow, I quite agree.

Floppy - the 'unable to mount location' when you double-click on the  floppy icon in Computer has been an ongoing problem since before Karmic  and is **still** not fixed in Maverick. What I usually do is...

```
sudo mount -t vfat /dev/fd0 /media/floppy0
```... but I've just tried this in Lucid and it's not working. Which is odd. It worked in Maverick the other day. :|

**EDIT:** Faulty memory. Mine, not the computer's. :wink: That code ought to work but doesn't - not in Lucid, Maverick or Natty. What does work is:

```
udisks --mount /dev/fd0
```Not elegant, having to open a terminal when you want to read a floppy, but you could make a launcher if you want.**[/EDIT]**

Md5sums - Linky 1 for you:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you follow the [http://releases.ubuntu.com/](http://releases.ubuntu.com/) link to your version, you  get to [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) . Now click on the MD5SUMS link  and save that page as MD5SUMS and make sure the MD5SUMS text file is in  the same folder as the downloaded ISO. Now go back to the first link  and scroll down to 'Semi-automatic method'. Open a terminal, cd to where  the ISO and MD5SUMS files are, and 'md5sum -c MD5SUMS' should do the  business.

---

### Post by kliq on 2010-11-12
Well, thanks very much for all that **coffeecat** and also apologies.

 Bliss, I can now use floppies again [to cheaply store small amounts of very valuable private data with multiple physical backup copies (manual 'RAID' !)]

  That's good, I didn't know that you could do that with Md5sums, but does that also check the GPG signature [which is what I cannot do]?

  As for the BZ2 files -  and assured by your convictions, I looked more closely at what I do and it turns out that I have been a bit spoilt by Knoppix and Mandriva. For a long time now I have been unzipping files that lack any extension (obfuscation) and, out of almost blithe/subconsious habbit, just hitting the Return key when a popup query appears which begins the unzipping. Ubuntu doesn't do that file data format check with the subsequent popup [for confirmation of its analysis]; it just stops with an Error message.
 So, yes, you are right; Ubuntu does do BZ2 unzipping.

  "**And another thing-!** "   - You're right again: The SB0090 is a sound card; the graphics card is a Radeon 8500LE 64MB DDR VO DVI.  Is that an able one?
I tried to disable Compiz - well I used sudo Top to kill it - it took about 6 goes but it went in the end. _BIG _mistake. So what is the proper way to disable it please?

I timed the USB2 [685MB] memory transfer this time: 2 mins start to eject on Knoppix; 6.75 mins start to eject on Ubuntu, the speed dropping to 2MB/s after 60% then down to 1.8MB/s by the finish time. I'll try Mandriva tomorrow.

---

### Post by coffeecat on 2010-11-13
> **kliq said:**
>  and also apologies.

None needed. :)

  > **kliq said:**
> That's good, I didn't know that you could do that with Md5sums, but does that also check the GPG signature [which is what I cannot do]?

To check the gpg signature of the md5sum hash, see here:

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)

I must admit, I've never bothered since the md5sums and the ISO come from trusted sources, but I suppose they could be hacked. :sigh:

> **kliq said:**
> So, yes, you are right; Ubuntu does do BZ2 unzipping.

I'm glad to hear it. :wink:

  > **kliq said:**
> the graphics card is a Radeon 8500LE 64MB DDR VO DVI.  Is that an able one
I tried to disable Compiz - well I used sudo Top to kill it - it took about 6 goes but it went in the end. _BIG _mistake. So what is the proper way to disable it please?

According to [this]("http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units") your 8500LE is R200-based, and according to [this]("https://help.ubuntu.com/community/RadeonDriver") you have full 3D support. Which rather surprised me since it was first released in 2001 and much later cards don't have 3d support. Whatever, the way to enable/disable compiz is to go to System > Preferences > Appearance > Visual Effects tab. Tick 'none' to disable, and any of the other boxes to re-enable.

> **kliq said:**
>  I timed the USB2 [685MB] memory transfer this time: 2 mins start to eject on Knoppix; 6.75 mins start to eject on Ubuntu, the speed dropping to 2MB/s after 60% then down to 1.8MB/s by the finish time. I'll try Mandriva tomorrow.

Very odd. No idea why the speed should be so slow in Ubuntu. I get much higher transfer speeds. In fact, last time I did a proper comparison, Ubuntu copied files to a NTFS (a Microsoft filesystem) USB drive quicker than Vista on the same machine. :rolleyes:

---

### Post by kliq on 2010-11-14
Thanks for  moving me along into the future with all that **coffeecat**.

After playing with Compiz the Terminal is now opaque;
and the mouse seems better whichever of the 3 graphics modes I switch it to; it did download some stuff (clue?).
I  have noticed a red-herring too: the mouse pauses jerkilly when straked  across the Firefox tabs and also in the F-Library when passing across  the 'sub-panes'' boundary's (left, right-upper, right-lower).
The pixel corruption persists and I have noticed it occuring much farther into the screen occasionally.

As for the stick:  well, - Mandriva managed 48 kB/s ! Although to be fair, it is 2008.1.

So, all-in-all, I think that unless you make any further points, then I will mark the thread as solved.

---

