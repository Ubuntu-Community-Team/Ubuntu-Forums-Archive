---
title: "Installation and Upgrade problems"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by Docmadness on 2011-10-14
Hey gang!

I've always used Windows in any computer I've ever had, but my harddrive died again due to Windows issues.  So I decided to give Ubuntu and try when I got my new harddrive.

My buddy had 10.04 and he gave it to me to install.  We thought that I could just upgrade to the new 11.10 version, but here is why I haven't been able to.

I finally got everything upgraded and worked out so I could do the slow version upgrade by upgrading to each version after 10.04 as recommended.  But everytime I do it, my download speed coming from your site drops down to UNDER 1kb/s.  I've ran speed tests on the modem and its pulling 1MB/sec, sometimes a little under.  So with the poor rate, it will take me a year to do it in this fashion.

So I found a blank disc and downloaded the 11.10 version and burnt it to disc to just do everything that way and skip all this upgrade stuff.  Everytime I go to restart my laptop and boot the new program from disc, it wont do it.  It reads that the program is on it when I get back to the 10.04 version that I have installed, but it will not let me do anything with it.

Is there something keeping me from doing it because I have the older version installed?  Do ya think that maybe the new version I downloaded was corrupt and didn't give me everything?  I double checked the files on the disc and it seems to have everything....

My buddy has a disc that works that I'm going to use this evening to see if it will boot up, but if there is anything you guys/gals can advise me of beforehand, that would be fantastic!

---

### Post by sikander3786 on 2011-10-14
Welcome to the forums :)

There is nothing like the older version is stopping you from booting the new disc. Are you sure your CD-ROM device is set as the first boot device in Bios menu? Refer to the manufacturers manual to find how to do it.

And are you sure you didn't burn a 'data disc' accidentally? You needed to 'burn the image to disc'.

It would also be better to check the downloaded image against any possible corruption and if you go to burn a new disc, do it at the lowest possible speeds.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Docmadness on 2011-10-14
Thanks for those links, but thats exactly how I did it the burning.  This is what comes up when I put the disc in:

'E:Unable to locate any package files, perhaps this is not a Debian disc or the wrong architecture'

And the file name is saved with .iso at the end, so I'm assuming its the correct file type.

---

### Post by sikander3786 on 2011-10-14
Can you please browse your disc on another PC? Do you mean it contains a .iso file on it? If yes, it has been burnt as a 'data disc' as I feared. Burning ISO link above would help, did you take a look?

Or ever, you can use a USB drive to boot if your machine supports it:

[http://www.tuxgarage.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html#create](http://www.tuxgarage.com/2011/06/ubuntu-switched-to-hybrid-disc-images.html#create)

---

### Post by Docmadness on 2011-10-14
I'll redownload it and try burning it again.  The entire file name is ubuntu-11.10-desktop-i386.iso

And yes, I browsed the file...it has a file in it named isolinux

I'd almost bet something happened when I originally downloaded it.  I do recall that I was at like 30% complete on the downloaded, walked next door to grab my phone charge, came back and it was done....and I was only away from the computer for 3mins.  

So I'll delete what I have and redownload it and try that out.  I downloaded it exactly how it states in that link. I actually found that yesterday before I burnt the first disc.  I'm using Ubuntu 10.04, so I don't have the option to 'burn as image'.  Is there anything I can download from the software manager to make sure get it done correctly....like a different burn program other than the default?

---

### Post by sikander3786 on 2011-10-14
The disc burn present by default in Ubuntu is Brasero which has got the option to burn an image. at the bottom of the list at the welcome screen.

I would recommend to check the image's MD5SUM once the download completes.

---

### Post by 23dornot23d on 2011-10-14
You need the Alternate CD or the DVD ........ for the majority of packages ......

---

### Post by Docmadness on 2011-10-14
I checked the MD5SUM file on the old download and it came up as an error.

So is that the reason for it not working?

---

### Post by mgmiller on 2011-10-14
If the MD5sum is bad, then you have a corrupted .iso and it won't work.  
Download it again.

Be patient, because the Ubuntu servers are being hammered right now due to the release of 11.10.

In 10.04 you don't have to run Brasero to correctly burn the live CD.
Just right click the .iso file and select "Write To Disc".  That should correctly create the live CD.

---

### Post by Docmadness on 2011-10-15
Thanks to everyone who has offered advice.

Ive been busy all afternoon and evening.  I got 11.10 downloaded again and checked the MD5SUM file and it came up fine this time.  So when I get up in the morning, I'm going to burn and try this again!

Again...thanks to everyone that has helped me with this!

Also, I posted something on another forum but noone responded about moving an entire file to an external harddrive.  I moved my music file to my hard drive and now need to move it back, but it wont let me do it.  I can move the files in it individually, but its has 2000 songs in it.  Is there anyway I can move the music file all at once?  maybe something I can download to do it?  I gotta do it before I can install 11.10.  I'm going to sleep, so I'll check back in the morning to see if anyone has commented.

---

### Post by jmate24 on 2011-10-15
Check the next post.. sorry got a little ahead of myself.

---

### Post by jmate24 on 2011-10-15
have you tried going to the multimedia and video section to post your question?

first of all all you have to do is go into 10.04 and right click your music folder and select copy then plug in an external hard drive that has enough space for your music say a 750 GB external hard drive if it is ntfs then you need to install a couple of things to write to it.

open up a terminal and type: (if you cannot find the terminal app then look in the top left corner of your screen click on Applications>Accessories>Terminal)

```
sudo apt-get install ntfs-config ntfs-3g libntfs* 
```

then open the ntfs config in either Applications>System Tools>Ntfs Config or in System> Administration> NTFS Config then check the Read/Write External Device option.

---

### Post by Using Debian on 2011-10-15
You can also use the command below to make a nice exact backup of your files.

Be sure to change the areas of the syntax below to match your setup.  For example
/media/[COLOR=Blue]**USB-750GBdrive**[/COLOR] most likely is not the exact name that your system will detect your USB drive as.

```
rsync -arvu /home/myusername /media/USB-750GBdrive/drive-data-from/myusername
```

---

