---
title: "sudo apt-get install gtk+-"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by bharadwaj on 2011-01-22
Hi,

I wanted to install linuxdc++, so I started out with installing its dependencies first. I installed scon and g++ there another dependdecy which said gtk+- i ```
sudo apt-get install gtk+-
```
And then it prompted me to download 130 MB file and later I get that 700 mb would be freed, having no clue of what I was doing I hit yes. And later something happened and all the ubuntu default software were removed. Openoffice is no longer there icons are gone the panels are gone.

Anybody knows what just happened?

thank you

---

### Post by owaiskhan11 on 2011-01-25
why dont you try using software manager it directly install the required dependencies nad tthe correct code is

sudo apt-get install gtk+-2.0

---

### Post by rasgra on 2012-05-28
I am experiencing the same problem as reported above, "sudo apt-get install libgtk2.0+-" unfortunately does not help.

It's a kind of frustrating problem as I pretty new to Linux and it's hard to know if I'm looking in the right direction.

What I've currently found out is that "dpkg --get selections |grep gtk" list is way shorter after the libgtk2.0+- installation.

---

### Post by oldos2er on 2012-05-28
Closed. Please start a new thread for your question, this one's a year and a half old.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

