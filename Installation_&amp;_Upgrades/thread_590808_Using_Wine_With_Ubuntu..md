---
title: "Using Wine With Ubuntu."
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Michaelin on 2007-10-25
I have Ubuntu Studio 7.10

I have just a beginner's knowledge and skills and need some help with understanding and using Wine. I understand the arguments regarding using native programs and dual booting etc. but the program I want to start with is Finale Notation Editor and this is reported in the Finale Forums to work well under Wine. I have allocated the entire hard drive to Ubuntu.

I have Wine installed but don't know where to go from here. Please excuse me if I ask some silly questions. I am new to all of this. 

(1) Do I need to have Windows XP installed to use Wine?
(2) I have Wine installed. How do I access it, where do I find it?
(3) How do I install my WinXP application to run under Wine.
(4) Once installed, how would I run the program.
(5) Does Win4Lin run Windows apps any better than Wine?

I really would appreciate help with these.

Many thanks.

Michael

---

### Post by Shazaam on 2007-10-25
psssttttt! lookee here.....
[http://www.linux.com/feature/118302](http://www.linux.com/feature/118302)
lilypond, noteedit, rosegarden, denemo can be installed through Synaptic.

1. No.  Consider the Wine program to be a simplified OS (not correct but used as an example). It makes a "fake C drive" that you install programs to.
2. Open a terminal and enter something similar to this
```
wine filename
```
where "filename" is the name of the program you want to run. You can also right-click the ".exe" and choose "Open with Wine"
3. See above.
4. "  "
5. I don't know.
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

After you install wine, a good thing to do IMHO is to install winetools.

---

### Post by Michaelin on 2007-10-25
Thanks for your reply.

I don't mind giving Rosegarden a try but it wont even open.

I've tried and tried but all I get is the opening icon and then it freezes and I have to reboot.

I've posted a separate thread about this but if you have any suggestions I'd be grateful.

Thanks.

Michael

---

### Post by jonkulp on 2008-02-18
I've gotten the Finale 2008 demo to install successfully under Wine, with only slight issues (piano brace displays oddly, ties look kinda funny).  All the notes look right, it opens my Finale files just fine, and after a bit of experimenting I found a way to get playback (important).  I wasn't able to get Finale 2006 from an install disc to install correctly, though.  Kept running into a wall when it asked me to install Java for Windows (already had Java environment installed but I guess WINE the Finale installer didn't recognize it).  

In any event, all you need to do is go to the command line, type "wine" and then drag the Finale setup.exe file icon into the terminal, then press return to start the Finale Installer.  There's a good article about this by Brian Bondari at this address:

[http://www.habibbijan.com/articles/run-finale-2007-on-linux-with-wine/](http://www.habibbijan.com/articles/run-finale-2007-on-linux-with-wine/)

You can also read my blog about setting up the audio part to get playback if you want:

[http://jonkulp.blogspot.com/2008/01/running-finale-on-linux.html](http://jonkulp.blogspot.com/2008/01/running-finale-on-linux.html)

I've been trying out Lilypond recently and it seems like a very powerful program.  I have no problem entering notes and slurs and dynamics.  All that is pretty straightforward, even just writing the code without a GUI.  The problem for me is making the finer adjustments--positioning expressive markings just right, displaying courtesy accidentals, stuff like that.  I must be putting the code in the wrong place b/c I keep gettning errors.  The GUI I tried out (GNU Denemo) was good only for note entry, as far as I could tell.  I couldn't use it to position dynamic markings, for example.  It's easy enough to enter notes as plain text, but the other stuff needs a GUI.  Still, if you're good at writing code and are comfortable with that environment, Lilypond could be an excellent alternative to Finale.  I think I'll probably just keep using Finale though, the one proprietary application I still find essential. 

Good luck!

JK

---

