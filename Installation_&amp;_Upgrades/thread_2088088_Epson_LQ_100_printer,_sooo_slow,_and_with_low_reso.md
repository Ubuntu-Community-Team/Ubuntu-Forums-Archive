---
title: "Epson LQ 100 printer, sooo slow, and with low resolution"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by Gluups on 2012-11-25
Hello everybody,

I am not very sure whether I should post here, or in the hardware forum. Or, as I discovered Ubuntu about a week ago, perhaps in "Absolute beginners", although absolute begins to be exaggerated as I installed Cairo-Dock after writing a script to handle screen copies. :guitar:

So, here is the problem. I have an Epson LQ 100 printer that runs jolly good on Windows, but on Ubuntu it takes about an hour to print a test page, and after that the resolution is so low that it is hardly readable.

This is the only problem I saw on that machine.

I tried several drivers that other people were satisfied with, the last one is Epson LQ 570+. This one is a little less slow, but still not quick enough, and the resolution is still so low.
The language used by the printer is Epson ESC/P2.

The system is Ubuntu 12.04.1 LTS, the memory size 494 MB, the processor is Intel Pentium 4 CPU 2.4 Ghz.

Any idea what to do ?

---

### Post by pdc on 2012-11-25
so this is a dot-matrix printer, at least 20 years old?

