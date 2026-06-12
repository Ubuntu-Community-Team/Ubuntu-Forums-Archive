---
title: "Windows Curse or Bad Luck? Unable to burn Ubuntu iso"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by holomate on 2006-06-22
First let me start off by saying that I've been burning cds for many months now and it's gone perfectly fine. Music, Data, even the occassional iso file (I had burned Breezy Badger's installation disc just fine) which is why I'm a little confused as to why I'm having issues with the Dapper Drake iso. I've looked over the installation instructions several times now, in different places (forums, wiki, help file) and just can't figure out what I'm doing wrong.

So for the hardware I'm using, my DVDR/CDRW burner is a Plextor PX-712UF connected via Firewire to a PC running Windows XP. Alternatively, I have another computer running Ubuntu Breezy Badger, but which has a very flakey JVC Burner from at least 7 years ago. I've tried it with both burners, however the JVC is very unreliable at the best of times, so I'll be concentrating mostly on the Plextor and XP.

My proceedure goes as follows:

1) Download Ubuntu Desktop ISO
2) verify the md5 checksum (done on both systems) which is spot-on
3) Burn the cd image using 1) Nero 2) XPBurnISO 3) an old installation of cdrwin .... and two different brands of CD-R discs
4) Take the cd out, pop it into my other computer, boot it up to the ubuntu installation selection screen. Though I have tried other computers available also.
5) Try either "Verify CD for Defects" or "Install Ubuntu"
6) Watch as it spouts out read errors somewhere along the way (possibly the same spot every time, but I have no way to be sure).

What am I doing wrong here? Is there any way to verify the data from an iso is being written properly (Nero has this option for normal data cds, but seems to lack it when burning an iso)? Are there instructions out there for repairing/checking broken burner drives (as mentioned, I don't seem to be having problems with any other burns)? Is there something about Windows that is preventing the burns from being done properly? Does it have to do with sector size and if so, how come there's no value to adjust this in Windows based burning software?

It's got me stumped. I think I'm under a gypsy curse that doesn't want me to try out the Ubuntu version I've been eagerly awaiting for weeks before June 1st.

](*,) When computers start acting up, I'm EXTREMELY glad to own a nice simple Playstation.

---

### Post by Dr. C on 2006-06-22
One suggestion is to slow down the burn rate on the CD burner. I would try burning at 1/2 to 1/4 of the maximum burn speed.

---

### Post by Compactman on 2006-06-22
I'm having this same problem with the alternate installation ISO..

Checked the MD5 and burned at the slowest speed possible.  Same spot it tells me I have a problem.

---

### Post by ubuntu27 on 2006-06-23
1) How do you download the iso? It is generally recomended to download with Bitorrent.

3) XPBurnISO? Haven't tried that, where do I get it? Did you try ["CDBurnerXP Pro"]("http://www.cdburnerxp.se/") ?

6) This tells me that it's either Hardware's fault (HD) or the CD was not burned correctly.

---

### Post by aysiu on 2006-06-23
Follow these directions:
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by holomate on 2006-06-23
[QUOTE=ubuntu27]1) How do you download the iso? It is generally recomended to download with Bitorrent.

3) XPBurnISO? Haven't tried that, where do I get it? Did you try ["CDBurnerXP Pro"]("http://www.cdburnerxp.se/") ?
[/QUOTE]

1) I have downloaded the iso both with Bit Torrent and a direct download from the nearest FTP mirror. In any case the MD5 matches, so the file should be down correctly.

3) As for CDBurnerXP Pro, I'm sorry that's the name of the program I meant. I must have scrambled up the name in my head when I wrote the post. Apologies

The CDs I've been burning have been at 4x, which seems to be the slowest mode that my burner supports. Thanks for pointing me to [http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html) , however that's one of the web pages I've looked at and have followed the steps exactly as listed.

I'm a bit doubtful that this is a hardware problem as I continue to be able to burn all other kinds of cds normally. I don't have any other isos handy to test with, but general data cds in Mode 1 or Mode 2 seem to be alright.

---

### Post by holomate on 2006-06-28
Now at work on completely unrelated machines I'm starting to have general problems with burning cds. So maybe I am cursed.

Could anyone recommend a guide/website on diagnosing reasons for "bad burns" or resulting cds that won't give their data up (easily)?

I mean I'm seriously perplexed these days. I follow the wizards or the processes and all I get is something that has problems. If i sound crazy it's because I just got home from work and I'm tired of thinking what could be wrong with burning cds :/

---

### Post by jingo811 on 2006-07-12
I seem to have a similar problem when trying to burn with Nero I get this message:

> The entered block size does not correspond to the image length.
The block size may be wrong.  Do you want to correct the value or ignore the problem?
This is the file I try to burn but didn't work:
**xubuntu-6.06-alternate-i386.iso**
It's very odd since the same procedure worked when I downloaded and burnt the Regular Dapper Draker iso a week ago. 

So all that's left for me is to test Psycocats iso tutorial tomorrow instead and see if things go my way.
--------------------------------------------------------------

**Cursed guy wrote:**
> Now at work on completely unrelated machines I'm starting to have general problems with burning cds. So maybe I am cursed.
I don't know much about the details that others described earlier but judging from what you wrote most recently.  It sounds like you might have bought a **different BRAND** of CDs that you **haven't** used in the **past**.  And it might be like so that your **new** BRAND of CDs aren't **compatible** with your DVD/CD burner.

Happened to me once in the past with my newest PC buy in the year 2004.  That was like a bitch-slap.

---

