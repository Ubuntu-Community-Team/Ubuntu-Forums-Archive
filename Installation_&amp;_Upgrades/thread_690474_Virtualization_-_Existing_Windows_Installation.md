---
title: "Virtualization - Existing Windows Installation"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by gunksta on 2008-02-07
Howdy Folks,

Linux and I went through undergrad,  a couple of jobs, and grad school together. I deleted Windows from my computer in 2000 and never looked back. Well, here I am in 2007 and I am working in a consulting firm . . . . using Windows!  :(

You have got to help me.

Our company has practically no IT structure/regulation so I immediately installed OOo, Fire Fox, Thunderbird, etc. to my laptop. But I really need to get off of Windows. Unfortunately, I have some requirements that make a complete break with Windows difficult (at least in the short-term). The company is offering to buy me a new Dell and I'm thinking about getting a system that I know they also sell with Ubuntu pre-installed. After I get it in my hot little hands, I want to partition the drive and install Kubuntu onto the system (rKward!, Kate!, etc. are sorely missed).

But I will still need to be able to open and distribute MS Access databases, Complex Word 2007 docs & spreadsheets, etc. Right now, Linux based options for these tasks are non-existent so I need to be able to use those darned MS programs part of the time.

What's the best choice for a virtualized environment? I'd like to be able to use the existing Windows installation in a virtualized environment from within Kubuntu. Unfortunately, the virtualization space is sooo complicated, I'm not sure which ones to look at.

I've read that KVM is going to become more supported in Hardy, but I'm not sure if it will do what I want. I'd prefer to not have to install Windows into a special container if I can avoid it. I'd prefer to keep this simple since it's not my computer. On the other hand, maybe that's not possible.

Thanks!
--andy

---

### Post by Fire_Chief on 2008-02-07
I have a similar setup on my work pc where I boot into Ubuntu and then load up WinXP in a virtual environment within Ubuntu. I chose to use VirtualBox for my virtualization app. I run Outlook 07, Communicator 07, Visio 07, and a few other apps in the XP environment. The plus side is that it works like a champ and the XP system never complains about anything abnormal. The down side for me at the moment is that I've not setup any shared folders between the virtual XP and Ubuntu to pass files back and forth. Once that's setup and working it will be all good. VirtualBox is very very easy to use, is free, and you can install it from the repositories via Synaptic.

You will not be able to virtualize your existing XP environment with VirtualBox. I looked into this option but it was too messy with driver changes and OS activation stuff.
The only product I know that can do this right now is VMWare Converter. It is free but you'd have to then use VMware Server (also free) for your VM. More info about VMWare Server and Converter is at

[http://vmware.com/products/server/]("http://vmware.com/products/server/")
and
[http://vmware.com/products/converter/get.htm]("http://vmware.com/products/converter/get.html")l

Good luck!

---

### Post by gunksta on 2008-02-07
Thanks!

I will look at Virtualbox before making any decisions. VMware is an option but it's proprietary. Based on what I can gather from [Wikipedia]("http://en.wikipedia.org/wiki/Kernel-based_Virtual_Machine"), KVM is more akin to Solaris' containers than a tool to easily let me run divergent operating systems. 

I did some reading on Wikipedia and I also like the way Xen sounds. But, I don't know too much about the latest Intel and AMD processors. The computer the company is going to buy me is going to be a laptop, and I'm not sure if the processors in laptops support the VT-x (intel) and AMD-V extensions. 

Does the Ubuntu community know if laptop processors like the Celeron support these extensions or do I need to get a laptop that uses a desktop processor and just suck up the lack of battery life?

--andy

---

### Post by gunksta on 2008-02-11
A website called techthrob.com has published an interesting review of virutalization environments available for *buntu. Based on this review and the feedback I've gotten in this thread, I think I am going to install and experiment with VirtualBox. It looks like a mature application and the OpenSource version will do everything I need it to do.

Read the article [here]("http://www.techthrob.com/tech/linux_virtualization.php").

---

### Post by zvacet on 2008-02-11
> VMware is an option but it's proprietary

Server is not and you have it in synaptic.

---

### Post by jet87 on 2008-02-11
> **zvacet said:**
> Server is not and you have it in synaptic.

VMware Server is proprietary, but free-as-in-beer.

---

