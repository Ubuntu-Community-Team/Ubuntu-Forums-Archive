---
title: "Unable to load facebook on 11.04 in any browser"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by bhupinderjitbawa on 2011-05-17
I just installed new ubuntu 11.04 ...and i wondering why i m not able to open facebook on any web browser.
Facebook opens but it takes too much time and doesnt show except few links no visuals at all..
look at the screenshot attached...
any solution??i have tried by clearing browsing data and  updated 11.04 so many times....

---

### Post by gsmanners on 2011-05-17
Looks like their style info and/or scripting has gone poof. If you ask me, that's a problem between where you are and whatever servers FB uses for that stuff (i.e. it's your ISP's fault so call them bug them about it).

---

### Post by silex89 on 2011-05-17
I agree, the problem is with the ISP or the network you are in has Facebook blocked, some routers are configured that way in my university, and when you try to log in in FB shows exactly the same in your browser. All the other webs are normal....


Regards and good luck! :D

---

### Post by bhupinderjitbawa on 2011-05-18
one thing i forget to mention that i have  dual boot os with window 7 and ubuntu 11.04... 
facebook is working pretty well on window 7 .but **ubuntu** has this kind of problem

---

### Post by bhupinderjitbawa on 2011-05-18
thank god i found solution..
previously i was creating dsl connection through network manager.

now i have established connection through ```
**$pppoeconf**
$pon dsl-provider
``` solved my problem...
thanx for the hint..

---

### Post by dineshs on 2011-05-18
> previously i was creating dsl connection through network manager.

I think the problem is with MTU.The default value is 1492 while using the command  line while NM uses 1500.If you want to use NM set MTU value as 1492 as explained [here]("http://ubuntuforums.org/showpost.php?p=10075155&postcount=2")

---

