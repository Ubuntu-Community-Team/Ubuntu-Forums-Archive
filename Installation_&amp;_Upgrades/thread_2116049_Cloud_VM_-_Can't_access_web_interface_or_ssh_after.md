---
title: "Cloud VM - Can't access web interface or ssh after completing installation"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by HeavenCore on 2013-02-14
Hi there

We have a VPS (Virtual Machine "in the cloud")

We installed Ubuntu 12.04 (the Zentyal ISO wasn't made available by the cloud provider) and then installed Zentyal manually via apt-get

We then had to add root to the sudo group before being able to login to the web interface.

Once logged into the web interface it started the Zentyal installation wizard - the only module we selected was "WebServer" - this installed fine.

It then asked us if the NIC was local or remote - it said that selecting local would prevent external access - or at least that was our interpretation, upon clicking next at that point the interface hung and our SSH session also got disconnected. I'm guessing we chose the wrong option & Zentyal did something funky with the NIC?

With this installation being in the cloud (I.e. a virtual machine in a remote data centre somewhere) we don't have console access short of having the cloud provider do it for us - i think they provide a buggy java based IP KVM for emergencies)

Assuming we selected the wrong nic type - how do we re-enable access to the web interface & SSH over the Internet?

We'll have to arrange console access via the IP KVM and bash whatever into the console - to be clear: we no longer have access to Zentyals web interface.

Please help

Regards

Jordon

---

