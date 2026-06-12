---
title: "Ubuntu doesn't think  Rhythmbox is installed - but it is!"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by joshzam on 2009-11-20
I've got Rhythmbox Music Player 0.12.3 installed on my Karmic system. I know I've got it installed because I can go to Applications > Sound & Video > Rhythmbox Music Player and it opens, I can play music, and check the version in the Help menu. There is no doubt that I've got Rhythmbox installed ;)

I just noticed that 0.12.5 was released in September. I don't know why Rhythmbox didn't update when I upgraded to Karmic just a few weeks ago. So, in an attempt to manually update RB, I went to Synaptic and noticed that 0.12.5 was indeed in the repositories but it didn't think that I had RB installed on my system! As I mentioned, I do.

I tried to just install the latest version from the repos over my existing version but running RB after the "update" just loaded my 0.12.3 again. So I removed RB via Synaptic and my 0.12.3 is still there! I can't even remove the version of RB that I already had.

I want to update Rhythmbox to the latest version and I would like my system to recognize the fact that it is already installed. Can anyone help me figure this out?

---

### Post by suzypeppercorn on 2009-11-20
Did you compile 0.12.3 in the first place? If you did synaptic would not know about it. 

Even if you did not compile 0.12.3, I would try and remove everything to do with Rhythmbox and then install the version in synaptic.

---

### Post by joshzam on 2009-11-20
> **suzypeppercorn said:**
> Did you compile 0.12.3 in the first place? If you did synaptic would not know about it. 

Even if you did not compile 0.12.3, I would try and remove everything to do with Rhythmbox and then install the version in synaptic.

That sounds like a great idea. How would you propose I remove RB if Synaptic doesn't think that I have it installed to begin with?

---

### Post by joshzam on 2009-11-25
Anybody know how to remove a program that isn't recognized by Synaptic? If I knew where Rhythmbox was installed, could I just delete the folder? How can I get my system to recognize a new version, freshly installed via Synaptic?

---

### Post by joshzam on 2009-11-26
I may have figured this out. Here's what I did:

I found where Rhythmbox was currently installed:
```
whereis rhythmbox
```
I was told rhythmbox: /usr/local/bin /usr/local/lib
In the terminal, I navigated to those two folders and manually removed all files and folders associated with Rhythmbox.
Just to check, I clicked on the icon for RB which was still in my panel and it failed to launch. Good.
I then went back to Synaptic and installed the latest version of RB and, this time, when I clicked on the same icon in the panel, the new version 0.12.5 loaded!
Now, when I check the installation with whereis, I get this:
rhythmbox: /usr/bin/rhythmbox /usr/lib/rhythmbox /usr/share/rhythmbox /usr/share/man/man1/rhythmbox.1.gz
It seems to be working fine now. I hope I didn't screw anything up.

---

### Post by suzypeppercorn on 2009-12-03
sorry i bailed on you. good work figuring it out. i don't think your solution will cause any problems :)

---

