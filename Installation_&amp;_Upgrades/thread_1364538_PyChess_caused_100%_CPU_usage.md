---
title: "PyChess caused 100% CPU usage"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2009-12-26
Thought I'd pass this along.
Used to use PyChess in Hardy and installed it in Karmic.

Was playing PyChess a couple days ago. Left it running after leaving it awhile just pausing it. Came back about an hour later to resume and started another game against the PC. Noticed it running slow and not very responsive. This is very unusual for a new i7. Then I noticed a smell of electrical component 'heat' you smell when some parts get too warm! Checked System Monitor and all 8 cores showed 100% CPU usage! Checked the processes running and there were several entries for PyChess showing ~96% use! Had a bit of trouble ending the processes for that app and ended up just quiting PyChess which seemed to correct this issue. 

Is there any issues with PyChess? 
Anyone have any ideas why it caused 100% CPU use on all the i7 cores?
Ram used only went up to 1.3GB while the CPU usage was at 100%.
The PC did feel warmer than usual. This is the first time it got that warm.

Played PyChess again today and decided watch what it did in System Monitor.
First my i7 was idling nicely with no strain a all.
Then opened PyChess. Then on checking System Monitor, 3 of the 8 i7 cores showed 100% use! Shutdown PyChess and those 3 cores dropped back down to normal idle. Started PyChess again and the same happened again, 3 cores showed 100% use! It looks like PyChess is causing this to happen in this desktop i7 Dell.

Don't have any idea how to stop it.

---

### Post by cybrsaylr on 2009-12-27
Anyone have any ideas on what caused this and is it a serious concern?
I'm afraid of using this game if it may cause some damage to my PC.

---

### Post by Soul-Sing on 2009-12-27
which engine do you use?
try crafty, this engine keeps on my chessclients cpu within normal
ranges.
the fruit engine is known as a cpu "eater"

---

### Post by cybrsaylr on 2009-12-27
Haven't a clue what engine I use.
How do you determine that and then switch to another?

---

### Post by Soul-Sing on 2009-12-28
settings: preferences: engines.
(crafty is a default chessengine afaik, but if not installed
please try it via synpatic packagemanager)

edit: i tried it on 8.04.3 gnome with PyChess and crafty works fine, and
with a "quiet" cpu...

---

### Post by cybrsaylr on 2009-12-28
OK when I check that two chess engines popup in use:
GNU Chess for Gnome 2.28.0 and
GNU Chess 5.07

If I install crafty  via synaptic package manager, will crafty replace the other two?

---

### Post by Soul-Sing on 2009-12-28
> **cybrsaylr said:**
> OK when I check that two chess engines popup in use:
GNU Chess for Gnome 2.28.0 and
GNU Chess 5.07

If I install crafty  via synaptic package manager, will crafty replace the other two?

No, you get an extra engine.

---

### Post by cybrsaylr on 2009-12-28
OK.
I installed crafty and switched to use crafty engine and the same thing happens.
When I open PyChess the 8 cores idle normal till I start the chess game. Then as soon as I start the chess game 3 of those 8 cores peg up to 100% usage again just like before!

---

### Post by Soul-Sing on 2009-12-28
> **cybrsaylr said:**
> OK.
I installed crafty and switched to use crafty engine and the same thing happens.
When I open PyChess the 8 cores idle normal till I start the chess game. Then as soon as I start the chess game 3 of those 8 cores peg up to 100% usage again just like before!

Sorry, strange...
Maybe another chessclient? But, again, on my dualcore 64bit system everthing is just fine. (on a 8.04.3 and 9.04 version)
- falanx and gnu chess gives almost 100% cpu usage...

---

### Post by cybrsaylr on 2009-12-28
Yeah, I was thinking the same. PyChess played fine on earlier Ubuntu versions on my other PCs. PyChess is only acting funny on my new i7 PC.
Also noticed when closing PyChess there is an audible 'pop' sound when shutting Pychess down.

---

### Post by cybrsaylr on 2010-01-02
Bump.....

Here's hoping someone will have a solution in the new year for this bug.
Or perhaps recommend another good Chess game that doesn't peg CPU use to 100% like PyChess has done to me.

---

### Post by mammoth23 on 2010-05-03
I had the same problem with pychess and the CPU. According to the page [https://bugzilla.redhat.com/show_bug.cgi?id=563668](https://bugzilla.redhat.com/show_bug.cgi?id=563668) and [http://code.google.com/p/pychess/issues/detail?id=526](http://code.google.com/p/pychess/issues/detail?id=526) the problem is caused by the analyzer mode. Therefore, in case you are a good chess player and you don't need the hint mode you can switch it off in the settings menu. This solves the problem.

---

### Post by cybrsaylr on 2010-05-03
Thanks mammoth23.
I'll give that a try. I had uninstalled PyChess to avoid this pegging problem. I'll give that solution a try if PyChess is installed again.

---

### Post by cybrsaylr on 2010-05-08
Seems to work. Played a game after changing the  analyzer mode settings as you suggested and so far no problems with PyChess.

---

### Post by cybrsaylr on 2010-05-08
Pegging returned today but not as bad as before!

Now only one core pegs to 100% as soon as PyChess is started.
Before 3,4,5 or more cores would peg to 100% when PyChess was started.
This didn't happen last night when I checked. Don't know why it is happening today. 

Both analyzer modes are switched off.
As soon as PyChess is started 1 core pegs to 100%.
As soon as I kill the game the 100% pegged core drops back to normal.

---

