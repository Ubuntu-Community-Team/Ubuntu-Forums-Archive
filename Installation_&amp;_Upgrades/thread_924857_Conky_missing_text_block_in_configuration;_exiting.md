---
title: "Conky: missing text block in configuration; exiting"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by KeybladeSephi on 2008-09-20
Hey everyone. I've heard great things about Conky, so I thought I'd try it out. However, whenever I type "conky" in the terminal, there is an error that says:

```
Conky: missing text block in configuration; exiting
```

How can I fix this? Thanks

---

### Post by Denestria on 2008-09-20
There should be a section at the end of your ~/.conkrc that looks something like...
TEXT
${color #A548CC}Date:${color}${font size=11}    ${time %a %e %b %G}${font}
${color #A548CC}Time:${color}${font size=11}      ${time %I:%M:%p}${font}
${color #A548CC}Uptime:${color}    ${uptime}
${color #A548CC}Kernel:${color}      ${exec uname -r|cut -b1-9}
${color #A548CC}Temp:${color}       ${acpitemp}C / ${acpitempf}F
${color #A548CC}CPU:${color}         ${freq_g}GHz  (${cpu}%)

---

### Post by KeybladeSephi on 2008-09-20
What if I have nothing in the conkyrc file? Should I just copy what you have in the text file you have attached? Thank you =]

---

### Post by Denestria on 2008-09-20
Give it a try or one of these.  It should be in your home directory and named .conkyrc

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)
You can customize it however you want.
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by KeybladeSephi on 2008-09-20
I have the file, but nothing's in there. Thanks, I'll see if I can get it to work

---

### Post by KeybladeSephi on 2008-09-20
Thank you, Destria, it worked. However, I see that it updates every 2 seconds. Is it possible to make it update every second?

---

### Post by Denestria on 2008-09-20
The configure line that controls this is **update_interval** or **music_player_interval**.

update_interval 1

---

### Post by equimen on 2009-03-15
Hi,

I am having the same problem with conky, but the difference is that I cannot fin the .conkyrc file in my home directory.

I've searched for it and everything, but still can't find it. I relatively new to Ubuntu, so I when you said"~/.conkrc" I dont know if I looked in the right place.

What should I do?

Thanks


EDIT: I just had to enable the view of hidden files, problem solved.

Now, the problem is that when I add Conky to the startup, it does not start up.

I Put the command :"home/ezequiel/.conky_startup_sh" but it doesn't work.

Any suggestions?

THank you

---

### Post by Usmaan on 2009-10-12
Copy and pasted but still the same message
Conky: missing text block in configuration; exiting

---

### Post by rduke15 on 2010-05-14
> **Usmaan said:**
> Conky: missing text block in configuration; exiting

In your config file, you need a single line containing "TEXT" without the quotes. The stuff you want displayed should be on the following lines.

---

