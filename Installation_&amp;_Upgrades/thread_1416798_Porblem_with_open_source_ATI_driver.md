---
title: "Porblem with open source ATI driver"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by Flaffen on 2010-02-26
I have the open source drivers for my ATI card, but when I try to run WoW in wine I get a error message that reads:

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  228
  Current serial number in output stream:  228

I've tried to find something about this and it seems its a common problem with Karmic. Problem is that I'm still a n00b with Ubuntu and I have no idea what to do.
I cant install the proprietary fglrx drivers as they dont support my card.
My ATI card is Radeon 9200 PRO, and I'm running Ubuntu 9.10.

Can anyone help?

---

### Post by Flaffen on 2010-02-28
Does anyone have any idea what this could be?

I'm in desperate need of help.

---

### Post by Flaffen on 2010-02-28
And when I write:
glxinfo | grep rendering or
glxinfo | grep
in terminal, I get this error too:
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

I have no idea what this is, but I'm guessing that my X or graphics drivers are not functioning properly.

Does anyone have any idea?

---

### Post by Mark Phelps on 2010-02-28
It could very well be that the level of 3D acceleration that WoW demands can not be met by the open source drivers.

But, given the card you have, and the lack of ATI drivers for your card that will work with 9.10, you have no source other than to use the open source drivers.

You might get more detailed help if you post this in the Wine subforum ...

---

