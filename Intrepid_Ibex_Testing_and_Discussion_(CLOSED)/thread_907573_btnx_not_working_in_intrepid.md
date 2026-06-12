---
title: "btnx not working in intrepid"
date: 2008-09-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DLGandalf on 2008-09-01
does anyone have an idea how to get btnx working in intrepid?

OR

getting evdev (which is autoloaded in intrepid with the new Xorg) to export more buttons. Currently the Xserver configs the mouse to show 9 buttons to apps like compiz, yet the xev tool shows me that buttons up to 14 are necessary with a mx1000.

---

### Post by ru7hl3ss on 2008-09-17
Posting in case anyone runs across this thread and hasn't seen the news on btnx:

"September 14, 2008

Good and bad news. Bad news first. Ubuntu Intrepid Ibex, which is to be released in October, breaks the foundations that btnx was built on. It seems that the kernel input event pipes can no longer be read. It is most likely related X.Org v.7.4. This means I will stop all development of btnx.

Then the good news. It seems evdev is catching up with today's input devices and reports all buttons from at least an MX Revolution. There exist methods to bind these buttons to other events. However, all of these are somewhat laborous and cryptic. One option is to develop a new GUI and daemon for binding these X mouse button events, similar to btnx, but one that lives only in x-sessions. It would sniff the X mouse events and send alternate keyboard/mouse events through XTest.

I do not have time to do this by myself. However, if someone is interested in developing something, get in touch with me. I have a few ideas that I would be glad to share and might even help in development."

[http://www.ollisalonen.com/btnx](http://www.ollisalonen.com/btnx)

---

