---
title: "Trouble installing Xubuntu on G3 iBook Clamshell"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by toekneebullard on 2006-11-28
I'm a total Linux newb.  I have once installed Kubuntu on my old computer, but didn't find much use for it and never really got it really going anyways.  Other than that, no linux experience.

So I got my hands on a G3 iBook Clamshell, and I'd like to get something more modern than OS 8.6 running on it.  I download the Xubuntu for PowerPC iso, and burn it.  When in OS8.6, the disc shows up on the desktop fine, all the files are there.  

So I boot with the disc, I get the boot command line, it starts going, and then I get a long list that starts with something about not having enough video RAM, and then lists a whole lot of "Buffer I/O error on device hdc, logical block [number varies]

I could understand that this onld thing may not be able to run the live disc, is there a way to just install without loading up the live portion?

Thanks for any help!
Tony

---

### Post by DirtDawg on 2006-11-28
> **toekneebullard said:**
> 

I could understand that this onld thing may not be able to run the live disc, is there a way to just install without loading up the live portion?

Thanks for any help!
Tony

Yes. You want the [alternate-install]("http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/") CD. It has a text installer for low-end systems. It should work.

---

### Post by toekneebullard on 2006-11-28
OK, got that going, and its installing, but I'm getting a whole lot of errors.  Currently it "Installing the Base System" and every item it brings up (i.e. "Retrieving base_files") it spends some time spinning the disc, and then I get a corrupt file error along the lines of:
WARNING: file:///cdrom/pool/main/b/base_files/base-files_3.1.13ubuntu2_powerpc.deb is corrupt.

This happens on every single thing it trys to retrieve.  I imagine this means it's not going to install correctly...any help?

---

### Post by linear on 2006-11-28
Sounds like a bad CD. Try re-burning at a slow speed (4x or less).

---

### Post by toekneebullard on 2006-11-28
Yeah, I've tried re-burning the disc 5 times now.  The slowest I can burn it at is 12x.  Each time it's claimed to have verified and everything.  Most of the other discs barely even booted.  

Why can't I have one of those fancy quick Ubuntu installs I keep reading about?

---

### Post by DirtDawg on 2006-11-29
> **toekneebullard said:**
> Yeah, I've tried re-burning the disc 5 times now.  The slowest I can burn it at is 12x.  Each time it's claimed to have verified and everything.  Most of the other discs barely even booted.  

Why can't I have one of those fancy quick Ubuntu installs I keep reading about?

It really does sound like a bad CD. Maybe try an md5 sum check. With large downloads, things are easily corrupted. You can check it for corruption with md5 before you burn the image to disc, most people do. Look for a tutorial on Google, as I don't know of any off hand.

Of course, you could always try downloading the install again and see if that one works. Just don't be too surprised if it doesn't.

Sorry things aren't working out for you as planned. Good luck.

---

### Post by linear on 2006-11-29
> **toekneebullard said:**
> The slowest I can burn it at is 12x.

What software are you using to burn? Perhaps it's time to try an alternative. (Also, what brand of media?)

---

### Post by Sigudian on 2006-11-29
i would recommend Verbatim(if thats how its spelled) CD's and DVD's

---

### Post by robin on 2006-12-01
I would recommend using CD-RW discs for installing, that way you don't waste a disc each time something goes wrong.  You don't have to buy many of them.  I re-use the same 2 or three for trying various versions of Linux.

---

### Post by user2037 on 2006-12-21
Had a similar problem with Xubuntu 6.10 on an Ibook G3 the other day. It would start the installation but stall and keep spinning the disc. Nero verified that the second burn attempt was burned properly but it stalled at the very same point (probably a corrupt download). Finally I downloaded the alternate version and checked the MD5 sum after it finished downloading. Then I burned the alternate file at the lowest rate --2x-- using an older CD-RW drive. The alternate CD worked as expected.

Burning to a CD-RW did not work for me since the Ibook would not recognize the disc. It was burned at 4x. Regardless, CD-RW's are not as reflective as CD-R's so unless the drive is really good at reading burned discs, it probably won't work.

