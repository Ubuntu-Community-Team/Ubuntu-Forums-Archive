---
title: "LAMP installation of Ubuntu 7.04 Server Edition can't accept incoming connections"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by nonyadb on 2007-04-25
Connection was refused from another computer on the network using IE and Mozilla, but the network connection is working on the LAMP installation because I was able to ping "www.google.com"

---

### Post by nonyadb on 2007-04-25
I found the answer myself and I thought I would put the answer here for anyone who has the same problem for the same reason.

The problem was that the option to install the LAMP server during the installation was the *only* option that required a checkbox to be marked. All of the other options during installation were selected by highlighting the choice and pressing "Enter", so I understandably assumed that the type of server selection would be the same.

This is something the developers may want to fix in the next version.

---

