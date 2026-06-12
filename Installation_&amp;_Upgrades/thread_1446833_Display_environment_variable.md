---
title: "Display environment variable"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by kakarala on 2010-04-04
Hi 

I am using ubuntu linux on windows7 using vmware. Can any one tell me how to set the display environmental variable
 I tried using command 

setenv DISPLAY hostname:0.0

 how do i select the numbers 0

---

### Post by Bachstelze on 2010-04-04
First, setenv is for csh-like shells. For sh-like shells (e.g. Bash) you use

```
export VAR=value
```

As for the values you need to set, we can't tell you the correct value if we don't know what you want to do.

---

### Post by kakarala on 2010-04-04
I am trying to use synopsis tools from the server.but to get gui i need to set the display environment variable. I cant set the display environmental variable

---

### Post by me13221 on 2010-04-05
It sounds like your question is about VMWare, not ubuntu.

---

