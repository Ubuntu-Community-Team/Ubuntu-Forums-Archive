---
title: "Cant Install Anything From Software Center!"
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by Ashfaqur Rahman on 2013-04-06
I Cant Install Anything.
When I Click On Any Item In The Software Center It Extends And Two Tab Shows "More Info" at the left corner and "Install" at the right corner.
I Can Click On The "More Info" button but i cant click on "Install" button.Why?

---

### Post by ibjsb4 on 2013-04-06
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

Get any errors?  Try the software center again.

---

### Post by Ashfaqur Rahman on 2013-04-06
I Have Entered This Code In Terminal And Got No Error.
But Still Facing Same Problem :(

---

### Post by ibjsb4 on 2013-04-06
Try [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9"), see if that works for you.

```
sudo apt-get install synaptic
```

---

