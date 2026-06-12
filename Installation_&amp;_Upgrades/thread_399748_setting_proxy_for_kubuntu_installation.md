---
title: "setting proxy for kubuntu installation"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by jfenwick on 2007-04-02
Hi,

I'm trying to install Kubuntu. I make it to step 6 and push install. The system seems to be fine until it gets to where it says scanning the mirror... then it just sits there at 2%. I suspect this is due to the fact that I'm behind a proxy. How do I set the proxy? I didn't see a field at any point during installation to set the proxy.

Thanks,

Jacob

---

### Post by spmsrh on 2007-04-02
I can't recall where to set the proxy, but I have a quick fix solution for now. Disconnect the network cable and proceed with the installation (for now). After installing, reconnect the cable.

to use apt-get, set the HTTP_PROXY environment variable in your .bashrc

---

