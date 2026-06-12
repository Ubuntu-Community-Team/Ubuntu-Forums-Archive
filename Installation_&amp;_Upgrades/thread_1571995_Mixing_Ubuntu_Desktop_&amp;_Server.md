---
title: "Mixing Ubuntu Desktop &amp; Server"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by Segmaster on 2010-09-10
Hello all! I'm new to the forums as a user, but have been using them for many years to assist in my Ubuntu endeavors. 

Lately I ran into a question that prompted me to join, because I couldn't find the answer on the forums already.

I recently acquired an older computer system from a friend of mine. I upgraded its storage, cooling system and RAM to decent levels, and now I want to install Ubuntu on it. Here's the problem: I want to use it as a NAS drive in addition to the standard desktop environment, and possibly use it as a web server in the future. What is the best way to do this?

As a side note, I will need to be able to access the file server from PCs, Macs, and other Ubuntu systems. The computer will be using a 802.11n PCI card for its network connection. (No Ethernet, unfortunately)

Should I install Ubuntu Server Edition, then follow up with Gnome and the other desktop specific packages?

Or should I install the Desktop Edition and then install the server packages afterwards?

Any help with this would be greatly appreciated. Also, if you have a better suggestion than those I already mentioned, feel free to suggest it. I'm open to anything, really.

---

### Post by clrg on 2010-09-10
I suggest you go with the Desktop Edition, as it will be easier to add services to a desktop than it is to add a desktop to a server.

If you want to share data with other operating systems, Samba is what you want. For a webserver, use Apache2, lighttpd or any of the other ones available.

I strongly recommend you don't use wireless for data transfer. Get a real Ethernet connection. It will be much faster and more reliable.

---

