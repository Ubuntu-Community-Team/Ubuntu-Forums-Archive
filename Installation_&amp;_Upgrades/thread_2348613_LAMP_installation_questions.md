---
title: "LAMP installation questions"
date: 2017-01-05
forum: Installation &amp; Upgrades
---

### Post by jjhudak on 2017-01-05
In going through the install procedure for server 16.04 LTS there is an option to install LAMP package - How can I find out what versions of Apache, MySQL, PHP are installed if I choose this selection?
In choosing this selection, is there a subsequent menu that will let me choose the version of any component?  
Or would it be better to install each individual package manually?
Thanks
J

---

### Post by ian-weisser on 2017-01-05
> **jjhudak said:**
> In going through the install procedure for server 16.04 LTS there is an option to install LAMP package - How can I find out what versions of Apache, MySQL, PHP are installed if I choose this selection?
Before installation, you can check each package at Launchpad.net.
During installation, you cannot check...but you have only one choice anyway.


> **jjhudak said:**
> In choosing this selection, is there a subsequent menu that will let me choose the version of any component?
No.

Each release of Ubuntu (14.04, 16.04, 16.10, etc) is compatible with exactly one supported version of LAMP components, and that is the version you get offered. Only the supported version gets security fixes. That's the price for a free, open, secure OS with community support.

You can install any version of any software you wish...but that version will be unsupported. You are entirely on your own for locating, installing, and maintaining it...and repairing any damage to your system that the unsupported software caused.

This question usually means that you want to run some non-Ubuntu software that you are familiar with...and that you are unfamiliar with Ubuntu.
Ubuntu is not a drop-in replacement for your previous OS. There is a learning curve. As a server admin, you do have some basic responsibilities to learn.

> **jjhudak said:**
> Or would it be better to install each individual package manually?
Makes no difference. Exactly the same packages will be installed in exactly the same way.


Advice: Many first-time Ubuntu power-users destroy their systems by accident. You can make it much easier on yourself if you build your first test server inside a Virtual Machine. Explore the options, learn how package management and permissions and networking work. Take notes. Then build your production system after all the mistakes.

---

### Post by jjhudak on 2017-01-05
> **ian-weisser said:**
> Before installation, you can check each package at Launchpad.net.
During installation, you cannot check...but you have only one choice anyway.

snip...

This question usually means that you want to run some non-Ubuntu software that you are familiar with...and that you are unfamiliar with Ubuntu.
snip..


thank you for the reply.
I am exploring various 'cloud' (e.g. owncloud, nextcloud, etc.) + ubuntu configurations and I am trying to understand dependencies and associated tradeoffs - one example - Owncloud 9.1 admin notes indicate to use apache 2.4 and PHP 5...16.04 uses php 7, and not sure about MySQL and Apache... 
Actually, I am trying to minimize risk and avoid huge time sinks in putting owncloud for example under 16.04.  
My impression is that most development efforts of the *cloud projects are 'out of synch' with LTS supports Linux distros (well, at least Ubuntu)....but then again, I've only been looking at the situation for a week or so...
Appreciate the insight.
btw, I've used VM's a lot in trying out new systems (and a couple of VMs at that).  I have run into issues with that approach that complicated the process, so I've cobbled together some 'generic' i86 platforms and simply swap in clean HDs to experiment with.
MUCH cleaner that way. If I don't like the result, scrub the HD and on to the next config.
J

---

### Post by SeijiSensei on 2017-01-05
If you want PHP 5 just install server 14.04 instead of 16.04.  14.04 has [support through 2019]("https://wiki.ubuntu.com/Releases").  Plus you'll get the added benefit of not having to deal with systemd!

---

### Post by jjhudak on 2017-01-05
thanks, but that is just one example.  there are others.  the version of my SQl in 14.04 is not the same as in 16.04...Now what would I do?  this going back and forth  between LTS versions is not going to work.....I'd prefer to stay with 16.04
K

---

### Post by jjhudak on 2017-01-05
thanks, but that is just one example.  there are others.  the version of my SQl in 14.04 is not the same as in 16.04...Now what would I do?  this going back and forth  between LTS versions is not going to work.....I'd prefer to stay with 16.04
K

---

### Post by cruciatus on 2017-01-05
I suggest you to install Bitnami LampStack. It's the bets option to have all you need to test and develop localy.

---

### Post by jjhudak on 2017-01-05
> **cruciatus said:**
> I suggest you to install Bitnami LampStack. It's the bets option to have all you need to test and develop localy.

Interesting, thanks
Could you please elaborate why, given my platform and using ubunt 16.04, why you think this approach would eliminate the dependency questions with the bitnami lampstack and *cloud?  Aside from a VM sandbox, does it help anything??
Thanks
J

---

### Post by cruciatus on 2017-01-07
1. You can Install many Bitnami LampStack and get them running without confict.
2. It's easy and simple to install. At most 2 clicks.
3. You get many useful frameworks, as zendframework, cakephp, and much others.
4. You can install it** without VM machines or cloud**. Select a local folder and run.

---

### Post by cruciatus on 2017-01-08
I have some Drupal sites in production, running on shared hosts and on  private server machines. All developed and tested using my local Bitmani  Lamp Stack.
They do not have dependencies related to bitnami or any cloud service provider.

---

