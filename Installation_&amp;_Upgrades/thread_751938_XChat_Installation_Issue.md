---
title: "XChat Installation Issue"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by Johnnny on 2008-04-11
I have the latest version of Ubuntu 7.10. I can't seem to install XChat. When I try to install XChat over in Add/remove I get an error:

"Cannot install xchat. This application conflicts with other installed software. To install XChat the conflicting software must be removed. Switch to the Synaptic Package Manger to resolve this conflict"

The problem is I don't know which software it is conflicting with. Any ideas?

--
EDIT:
 Nvm, I managed to solve it.

---

### Post by Erin on 2008-04-11
Would you care to post 'how' you solved it?

---

### Post by Johnnny on 2008-04-12
Sure....I went to Systems, Administration, Synaptic Package Manager, settings, repositories. In Ubuntu Software tab, make sure all boxes are checked except for the following:

 - Source code
 - Installable from CD-Rom/DVD (Officially Supported)

After that I hit the "Reload" button. Went to Add/Remove in Applications and installed XChat.

---

### Post by Erin on 2008-04-14
Glad it worked for you. Of course it now means people can now see a method that may work for them.

E.

---

