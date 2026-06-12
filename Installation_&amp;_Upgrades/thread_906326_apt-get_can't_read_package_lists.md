---
title: "apt-get can't read package lists"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by iBalaganof on 2008-08-31
Hi everybody,

  It seems like recent Hardy update messed up my system. I can't get updates anymore nor can I do anything else with apt-get. When I get either of the below:
sudo apt-get update
sudo apt-get remove <pkg_name>
sudo apt-get -f install

I get the following:

Reading package lists... 0% 

  and that's it - no more progress - just sits there for ever and never halts.

  Does anyone have any ideas about the cause of this problem and know how to fix it?

---

### Post by Structed on 2008-09-01
I have the same problem.

Just installed frshly from CD in a VMware. apt couldn't get a conection to the package server during the install.  So this could happen because the vm-network. so after install I successfully configured my eth0. when I ping the package mirror, I get a pong.

But apt - it just gets 0% when connecting...

---

