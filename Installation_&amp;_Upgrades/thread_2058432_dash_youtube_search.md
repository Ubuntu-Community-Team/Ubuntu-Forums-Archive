---
title: "dash youtube search"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by ajdinm on 2012-09-15
Hello,
I was following [this]("http://www.upubuntu.com/2011/12/search-youtube-videos-from-unity-dash.html") guide and when wrote last command (**sudo apt-get install lens-video scope-youtube)  **and terminal wrote me: "E: Unable to locate package lens-video).
How can I solve this ?

---

### Post by Paddy Landau on 2012-09-15
That was written before 12.04. I'm not at my computer at the moment, but 12.04 has that functionality built in, doesn't it? Open Dash, press the video lens icon, and search. But my experience is that the search is rather poor.

---

### Post by ajdinm on 2012-09-15
> **Paddy Landau said:**
> That was written before 12.04. I'm not at my computer at the moment, but 12.04 has that functionality built in, doesn't it? Open Dash, press the video lens icon, and search. But my experience is that the search is rather poor.
I tried and that search is kinda poor. Doesn't show results (I typed song from local bend, cca. 50k views, ubuntu didn't found it, etc). Not really what I expected.

---

### Post by deadflowr on 2012-09-15
> **ajdinm said:**
> Hello,
I was following [this]("http://www.upubuntu.com/2011/12/search-youtube-videos-from-unity-dash.html") guide and when wrote last command (**sudo apt-get install lens-video scope-youtube)  **and terminal wrote me: "E: Unable to locate package lens-video).
How can I solve this ?

Packages need to be one long string, so the command you've run has broken the package into two, lens-video and scope-youtube. 
But I,m with Paddy in thinking I thought that function was already built in.

---

### Post by Paddy Landau on 2012-09-16
> **deadflowr said:**
> Packages need to be one long string, so the command you've run has broken the package into two, lens-video and scope-youtube.
That is incorrect. There are two packages that need to be installed, and so the command is correct as it stands.

However, I'm back at my computer, and I notice that lens-video package is not on the indicated PPA. There is no way that it will work. 

Try the following. I don't know if it will work, but it is worth a try.

[LIST=1]
[*]```
sudo apt-get install scope-youtube
```
[*]Log out and in again (or reboot).
[*]Try Dash > video lens > search.
[/LIST]
If it works, let us know. If it doesn't work, undo your changes as follows.
```
sudo apt-get purge scope-youtube
sudo add-apt-repository --remove ppa:atareao/lenses
sudo apt-get update
```> **deadflowr said:**
>  But I,m with Paddy in thinking I thought that function was already built in.
Yes, I've re-tested, and it really is a poor-quality search!

---

### Post by ajdinm on 2012-09-16
Unfortunately, nothing worked. Let's just hope it will be possible in upcoming Ubuntu versions.

---

### Post by Paddy Landau on 2012-09-16
> **ajdinm said:**
> Unfortunately, nothing worked.
Did you run the commands to undo the PPA? I strongly recommend that you do, as the PPA is obviously no longer maintained.

Have you tried searching through the built-in video lens in the Dash? I know it's rather poor, which is why I go to YouTube anyway when I wish to find something.

---

### Post by ajdinm on 2012-09-16
I have removed PPA stuff.
Dash video lens sucks for me, so I'm sticking to browser and url for now.

---

