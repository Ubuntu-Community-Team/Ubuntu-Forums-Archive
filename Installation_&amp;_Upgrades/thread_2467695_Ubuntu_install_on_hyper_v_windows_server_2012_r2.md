---
title: "Ubuntu install on hyper v windows server 2012 r2"
date: 2021-10-05
forum: Installation &amp; Upgrades
---

### Post by codesolve on 2021-10-05
When installing Ubuntu 21 desktop I get the following error “initramfs unpacking failed write error"

What is causing this problem?

---

### Post by yancek on 2021-10-05
That's a very cryptic post.  Where did you get the Ubuntu iso you downloaded?  From the official site?  Did you do an md5 checksum on it after it was downloaded to verify that it was not corrupted during the download process over miles and miles of wire?  At what point in the process do you see this message?

---

### Post by ActionParsnip on 2021-10-05
Did you SHASUM the ISO you downloaded to make sure the ISO is complete and consistent or use torrents to pull down the file? Bad files will cause issues. What settings do you have in the HyperV guest? What steps did you use to set it up?

---

### Post by TheFu on 2021-10-05
> **codesolve said:**
> When installing Ubuntu 21 desktop I get the following error &#8220;initramfs unpacking failed write error"

What is causing this problem?

Lacking any other knowledge, I'd say hyper-v is the issue.  Does it support Ubuntu 21.04?  In general, new users should run only LTS releases. That would be 20.04. On servers, only LTS releases should be deployed.
Of course, there are exceptions, usually for non-VM installs to extremely bleeding edge hardware. VMs hide the real hardware so those exceptions don't apply.

May have better luck on Windows-Centric/Hyper-V using forums.  Most people here will use virtualbox for their hypervisor on a desktop and server people will probably use KVM/QEMU with libvirt on Ubuntu hosted systems.

---

### Post by MAFoElffen on 2021-10-07
LOL. This is a question that concerns Virtualization, as well as concerning installations (as a Guest VM).

Hyper-V is Ubuntu VM friendly. MS has had a relationship Canonical since 2014, with projects concerning Docker, Cloud Computing (Azure), and WSL.

I have never had problems installing and running Ubuntu as a VM Guest "anywhere", including not having any problems with it on Hyper-V.

What is curious, is that no one yet has asked you about the spec's of your Virtual Host, and the settings of your VM(???)

I am gong with suspecting either a corrupted image, or running low on virtualized resources. If you let it go though the fie check at the start of the  install, instead of skipping it... Then I am going on resources.

It is Ubuntu 21.04 Desktop right? Where I usually divy out 2 vcpu's and 4 GB RAM. Sometimes I might give a but more RAM on the install, then cut it back. Also, I give about 1.5 to 3 times the Max Ram amount in "swap"... Sometimes if you just pick the default on 21.xx, I notice if I go back and look at it, the swap will be missing. This has happened 3 times in the last 3 months. But I do 2-4 installs a day. If I am not scripting it out or deploying an image, I always choose "Other" and set things how I want. But that's just because I am very particular and I don't trust a default to be "default".

If you keep an eye on your Hyper-V Manager window while it is installing and toggle the MEM Stats over on the VM, you might see where during that process that you are going to see a spike. It's a compression (heavy cpu and memory load) and a heavy write at the same time. This is why I give it a carbo-load treat for the install. If you check the install logs on your VM, you might see where it hit a problem during that. Especially if you don't have a sway configured.

And yes, even Windows uses a "swap file" for those just in cases. Make sure you have a fail-safe swap partition to spill over to. If you did, good on you and then check it off the list of the possibles.

These are just things that hadn't been mentioned, when focus was a bit shifted onto other things.

---

