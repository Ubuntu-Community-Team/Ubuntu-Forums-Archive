---
title: "Niggling problems after upgrade--&quot;the thick plottens&quot;"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by questant on 2010-08-26
I've completed an upgrade from 9.04 through 9.10 to 10.04 (Lucid).  I have found a number of menu items do not function following the upgrade:

About Ubuntu: Busy wheel but no window or text
Help & Support:  Busy wheel but no window or text
Report a Problem:  Busy wheel but no window or text
Screensaver:  Will set choices for screensaver pictures but will not release necessity for password regardless of setting.
Applications>Other>Menu Editor [gmenu-simple-editor]:  Setting or removing check marks for games has no impact on the Applications menu
System>Preferences>Main Menu [Alacarte]: works the same as amenu-simple-editor and will not respond to Games menu changes.

I wonder how many more of these will likely surface.  I suspicion we are dealing with some bugs here but, unfortunately "Report a Problem" doesn't function so reporting these requires going around "Robin Hood's Barn" to open a report.  Having asked about "About Ubuntu" and "Help & Support" some days back with no responses, I am not optimistic with this one.  But a special thanks to anyone who will respond to this (these) issues (especially "Report a Problem").

---

### Post by mörgæs on 2010-08-26
How does the machine work, if you boot a 10.04 live CD? This will tell whether the hardware does not like 10.04 or whether something went wrong in the update process.

---

### Post by questant on 2010-08-31
mörgæs:  Sorry it took so long to answer your question.  As the installation was done as an on-line upgrade, I did not have the cd etc.
I have booted with the Live CD and am now replying to your question from that instance.  I now have "About Ubuntu" and "Help and Support" coming up just fine.  I would therefore conclude the problem is not an hardware problem  It is either an executable problem or a missing documentation link problem.  In the past, I've noted other programs that run Ubuntu/Gnome will start, not find their documents and quit without an error message or any indication of any error.  In this case, I suspect either a corrupt executable or a missing document or faulty link.  The problems are:
I cannot find the name of the executable that starts those applets.
I cannot find the document names being called.
I cannot activate a Properties box for those applets.  I therefore assume the executable code must either be built into Gnome or into some other feature of the interface that is screened from the user.
I do not have access to "Report a Problem" in the Live-CD.  It is not, by default, on the "Other" menu.  I did edit the menu and then try the applet.  It failed.  But given the fact I am running the live-CD, I would anticipate there might be complications in the compilation of the hardware and configuration list this applet prepares for a problem report.  So I suspect the Live-CD test is likely not valid for its functionality not only on this system, but any system.  Please correct any misconceptions I might have made here.  While I am not a novice, I have vast barns of ignorance and relish the opportunity to fill them with correct information rather than bogus assumptions.
Thank you in advance for any further assistance.
I have done a bug report through other channels but am not sure I selected the right vector of entry for that purpose.

---

### Post by mörgæs on 2010-08-31
I believe that a boot with a live CD is indeed one of the best tests you can do before installing. 

There are many questions like yours in the fora. It is likely that something went wrong during the online upgrade, and hence a fresh install will solve the problem. 

Rather than trying to investigate and troubleshoot the system I would go for a new install of 10.04. Best is to have wired internet access while installing.

---

### Post by questant on 2010-09-01
Thank you for your response.  I will determine if there is any data I need to preserve (inevitably) and the back it up.  With a fresh install, there is another, more pressing issue and that is custom configurations.  I shall look for a utility that will possibly automate a back up of configurations as well.  To be honest about it, I've not been one in the past to jump to the fresh install because I learn a great deal more solving the glitches and conflicts in spite of the time it takes.  But thanks once again for your response and I will likely do a fresh install.
I did notice that when I checked the CD to see if it would properly read before a reboot, I was automatically asked if I wanted to add the cd as an upgrade repository.  Is there a way to install over an existing install as an upgrade.  Some OSs permit installation on top of themselves to solve corruptions--a convenient Microshaft feature in the past (I make a living as an intransigent problem trouble-shooter for the M$ OSs).

I would still like to know what executable actually renders the About and Help windows and also the actual names of the docs they render from the menu.  I haven't had much luck finding such a discussion on the net on those subjects and I'm usually pretty successful with search engines.  I cannot even determine whether or not it is a Gnome function or an Ubuntu function rendered into Gnome.  In any event, thanks again for your feedback

---

