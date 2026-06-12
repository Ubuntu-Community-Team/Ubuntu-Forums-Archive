---
title: "Live CD will start, but Install won't"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by ryber on 2007-05-01
I have previously worked with 6.06, but this is my first run through with 7.  I have been able to get 6 installed fine before.  I'm working on the same machine, but from a clean HDD, and am able to get the LiveCD to run, but using the Install icon, Ubuntu won't do anything, except spin the CD endlessly.  Any ideas?

---

### Post by Topsiho on 2007-05-01
I think the installer on the Live CD has a flaw as on one of my computers I could not install Feisty using the Live CD (it did not even boot I must admit).
However, using the alternate CD I could install Feisty without a hitch, so I suggest you try the alternate CD.

Topsiho

---

### Post by chrisgreende on 2007-05-01
I am having a similar problem.  New to Linux and ubuntu, I am keen to move away from Windows XP.

I have an HP OmniBook XE3 and have tried to boot off the Ubuntu 7.04 live CD.  Although the initial splash screen isdisplayed, the screen then goes black with two white boxes displayed then olthough I hear CD activity I get no further.

When I remove the live CD, the laptop boots normally into windows XP.  Has anyone any ideas to support a newcomer into the Linux fold

---

### Post by Topsiho on 2007-05-01
To Ryber:

I reread your post and (suddenly I) see you installed a clean HDD. Maybe, I am not sure, you have to format it first using, I suggest, the GParted Live CD, which you can download as an .iso file (search for it using Google), and burn it as an image.

Topsiho

---

### Post by Topsiho on 2007-05-01
To chrisgreende:

I think your Ubuntu screen settings are not correct and so the screen goes black (or does (not so) funny things). You can correct this probably by giving the necessary boot options. I am sorry I do not know which, but you should add the correct screen options, which you should find out  your self (Google is your friend, or maybe you can find it somewhere on this forum).

I give this information to try and put you on the right track :)

Topsiho

---

### Post by chrisgreende on 2007-05-01
> **Topsiho said:**
> To chrisgreende:

I think your Ubuntu screen settings are not correct and so the screen goes black (or does (not so) funny things). You can correct this probably by giving the necessary boot options. I am sorry I do not know which, but you should add the correct screen options, which you should find out  your self (Google is your friend, or maybe you can find it somewhere on this forum).

I give this information to try and put you on the right track :)

Topsiho

Thanks Topsiho.  I have now downloaded ubuntu 6.06 and tried to install that version.  Same thing happens black screen and all that.  I will now play with the settings on the initial splash screen and see if that has any effect.

---

### Post by ryber on 2007-05-01
> **Topsiho said:**
> To Ryber:

I reread your post and (suddenly I) see you installed a clean HDD. Maybe, I am not sure, you have to format it first using, I suggest, the GParted Live CD, which you can download as an .iso file (search for it using Google), and burn it as an image.

Topsiho

I ran GParted before I posted, and it still didn't want to install.  I tried to install Ubuntu 6, and now it doesn't seem to want to run either.  I think now that I may have a problem with the CD drive in the laptop I'm working with.  I'm trying it again, and the Install screen is at least starting to come up now.  I may give the Alternate CD a try, and if that doesn't work, I'll see if I can switch out the CD drive.

---

### Post by theGasman on 2007-05-01
Hi,

I too am new to Linux, and have exactly the same problem as you describe, with both versions 6 and 7.
In the boot options, delete splash and silent. This will show you all the drivers loading and let you get closer to the root of the problem instead of a black screen.

When I did this the last thing I see is something like "tty" not loading.
A quick perusal of the forums shows that this error can be caused by many different things, and trying to get the cause can be timeconsuming and fruitless.

I don't have time to waste so am looking at other distros or going back to Windows.
Let me know if you have any success.

Martin

---

### Post by chrisgreende on 2007-05-01
> **theGasman said:**
> Hi,

I too am new to Linux, and have exactly the same problem as you describe, with both versions 6 and 7.
In the boot options, delete splash and silent. This will show you all the drivers loading and let you get closer to the root of the problem instead of a black screen.

When I did this the last thing I see is something like "tty" not loading.
A quick perusal of the forums shows that this error can be caused by many different things, and trying to get the cause can be timeconsuming and fruitless.

I don't have time to waste so am looking at other distros or going back to Windows.
Let me know if you have any success.

Martin

Thanks Martin

I did not see the "tty" message on screen, but I will investigate it further.

I thought the problem might be a graphics driver problem, and I found something about loading 7.04 and a drivers disk, but I dont know whatthe drivers disk is they are talking about.

Chris

---

### Post by poseydonbgd on 2007-05-01
Hello i have similar problem 7.04 live work ok but install stack in 35% cd is runing like install but nothig happens 4 hours and just stand in 35% i have try few times but same result daper drake work ok on same comp configuration is  msi kt6 delta barton 2800+ 1gb kingston wd 40gb ati radeon 9700pro.Can any1 help?
Thx

---

### Post by Topsiho on 2007-05-02
I am sorry I can not give any help except suggest again you try the alternate CD, and check your CD's whether they are faulty or not.

Check the md5sums, and check them while burning (as an *image*), and check them in the diskdrive with which they are installed.

And also checkout the reported bugs and whether there are solutions for them.

Good luck,

Topsiho

---

### Post by Encryption on 2007-05-02
I have had this problem...

I am running FF 7.04 on my Packard Bell Laptop, i was going right from 6 so i had to clean install it. It got to a certain way and then appeared to stop doing anything. I have had this problem before when installing large files, something to do with my laptop overheating. 

This however was not the case in my situation. It was simply that i was not leaving it long enough, i doubt this will be the same but i am only throwing ideas around lol. I had to leave mine for a good hour before it moved from 16%.

Just a though, enc.

---

### Post by Topsiho on 2007-05-02
How much memory do you have (I mean inside the computer :) ), how much free space on your hard disk? If you let a perfect whale swim in a bathtub it won't go nowhere ....

Just a thought, I experienced this once myself.

Topsiho

---

### Post by flycharlles on 2007-05-07
Hi there,

  I am having problems as well to install Ubuntu/Kubuntu on my HP Omnibook XE4100,I have managed to install the live CD on my old AMD Durom/American Megatrans Desktop pc,but no luck with the same cd.I have even burned in other CD a version of Kubuntu,it loads but i can find the install logo/shortcut the display,please could someone give me any suggestions
thanks

---

