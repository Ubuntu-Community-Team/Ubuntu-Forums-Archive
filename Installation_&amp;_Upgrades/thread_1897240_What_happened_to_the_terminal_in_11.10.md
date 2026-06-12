---
title: "What happened to the terminal in 11.10?"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by ladasky on 2011-12-18
I just upgraded.  Wow, this is the worst Linux upgrade I've ever done, and I've been with Ubuntu since 6.04.  Fortunately I have some computer experience, so I'm not lost.  I'm annoyed, but I'm solving my problems one by one.

Anyway, some of my fixes apparently require me to go down to the command prompt.  So when I click on "Dash Home" and search for "terminal", I get these two antiquated-looking choices, XTerm and UXTerm.  They're both command-line terminals.  They're also identical, as far as I can tell.  Most importantly, they're stripped of even the most basic features that I came to expect in the terminal application from earlier revisions of Ubuntu.  Where's the menu?  Why can't I copy and paste from other windows?

Finally, I've installed ipython, a terminal-based application, and it invokes GNOME Terminal 3.0.1, a full-featured terminal application of the kind that I expect.  Where do I find GNOME Terminal?  Searching for it under "Dash Home" only brings up ipython.

Thanks for any help!

---

### Post by grahammechanical on 2011-12-18
I too have XTerm and UXTerm. I do not know why. I also have Terminal. I have never been without it. So I do not know why you do not have it.

Try searching for it in the Ubuntu Software Centre to see if it is installed. You might find that Synaptic Package Manager is not installed either. If you want to use Synaptic, that is.

Regards.

---

### Post by bluexrider on 2011-12-18
> **ladasky said:**
> I just upgraded.  Wow, this is the worst Linux upgrade I've ever done, and I've been with Ubuntu since 6.04.  Fortunately I have some computer experience, so I'm not lost.  I'm annoyed, but I'm solving my problems one by one.

Anyway, some of my fixes apparently require me to go down to the command prompt.  So when I click on "Dash Home" and search for "terminal", I get these two antiquated-looking choices, XTerm and UXTerm.  They're both command-line terminals.  They're also identical, as far as I can tall.  Most importantly, they're stripped of even the most basic features that I came to expect in the terminal application from earlier revisions of Ubuntu.  Where's the menu?  Why can't I copy and paste from other windows?

Finally, I've installed ipython, a terminal-based application, and it invokes GNOME Terminal 3.0.1, a full-featured terminal application of the kind that I expect.  Where do I find GNOME Terminal?  Searching for it under "Dash Home" only brings up ipython.

Thanks for any help!
I believe Ctrl+Alt+T should evoke a terminal

and/or Alt+F2 gnome-terminal

---

### Post by ladasky on 2011-12-18
> **bluexrider said:**
> I believe Ctrl+Alt+T should evoke a terminal

and/or Alt+F2 gnome-terminal

Thank you, bluexrider, both of those options work!  

Now, using Alt-F2, I see something strange.  As I type, the "Run Command" widget starts searching through possible applications for matches.  And it comes up with "gnome-terminal.wrapper".  What exactly does the "wrapper" part signify?  And why doesn't Terminal qualify as an application that you can search for with the "Dash Home" widget?

I guess these questions are not important now that I've found a decent terminal, but I have to wonder at the organizational decisions behind my difficulties.

---

### Post by bluexrider on 2011-12-18
> **ladasky said:**
> Thank you, bluexrider, both of those options work!  

Now, using Alt-F2, I see something strange.  As I type, the "Run Command" widget starts searching through possible applications for matches.  And it comes up with "gnome-terminal.wrapper".  What exactly does the "wrapper" part signify?  And why doesn't Terminal qualify as an application that you can search for with the "Dash Home" widget?

I guess these questions are not important now that I've found a decent terminal, but I have to wonder at the organizational decisions behind my difficulties.
don't know what a gnome-terminal.wrapper is?? haven't seen that one yet.

---

### Post by ladasky on 2011-12-19
> **grahammechanical said:**
> You might find that Synaptic Package Manager is not installed either. If you want to use Synaptic, that is.


Thanks, Graham -- after struggling for a few hours with Ubuntu Software Center, I decided there was NO WAY I was "upgrading" from Synaptic.

---

### Post by swajime on 2011-12-21
"worst upgrade ever" has been my experience also :confused:

I've been doing almost nothing but hunting for fixes for this bug, that bug, this isn't here anymore, and that isn't here anymore.

I just did a fresh install on somebody else's computer and I see that my mess is rather incomplete as well.

Thanks for the Ctrl-Alt-T tip.  :)

---

### Post by Gideo on 2012-05-14
The solution I have found. 

apt-get install gnome-terminal. 


Suddenly it came up with the same configuration previous to the upgrade.


C U

---

