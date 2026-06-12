---
title: "signed packages"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by JacekZ on 2008-04-10
Hi,
I tried to do the following:
```
apt-get -y install install audacity bluefish gnomesword gnucash gocr gramps gthumb gtypist gqview lynx nautilus-image-converter pdfedit renrot stellarium unison xpdf

```
..which failed with the message that I needed to use "--force-yes" as some of the files aren't signed.  The apt-get man page says don't do that.  But I did ..and it worked OK.  Still I'd like someone to explain to me how Ubuntu respoitories do the signing.  Everything I've read says they are signed, I believe that most if not all the above programs come from Universe.  Do I need to install a signature key or something for Universe?  I can't seem to find anywhere that tells me the official addresses of the respositories, what the apt-line for them should be, or where to find their keys, how to enter that into synaptic (which also says these programs aren't signed).  Now bluefish and gnucash are hardly obscure programs, so I'd expect them to be maintained and signed.  Perhaps someone could enlighten me on this.
Many thanks
Jacek

---

