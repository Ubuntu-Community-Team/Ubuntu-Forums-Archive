---
title: "How to update 20 machines automatically."
date: 2018-12-24
forum: Installation &amp; Upgrades
---

### Post by luca-dgh on 2018-12-24
In our institute I have 20 HP all-in-one machines (one per classroom) with ubuntu 18.04 plus one server, ubuntu 18.04 as well, that I can use to remotely manage all the machines.
Now I have to find a method to update these machines automatically. I red [AutomaticSecurityUpdates]("https://help.ubuntu.com/community/AutomaticSecurityUpdates") from the wiki, but that solves only half of the problem. I mean, what about a kernel update that usually ask for the password? Or what about firefox (or other packages) that sometimes gives important updates not necessarily about security? What about a package that requires to install a new library so the password is needed?
Finally, aprox 2-3 times per month we receive a new version of the kernel: how to remove automatically the previous versions?
I can't figure myself spending hours going on every machine and doing manually all those operations.
Any suggestion?

---

### Post by Tadaen_Sylvermane on 2018-12-24
Only 3 options come to mind for me. There may be better options, but this is what I got.

First, give yourself ssh access to each machine, then you can run them over a terminal that will work as a local terminal on each machine. Then just update as you would any other machine at a terminal.

Other option is more drastic. Assuming you have wired networking, maybe look into PXE booting these machines with LTSP. It is designed for classroom use. Single point of control. Update the image on the server and reboot the clients for each to be updated fully. Very simple. Requires it's own DHCP server though, not to much trouble but depends on your network. I use LTSP at home to pxe boot media centers. Only have a couple right now but it is much simpler than trying to manage each machine separately.

There are other enterprise options for managing multiple machines, but I feel they would be serious overkill depending on your use case.

Lastly there is the unattended-upgrades package. I do not use this, so don't know how well it would work for you. Not sure if it is just security updates, or can be configured to do all updates. Certainly worth researching.

---

### Post by The Cog on 2018-12-24
It may be worth looking at **ansible** which is an application designed specifically for managing large numbers of machines like this. It has a requirement that it can use SSH to log into the machines, and it is usual to arrange a passwordless SSH for it (using public keys). Other than that, no changes are needed on the target machines. Ansible itself runs on your controlling machine (your laptop perhaps?) Ansible then has a task list in a playbook that it runs through. Once it is set up, telling it to update the kernel on 20 machines should take just a few minutes. The time spent learning about ansible may 
[https://www.google.com/search?q=getting+started+with+ansible](https://www.google.com/search?q=getting+started+with+ansible)

---

### Post by CatKiller on 2018-12-24
It's probably also worth looking at setting up a local cache for the upgrade files. No sense in getting them from the Internet 20 times when you only need to do it once.

---

### Post by luca-dgh on 2018-12-24
Thank you tadae, my network now is on Wi-Fi, not wired so I can't use LTSP.
But the suggestion from catkiller is very interesting, I'll look for tutorials on the net.
Thank you all.

---

