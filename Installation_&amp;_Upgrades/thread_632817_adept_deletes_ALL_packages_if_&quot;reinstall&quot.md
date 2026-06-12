---
title: "adept deletes *ALL* packages if &quot;reinstall&quot; chosen"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by moron on 2007-12-05
Howdy.  I recently upgraded from Feisty to Gutsy (Kubuntu) and the process seemed to go perfectly other than having to update my video driver to get OpenGL support back.  I noticed that I had lost overlay support in mplayer and so decided to try a re-install of of the libxvl library in case that would fix things.

I launched adept, searched for libxvl and then once it was found, right clicked to get the menu option for "reinstall".  When I hit "apply changes" I was given a dialogue  that was stating that all sorts of things were being removed.  Initially I did not clue in but then realized that Adept was deleting *everything* (it had deleted a bunch of KDE before I finally clued in and killed it).  At the top of the list was *adept* - I had to use apt-get to actually re-install adept (luckily that was still around),

I am now in the process of trying to get everything back though things seem a little wonky (when I re-started KDE it acted like it was the first install).

Anyway, has anyone encountered similar behaviour with Adept? Any suggestions on how to narrow down what all got deleted?  Also, any ideas as to what the (&^*%&%$ was up with Adept?  I am assuming that "rm -R *" is not normal behaviour for a single re-install selection.

=)

Cheers

---

