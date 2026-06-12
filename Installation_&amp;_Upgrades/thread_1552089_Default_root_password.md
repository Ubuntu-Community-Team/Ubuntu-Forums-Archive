---
title: "Default root password???"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by fuddlestack on 2010-08-13
Hi all, new chum on Ubuntu block. Worked with UNIX years ago, want to get back in.

Just installed the 10.04 netbook remix on spare Asus eeePC 900 to muck about with and see what's what.

Installation doesn't let me specify a root password, and none of the old chestnuts I remember from UNIX days work.

Qu. What is the default root pwd? Or is it a state secret?

TIA

JohnE

---

### Post by sikander3786 on 2010-08-13
Hi.

Welcome to the forums and Linux once again.

Root account is disabled by default on Ubuntu. You can use *"sudo"* for root previliges and *"sudo su"* for a root prompt (I am not sure).

You can set the root password by typing

*sudo passwd root*

Regards.

---

### Post by lisati on 2010-08-13
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kerry_s on 2010-08-13
root is locked in ubuntu, ubuntu is a sudo system. 
anything asking passwords wants your user password.

---

### Post by Gorilllanobaka on 2010-08-13
It is not...

The problem is ...doing stuff in root can result in nasty problems...(Trust me on this i`ve learned it the hard way :P)

Hence the reason you do not really have acces to it.

But you can "sudo" your way around...

You do not really need it...

---

### Post by fuddlestack on 2010-08-13
Thanks for the swift replies and the references, everyone. Yes, Gorillanobaka, I am aware of what horrors root can perpetrate - I used to teach UNIX, around 20 years ago.  Memory Lane has a few potholes in it, though.  I will sudo myself around carefully...

Cheers,

JohnE

---

