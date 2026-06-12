---
title: "[SOLVED] Firefox problem in Ibex RC"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by oOarthurOo on 2008-10-24
I just installed Ibex on a computer that dual-boots XP, and has a shared NTFS partition with data and settings and such. I fired up Firefox from within Ibex by running "firefox -p" then pointed it at my existing profile on the shared partition.

It seems to work ok in most respect, however if I try to type anything into the address bar it gives me this error message:
```
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias(google.ca)
7:getEngineByAlias(google.ca)
8:getShortcutOrURI(google.ca,[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()
```

This occurs for example if I try:
google.com
[www.google.com](www.google.com)
[http://google.com](http://google.com)
[http://www.google.com](http://www.google.com)

This profile works fine on the windows side of things. Just for kicks I created a new default profile that rests entirely on the ext3 Ibex partition and the problem **DOES NOT** persist.

[I][COLOR="Silver"]Incidentally, if someone could tell me how to prevent keystrokes from turning into happy faces I would be much obliged.

Update: Change from quote to code fixes that issue.[/COLOR][/I]

Update: I have rebooted and restarted the profile and I am not able to reproduce the error. If I can't make it come back in a few hours I will mark this thread as solved.

---

### Post by oOarthurOo on 2008-10-24
I've been unable to reproduce the problem.

---

