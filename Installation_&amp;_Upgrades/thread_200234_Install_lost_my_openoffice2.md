---
title: "Install lost my openoffice2"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by dgermann on 2006-06-19
Hi--

I have just finished the upgrade on my third Ubuntu machine. If this goes well, then the fourth and last comes tomorrow or Wednesday.

But this one has lost my OpenOffice.org2 applications.

The only thing under Applications>Office are Evolution, Kivio and Kword. Reinstalling under Synaptic does nothing to allow it to work. Clicking on an .odt file produces only a list of the files inside it, rather than opening it. Right clicking on the file and using Open With does give me a choice of OpenOffice Writer, but clicking that returns an error "could not find ooffice2".

This is a production machine for my office, so I need it back quickly.

Any ideas?

---

### Post by stlutz on 2006-06-20
In dapper, the command to launch openoffice writer is "oowriter", not "oowriter2".

In Synaptic, are any of the versions you have listed the 1.9xxx versions?  Everything should be 2.02.

For me the upgrade removed openoffice, so I had to reinstall that afterward.

---

### Post by dgermann on 2006-06-20
stlutz--

Thanks for getting back to me so quickly.

All my installed versions of OOo under Synaptic appear to be 2.0.2.

I was able to get a semblance of OOo up by doing /usr/bin/ooffice. But it does not recognize any documents, nor even templates--it gives me a screen asking what filter to use for the document.

One thing I did with this installation in 5.10 was to edit the oowrapper file so that things pointed to the same places as in 1.9. I wonder if that is getting in the way somehow.

The other thing I can think to do is to remove it all (and lose all my templates and dictionaries and settings?) and reinstall, perhaps from the versions available at the OOo site. Not sure I want to do that yet....

Thanks, stlutz!

---

### Post by clarknova on 2006-06-20
I lost my openoffice2 as well. I was using it (1.9x, of course) in Breezy, and when I dist-upgraded to dapper, only writer and calc appeared in the office submenu, but they wouldn't run.

I edited the menu entry for writer, changing the command to ooffice, among others, but have not so far been able to elicit anything more than an openoffice splash screen, followed by nothing.

I have already reinstalled every OOo-related application I can find, to no avail.

---

### Post by clarknova on 2006-06-20
My goof. Apparently openoffice.org-kde does not depend on openoffice.org, which, when I installed it, corrected the problem. Hope this helps.

---

### Post by dgermann on 2006-06-20
clarknova and stlutz--

Thanks folks!

The problem seems to be solved. I was afraid of uninstalling and reinstalling, but that is what I did--deleted everything that said openoffice under synaptic and then only installed openoffice.org. That corrected all the problems I had noticed.

Oh, had to install the help file for english too--there are two and the one without the "2" in its name is the correct one.

Apparently there were some older versions of OOo on the disk that were getting in the way and this removed them.

The uninstall and install facility with synaptic seems to work extremely well. It preserved all my settings and templates etc. The only thing that does not seem to be there is a font called WingDings which I think I had before.

Thanks, folks!

---

