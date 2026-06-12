---
title: "Firefox, User agent switcher"
date: 2008-09-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by plun on 2008-09-23
I am using this addon for switching identification

[http://packages.ubuntu.com/intrepid/useragentswitcher](http://packages.ubuntu.com/intrepid/useragentswitcher)

I am trying to add a XML file to the agent.

[http://www.user-agents.org/](http://www.user-agents.org/)


I got import errors and is Ubuntu/Linux using a special XML format ???

---

### Post by ubulette on 2008-09-28
You can export from that Addon and compare the format.

It looks pretty simple, it's just a list of <useragent/> like this one:

```

<useragent description="Netscape 4.8 (Windows XP)" useragent="Mozilla/4.8 [en] (Windows NT 5.1; U)"
appname="Netscape" appversion="4.8 [en] (Windows NT 5.1; U)"
platform="Win32" vendor="" vendorsub=""/>
```

---

