---
title: "[SOLVED] New firefox updates break browser"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by psychobillyjekyll on 2008-07-29
The new updates for firefox will break your browser. I just performed the updates a few minutes ago and noticed a)a loss of functionality and b)this assertation failure message when firefox is started > ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:updateDisplay()
10:init()
11:([object XULElement],5)


If anyone knows how to revert back to the old firefox or fix this error, please reply to this post.

Thanks,
Justin

---

### Post by tuxxy on 2008-07-29
> The new updates for firefox will break your browser. I just performed the updates a few minutes ago and noticed a)a loss of functionality and b)this assertation failure message when firefox is started

They will not break **everyones** browser, mine for one, firefox is running fine im posting from it right now.

---

### Post by wannadumpwindows on 2008-07-29
I just installed them, and it went fine for me. Restarted and everything. No problems at all. :)

---

### Post by psychobillyjekyll on 2008-07-29
Here is another assertation error
> ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias([http://ubuntuforums.org/showthread.php?p=5479216#post5479216](http://ubuntuforums.org/showthread.php?p=5479216#post5479216))
7:getEngineByAlias([http://ubuntuforums.org/showthread.php?p=5479216#post5479216](http://ubuntuforums.org/showthread.php?p=5479216#post5479216))
8:getShortcutOrURI([http://ubuntuforums.org/showthread.php?p=5479216#post5479216](http://ubuntuforums.org/showthread.php?p=5479216#post5479216),[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()
14:handleEnter(false)
15:onKeyPress([object KeyboardEvent])
16:onxblkeypress([object KeyboardEvent])


This error occurs when text is entered into the address bar such as "imdb" or "amazon.com" and enter is pressed.

---

### Post by tuxxy on 2008-07-29
You could try reboot/re-install firefox

---

### Post by psychobillyjekyll on 2008-07-29
Sorry, I feel like an @$$. I restarted the process again and now everything works again

---

### Post by Sef on 2008-07-29
> Sorry, I feel like an @$$. I restarted the process again and now everything works again

Don't feel too bad.  We all have felt that at one time or another.

---

