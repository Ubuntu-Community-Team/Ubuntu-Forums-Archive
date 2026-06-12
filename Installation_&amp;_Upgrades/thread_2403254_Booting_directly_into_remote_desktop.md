---
title: "Booting directly into remote desktop"
date: 2018-10-09
forum: Installation &amp; Upgrades
---

### Post by iankearns on 2018-10-09
Hi all

Am an Ubuntu user (have a couple of servers and have used desktop a few times) however I have a HP Jack Black Notebook 14-AC100na which has a fixed 32Gb storage which doesnt hold much these days so want to really use it as a launchpad for remote desktop sessions to VM's held on a local ESXi server.

Ideally this would just be the laptop booting into a menu with a list of VM's available by name or IP address (I would like to be able to edit that menu when I add or remove VM's). The user then selects the desktop they want and then the laptop continues to boot to that chosen VM.

Can anyone point me to a resource that can walk me through this or offer and pointers.

Appreciate all comments

Ian

---

### Post by TheFu on 2018-10-09
GUI programs cannot be started until after a user logs in and starts an X-session. Then you can run a GUI automatically using the method that the DE you run uses.

You cannot boot directly into this GUI you seek. Unix GUIs just don't work that way.

For remote desktops, I prefer NX-based solutions. They are faster than other options 2-3x faster. **x2go** is the easiest to setup on the remote systems and my local desktop.  Just follow the PPA instructions for each (client/server) from the x2go website. I've used x2go daily for 5 yrs from the same room or 5 different continents.

If you are stuck using rdp or vnc, remmina (or something with a name close) is probably the easiest answer. I've never used it.  You can google "remmina vs" to find other alternatives.

My main desktop runs in a KVM VM and has ... 
```
$ df
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        20G   17G  1.9G  90% /

```
of local storage. I've been using it since 2010. So whatever you are doing that sucks storage, it isn't the OS or normal productivity files.  I keep media on network storage, not the desktop. That's really the trick to using 20G or less storage.  Of course, the network storage has room for 25TB via NFS.

Another, more radical solution, would be to switch from VMware to KVM as the hypervisor. We did in 2010 and never looked back. But that's a tougher decision.  KVM works nicely with libvirt and virt-manager. Virt-manager is a GUI that works over an ssh tunnel to manage VMs or view the VM console or GUI. I thought virt-manager worked with ESXi too, but I don't know. It works with Xen, LCX, VirtualBox, KVM, and a few other virtualization-like solutions.

---

### Post by iankearns on 2018-10-09
Thanks for the detailed reply and your time.

I am trying to mirror a solution that I saw whilst using an internet cafe when I was in the USA in the summer. I did ask the chap who was running the shop but he wasnt fully up to speed on how it was all setup.

I can only presume that the Ubuntu desktop was set to auto login (if that is an option) into the X-session / GUI and then run a script to bring up the options menu. From there the user then logs into the remote desktop session.

Rather than having individual profiles on one laptop we tend to have individual VM's that we can connect / disconnect to and from when we want. Also means that we can use multiple mobile devices (tablet/phone) to connect to them wherever we are.

So I suppose my challenge boils down to:-

1] auto login to Ubuntu desktop 
2] auto run a menu (BASH script??) to establish the connection through to the VM via a RD client

regards

Ian

---

### Post by cmcanulty on 2018-10-09
I have several computers set to autologin with xubuntu and so I can restart them remotely and get logged in to desktop. However they have to be running already. I use VNC or rdp for this. RDP in the newest linux version won't share screens so I reach non logged in users with rdp.

---

### Post by TheFu on 2018-10-09
I did a little googling: [https://rpitc.blogspot.com/p/main-documentation.html](https://rpitc.blogspot.com/p/main-documentation.html)
There's also the LTSP, but I don't know how that physically connects.  If over a network or directly using video, keyboards, mice.

Ah ... almost forgot.   For remote desktops, don't use fancy, 2D or 3D GPU GUIs.  That means you need to avoid Gnome3, Unity, and KDE.  Stick with Mate, XFCE, LXDE or a pure WM setup on the remote VMs.

---

### Post by iankearns on 2018-10-09
Thanks for the replies and the assistance

---

### Post by TheFu on 2018-10-09
If you come up with a workable solution, please post a summary about it here.  Also why whatever was suggested didn't work is helpful too!  Someone else could start from that point next time.

---

