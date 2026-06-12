---
title: "won't boot after clean gutsy install?"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Bubs on 2007-10-25
This is Messed up.  I had trouble upgrading from fiesty to gutsy.  So I decided to do a clean install.  well I got the disk told it which Hard drive I want to install it on.  I have three HDD's but the other 2 are just for storage.  go through the install no problems but then I reboot and it tells me there is no system on the drive.  I'll have to repost the exact message since I'm using the liveCD to post this.

Whats the Deal?  It was working an hour ago with fiesty.  I finally got it to upgrade to gutsy but I don't think it went well so I decided to clean install.  I've done it twice now.  same message both times.

i have checked the md5sums and everything for the cd checks out.  I even used different cds

---

### Post by thelocust on 2007-10-25
I'm pretty sure your install is good your having a problem with GRUB so get your self a Super GRUB Disk and reinstall GRUB and Install it on the MBR and you should be good (had the same problem by the way even after I got it to reconize GRUB I still had to edit what HDD to boot off of)

---

### Post by Bubs on 2007-10-26
thanks man I'll try that if this next install doesn't work...  hope it does.

---

### Post by logos34 on 2007-10-26
Try booting from the other 2 hard disks.  Anything?

---

### Post by Bubs on 2007-10-26
OK, I'm not at your solution yet so it may be the answer to my frustration. 

but I've been using ubuntu off and on since the release right before the 6.06LTS.  I've used numerous other distros also.  And I only mention that not to be some kind of *** to say "im so great I've been here a while"  really i still don't know much about linux.  I can trouble shoot small things but not much.  but every install i've done ask where I want to install the boot loader.  I don't really know much about what they say but they usually say go with the default, and I do.  

older ubuntu's do that too.

why not this one?  

PLEASE keep in mind that I love ubuntu on my desktop, I doubt i'll switch to something else.  Ubuntu has ALWAYS worked for me in the past.  and I'm sure that Gutsy will work well for me in the future...

I'm not really going anywhere with this post.  It's just a frustration rant a 1:00 in the morning trying to get a system up and running that i've been working on since 5:00 this evening.

but dev team...  if all you wanted was to make me cry...  just call me up and tell me my grandma died.  I'll give you the number.  I just want a working install... thats it!

bubs.

---

### Post by Bubs on 2007-10-26
no the other 2 hard disks don't have an OS on them.  I made sure of that in the install part... I did install ubuntu on one of them before.  wasn't good since I had things on that disk I really wanted to keep...  Oh well.

---

### Post by thelocust on 2007-10-26
I gotta go with Bubs on this one for some reson Gusty did not detect a default HDD which it just got done installing on and when I entered in the correct info it still skrewed up.

---

### Post by Bubs on 2007-10-26
another thing that may be helpful is that when I get an error it says hit any key to continue

then I hit a key and it brings me to a list of 3 OS's a ubuntu 7.10, a 7.10 recovery, and a memtest.  but when I select one it gives me the same error that I got before.  which I can't post yet since I haven't been back to the screen.

---

### Post by Bubs on 2007-10-26
and the message is...

"Error 22: No such partition

Press any key to continue..."

---

### Post by thelocust on 2007-10-26
>  
another thing that may be helpful is that when I get an error it says hit any key to continue

your making progress instead of hitting enter on the ubuntu option hit "e" twice that shoud bring up something that looks like "(hd0,0)" change the numbers around until it works i.e hd1,0 hd0,1 and so forth. when you change them hit enter and then "b" to try and boot.

---

### Post by Bubs on 2007-10-26
ok I got the super grub disk.  went in and tried to install grub on the MBR it says it did but I restart and still the same error.  however I can use the SGD to boot my install of ubuntu.  so I know the install worked.  but how do I get it to boot.

Oh and "thelocust" in the SGD i noticed that the partition for ubuntu that it was using was on (hd2,0) but I hit e twice after that and it's set up to (hd2,0)

so...  any more ideas?  I can boot my install with the super grub disk.  and i've done that twice now and everything seems to be working well.

---

### Post by thelocust on 2007-10-26
So you set it up for (hd2,0) and hit "b" to boot it and you still get the
 
"Error 22: No such partition

Press any key to continue..."

---

### Post by Bubs on 2007-10-26
yes.  that is correct.

---

### Post by Bubs on 2007-10-26
is there anything I can do to grub while I'm actually booted in to ubuntu?  since I can get in with the super grub disk.

---

### Post by thelocust on 2007-10-26
Did you try diffrent numbers?

---

### Post by thelocust on 2007-10-26
>  
is there anything I can do to grub while I'm actually booted in to ubuntu? since I can get in with the super grub disk. 

 
Yes but you can't relly test it out with out rebooting. But if you want it is a file called menu.lst under /boot/grub/ you have to open it as root to edit it and towards the bottom you will see where you can edit the (hd2,0).

---

### Post by Bubs on 2007-10-26
different numbers as in how?  

Like (hd3,0) or (hd2,1) ?

---

### Post by thelocust on 2007-10-26
Yea
 
(hd0,0)
(hd0,1)
(hd0,2)
(hd0,3)
(hd0,4)
(hd1,0)
(hd1,1)
ect...
 
until it works then go in and edit the menu.lst file for the one that worked.

---

### Post by Bubs on 2007-10-26
alright.  I'll give that a shot.  it there a reason you stopped at 4?  just curious.

---

### Post by thelocust on 2007-10-26
No just go lazy but I don't think you'll have more than 5 partitions on any one drive
 
hd0=drive,0=partition on drive (0 is the first)
 
so hd0,0 is that first partition on the first HDD.

---

### Post by Bubs on 2007-10-26
dude you rock!  it was (hd0,0) changed it in the menu.lst rebooted and it booted fine!  Thank you for the help!

and if your ever in the indianapolis/terre haute indiana area.  I owe you some dinner or something!

---

### Post by thelocust on 2007-10-26
No problem gald your up and running.

---

