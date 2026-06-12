---
title: "Installing ceph client on ARM64 hardware"
date: 2021-12-02
forum: Installation &amp; Upgrades
---

### Post by tjcw on 2021-12-02
I have an ARM64 server (i.e. not x86-64) and I am trying to install the ceph client. I am running Ubuntu 20.04 fully updated.
I get
tjcw@cuttlefisharmserver:~$ sudo apt install ceph-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'open-infrastructure-ceph-tools' instead of 'ceph-tools'

  and several success messages indicating that this package installs OK; but when I try the next command I get

tjcw@cuttlefisharmserver:~$ sudo apt install ceph-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ceph-common : Depends: librbd1 (= 15.2.14-0ubuntu0.20.04.1) but 16.2.6-1bionic is to be installed
               Depends: python3-ceph-argparse (= 15.2.14-0ubuntu0.20.04.1) but 16.2.6-1bionic is to be installed
               Depends: python3-ceph-common (= 15.2.14-0ubuntu0.20.04.1) but 16.2.6-1bionic is to be installed
               Depends: python3-cephfs (= 15.2.14-0ubuntu0.20.04.1) but it is not going to be installed
               Depends: python3-rados (= 15.2.14-0ubuntu0.20.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
tjcw@cuttlefisharmserver:~$

What is wrong ? Do I need to build something from source ? Or do I need to wait until the Ubuntu build team addresses the issue ?

---

### Post by MAFoElffen on 2021-12-02
What is your Arm64 device that you are trying to install to? How many Ceph nodes do you plan to have?

---

### Post by tjcw on 2021-12-02
I'm not sure exactly what kind of ARM64 processor I have, but it's not an embedded processor. I will ask later today exactly what it is.

This system currently has 3 nodes l=; this one, plus 100gE networking to 2 embedded nodes witrh Xilinx gate arrays. It will grow, and it will get replicated many times.

I'm only trying to install ceph client on this node.

---

### Post by tjcw on 2021-12-03
It's one of these [https://www.xilinx.com/support/documentation/data_sheets/ds891-zynq-ultrascale-plus-overview.pdf](https://www.xilinx.com/support/documentation/data_sheets/ds891-zynq-ultrascale-plus-overview.pdf)

---

### Post by MAFoElffen on 2021-12-04
LOL... So what architecture are the first three nodes?The reason I'm asking, is the first node is usually includes ceph-admin and ceph-deploy, to deploys any additional nodes to the cluster... Are the previous 3 nodes all Arm64? if not, is that why this node is being installed in pieces instead of being deployed as an image from ceph-deploy?

At least that was how it was installed as initial on 18.04... In the initial install under 20.04, then they changed to doing a snap install of MAAS and JuJu... which I still prefer not to use Snap... The only reason I know this was from dong iVirt w/ Ceph Storage.

NOTE: An Admin or Mode should please move this thread to Server to get more exposure in the right area...

---

### Post by tjcw on 2021-12-04
The other nodes are embedded ARM64 with FPGA  [https://www.xilinx.com/support/documentation/user_guides/ug1085-zynq-ultrascale-trm.pdf](https://www.xilinx.com/support/documentation/user_guides/ug1085-zynq-ultrascale-trm.pdf)

We have another problem with docker on the embedded nodes. Trying to set up a ramdisk (to mount on /var/lib/docker) causes a kernel panic for anything above 2GB. Yes we have reported it to Canonical support. So trying to deploy by hand. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1952185](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1952185) .

---

### Post by MAFoElffen on 2021-12-04
Yes. Understood. Will try my best from my limited experience with Ceph on Ubuntu and CentOS. 

I have Arm64 hardware... But have only done Ceph on Amd64 on Ubuntu and CentOS... So I know how it "should work and install" and can see what might be different. 

But I am only familiar with installing CephAdm on the first node, then deploying nodes from there to other child nodes, off various methods for that first, parent node. What instructions are you trying to follow fro a manual install of a child node, that doesn't follow being "DEPLOYED" from a parent node? I would like to look into that. to see what I see from that...

EDIT... I looked up the packages that you tried to install in your first post, from my Arm64 Hardware, and get errors, saying that they are not seen because they are only 'virtual packages'(???) I do see cephadm... and many other packages... but not any that you tried to install. So curious about the recipe you are trying to follow.

---

### Post by MAFoElffen on 2021-12-04
I'm thinking that if you did:
```

sudo apt install --simulate --install-suggests ceph ceph-deploy ceph-common | more

```
As a simulated dry run of the install...Well, it's not as simple as just installing those packages... Includes lots of configuration of files.

That is what I show as the 3 main packages to install the initial node of Ceph, then deploy from that node... Just saying...

EDIT: I was going to post what mine (Arm64) said as output, but it would have had to have been pasted to a pastebin... That generates lots of lines of output, but had a successful diagnostic dry-run of the install.

---

### Post by tjcw on 2021-12-05
tjcw@cuttlefisharmserver:~$ sudo apt install --simulate --install-suggests ceph ceph-deploy ceph-common 2>&1|tee inst.log
[sudo] password for tjcw: 
Sorry, try again.
[sudo] password for tjcw: 


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ceph-common : Depends: librbd1 (= 15.2.14-0ubuntu0.20.04.1) but 16.2.6-1bionic is to be installed
               Depends: python3-ceph-argparse (= 15.2.14-0ubuntu0.20.04.1) but 16.2.6-1bionic is to be installed
               Depends: python3-ceph-common (= 15.2.14-0ubuntu0.20.04.1) but 16.2.6-1bionic is to be installed
               Depends: python3-cephfs (= 15.2.14-0ubuntu0.20.04.1) but it is not going to be installed
               Depends: python3-rados (= 15.2.14-0ubuntu0.20.04.1) but it is not going to be installed
               Suggests: ceph-mds but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
tjcw@cuttlefisharmserver:~$

---

### Post by MAFoElffen on 2021-12-06
And if you do
```

sudo apt install -f 

```
...to correct the broken packages that it says you currently have, then run it again?

---

