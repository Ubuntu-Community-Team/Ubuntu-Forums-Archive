---
title: "Can somebody please tell me why git keeps hanging up on me?"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by agentchange on 2010-06-27
> justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-sconklin/drm-intel.git
Initialized empty Git repository in /home/justin/drm-intel/.git/
fatal: The remote end hung up unexpectedly
justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-sconklin/drm-intel.git
Initialized empty Git repository in /home/justin/drm-intel/.git/
fatal: The remote end hung up unexpectedly
justin@justin-desktop:~$ 
justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-2.6.35-rc3.git  
Initialized empty Git repository in /home/justin/ubuntu-2.6.35-rc3/.git/
fatal: The remote end hung up unexpectedly
justin@justin-desktop:~$ 
justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/ubuntu/
Initialized empty Git repository in /home/justin/ubuntu/.git/
fatal: The remote end hung up unexpectedly
justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/ubuntu/Ubuntu-2.6.32-23.16
Initialized empty Git repository in /home/justin/Ubuntu-2.6.32-23.16/.git/
fatal: The remote end hung up unexpectedly
justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/ubuntu/Ubuntu-2.6.32-23.16.git
Initialized empty Git repository in /home/justin/Ubuntu-2.6.32-23.16/.git/
fatal: The remote end hung up unexpectedly
justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/ubuntu/sconklin/drm-intel.git
Initialized empty Git repository in /home/justin/drm-intel/.git/
fatal: The remote end hung up unexpectedly
justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu/linux-2.6/.git
Initialized empty Git repository in /home/justin/linux-2.6/.git/
fatal: The remote end hung up unexpectedly
justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu/ubuntu-lucid.git
Initialized empty Git repository in /home/justin/ubuntu-lucid/.git/
fatal: The remote end hung up unexpectedly
justin@justin-desktop:~$ 
justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/ubuntu/Ubuntu-lts-2.6.35-1.1.git
Initialized empty Git repository in /home/justin/Ubuntu-lts-2.6.35-1.1/.git/
fatal: The remote end hung up unexpectedly
justin@justin-desktop:~$ 
justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/git?p=bradf/ubuntu-lucid/.git;a=summary
Initialized empty Git repository in /home/justin/ubuntu-lucid/.git/
fatal: The remote end hung up unexpectedly
justin@justin-desktop:~$ git clone git://kernel.ubuntu.com/git?p=bradf/ubuntu-lucid/.git
Initialized empty Git repository in /home/justin/ubuntu-lucid/.git/
fatal: The remote end hung up unexpectedly



Are all of these different links in gitweb useless or what?

---

### Post by agentchange on 2010-06-27
The only thing I can think of is that I followed these instructions on how to get a new kernel "for Ubuntu" ( [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)), and now it doesn't like it that I want to go with the flow on the official Ubuntu method.

---

### Post by agentchange on 2010-06-27
I could go back to the original in Synaptic, but then I will lose these changes.   Hmm.  What to do...  Of course, if I can't access git, it's kind of a moot point, so the question remains... why?

---

### Post by agentchange on 2010-06-27
I tried turning off my firewall and that is not the issue.

---

### Post by agentchange on 2010-06-27
fixed

---

### Post by dsjbirch on 2010-08-04
How did you fix it? I'm having a similar problem with gitosis!

---

### Post by prefabSOFT on 2010-10-13
> **agentchange said:**
> fixed

It indeed would be less selfish if you'd also poste the fix since chances are other people would run into the same issue.

---

### Post by Akkarin0682 on 2010-10-13
What did you do to fix it?

---

