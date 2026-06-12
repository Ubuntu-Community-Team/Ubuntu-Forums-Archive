---
title: "Can't install nvidia-current after installing hardware enablement stack"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by bamm on 2013-02-18
Hello. This is my first post in Ubuntu Forums.

I am running 12.04 precise pangolin LTS. I installed the LTS Hardware Enablement Stack using the following command:

sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal  

Everything installed correctly. I rebooted into the new kernel and found that everything works, so I uninstalled the old kernel 3.2.0 and restarted again.

Strangely, now I cannot install the package nvidia-current. Here is the output:

$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11
                  Depends: xserver-xorg-core (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.

Question: Are there any special steps needed to install nvidia-current on 12.04 with hardware enablement?

Furthermore, I wanted to know why there is a failed dependency, so I ran

$ apt-cache show xserver-xorg-core-lts-quantal | grep Provides:

and it gave me the following:

Provides: xorg-input-abi-18, xorg-renamed-package, xorg-renamed-package-lts-quantal, xorg-video-abi-13, xserver-xorg-core

Thus xserver-xorg-core-lts-quantal already provides xserver-xorg-core, so I am wondering why apt-get thinks that xserver-xorg-core is not installed?

---

### Post by dino99 on 2013-02-18
xorg need to accept ABI > 11, but have not yet been upgraded; so have to wait  

[https://bugs.launchpad.net/ubuntu/+source/xorg-lts-quantal/+bug/1125413](https://bugs.launchpad.net/ubuntu/+source/xorg-lts-quantal/+bug/1125413)

---

### Post by bogan on 2013-02-18
Hi!,** bamm**,

You Posted```
:I am running 12.04 precise pangolin LTS.
```Presumably that was 12.04.2, but was it from an update, or with a clean install ?.

Both will show 12.04.2 from: ```
cat /etc/lsb-release
``` but it needs 'uname -r' to distinguish, or the contents shown in Synaptic.

When I tried to install a nvidia driver from Synaptic, [ Edit: in a clean install of 12.04.2] I got a warning that a lot of the 'lts-quantal' and backports files would be uninstalled, so I dropped it and installed the Nvidia.com downloaded driver, without problems.

There are other similar reports - installing 'Steam'. for example.

Chao!,** bogan**.

---

### Post by bamm on 2013-02-19
Hi Bogan,

Yes I meant 12.04, not 12.04.2. In fact, the reason I installed the LTS Hardware Enablement Stack is to upgrade it to 12.04.2 without having to reinstall, because my system is already configured to my liking.

I mentioned in my original post that I performed the upgrade by running the following command:

sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal

---

### Post by bamm on 2013-02-19
Hi Dino99,

Thanks for the explanation. Will a fix be out soon? If not, is there a way to revert my upgrade? Thanks.

---

### Post by Mr.Dunham on 2013-02-23
Hi,

Same thing happened to me, although I performed a clean new installation of 12.04.2
Still, the Nvidia drivers are activated and in use, according to "Additional drivers" (jockey-gtk), showing up as "version current-updates" and it's 304. A bit old, but works perfect for me. Strangely, they activated themselves, contrary to all previous versions where you had to activate them.

From what we see from dino99's post above, it's a bug, so we'll have to wait. I still didn't try downloading them from Nvidia's site as bogan said, but I'll check it out.

Thanks.

---

### Post by bamm on 2013-03-19
Hi Dino99,

Is there any update yet on this issue? Thanks.

---

### Post by bamm on 2013-04-12
What is the status of this bug?

---

### Post by bamm on 2013-04-12
Hi Dino99,

The bug you mentioned is tagged workaround-exist. However, running the workaround doesn't work for me. Would you know of a better solution? Thanks.

Bamm

---

### Post by Bobhuber on 2013-04-12
sudo apt-get install xserver-xorg-lts-quantal libgl1-mesa-glx-lts-quantal

This worked for me from a clean backup.I do use the latest nvidia from there site however.

---

