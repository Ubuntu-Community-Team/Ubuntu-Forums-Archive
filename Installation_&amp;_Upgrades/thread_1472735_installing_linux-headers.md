---
title: "installing linux-headers"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by doesntcount on 2010-05-04
Need to install linux-headers so I can install vmware tools on my ubuntu 10.04 guest os. 

nkaun@nkaun-pc2-linux-vm:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Couldn't find package linux-headers-2.6.32-21.32

How do i get the linux headers installed? Is 2.6.32-21 good enough? I somehow doubt it.

Thanks.

---

### Post by oldos2er on 2010-05-04
Do you have the source code repositories enabled? Check System, Administration, Software Sources.

Edit: And unless it's in the proposed repos, 2.6.32-21 appears to be the most recent.

"Is 2.6.32-21 good enough? I somehow doubt it."

Good enough for what, exactly?

---

### Post by gzarkadas on 2010-05-04
Use ```
sudo synaptics
``` to open the synaptics package manager and type `linux-headers' in the search box. Then select the type that fits in your case (-generic is the most probable). 

PS: Your command failed because you didn't append the type of headers wanted.

---

### Post by doesntcount on 2010-05-04
Weird, no example i saw suggested that I needed to append "-generic". Also, when i open up synaptic, i see 2.6.32-21-generic, but uname -r shows 2.6.32.21.32. I'm worried that the extra .32 is important. If it's not, then i'm okay.

---

### Post by oldos2er on 2010-05-04
I must be going blind (sigh). "sudo apt-get install linux-headers-$(uname -r)" is a perfectly good command.

---

### Post by doesntcount on 2010-05-04
Sigh. I tried using 2.6.32-21-generic, and received this error while configuring the vwmare tools:

```
What is the location of the directory of C header files that match your running
kernel? /usr/src/linux-headers-2.6.32-21-generic/

The path "/usr/src/linux-headers-2.6.32-21-generic/" is not valid.
Would you like to change it? [yes] yes

```

Frustrating how not out of the box ubuntu is with vmware workstation.

---

### Post by doesntcount on 2010-05-04
> **oldos2er said:**
> I must be going blind (sigh). "sudo apt-get install linux-headers-$(uname -r)" is a perfectly good command.

I know! I've used a dozen times before :(

---

### Post by doesntcount on 2010-05-04
So, it looks like my linux-headers are installed, but the vmware-config tool can't find them, even though i'm providing it with a perfectly valid path.

Has anybody had problems install vmware tools on ubuntu 10.04 like this? Did you find a solution for it?

---

### Post by gzarkadas on 2010-05-04
Try to cd to '/usr/src' and run `ls'. If you see a plain 'linux-headers-2.6.32-21' then specify this path to vmware-config.

---

### Post by gzarkadas on 2010-05-04
I re-read your posts and the version numbers that you report > 2.6.32.21.32 suggest that you need one of those packages (at least those I found in my synaptic lists):


[LIST]
[*]linux-headers-generic
[*]linux-headers-386
[*]linux-headers-generic-pae
[/LIST]
It probably has to do with the fact that you run Ubuntu through a virtual machine (if I understand it right). Try to install those packages (note if their version in synaptic matches yours) and rerun your vmware-config.

---

### Post by doesntcount on 2010-05-05
Looks like it's a bug in vmware's install scripts in Workstation 7.0. I've downgraded to 6.5 and everything works great. Stupid Workstation 7.0 :/

---

### Post by dgremy on 2010-10-07
I was disappointed with vmware-tools install on 10.04 server, but finally got it to work.

first create a symbolic link to the correct folder:
          ln -s /usr/src/linux-headers-2.6.32-24-generic/include /usr/src/linux-headers

after that was done went back to vmware-tools installer and pointed the installer to the folder:
         /usr/src/linux-headers

it then found the path to be valid and completed the installation.

---

