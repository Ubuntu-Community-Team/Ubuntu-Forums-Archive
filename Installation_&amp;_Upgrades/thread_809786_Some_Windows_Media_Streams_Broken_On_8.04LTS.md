---
title: "Some Windows Media Streams Broken On 8.04LTS"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by notrublw on 2008-05-27
Streaming CBC domestic services 
     [http://www.cbc.ca/listen/index.html#](http://www.cbc.ca/listen/index.html#)
which use windows media does not work on 8.04 LTS.  It did work on 7.10.
Both the links from the cities/studios listed on the above page, and the   
"Direct CBC.ca URLs for listening to CBC Radio"
     [http://www.cbc.ca/listen/streams.html](http://www.cbc.ca/listen/streams.html)
do not work, regardless of bandwidth option chosen.

What happens is that then one of these links is chosen, e.g.
     [http://www.cbc.ca/livemedia/cbcr1-toronto.asx](http://www.cbc.ca/livemedia/cbcr1-toronto.asx)
the "mplayer plugin" opens up, theres a real fast message about connecting to server (so fast I can't see the url), and then it just says "Stopped".
If one hits the "play" button in the lower left hand corner the same sequence occurrs.

ABC radio Windows Media streams ([http://www.abc.net.au/radio/](http://www.abc.net.au/radio/)) display the same behavior.

Some windows media streams seem to be working:
     [http://www.bbc.co.uk/6music/](http://www.bbc.co.uk/6music/)
     [http://www.bbc.co.uk/bbc7/](http://www.bbc.co.uk/bbc7/)
     [http://www.rte.ie/radio/](http://www.rte.ie/radio/)
     [http://www.jazzandblues.org/index.aspx](http://www.jazzandblues.org/index.aspx)

This is a real pain for the CBC as except for an 'experimental' (and slow) Ogg Vorbis stream of Radio 1 and Radio 2 they use Windows media exclusively.

Any ideas on what's going on and what I could do about it?  Thanks.

---

### Post by jimv on 2008-05-27
What happens if you right click on the .asx file link, save the .asx file, and then open it with movie player?

---

### Post by notrublw on 2008-05-28
That works.  So I need to set preferences to open up .asx files with totem?
Thanks.

---

### Post by jimv on 2008-05-28
I don't know for sure why that works...but maybe it has something to do with Firefox's network settings?

---

