---
title: "keeps freezing"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by thedarkside on 2010-02-20
i switched 2 ubuntu instead of vista ,had a mate who introduced me 2 ubuntu 9.10.
 though it's become a major problem ubuntu can be on for upto 3 weeks or 2 times in a day ,then the screeen freezea wont even restart or shutdown
so i shut it down from my desktop and on boot up says (control+d) will determine this shell... have 2 reinstall it must be up 2 twenty times now ,doing me head in..
there are no errors on the disk i know nothing about p.c's basically but think maybe .nvidia or firefox is the problem as it 

please help....

---

### Post by quixote on 2010-02-21
Screen freezes happen when the graphics setup in the X windowing system has some kind of problem.  To troubleshoot that, some more info is needed:

--what model of computer do you have?

--what's your video card? (You can find out by typing in a terminal (Applications > Accessories > Terminal) ```
sudo lshw
```That  gives you way more info than you want, but scroll the output back up toward the beginning and look for a line or lines starting with "display.")

--how much system memory do you have?

---

### Post by thedarkside on 2010-02-21
:confused:
cheers quixote 
my p.c. is a 32 bit compaq pressario
system memory 5 gb (gib)
not sure about the video card but this what ive got ??????
amd athlon 64 processor 3500+
version 15.15.2
& g force 6150 le     these mean little to me ?

---

### Post by quixote on 2010-02-21
That sounds like you have a NVIDIA GeForce 6150 GPU graphics. Your CPU is a 64-bit AMD Athlon which is an excellent, fast chip.  With 5 GB of memory, that's quite a system you have there . . . except that with a 32-bit operating system, you're not using most of it :).  

32-bit systems use 2GB of memory at most, and you're using your CPU at less than half-strength too.  The freezes are probably because you don't have the right driver for Nvidia graphics (just as you thought) since that needs its own special setup.

Since you've been reinstalling on a near-daily basis as is, I guess one more time won't matter?  If so, I'd suggest getting the 64-bit version of Karmic: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), click on "Alternative download options," and select "64-bit".  After it's downloaded, burn to a CD, and install from it the same as from your 32-bit LiveCD.

As for Nvidia, it's been a while since I had to fight with it.  I *thought* that Karmic went out and found the right drivers for it after you installed.  A little message pops up saying something like, "Your system needs restricted drivers.  Do you want to install them?"  Do you get that?  If so, what do you do then?  I'm hoping that if you get the right 64-bit version for your system, you'll automatically get the Nvidia driver you need, and all your problems will be solved :D.  (I know.  That would be too easy.)

---

### Post by thedarkside on 2010-02-22
thank's for info so far

i added memory 2 this last year
& your correct about the restricted drivers it comes while your doing your first updates when each time ive re-installed it (see it in me sleep).
 it then gives you three drivers 1 of which is highlighted saying we recommend this but  when its froze  again i use a different 1
but with the same problem ive been lucky this weekend its not done it since thursday.
also if i remember you burn the new disk with a iso ? heard someone mention it !!!
ps gonna have 2 take some time off gimp to start learning how deal with p.c. problems instead.
pps thanx once again very greatfull

---

### Post by quixote on 2010-02-22
Yeah, sometimes the recommended driver shouldn't really be recommended.  If you've found one that seems to work, stay with it and keep your fingers crossed! :S

To burn a downloaded .iso you can right-click on the .iso, and select "Brasero" to burn it with.  Accept the defaults, and it should work.  (Famous last words.) 

Hope this keeps working for you.  If not, search the forums for Nvidia 6150 and Toshiba Satellite.  There'll probably be more there than you ever wanted to know.

PS. I use gimp a lot.  great program.

---

### Post by thedarkside on 2010-02-23
cheers quixote

burnt it yesterday done a bit of read up 1st there was 2 options i think 2 burn the file or a 2nd option wasnt sure so i burnt both of em & it was the 1st one that worked checked disc for errors ok !!! i was actually pretty pleased with that 1st time.
and i did keep going through the list of drivers until i run out but came too nothing  
 i was gonna wait till ubuntu crashed 2 put the 64 bit on ,but gonna check where me parcels are online then go for it !!
ps did u know there supposed 2 be removing gimp off ubuntu for another programme ?

---

### Post by quixote on 2010-02-23
Let us know if the 64-bit install helps! (If you wind up with more crashes and installing it.)

(I have mixed feelings about not having gimp preloaded. It's just a click to install it, so it seems like it shouldn't be a big deal, but somehow it seems like a shame anyway.)

---

### Post by thedarkside on 2010-02-24
yeah i will do gonna do it in a minute ,was gonna wait till it crashed but nothing to lose if you dont hear from me for a bit its not crashed but will let you know either way, dont have any ide this thread is gonna stay on !!!
cheers for all so far.
:P:P

---

### Post by thedarkside on 2010-02-24
houston we have problems

no it went totally pearshaped straight away with a warning sign saying 'kernel problem!!! blah blah blah so i aborted while i could the screen didnt look right from the moment i looked @  it though...
i shall look at the suggestion you mad in a previous one cheers again i will let you know how i am coping..:confused:

---

### Post by quixote on 2010-02-24
Oh, %&*!#.  The only thing I can think is the CD didn't burn correctly, so I checked through what the CD/DVD creator does (aka Brasero).  The default "Burn File" is the wrong one for what you need.  Sorry that I told you the defaults would be okay!  You need "Burn Contents."  

(Rant: I dislike Brasero more or less intensely.  It's always pulling crap like that.  K3B is much better.  It'll pull in a whole bunch of KDE libraries, but it's worth it.  Can be installed via synaptic, if you decide later you want to try it. /Rant)

---

### Post by thedarkside on 2010-02-24
dont worry about it,your tryna help me out ive not got a clue i will burn it again in the way you have just suggested , is there a  need to delete the 32 bit 1's ? in  palimpsest i can do that in system/then disk utility ?
i will have 2 burn the disc again 2 moz got some crap paper work 2 do or me throat gets cut.
cheers

---

### Post by thedarkside on 2010-03-01
quixote 

searched & searched through the forumns many people had problems the hang's or freezes problem like mine.
there was quite that had compaq presaro like mine or hewlit packard some said they did not have the problem with eariler versions of ubuntu until 9.10 came out.. 
there was 1 guy cant remember he's name just quoted a link to another reply stating 'all of you with this problem ,follow this link'  it suggested that if u enabled the proposed karmic updates it that it would stop ,and it did (but not considering meself out of the woods yet touch been 4 days) .
cheers again 4 your effort's even though it didnt pay off learnt some stuff i didnt know from you cheers owe u a drink next time i'm in l.a.
:p:p:p:p

---

### Post by quixote on 2010-03-02
I hope it's still working!  And I like the idea of getting a beer for nothing. :mrgreen:

---

