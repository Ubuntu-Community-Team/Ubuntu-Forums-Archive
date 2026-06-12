---
title: "Log in to a ubuntu server from anywhere"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by snavier on 2007-07-30
Hi ubuntu users,

I am new on this forum. I have some questions about ubuntu.

I was send to work on a ubuntu server (with xubuntu desktop, installed with sudo apt-get install xubuntu desktop)


There is no icon on the desktop

1) Is this so by default?

2) How can you put icons on the desktop?

3) How can I figure out which version of ubuntu is installed on the server? Is there maybe a command to execute to see the version?

 I want to remote log in to the server.
So I went to: Applications - System - Synaptic Package Manager and so I select vnc-common to install.
I thought that I should see a vnc screen after I have done this steps but I can't see any vnc option.

What must I do further to install vnc on the server to login from a windows computer ?

I am looking forward for a reply.

Many thanks

Samuel

---

### Post by buntunub on 2007-07-30
"There is no icon on the desktop

1) Is this so by default?"

Not sure. I know that if you go to the xfce control panel, desktop, allow xfce to control, things just "worked" for me, including icons and the lot.


"3) How can I figure out which version of ubuntu is installed on the server? Is there maybe a command to execute to see the version?"

In terminal, "uname -r", or "uname -a" should tell you what you need to know, or at least what kernel version, which points at which version of xubuntu.

"I want to remote log in to the server.
So I went to: Applications - System - Synaptic Package Manager and so I select vnc-common to install.
I thought that I should see a vnc screen after I have done this steps but I can't see any vnc option."

Ubuntu comes standard with an application called "remote desktop" in the Internet tab area. You can use that and it has the same basic functionality of a simple vnc. It also comes standard with ssh client. So long as your remote systems are running the ssh server daemon, your good to go. There are a couple extremely good wiki's to get that setup at ubuntu wiki. To ssh/vnc into your ssh server from OUTSIDE the network, your router must be configured to accept incoming ssh requests (usually disabled by default). Seems complicated, but its really quite simple to setup. Pay close attention to your ssh servers sshd_config settings, and you should be fine.

"What must I do further to install vnc on the server to login from a windows computer ?"

As above. You need to install and configure the ssh server daemon. Default settings will probably do the trick for you, but without knowing your specific setups and requirements, its hard to say. From a Windows machine, just use Putty, which is the open source windows version of ssh/vnc and comes with a (somewhat complex) gui.

---