[http://www.youtube.com/watch?v=G-aqnsCTnAs](http://www.youtube.com/watch?v=G-aqnsCTnAs)

OpenPrinting is the source for open source printing

[http://www.openprinting.org/printer/Epson/Epson-LQ-500](http://www.openprinting.org/printer/Epson/Epson-LQ-500)

this sort of listing would be close to your printer

......some might suggest you treat yourself to a new printer ..go on ..you deserve it ........Christmas is coming.........splash out ......... :)

---

### Post by Paddy Landau on 2012-11-25
As you have just 494Mb, I imagine that you use Windows XP.

Ubuntu 12.04 is made for machines with rather more memory; at least 1Gb is recommended (more if you use 64-bit).

It is possible that the lack of memory is compounding your problem

Try loading [Lubuntu]("http://lubuntu.net/") (part of the official Ubuntu family but for low-spec computers) on a Live CD and see if the printer works a bit better. Or even [Bodhi]("http://www.bodhilinux.com/"), an unofficial but mature Ubuntu distro for even lower-spec computers.

---

### Post by Gluups on 2012-11-26
> **pdc said:**
> so this is a dot-matrix printer, at least 20 years old?

[http://www.youtube.com/watch?v=G-aqnsCTnAs](http://www.youtube.com/watch?v=G-aqnsCTnAs)

OpenPrinting is the source for open source printing

[http://www.openprinting.org/printer/Epson/Epson-LQ-500](http://www.openprinting.org/printer/Epson/Epson-LQ-500)

this sort of listing would be close to your printer

......some might suggest you treat yourself to a new printer ..go on ..you deserve it ........Christmas is coming.........splash out ......... :)

Well, going to have a look ...

---

### Post by Gluups on 2012-11-26
> **Paddy Landau said:**
> As you have just 494Mb, I imagine that you use Windows XP.

Ubuntu 12.04 is made for machines with rather more memory; at least 1Gb is recommended (more if you use 64-bit).

It is possible that the lack of memory is compounding your problem

Try loading [Lubuntu]("http://lubuntu.net/") (part of the official Ubuntu family but for low-spec computers) on a Live CD and see if the printer works a bit better. Or even [Bodhi]("http://www.bodhilinux.com/"), an unofficial but mature Ubuntu distro for even lower-spec computers.

Well, this sounds as bad news.
For Windows, on another machine, I have 1 GB, but the machine with Ubuntu has just arrived a week ago, installed by volunteers.

Should have to redo everything from the beginning ?

And ... during a good week I installed everything that had to be automated ...

Thank you for your answer, it really seems to have to be considered.

---

### Post by Gluups on 2012-11-26
> **pdc said:**
> so this is a dot-matrix printer, at least 20 years old?

[http://www.youtube.com/watch?v=G-aqnsCTnAs](http://www.youtube.com/watch?v=G-aqnsCTnAs)



This is it exactly, I already saw that video last week.
You know, a machine that still works as brand new after 20 years, and has no problem should you let it alone three months, this is a resource, even if a little noisy.

> 
OpenPrinting is the source for open source printing

[http://www.openprinting.org/printer/Epson/Epson-LQ-500](http://www.openprinting.org/printer/Epson/Epson-LQ-500)

this sort of listing would be close to your printer

......some might suggest you treat yourself to a new printer ..go on ..you deserve it ........Christmas is coming.........splash out ......... :)Hum, I also visited that site last week, and maybe it was there I downloaded the LQ570+ driver. But after doing other operations on the system I am more receptive to some keywords, and now that I know that cups is part of the system, I discovered a directory of documentation on the topic of printers.

So, very nice to come there back at the good moment, that leads me to read the documentation ... on the machine itself :)

And supposing nothing there gives anything convincing, I shall have to give more priority to Paddy's answer. Perhaps it can be more simple (take less time) to take the problem the other side, and install more memory, if possible.

---

### Post by Paddy Landau on 2012-11-27
> **Gluups said:**
> Well, this sounds as bad news.
For Windows, on another machine, I have 1 GB, but the machine with Ubuntu has just arrived a week ago, installed by volunteers.

Should have to redo everything from the beginning ?

And ... during a good week I installed everything that had to be automated ...

Thank you for your answer, it really seems to have to be considered.
Hmm, if you didn't install Ubuntu yourself and you rely on volunteers, first see if you can get your printer working. If your computer works satisfactorily, perhaps you need to leave it as it is.

If, however, you find that your computer runs too slowly for you, then you can consider changing to Lubuntu. The good news is that you can install it "over" your Ubuntu — not perfectly, but pretty well — through the Ubuntu Software Centre. In that case, you will have a choice of which one you want to use every time you log in!

But wait until you know whether or not your computer is fast enough for you before deciding.

---

### Post by Gluups on 2012-11-27
I realized that during printing, the memory use is stable at 54.5% (including the system monitor), and that the processor use varies between 40 and 95%, mostly between 70% and 80%.
With Epson's generic driver for 24 pin printers, the quality is less poor, but the duration is not better.
Maybe some more investigations risk to be useful. Probably on Thursday.

---

### Post by Gluups on 2012-12-02
Well, I am sorry I shall not spend as much time as I thought on this these days, so here are a few screen copies I made a few days ago.

---

### Post by Gluups on 2013-01-01
Well, some news about this ...
During printing, I opened the system monitor, that showed me that about one third of the memory was free. So, perhaps this was not the point ...
While reading the documentation about installing a printer, I had the idea to try the connection via USB. This was a good idea : with the same quality, the test page went out in 5 minutes, against one hour via parallel port. With a correct quality, the time rises to 13 minutes, which is correct considering the hardware. A text page with a photo went out in two minutes thirty, so what takes time to print are the two vertical lines at both sides.
I am still interested by an explanation, the drawback of this solution is that I have a USB port less free (and a parallel/USB thread).

This being said, I still have a problem (or perhaps two).
The printing crashes at the end of the first page, and I have to switch the power of the printer off and on, and depress the "next page" button to eject the paper.
The other problem is that if I cancel a print task, OK it disappears immediately from the queue, on the screen, but some garbage still remains to be printed, and I have to loose a sheet of paper to evacuate it.

The error reaction is set to "try the task again", I imagine I should set it to "abandon" to try ...
The driver is Epson-24-pin. Is it that recent that some mistakes in it still were undetected ?

---

### Post by Gluups on 2013-01-07
> **Gluups said:**
> 
I am still interested by an explanation

Epson has one :
[http://download.ebz.epson.net/faq/linux/faq_lc_00010.html](http://download.ebz.epson.net/faq/linux/faq_lc_00010.html)

---

### Post by Gluups on 2013-02-24
Eventually, after using USB for a while, this question has been solved from the French forums : the parallel port has to be configured in the BIOS parameters.


Am I not supposed to write "SOLVED" in the topic of the first message ?
It appears no more editable.

---

### Post by Paddy Landau on 2013-02-24
> **Gluups said:**
> Eventually, after using USB for a while, this question has been solved from the French forums : the parallel port has to be configured in the BIOS parameters.
I'm glad you managed to find the answer.

> **Gluups said:**
> Am I not supposed to write "SOLVED" in the topic of the first message ?
[How to mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

