---
title: "Package Manager Problem"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by FukanzenNa on 2008-06-16
I currently have a functioning install of ubuntu hardy, well it was functioning anyways. I was leaving my computer on for a little while longer than usual because I was downloading a file by means of bit torrent (however I think this has no connection to the main problem). After I came back to my computer I noticed a red minus sign where the update manager panel icon should be and when I hovered over it, it said "A problem occurred when checking for updates". When I tried to open up the update manager by clicking on it, it tried to start up the manager and then failed (closed before the window did anything). I tried opening the synaptic package manager thinking I'd fix the problem from there, same thing happened. I went the the add/remove applications just to check, same problem, loads the window and then fails. I had no idea what to do from a terminal for this particular situation and so I decided to wait on that. I would like to know what the possible causes for this problem are, and then maybe a way I could fix it from the terminal (seeing as though I can't add/remove packages of any type any other way).

---

### Post by iaculallad on 2008-06-16
Using your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by FukanzenNa on 2008-06-17
Thanks, it worked like a charm. I owe you one, I was going to just reinstall hardy because I'm not creative and didn't know how extensive this problem was. But thank you very much! (^-^)

---