An md5-sum tool for Firefox:
[http://mdhashtool.mozdev.org/installation.html](http://mdhashtool.mozdev.org/installation.html)

---

### Post by jimb-il on 2006-12-26
I'm reading this thread with interest, as I'm also trying to run the ubuntu livecd on a clamshell ibook g3-366, with 320 mb RAM. I'm realizing that at least on my machine, the cd-rom drive (original Matshita/Matsushita CR-175) isn't capable of reading 700 mb cd-r's reliably.

At first all I could get to run on the drive were commercially produced cd's, but then I noticed some success playing older audio cd's I'd made using 650 mb, 74-min. cd-r's from before those got supplanted by 80 min, 700 mb discs in the shops. I've also been able to get the drive to read an old 4x, 650mb cd-rw disc I had lying around, with various newly burned content I put on it using Nero 6 on a Win XP machine. I've been convinced enough to order a stack of 650-mb cd-r's online, but they haven't arrived yet so I'm not sure if they'll serve for burning a disc that can be read by my clamshell ibook.

Trouble is, the edgy and dapper livecd's won't fit on a disc of that capacity, as the iso's are over 690 mb apiece. Still, they may at least suffice for running ubuntu installer iso's that are small enough to fit on the lower-capacity discs, e.g. the server distro that's a little under 500 mb -- [http://ubuntu-releases.cs.umn.edu/edgy/ubuntu-6.10-server-powerpc.iso](http://ubuntu-releases.cs.umn.edu/edgy/ubuntu-6.10-server-powerpc.iso)  . I actually was able to get that old cd-rw recognized with this image on it this evening, but didn't proceed with the installation because I didn't want to overwrite my existing OS 9.2.2 setup.

For what it's worth, I'd like to suggest that the troubles discussed in this thread might have to do with the capabilities of the clamshell's internal cd-rom drive, rather than problems with the burn of the .iso. How might this compare to others' experiences?

cheers,
Jim

---

### Post by jimb-il on 2007-01-03
Answering my own question :-). Trial and error led me to a cd-r that my clamshell ibook with the 'matshita cr-175' drive can recognize, and from which I can run the ubuntu livecd for ppc. The trick was to find Taiyo Yuden discs - what worked for me were the Sony "audio CD-R" discs I picked up in my local Walgreens as a 30-pack. Sony, Fujifilm and other brands whose discs are marked "made in Japan" in the fine print are likely to be TY's. Although these are 80min, 700mb discs, they worked fine -- which is fortunate, given the filesize of the .iso image. The drive refused to read anything else I burned onto, including Ritek and CSC manufactured discs labeled Memorex, Maxell, "computer essentials" (Walgreens brand), and Imation -- every one of those thrashed and whirred. Evidently the dyes and processes used by various makers of CD-R's are proprietary, and although most modern readers and burners can cope with a variety of them, older drives like the clamshell ibook's can be very finicky about whose they work with.

At any rate, with the disc properly burned, I could load the edgy eft ubuntu livecd directly onto the clamshell, where it looks pretty cool. The default boot-up failed with a complaint about insufficient video RAM, but the "video=ofonly" option suggested in the startup screen did the trick.

Hope this info is helpful to others.

---

### Post by gurnemanz on 2007-01-03
Thank you very much, Jim - this sounds very much like the trouble I'm having with the install on my G3 500mhz 500meg Pismo Powerbook. I hadn't thought about changing media to find something more suitable for an old and beat-up cd-r/dvd.

Stopping by Walgreens I am, on the way home.

g.

---

### Post by Carcenomy on 2007-02-08
Jim, your setup is like the mirror-image of my iBook :)

There's too many little niggles that I can't figure out, I'm curious as to if you are having similar issues, or if I've done something wrong. #1 gripe is power management - for some reason when the machine is placed into standby, the LCD doesn't power down. On top of that, my brightness controls don't work...

The other is booting. It's slow, and there's no feedback whatsoever. The screen flashes white, then it's black for a long time until the login screen appears.

Just curious of it's only my iBook acting up, or if it's a constant between Clammies.

---

### Post by tfcheng on 2007-08-07
thank you, jimb-il, for sharing this information with us. I just started to use ubuntu on my clamshell (G3, 300, tangerine). Like many cases, I burned a lot of installation CDs just to be able to boot the darn thing. After seeing your post, I bought a pack of 30 Sony's CD-R for music, burn the 6.10 powerpc image, and the cdrom recognize it at the first attempt. I think this information should be made official and put it onto ubuntu's powerpc webpage, so people wont get frustrated when installing it on their ibook. Thank you!1

TFC

---

### Post by BrandonMills on 2007-11-14
Hey guys. I wanted to just add that this worked for me, as well. 

Had a Blueberry clamshell that I didn't know what to do with. All CDR media was failing, so I assumed CDRs in general weren't going to work. It wasn't until I read this thread that I figured to try some of the Taiyo Yuden media on the drive. 

Now I have XUbuntu 7.10 running on this old clamshell. :) and 99 CDs left for any other CD drives that give me problems.

---

