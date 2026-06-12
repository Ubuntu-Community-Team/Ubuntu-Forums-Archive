---
title: "bash script help"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by sephirothsigep on 2008-02-03
alright so I am trying to write a bash script that will open firefox for me and then do some stuff and then close it for me. i have everything working but the closing of firefox. i can not figure out the regular expression to send to the command kill so here is what i have so far
```
ps -C firefox-bin  | xargs grep '\>[0-9]' | xargs kill
```


ps -C firefox-bin returns the following 
```
  PID TTY          TIME CMD
17074 ?        00:01:38 firefox-bin
```
I need the 17074 out of this output from ps and none fo the other junk so that i can give it the kill command. any help would be great

---

### Post by Dennis on 2008-02-03
I´m totally new to this stuff, but is this any help?

kill $(pidof -x firefox)


from: [http://www.tldp.org/LDP/abs/html/system.html#KILLPROCESS](http://www.tldp.org/LDP/abs/html/system.html#KILLPROCESS)

---

### Post by LaRoza on 2008-02-03
What about:

```

killall firefox

```

---

### Post by jonmack on 2008-02-03
The special var ```
$!
``` gives the PID of the last executed process, so you could save that to a variable or a file immediate after you fire up firefox.

[EDIT] Then use that that variable in a kill command, obviously...

Cheers,

---

