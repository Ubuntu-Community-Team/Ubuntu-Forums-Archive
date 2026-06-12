---
title: "Problem Installing on Old Hardware"
date: 2014-01-19
forum: Installation &amp; Upgrades
---

### Post by jelly on 2014-01-19
I'm trying to install Xubuntu 13.10 on a Compaq Presario SR1000 (I know, I know - it's a donation and all I've got right now):

[http://reviews.cnet.com/desktops/hp-compaq-presario-sr1000/4507-3118_7-30912990.html](http://reviews.cnet.com/desktops/hp-compaq-presario-sr1000/4507-3118_7-30912990.html)

There seems to be a problem loading X however.  I get the boot menu, choose to install, then the graphical boot displays.  After a while it flicks into a graphical display a couple of times - first showing a medium-grey background with a mouse pointer, then back to just a text cursor, then to a black background with a mouse cursor, then back to the text cursor indefinitely.

Going to the terminal and looking at /var/log/Xorg.0.log shows that there is a segmentation fault at address 0x0, and the server terminates with error.  Looking at the boot log it says that "load fallback graphics devices" failed.

Any help in getting this going would be greatly appreciated.  Is this a lame duck or can it be rescued?

---

### Post by ajgreeny on 2014-01-19
What happens if you try to boot to a live system; do you get to the xfce desktop?

512 MB ram is a bit low for Xubuntu, but if you have the max 1GB on that machine it should be enough, but the other important hardware part is the graphic card; what is that?  If you're not sure let's see the output of ```
lspci | grep -i vga
```

---

### Post by jelly on 2014-01-19
I've only got 512MB of RAM, of which an unhealthy chunk (32MB - 128MB) is shared as video RAM.  If I can get it working, and something better doesn't show up, I'd of course look at trying to get the 1GB.

Here is my output from lspci:

```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 622/761Gx PCIE VGA Display Adapter
```

---

### Post by Bashing-om on 2014-01-19
jelly; Hi !

sis graphics can be problematic;
Some guidance and info:
[http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)
[http://ubuntuforums.org/showthread.php?t=2172375&page=8](http://ubuntuforums.org/showthread.php?t=2172375&page=8)
From those who have been there and done that.

Not going to wish you luck as it is
[INDENT][INDENT][INDENT][INDENT]all hard work
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jelly on 2014-01-19
Hmm.  I think I'm going to spend another week or so trying to get more hardware before embarking on this particular journey.  I've been down that sort of road long ago, and it's one I'd rather not travel again.

Thanks for the pointers though.

---

### Post by Bashing-om on 2014-01-19
jelly; Yeah !

That might be the best course, I also had a serious problem with my graphics on this box. A cheap $15 ATI card solved all of it for me !

[INDENT][INDENT][INDENT]sometime one way
[INDENT][INDENT][INDENT][INDENT]sometimes another
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mörgæs on 2014-01-20
Did you try Xubuntu 12.04? 
SIS cards are often easier to deal with here than 13.10.

By the way, you have an AMD socket A processor. They do not support SSE2, so you will not be able to play Flash. Not trying to kill the project, just giving realistic expectations.

---

### Post by jelly on 2014-01-20
> Did you try Xubuntu 12.04?

No, I should have tried the LTS.. I'll give that a go tonight.  Someone else has just donated a computer which I'm picking up this afternoon, so hopefully that won't have an SiS graphics card.  I never thought I'd see the day where I'm actually hoping for an Intel graphics card!

> you will not be able to play Flash. Not trying to kill the project, just giving realistic expectations.

No, that's fine.. in an odd way that actually helps.  I work for a charity shop and we need a computer in the book department to help value books and sell online - so all we need is a web browser viewing HTML.  The low RAM is my main concern for this, but if I can get something going I'll seek out more.

Eventually my constant moaning will force the organisation to give me a reasonable PC, but in the mean-time I need to get on and make money with what I can get hold of (further strengthening my case).

Thanks for the advice!

---

### Post by jp734 on 2014-01-20
I would recommend lubuntu. I installed it on my old hp 750n that has p4 2.4gh and 768mb of ram and I purchased a used nvidia fx5200 for less than 10 bucks and it's performing just fine. Also, I'm using fluxbox for my window manager to make it even lighter.

---

