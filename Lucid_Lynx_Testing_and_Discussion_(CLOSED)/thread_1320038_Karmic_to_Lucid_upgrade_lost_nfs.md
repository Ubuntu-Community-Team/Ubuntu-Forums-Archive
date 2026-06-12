---
title: "Karmic to Lucid upgrade lost nfs"
date: 2009-11-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dfink on 2009-11-08
Really a noob but still persistant. I had assembled a working diskless boot system using 9.10 karmic. Once the new lucid was available I ran the upgrade and all went great except the kernel appears to have lost support for nfs.
I can install nfs-kernel-server but when I try to start it I get the message that the NFS server did not start. * 
 
Stopping NFS kernel daemon [ OK ] 
* Unexporting directories for NFS kernel daemon... [ OK ] 
* Not starting NFS kernel daemon: no support in current kernel.
 
I thought NFS was enabled by default in ubuntu

---

### Post by omegamormegil on 2009-11-08
I'm sorry you are having trouble, but I'm not at all surprised. In fact, I'm surprised that anything in Lucid works this early in the development cycle.  

I would definitely wait to upgrade to Lucid until later in the development cycle, if at all.  Lucid will not be released until April, and if you care at all about stuff working you should not use a development version.  While some people like to run development versions of Ubuntu, they are only intended to be used for testing.  

The specific problem you are having is caused by the fact that some parts of the new version of Ubuntu have been loaded (like perhaps a new NFS), but other parts (like a new/functional kernel) haven't made it into the archive yet.  It is still very incomplete.

---

### Post by dfink on 2009-11-09
Thanks for the reply. I am suprised that NFS would not be one of the first areas covered. Everything has worked except that. Though a noob I have managed to get a functional beowulf style cluster functioning with folding at home along with ganglia monitor and FahMon. Fahmon is terrible to install but everything was pretty much available for lucid to make it all work. I still have a dell blade that I was nfs diskless booting to karmic that I would like to tie into the cluster but without nfs it won't boot.

---

### Post by dfink on 2009-11-10
Well I think I got the problem solved. I downloaded the kernel, reconfigure with menuconfig, recompiled the kernel, loaded and NFS service came back working just fine. So something got lost in the upgrade it is not that they haven't developed it yet.
Hope this helps someone.
 
I now have a fully functional 21 CPU 8 node beowulf cluster running on lucid lynx with ganglia, folding at home and FAHmon all running together. I have absolutly no use whatsoever for this system but it was / is a learning experience.

---

