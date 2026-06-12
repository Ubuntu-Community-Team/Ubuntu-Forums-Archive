---
title: "What are limitations of Gutsy 64bit?"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by Kokesh on 2007-12-17
Can I normally install 32bit .deb packages under 64bit Gutsy Gibbon? I have AMD X2 4000+ dual core CPU and Gutsy 32bit installed.

---

### Post by logos34 on 2007-12-17
the question is what are the limitations of x86...you should use the amd64 .debs with 64-bit--in most cases there is 64-bit equivalent to a 32-bit app.  But you can install stuff like 32-bit mozilla firefox browser and 32-bit plugins if you want.  Kilz over in the x86_64 forum will give you an earful on this subject.  With one or two exceptions I'm 32-bit free on my x64 gutsy ubuntu studio installation.

---

### Post by Kokesh on 2007-12-17
That's great. I just wasn't sure if it will bring me any advantages to run 64bit system and also if there are any problems in case I need to install 32bit app.

Do you know, if programs running under Wine and Virtualbox would be affected?

---

### Post by Kokesh on 2007-12-17
and also one thing... is there some performance advantage to run 64bit OS instead of 32bit on AMD64bit dualcore?

---

### Post by logos34 on 2007-12-17
I'm running the same windows programs on wine I was before on x86 gutsy and no problems.  (i.e. 32-bit programs from my x64 win xp pro partition, like EAC, foobar2000, mediacoder, etc).  
Haven't tried virtualbox though.

You'll notice the difference when you do any compiling, tarring/zipping files, audio/video encoding, etc.  And apps seem to open faster...things are just a bit zippier. (I haven't seen much faster boot time though)

edit: no idea about dual core

---

### Post by Kokesh on 2007-12-17
OK, I think I'm switching to 64bit. I believe I can't upgrade from Gutsy 32bit, so I have to get prepared for that :)

---

### Post by logos34 on 2007-12-17
yeah, unfortunately you can't upgrade across architectures.  I understand you wanting to be prepared.  Same here.  But now EVERYTHING works (for me that is), so it was a no-brainer to migrate to 64-bit ubuntu.  Mplayer, hitherto my nemesis, works really nicely now, I know not why.  Flashplugin-nonfree and w64codecs have made life so much easier now in x64.  

You know, you might consider what I did--install x64 gutsy alongside your 32-bit (provided you have a partition/space to spare) and run them together until you're absolutely satisfied with x64.  Then transfer your docs and delete x86 gutsy.   Or if it doesn't go well, delete x64.

---

### Post by Kokesh on 2007-12-17
I am just emptying 58.6GB partition, I'll put it there. I will write the result here. If not, then I had heart attack:)

---

