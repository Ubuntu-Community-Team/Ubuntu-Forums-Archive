---
title: "Adept &quot;add repository&quot; adds foreign character+dies"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by Ubuntiac on 2007-02-16
For some reasone when I add a repository, either via adepts "Manage repositories", or editing sources.list with nano / kate, it shows fine in sources.list, but adept shows the distribution part appended with a y with an umlaut (the two dots above it).

It then crashes any time I try to "Fetch updates" until the new line is removed.

It's done this since I first used ubuntu dapper (and now in Edgy and Feisty)

Any ideas?

---

### Post by Ubuntiac on 2007-02-16
Seems there's some generally invisible character required at the end of the line for any new repositories or adept doesn't work.

If you edit sources.list manually in kate (in kubuntu) and presumably gedit (in ubuntu) you can see this mysterious character at the end of all the other lines. It's like a full stop / period but smaller.

to do this just enter:
```

sudo kate /etc/apt/sources.list
```

in kubuntu

or:
```
sudo gedit /etc/apt/sources.list
```

in ubuntu (though I haven't tested whether the mystery character is visible in gedit)

Just copy it from another line to the end of the repository you're adding and voila!

Worked for me anyway! :KS

---

