---
title: "new to ubuntu, need help on new system"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by jon61484 on 2007-02-09
First off, no I am not new to vbulletin, I know where the search button is and I used it. Information regarding what I am going to ask is very hard to decipher, especially since I am really new to linux. windows, dos, yeah I know pretty much everything needed to do in those areas.

so... I have an issue. I can't exactly copy the ubuntu iso to a cd. as my cd-rw died. :( but I've been researching, and to my dismay, it's very difficult to find the information I need.

I found a utility called Grub, but like said, being new to linux I am not sure how to use it. I guess what I'm trying to say is, is there any way to install Ubuntu Linux onto my system from winthin a windows or dos environment?

My first thought was to mount the iso image as a drive and go from there. but... unfortunately doing this inside windows or inside dos is *past* the boot point. no good.

since I can decompress all the files from the iso file inside windows, can I go back into grub and start the install from any of those files?

thank you for any help. I'm very eager to get this working.

---

### Post by Sqwishy on 2007-02-09
Grub is a bootloader. I'm pretty sure you can't install ubuntu from grub. Don't you have somewhere else you can burn the cd?

---

### Post by jon61484 on 2007-02-09
trying to find friends lol

---

### Post by Sqwishy on 2007-02-09
> **jon61484 said:**
> trying to find friends lol :lolflag: 
if you're realy desparate you can get 5.10 shipped to you for free. Or pay for the newest version for like $10
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by housam on 2007-02-09
> **jon61484 said:**
> trying to find friends lol

Why not trying your local library . they have fast Internet links . You can burn the live CD there. Also any net cafee in the neighborhoods can do the job.

---

### Post by jon61484 on 2007-02-09
No I am trying to ger ahold of friends that have use of a cd burner to see if I can burn it. lol. I set myself up for that.

I did however order 6.06 LTS though. Hey, if it's free...

---

### Post by jon61484 on 2007-02-09
I will get ahold of my friend nick later. maybe ask him to download and burn it for me in exchange for some of the old computer crap I need to get rid of.

I am proud of my machine though. Nothing intense by today's standards, but for what's in it, and the fact of the way it's overclocked, I am very please so far during windows stuff. but I hate windows... damn. wish my cd writer wouldn't have died.

---

### Post by Sqwishy on 2007-02-09
> **jon61484 said:**
> No I am trying to ger ahold of friends that have use of a cd burner to see if I can burn it. lol. I set myself up for that.

I did however order 6.06 LTS though. Hey, if it's free... :lolflag: k that's good that you got it, have fun! ^^

---

### Post by jon61484 on 2007-02-11
As of right now I am running Ubuntu 6.10 Edgy from my other computer. ;) I was able to make good use of a CD burner.

So, I put the CD in my cd-rom of THIS computer, test the cd for errors, nothing. Boot it up as a livecd (using firefox off of it right now) and all is well. Turn on my other computer, put the cd in, and as soon as I push enter for install, as the green bars are going across the screen, it has some little pixels in weird places (a pattern actually) in a thin line going across the screen. as the bar nears it's end the pixels move at the same rate with the bar.

Right after the first progession bar hits 100% it says something like

--- CRC fails
system halted

I am wondering if it is because of my ram or my hard drive. but I'm going to test it later. I wanted to make sure the copy of my cd was good. and it is. ;) I like this alot better than suse.

---

### Post by jon61484 on 2007-02-12
Alright. So. here's how it goes.

For whatever reasons, my other computer is having issues. It's either something is wrong with the motherboard and I'm going to have to scrap it and use another, or it is a hard drive issue.

So I got this 80GB western digital hard drive from a friend. I started to reformat it, thought everything was going good. For whatever reason, when I put it in my other computer (Intel P3 600mhz, i440BX chipset on a microstar motherboard. 256MB PC100 SDRAM) it won't even acknowledge a hard drive in the bios.

So I put it here on this computer, disabled the SCSI hdd (this is a P4 3Ghz with 1GB ram) and the motherboard acknowledged it. Right now I am reformatting it to install ubuntu. (from ubuntu live cd)

I am hoping I can install it to this hard drive, now *correctly* reformatted, and that it will happily boot up and go through any setup procedures it may need. Is there going to be an issue because I am setting it up on this computer and swapping the hard drive back to the other?

thanks



PS: Also, I took two thirds of the HDD space and used it for linux. Took 2GB and used it for swap, the rest is for NTFS data. (it's important for me to be able to use this for windows data just in case.) Do you guys think 2GB for swsp space is enough, too much, or doesn't really matter?

---

### Post by housam on 2007-02-13
> **jon61484 said:**
> 

PS: Also, I took two thirds of the HDD space and used it for linux. Took 2GB and used it for swap, the rest is for NTFS data. (it's important for me to be able to use this for windows data just in case.) Do you guys think 2GB for swsp space is enough, too much, or doesn't really matter?


2 Gb swap is too much. as it acts only as a virtual memory. Normally we size it as 2xRAM . But more than 1 Gb is waste of space.

---

