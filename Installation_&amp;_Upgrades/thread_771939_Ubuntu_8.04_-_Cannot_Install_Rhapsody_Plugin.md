---
title: "Ubuntu 8.04 - Cannot Install Rhapsody Plugin"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by mtb142 on 2008-04-28
I'm trying to use Rhapsody (the web based version), but I can't install the Firefox plugin.  I'm running Ubuntu 8.04 and using Firefox 3 Beta 5.  I can get to the point where it downloads and starts to install the plugin, but then a message pops up that says,

"Firefox could not install this item because "install-l71..rdf" (provided by the item) is not well-formed or does not exist. Please contact the author about this problem."

I click OK to that then another message says,

"Firefox could not install the file at 

[http://forms.real.com/real/player/download.html?f=unix/rhapx/RhapsodyPlayerEngine_Inst_Linux.xpi](http://forms.real.com/real/player/download.html?f=unix/rhapx/RhapsodyPlayerEngine_Inst_Linux.xpi)

because: Unexpected installation error
Review the Error Console log for more details.
-203"


The error console lists a bunch of lines that look something like this:

Failed to load XPCOM component: /usr/lib/xulrunner-1.9b5/components/libpyloader.so




I used to use Rhapsody fine on Ubuntu 7.10 with Firefox 2 so I'm thinking it's something to do with the new version of Ubuntu and/or Firefox.

Anyone else have this problem or know a solution?

Thank you

---

### Post by gmendoza on 2008-04-28
Having the exact same issue here on two machines.  It appears to be a Firefox compatibility problem with their installer.

Someone has posted the first request for help on Reals site, and I have posted the second message with some error details.  Hopefully they can fix this quick.

[http://real.lithium.com/real/board/message?board.id=InstallingRhapsody&message.id=29597](http://real.lithium.com/real/board/message?board.id=InstallingRhapsody&message.id=29597)

---

