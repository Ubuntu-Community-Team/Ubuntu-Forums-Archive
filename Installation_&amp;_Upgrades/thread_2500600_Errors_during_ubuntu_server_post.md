---
title: "Errors during ubuntu server post"
date: 2024-09-06
forum: Installation &amp; Upgrades
---

### Post by rfxd on 2024-09-06
Hi!. First of all, i want to thank all the forum members that are helping people like me with their problems. My problem is that when I boot ubuntu server after i installed it, it gaves me this error: "i2c i2c-1: sendbytes: Nak bailout". I test from the 20.04 version to the 24.04 and still gives me the error. What is causing this?

---

### Post by TheFu on 2024-09-06
In general, the way to find solutions for any error is to take that error, and use it in a web search, then look through what others have done to solve it.  So, which of those other solutions did you try already?  What about each, be detailed, didn't work?

Best if you show the exact commands used and the _relevant output._ 

When looking through errors in logs, look a little above and below the error you think is a problem.  Often, the error we see isn't really the first actual error causing all the problems.

---

### Post by rfxd on 2024-09-06
I searched the error online and what i found is mainly grapichs drivers issues. I tried some solutions that i saw on other posts, but that didnt woked. Now i dont really know what do i do now

---

### Post by TheFu on 2024-09-06
I'll say it again.

> **TheFu said:**
>  So, which of those other solutions did you try already?  What about each, be detailed, didn't work?

Best if you show the exact commands used and the _relevant output._ 

When looking through errors in logs, look a little above and below the error you think is a problem.  Often, the error we see isn't really the first actual error causing all the problems.

Hard to help without the requested questions being answered.

---

### Post by rfxd on 2024-09-06
-Beacuse I have a hp server, I tried upgrading and downgrading the ilo firmware. Then y deleted and did again the raid configuration and nothing. Still the same error. 

- It hapens sometimes, for example now it doesn't fails. It normally occurs at the tiem that output the task with a green "Ok" .The exact output of the error is : [243.58] [COLOR=#000000]i2c i2c-1: sendbytes: Nak bailout. It keeps hapening also after you log in. I have noticed that one time it didn't boot and have to reset the server.l[/COLOR]

-I am quite new to the ubuntu os, and i dont really know where can i find the log, so if you can let me know, it will be helpful

---

### Post by TheFu on 2024-09-06
[https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) will be helpful for some basic knowledge that all server admins need to know. Also, help.ubuntu.com has information for searching/reading system logs efficiently. Are there known issues with your exact server model and Ubuntu or Linux?

---

### Post by rfxd on 2024-09-06
Thanks for the info, I will take a look. My server was just running fine on ubuntu until some days that i noticed the error

---

### Post by rfxd on 2024-09-07
UPDATE: now it seems to work. It gave me a error about unstable clock, so i changed the bios battery at the motherboard and now seems to work. Thanks for the help

---

### Post by TheFu on 2024-09-07
> **rfxd said:**
> UPDATE: now it seems to work. It gave me a error about unstable clock, so i changed the bios battery at the motherboard and now seems to work. Thanks for the help

Logs are useful.  For anything that isn't obvious, ALWAYS start by looking at the logs.  Everyone's eyes gloss over the first 50 times, but it does become more familiar and you'll get better at it.

BTW, who would have been able to tell you to check the BIOS battery from the error you posted?  "not nobody"   I haven't had a BIOS battery fail in over 15 yrs, so definitely not me.  I did have a chromebook brick itself because I left the main battery disconnected too long - that model doesn't have any BIOS battery. The BIOS is maintained from a small capacitor and/or the main battery only.

Lastly, when an issue is solved, please, please, please, mark the thread as SOLVED using the thread tools button. Helps both people searching for answers AND saves people wanting to help from wasting their time once something is SOLVED already.

---

