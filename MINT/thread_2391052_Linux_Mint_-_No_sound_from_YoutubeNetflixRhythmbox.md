---
title: "Linux Mint - No sound from Youtube/Netflix/Rhythmbox"
date: 2018-05-05
forum: MINT
---

### Post by drpeppercan on 2018-05-05
Hi all,

It's strange, because I can hear the sound when doing the testing in the Sound control panel.
I am using headphones connecting via a USB port.

Any ideas?

Thanks guys!

DPC

---

### Post by #&amp;thj^% on 2018-05-05
Have you tried with "pavucontrol" and then looking at the playback tab>> if it is your browser or player being used then make sure the right option is in use.  See screenshot.

---

### Post by drpeppercan on 2018-05-05
These are my settings:

[IMG]http://pasteall.org/pic/show.php?id=13917060acd2ddfb6c3f569b59e344c4[/IMG]




[IMG]http://pasteall.org/pic/show.php?id=8095c76d81e9cbd773396200eb2e4159[/IMG]

[IMG]http://pasteall.org/pic/show.php?id=8383e77dd81a18d2b1bb3f8b8e9ce8b9[/IMG]


[IMG]http://pasteall.org/pic/show.php?id=5ab317667ef1bf55b812cfac4c63be8e[/IMG]

---

### Post by wildmanne39 on 2018-05-05
*Thread moved to **MINT for a more appropriate fit**.*

---

### Post by #&amp;thj^% on 2018-05-05
> **wildmanne39 said:**
> *Thread moved to **MINT for a more appropriate fit**.*
Thanks wildmanne39 ;)

> **drpeppercan said:**
> These are my settings:

[IMG]http://pasteall.org/pic/show.php?id=13917060acd2ddfb6c3f569b59e344c4[/IMG]




[IMG]http://pasteall.org/pic/show.php?id=8095c76d81e9cbd773396200eb2e4159[/IMG]

[IMG]http://pasteall.org/pic/show.php?id=8383e77dd81a18d2b1bb3f8b8e9ce8b9[/IMG]


[IMG]http://pasteall.org/pic/show.php?id=5ab317667ef1bf55b812cfac4c63be8e[/IMG]
I think you are using just stock Volume Control for Mint, so what dose this show from the terminal:
```
apt policy pavucontrol
```
If it is already installed then run in the terminal:
```
pavucontrol
```
Then look there for what I showed you in my screenshot.

---

### Post by drpeppercan on 2018-05-05
Never mind guys!
It's working now!

Thanks everyone! :)

---

### Post by #&amp;thj^% on 2018-05-05
Glad to hear it's working, but was it automagicaly (Just started working on it's own) or were more steps by you needed.
This helps others looking or searching for the solution.

---

### Post by drpeppercan on 2018-05-05
As I went for a 2nd time to every page in the Sounds Settings panel, I must have changed something to the right thing. That's when I made the screenshots.
So basically as long as each of those pages show the same I choice, it should work for anyone else too.

---

### Post by #&amp;thj^% on 2018-05-05
That's Helpful thanks for sharing your steps needed.
Although the same can be accomplished through "pavucontrol"
Now if you would mark it as solved>>Going to your first post and in the top right>> Thread Tools>>mark as solved.
Thanks
Cheers

---

