---
title: "Kubuntu freezes on startup (Duel Booted)"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by Enroth on 2006-11-18
I recently got a new computer, and decided I want to duel boot it with Windows and Ubuntu. The other day I set about learning how to do this, and then proceeded to install the two. As suggested I installed Windows first, and all went fine. Secondly I went to install Kubuntu (Edgy Eft) and that install seemed to go fine as well. After they were both installed I could boot into Windows fine, but upon trying to load Kubuntu, the process freezes.
As in, the window with Ubuntu pops, up (I can only guess the loading screen) and the blue bar gos across the screen, as it reaches the end the screen flickers, and reappears the same, but now it has a green line running the length of the screen (about the hight of the loading bar) and it sits there until I restart the computer.

Installation Settings:
As I have one 300Gb hard drive I wanted to give each operating system 50Gb of space, and then leave the rest (in preferably 2, 100Gb part ions) for shared storage (I did use fat32 for them).
I also used a 2 Gb swap space.
I have installed several times (with different settings), and don’t mind starting again from scratch, with a different layout.
Both the OS part ions and the swap were primary.

That is all the information I can thing of giving, except it was a D/L version, and a dapper drake one is arriving in the mail soon. (Ordered it first then a friend gave me a copy of the newer version) so I hope it is enough. Thankyou for any help.

---

### Post by an.echte.trilingue on 2006-11-18
Me thinks you need to configure your video card.

Can you boot into the failsafe/text only mode?

---

### Post by Enroth on 2006-11-18
yes, but once there didnt know what to do, thanks for the lead.

---

### Post by Enroth on 2006-11-18
just for the extra information i have a
Gecube ATI Radeon X850Pro 256Mb DDR3 (PCIE)
video card, if anyone knows how to configure it.

---

### Post by an.echte.trilingue on 2006-11-18
I do not know about that card specifically, but assuming that it is not a really old card and that you have an internet connection, do this:

1. Follow the instructions at [this link]("https://help.ubuntu.com/community/Repositories/CommandLine") to enable the multiverse and universe repositories.

2. Install the ATI driver.
Code:

sudo apt-get update sudo apt-get install *fglrx*

3. Configure your grafic card to use the ATI driver (fglrx)
Code:

sudo dpkg-reconfigure xserver-xorg

be sure to select the proper driver (fglrx)

4. Enjoy ubuntu.

Take care,

-mat

---

### Post by Enroth on 2006-11-18
thankyou for the reply mat.
It helps except now I have to work out how to conect to the internet, tried just then (using wvdial), but it seems to be a job for tomorow (its 1:00 am) If there is a way to do it without conecting to the net that anyone know of that would make it easier, but i supose it dosnt work like that. Unless I can use my old computer (the one I am using now to d/l the files?)

---

### Post by steveyos666 on 2006-11-18
I'm in no way shape or form a professional, but if it's a CD-R did you test it before installing?

Hey you never know :D

---

### Post by Enroth on 2006-11-18
I guess you mean "check cd for defects" yes I did that, and it came up clean. If not were is the test you are talking about?
I am just looking through the files linked through the '/etc/apt/sources.list' located in the tutorial given to me by mat, but I cant work out how it is set up, I have seen other posts were people link to a different drive were the files are located, and wouldn&#8217;t mind d/l the driver and placing it in one of the shared partitions I mentioned earlier, or a cd. Can I do that in this case?

---

### Post by Enroth on 2006-11-18
Hi all,
Just like to thank everyone for there help, I believe I have fixed the problem (not entirely sure but I can make it to the desktop screen)
for other people who experience this problem I went [here]("http://www.ubuntuforums.org/showthread.php?t=190133&highlight=x800")

although the desktop loaded there was no install shortcut (dose anyone know if this is a problem) so I just stoped at end of step 2.

Looking forward to Using Kubuntu, and hopefully getting to a stage were I can help others
Cheers.

---

