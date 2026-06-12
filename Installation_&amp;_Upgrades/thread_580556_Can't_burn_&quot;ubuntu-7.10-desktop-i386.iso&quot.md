---
title: "Can't burn &quot;ubuntu-7.10-desktop-i386.iso&quot; to CD"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by bliffle on 2007-10-18
I DLed the torrent "ubuntu-7.10-desktop-i386.iso.torrent" today from "http://releases.ubuntu.com/7.10"  and fired up "Deluge" and a few hours later I had "ubuntu-7.10-desktop-i386.iso", which I then attempted to burn with gnaomeBaker, 3 times, and each time it hungup trying to write the first record. I repeated the burn attempt several times, losing a fresh CD each time, but the same result. Same thing with "Brasero". So I  tried a different computer with the same results.

Now I'm waiting for a different torrent, having gotten a Gutsy .torrent file from "BTJunkie".

Has anyone gotten that torrent to successfully download that ""ubuntu-7.10-desktop-i386.iso" file and burn it?

---

### Post by mrvertigo on 2007-10-18
did you check with the md5, was it a sane download?

---

### Post by bliffle on 2007-10-18
I DLed the torrent "ubuntu-7.10-desktop-i386.iso.torrent" today from "http://releases.ubuntu.com/7.10"  and fired up "Deluge" and a few hours later I had "ubuntu-7.10-desktop-i386.iso", which I then attempted to burn with gnomeBaker, 3 times, and each time it hungup trying to write the first record. I repeated the burn attempt several times, losing a fresh CD each time, but the same result. Same thing with "Brasero". So I  tried a different computer with the same results.

Now I'm waiting for a different torrent, having gotten a Gutsy .torrent file from "BTJunkie".

Has anyone gotten that torrent to successfully download that ""ubuntu-7.10-desktop-i386.iso" file and burn it?

---

### Post by bliffle on 2007-10-18
> **mrvertigo said:**
> did you check with the md5, was it a sane download?

I'm not sure how o check the MD5, but I assume there's a string in the torrent that can be used by a program somewhere that creates a new string from the DLed file and compares them. So, where's the MD program?

---

### Post by Lord Landis on 2007-10-18
I don't know about Gnomebaker, per se, but if you use K3B it will automatically calculate the MD5 when you select 'Burn CD Image'.  After you select the image file, wait about 30 seconds or so for it to do the crunching, then just compare it to the hash provided by the site you got the torrent from.

Alternatively, open a terminal, change to the directory where you put the .iso, and code the following:

```
md5sum *filename*
```

For more detailed instructions, check this link:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by mrvertigo on 2007-10-18
ty loard landis

---

### Post by bhold on 2007-10-18
md5sums for Ubuntu 7.10 iso files are at 
[http://us.releases.ubuntu.com/7.10/MD5SUMS](http://us.releases.ubuntu.com/7.10/MD5SUMS)

Run md5sum in a terminal window to check your downloaded iso - no match, no good. I downloaded several times today before I got a good one, and the download was real slow. It might be better to wait a few days until the servers are not cranking so hard.

---

### Post by d_in_Conduct on 2007-10-18
I downloaded the same torrent, burned with K3b (at about 1/2 the speed my burner is capable of) and installed it.

Now if I can only get Gutsy to play nice with my wireless.

But, anyway, there doesn't seem to be anything wrong with the torrent... and I had it disconnect 3 times before I got it all.

---

### Post by FredB on 2007-10-18
Gnomebaker seems to be a *crappy* burn software. I use either brasero or Nautilus wizard, and all my burns are ok.

And using official torrent tracker gives 99.99% of the time a good iso. Every single piece is verified.

---

### Post by Lord Landis on 2007-10-19
> **mrvertigo**: ty loard landis

Eh?  I'm not quite sure what you meant there...

---

### Post by bliffle on 2007-10-19
The torrent DL finished and then instead of using 'gnomeBaker' or 'bracero' I did what the formal gutsy instructions say and I right-button clicked in the ubuntu file list and chose write-to-disk. It said it was burning and in a few minutes it'll be done. I'll try that liveCD on another computer and report.

---

### Post by bliffle on 2007-10-19
The CD burn appeared to go OK, but I couldn't do the MD5SUM because the list of MD5SUMs that they have at 'ubuntu.com' doesn't include 7.10! It only goes up to 7.04!

However, it appears to boot up, so I chose "Check cd for integrity" and it's doing that now. 

I tried to discover the MD5SUM for this DL. I'm sure it's in the little torrent tickler file, but I can't load that into a text editor becuase I don't know which character encoding it's in, and text editor insists on knowing.

OK, it finished checking and the CD is OK. It'll reboot into liveCD ubuntu for 7.10. With luck I'll be able to come into the ubuntu forums from that computer, if the wireless comes up, which it did on the kubuntu 7.04 liveCD. Gutsy shoule be able to do it too, right?

---

### Post by bliffle on 2007-10-19
Phooey! Wifi doesn't work. The antenna icon blinks, but I can't get to the internet.

Later.

---

### Post by Lord Landis on 2007-10-19
Sorry to hear your WiFi isn't working properly.  I can't really provide much help with that since my laptop doesn't even have it, but I DO have a list of the md5 sums for you (though it sounds like you're already past that point).

Use this link:  [http://mirror.anl.gov/pub/ubuntu-iso/CDs/7.10/MD5SUMS]("http://mirror.anl.gov/pub/ubuntu-iso/CDs/7.10/MD5SUMS")

---

### Post by bliffle on 2007-10-19
Thanks for the MD5SUMs info!

Bingo! The wifi started working. I'm on that very T60 right now. The hardware icon is glowing steadily.

Now, where's that darn SOLVED button?

---

