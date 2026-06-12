---
title: "virtual cdrom problem"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by saurabh4485 on 2012-09-27
Hi,

I just created one image using command below :

kvm-img create -f qcow2 server.img 5G

Now,I am booting the booting the KVM instances with the OS installer ISO in the vitual CDROM command buts its not completed yet more than 18 hours this below command is running.

sudo kvm -m 256 -cdrom ubuntu-12.04-server-amd64.iso -drive file=server.img,if=virtio,index=0 -boot d -net nic -net user -nographic -vnc :0

Please tell me virtual CDROM option is feasible or not?


Regards
Saurabh

---

