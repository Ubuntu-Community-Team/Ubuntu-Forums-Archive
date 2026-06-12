---
title: "[SOLVED] Firefox upgrade problems"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-09-24
I use AMD64 and got the notice to upgrade Firefox. I did! Restarted and:

1. There is no start page anymore
2. There is no search anymore
3. Edit/preferences is an empty ( tiny ) box

Any thing typed into the search box results in something like:
> ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias([http://ubuntuforums.org/](http://ubuntuforums.org/))
7:getEngineByAlias([http://ubuntuforums.org/](http://ubuntuforums.org/))
8:getShortcutOrURI([http://ubuntuforums.org/](http://ubuntuforums.org/),[object Object])
9:([http://ubuntuforums.org/](http://ubuntuforums.org/),[object Object])
10:([http://ubuntuforums.org/](http://ubuntuforums.org/),[object Object])
11:canonizeUrl([object KeyboardEvent],[object Object])
12:handleURLBarCommand([object KeyboardEvent])
13:anonymous(textentered,[object KeyboardEvent])
14:fireEvent(textentered,[object KeyboardEvent])
15:onTextEntered()
16:handleEnter(false)
17:onKeyPress([object KeyboardEvent])
18:onxblkeypress([object KeyboardEvent])


How can I fix that?

bye

R.

---

### Post by ELMIT on 2008-09-24
found it!

In another window Firefox was still running, ...
Completely stop firefox and restart solved it.

bye

R.

---

