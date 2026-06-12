---
title: "Can't run Ubuntu Live CD"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by BluOzz on 2010-07-22
Hello!

Yesterday I wanted to check out the new Ubuntu version (10.04) but unfortunately this failed...

I downloaded as usual the Ubuntu live CD image and burnt it on a RW-CD I had.
I used Nero's software under Win XP Pro... The creation of the CD was fine... It booted from the CD, I choose the language, the try Ubuntu without installing...
After this point nothing went as it should... I got a lot of error messages, the screen was in text mode... it finaly stoped with a text mode ubuntu command line...
The errors were mostly I/O errors... I tried to use the check disk option... but also failed... same kind of errors... and at the end somthing like trying to connect to plymouth.... connection refused....

My computer configuration is the following:
AMD Athlon 2800+ (sk. 754)
2.5GB RAM (1x 512MB, 2x1GB, all different modules)
Epox 8KDA3i nForce3 250 motherboard
ATI Radeon 9550, 256 MB video card
A realtek based NIC, PCI slot
A TV tunner based on ATI Theater 550 Pro
200 GB, serial ata, WD hard drive
Optiarc AD7170s serial ata DVD-RW optical drive
Seagate 7200.2 40GB ATA133 hard drive
1.44MB floppy drive

Could this be due to unsuported chipset?

WinXP runs fine... I had in the past ubuntu (8.x, 9.x...) installed on this PC (maybe at that time I had 1GB of ram less) and did not have any troubles like this...

Any ideeas where could the problem be?

Many thanks in advance!

---

### Post by krimzonstarr on 2010-07-22
I have had a LOT of problems downloading .iso's for LiveUSB testing lately. Usually they won't boot at all.

After much trial and error, I found the culprit... Corrupt downloads through the browser. Once I started using torrents to download disk images, all my problems went away.

Always make sure to use a checksum to verify your downloaded file before burning up media!

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) Is the UbuntuWiki instructions on how to verify the md5 hash on Linux, Windows, and Mac.

Bittorrent downloads can be found at: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)

Good luck, and happy Ubuntuing!

---

### Post by BluOzz on 2010-07-22
Hmm... this would be a first...

But... I also tried kubuntu... which I downloaded using torrents (uTorrent is my application of choice). Same problems... exactly the same behavior...

I should try and check the md5 sum before burning an image... good thing I used a rewritable CD...

Today, just out of curiosity I tried the openSUSE live CD and it worked...

I'll download the images again and check the md5 summs...

10nx for the advice!

---

### Post by BluOzz on 2010-07-23
Hello again!

I did a test with the kubuntu ISO:
1. downloaded the iso from the website, using the direct browser download option.
2. tested the iso with winMD5sum; result: test OK!
3. booted from the CD
4. choose Check CD integrity... samr behaviour as described in the first post. the screen reverts to text mode... reaches a point telling me that it is going to select pIII_sse function for checksumming... but nothing usefull...
I also get some stdin error 0; etc...
5. tried the try weithout installing option... againg, text mode... stdin errors, other errors I cannot remember an finaly:

[138.516000] BUG: soft lockup - CPU#0 stuck for 61s! [plymouth:1448]

From this point on I would only get this error.
Not even ctrl+alt+del no longer works.

Soething's wrong... either with my system or with the hardware compatibility...

To bad I don't have another computer to test the CD...

---

### Post by nerdtron on 2010-07-23
> 

WinXP runs fine... I had in the past ubuntu (8.x, 9.x...) installed on this PC (maybe at that time I had 1GB of ram less) and did not have any troubles like this...




Since previous releases ran on your system when it had lower RAM, the added RAM could be a cause. Are you sure the RAM modules are of the same speeds?

---

### Post by BluOzz on 2010-07-23
All the ram modules are the same speed, DDR400.

They have different timings, but I've adjusted the Bios settings to very tolerant timings, so I won't have problems.

I remember that after I got the last 1GB modules, I played with the timings a little bit and with overclocking :).

Each time, I ran extensive memtest86+ test to check for stability issues. The non overclocked settings I currently use have also been tested extensively (I think I let the test run for a few good hours...).

openSuse boots fine... I also want to try Mint and Fedora. I also played with these distributions in the past.

And I just remembered: I used a 9.10 live CD a couple of months ago, on the same configuration as the one we're talking about. Did not have any problems at all....

---

### Post by deadalus.globalnode on 2010-07-23
Try pressing F6 and select the no mode set option.

---

### Post by krimzonstarr on 2010-07-23
Sorry I can't help more, hardware isn't much of my specialty. I have always been one of those lucky ones where most distro's always "just work."

I do remember seeing a lot of complaints with Plymouth though. Perhaps try another distro, or drop back to a previous release to see if that fixes your problems?

---

