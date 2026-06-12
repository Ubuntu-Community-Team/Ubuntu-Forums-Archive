---
title: "Can't get to live CD start-up screen"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by kudzu on 2012-05-12
Hey everyone,

I'm running Ubuntu 9.10 on my Dell Latitude D630, and I've decided to upgrade to Ubuntu 12.04. I've quickly run into a problem, though, as despite my creating a live CD and then setting my computer to boot from the CD drive, I can't get the live CD to boot at all; I end up staring at a black screen, with a nothing but a cursor blinking in the upper-left hand corner. This screen won't accept any commands, and all I'm able to do is press the power button on my computer to turn it off.

Here's the background on how I got this far: I downloaded the ISO from the Ubuntu website, confirmed the file's md5sum to be the same as the md5sum listed on the Ubuntu website, and then burned the ISO onto a CD using the lowest burn speed possible (it ended up average 11x). I downloaded the md5sum file from the Ubuntu release page and then checked my newly-created Ubuntu live CD against the md5sum, and everything was said to be ok. 

I don't recall having any problems of this nature when installing Ubuntu 9.10 a few years ago. I've searched these forums and the rest of the web for solutions, but they seem to primarily be addressing problems that occur after one gets to the live CD start-up screen. I can't even get that far. There were several mentions of the possibility that the video card could be messing things up (which would make some sense to me, seeing as how I had the video card replaced about a year ago), and that I should set my computer to "nomodeset," but the suggested methods for doing that assumed that I could get to the live CD screen, which I cannot. I did see one suggestion that mentioned opening GRUB and adding "nomodeset" there, but my GRUB file was completely empty. I copied someone else's GRUB information that they had posted in the thread, including "nomodeset," and restarted, but nothing changed.

I'd really appreciate any suggestions that you all might have for me.

---

### Post by carl4926 on 2012-05-12
Are you able to test your burned cd on another machine? Or even in VM in your current install?

---

### Post by kudzu on 2012-05-12
I just tested it on my 8-years-old Gateway running Windows XP, and it did exactly the same thing - black screen with blinking cursor in upper-left hand corner, accepts no input. I guess that would point to the CD being the problem, then, wouldn't it? I can't what would have gone wrong during the downloading and subsequent CD burning processes, though. Should I just try the whole thing over again?

---

### Post by carl4926 on 2012-05-12
I always download with a torrent client, it does the checking for you and you don't need to re-download (ever), you can just force a re-check of the file

Burn it with k3b if you can
And as slow as you can

---

### Post by kudzu on 2012-05-12
I went ahead and re-downloaded the ISO from Ubuntu's website and burned it to a different DVD, and sure enough, it worked, and I'm posting from Ubuntu 12.04 right now. I guess I should have tried to re-download and re-burn before I posted this topic, but everything seemed to have gone so smoothly with the downloading and burning process that I would never have guessed that the problem could have occurred during those steps. Sorry for the superfluous topic, folks.

---

