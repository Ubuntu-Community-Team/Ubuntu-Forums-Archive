---
title: "Newbie install feedback (it went ok btw)"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by ricster on 2007-06-22
Just some feedback / critique. My install worked first time, usb modem worked first time, online very quickly thank you!

my original setup:

40gb hd
5gb windows 98 partition
35gb data partition (including games installs) with 17gb free, defragged and ready

Downloaded 7.04 livecd iso via torrent and burnt - ok
booted cd , did integrity check - ok
noted that it could "see" my fat32 drives (happy!)
installed

everything was going fine until i got to the partion part at first it wanted me to pick a portion of the drive to partition for install. No mention of windows being detected, no mention about if it planned to format over or preserve all my data.

So i wen to the manual partition option

clicked EDIT on the 35gb partition, it then asked me how large i wanted the NEW partition to be. A bad choice of words IMO as i wasnt creating a new partition i was resizing an original one. IIRC it did note that there was 17gb free and suggest i grab it all but it was a few moments before i realised that i just needed to choose the new size for the existing one, sized it down to 25gb which took less than a minute.

Next i created two partitions, a 9gb one and a 1gb one. Having used a couple of linux flavours before i knew to set one to ext3 and the other to swap but then it wouldnt let me continue because i hadnt chosen a root mount. in order to proceed i had to Select a Root Partition by Mounting the EXT3 Partition to "/" .

two things:

1) "root" and "/" dont directly equate unless you know about linux generally (whilst i had selected the "manual" option it neednt have been the same as the "advanced" option if you get me)

2) that last bit sounds like something Kim Bauer might say, hardly newbie friendly



On reflection it would be nice if my install options had fallen somewhere between "auto" and "manual". I would have liked some assurance that my windows install would not be killed and the option to decide there and then which would boot by default. It would have been nice of it to notice the 17gb of free space at the far end of the drive and just let me say "OK, i'd like a 9gb system partition with a 1gb swap partition over there please" without having to go through all the clicking and resizing to do so. 

It would be even nicer if the partition creation was a little nicer than that, it could just ask me how much "space" i wanted to use for the "install" and just have it default to 1gb swap included within that figure (so in my case i would have just said "10gb please")



anyway, i'm more than happy with my shiney new ubuntu, really glad it "just worked" with my sound card and video card and i can use my fat32 partitions (though it did make me jump through some download hoops just to play an mp3, i guess there's only so much space on a livecd though). The wife thinks it's a bit wierd (though the default orange theme handily matches the color of my modded case!) but is happy to get used to it and has already used Evolution and Firefox and knows that OpenOffice wont be exactly the same as MS word, but again, happy to get used to it. So thumbs up from me and the wife.

Linux? Desktop ready? is for us!

---

