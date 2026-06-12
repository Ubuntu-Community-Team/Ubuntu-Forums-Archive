---
title: "Copying repositories from a computer to another"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by GTMoraes on 2011-02-11
Hey, I'm using Ubuntu Maverick

On my university, the technology center uses the Ubuntu 10.04 LTS. I've been told by my teacher to get GCC for the C language. 
Searching for GCC on my netbook, I can find two programs:
Sysinfo (why?)
GGcov (doesn't open)
Searching for GCC on the TC Computer, I can find 115 programs...
The administrator wasn't there at the moment I checked this, and he'll not be there on this weekend so... I would like to do this by myself tomorrow.
With my vast one-week experience with ubuntu, I think such software abundance from the TC computer side is related to repositories. I would like to copy them all to my netbook, if it's possible.

I've shortened my question for a better reading pleasure. Sorry if I sounded gross
Thanks!

---

### Post by oldos2er on 2011-02-12
Use lower-case letters in your search: ```
apt-cache search gcc
```

```
sudo apt-get install build-essential
``` will get you the bare basics to compile software. I'd probably install gcc-4.3 gcc-4.3-base and gcc-4.3-doc too.

---

### Post by GTMoraes on 2011-02-12
Oooooo that did the trick.
However, I can only see 51 programs this time.. The Technology Center there got 115.

There's no way I can copy the current repositories from a machine to another?

---

### Post by arpanaut on 2011-02-12
You need the universe and multiverse repositories enabled in your sources.list to have all the other packages available.

But, except under special circumstances/uses, you will not need to have all available installed.
build-essential will provide the packages that will build/compile in most cases.

Install the others when/if needed.

---

### Post by GTMoraes on 2011-02-12
Thanks for the reply!
They were activated.
Seems like I can export fom the TC computer and then import to my netbook using the Synaptic package manager, but I'm not sure how

---

### Post by arpanaut on 2011-02-12
Don't know, with those repos enabled, when I search "gcc" I have 122 available.
That's on 10,4 LTS completely updated.  

You shouldn't need to use other repos than what you have now.
Do an update in synaptic and see what it gives you.
And as I said before that you will probably not need most of those packages to use the compiler in most cases.

PS Please assure that you have permission from the administrator of that system before you go messing about.

---

### Post by GTMoraes on 2011-02-12
Thanks for your answer!
Hm, maybe that amount of software is just for the 10.04 (the same version the machine's using there), not sure.. I'll leave this thread open 'till monday night, when I ask the administrator about it (they say he knows alot about Ubuntu)

--
Don't worry, even if I wanted to mess things up, I'm in the very limited user session and I don't know the administrator pass :P

-------------------------------------------------------------------------
Oooooo I've got it! the Program's center was hiding the "technical itens". At the bottom of the window, there is a "Show 160 technical itens" button. Now I've got 162 programs listed!

Thanks for the support, guys :) Feels like I can really count on you guys for my troubles

---

