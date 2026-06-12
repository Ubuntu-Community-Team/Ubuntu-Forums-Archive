---
title: "Problems installing KVM from https://ubuntu.com/blog/kvm-hyphervisor"
date: 2023-03-21
forum: Installation &amp; Upgrades
---

### Post by skywalker007 on 2023-03-21
[FONT=arial]Hi, my whole day has been around attempting to install KVM

I have now started a new thread specifically because I am using this site as it seems to be supported by this page..

[https://ubuntu.com/blog/kvm-hyphervisor](https://ubuntu.com/blog/kvm-hyphervisor)

I have done as they mention on the site STAGE 1, and then STAGE 2. When I get to the final point STAGE 3 where I need to install, I need to enter a single very long line of code:

[sudo virt-install --name ubuntu-guest --os-variant ubuntu20.04 --vcpus 2 --ram 2048 --location [http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/](http://ftp.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/) --network bridge=virbr0,model=virtio --graphics none --extra-args='console=ttyS0,115200n8 serial'][/FONT][FONT=arial]

Installation does start and then it ends like this:

Starting install...
Retrieving 'linux'                                          |  10 MB  00:02 ... 
Retrieving 'initrd.gz'                                      |  49 MB  00:10 ... 
Allocating 'johan.qcow2'                                    | 4.0 MB  00:06 ... 
Creating domain...                                          |    0 B  00:00     
Running text console command: virsh --connect qemu:///system console johan
Connected to domain 'johan'
Escape character is ^] (Ctrl + ])

I do not get a comand prompt afterwards and if I say I am going to close the console, it says a process is still running in the terminal. But I have left it like this for almost 30 minutes now.
This is a example where I have changed the [ubuntu-user] part in the code to [johan].
It did exactly the same when I left the name as [ubuntu-guest] in my first attempt, except it obviously said [console ubuntu-guest] instead of [console johan]

Appreciate all assistance
Thanks
Johan[/FONT]

---

### Post by ajgreeny on 2023-03-21
Do you need or want to continue doing everything in terminal as I think you may find it much easier to use the GUI virt-manager and just install virtual OSs that way.
There is  good illustrated web site which show how to do this from start to finish and there is a.so aspecifjcally Ubuntu wiki help page which does the same thing making KVM installations similar in many ways to using Virtualbox.

I will find the links for you and post again once found.7

EDIT:
Here you are with the first link.
[https://linuxhint.com/install-kvm-ubuntu-22-04/](https://linuxhint.com/install-kvm-ubuntu-22-04/)
And here's the second. Scroll down near the bottom to see information about **virt-manager**, the GUI part which acts a bit like the VBox manager window.

---

### Post by skywalker007 on 2023-03-21
Thanks...:P I really would not prefer to do in in terminal as it took a very long time and I had no success today.

Thanks
Johan

---

### Post by MAFoElffen on 2023-03-22
If you want to continue doing it from cli, then first get rid of 'hung' the terminal session and restart a terminal session. The VM is still running.

To check that, do
```

virsh list

```
With just those option, virsh will just show the running domains, such as this
```

mafoelffen@Mikes-B460M:~$ virsh list
 Id   Name                    State
---------------------------------------
 6    lunar-lander-01-01      running
 14   ubuntu-server-22.04.2   running
 17   penryn-01               running

```
If you don't see it running, then do
```

virsh list -all

```
Which is going to show all your VM domains. Example
```

mafoelffen@Mikes-B460M:~$ virsh list --all
 Id   Name                          State
----------------------------------------------
 6    lunar-lander-01-01            running
 14   ubuntu-server-22.04.2         running
 17   penryn-01                     running
 -    console01                     shut off
 -    fedora37                      shut off
 -    fedora38                      shut off
 -    iso-tester-01                 shut off
 -    linux2020-2                   shut off
 -    lunar-efi-01                  shut off
 -    lunar-lander-00               shut off
 -    lunar-lander-01               shut off
 -    lunar-lander-04               shut off
 -    lunar-lander-05               shut off
 -    lunar-lander-07               shut off
 -    lunar-lander-07-01            shut off
 -    lunar-lander-08               shut off
 -    lunar-lander-10               shut off
 -    lunar-lander-zfs              shut off
 -    lunar-server-01               shut off
 -    lunar-server-03               shut off
 -    lunar-server-04               shut off
 -    lunar-server-06               shut off
 -    lunar-server-22.04-zfs        shut off
 -    lunar-server-cloudimg-amd64   shut off
 -    lunar-server-lightvnc         shut off
 -    lunar-server-template         shut off
 -    lunar-server-zfs-23.04        shut off
 -    lunar23.04-2                  shut off
 -    lunar23.04-3                  shut off
 -    proxmox-7.3-1                 shut off
 -    rollingrino22.04-1            shut off
 -    solaris11                     shut off
 -    ubuntu-core22-20221218        shut off
 -    ubuntu-guest                  shut off
 -    ubuntu16.04                   shut off
 -    ubuntu18.04                   shut off
 -    ubuntu20.04                   shut off
 -    ubuntu20.04-s390x-2           shut off
 -    ubuntu22.04                   shut off
 -    ubuntu22.04-10                shut off
 -    ubuntu22.04-11                shut off
 -    ubuntu22.04-12                shut off
 -    ubuntu22.04-2                 shut off
 -    ubuntu22.04-3                 shut off
 -    ubuntu22.04-4                 shut off
 -    ubuntu22.04-5                 shut off
 -    ubuntu22.04-6                 shut off
 -    ubuntu22.04-7                 shut off
 -    ubuntu22.04-8                 shut off
 -    ubuntu22.04-9                 shut off
 -    ubuntu23.04-4-zfs-luks2       shut off
 -    win11-RMS                     shut off
 -    win2k22                       shut off
 -    xubuntu22.04-01               shut off

```
To start a Domain from the commandline, the format is: virsh start <domain_name> like this:
```

mafoelffen@Mikes-B460M:~$ virsh start ubuntu23.04-4-zfs-luks2
Domain 'ubuntu23.04-4-zfs-luks2' started

```
You can connect from the graphical virt-viewer session via
```

mafoelffen@Mikes-ThinkPad-T520:~$ virt-viewer --connect=qemu+ssh://mafoelffen@10.0.0.3/system ubuntu23.04-4-zfs-luks2

```
If you do like you probably did, and described the problem of it looking like it is 'hung'... That means that there is no [EMAIL="getty@ttyS.servic"]getty@ttyS.servic[/EMAIL]e started that is listening on the pty serial console... Go back to the above to connect to your VM... At the command prompt do:
```

sudo nano /etc/default/grub

```
Add this to this line, (look inside the quotation marks):
```

GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]console=ttyS0,115200[/COLOR]"

```
Then save and exit the editor. Then do
```

sudo update-grub

```
Reboot. Then close the virt-viewer window and go back to your terminal session... 

Passing the kernel that boot parameter, when the system boots, systemd will create an start the getty@ttyS service and open a listener for the pty console.

Example:
```

mafoelffen@Mikes-B460M:~$ virsh --connect qemu:///system console ubuntu-core22-20221218 --force
Connected to domain 'ubuntu-core22-20221218'
Escape character is ^] (Ctrl + ])


```
Note that serial consoles boot to this first and are listening for input... Hit the <Enter> key
```

Password: 
Welcome to Ubuntu 22.04 LTS (GNU/Linux 5.15.0-56-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
Last login: Wed Mar 22 04:34:34 UTC 2023 on ttyS0
mafoelffen@ubuntu-core-22:~$ 

```
Have fun... But as DuckHook said, that is really the hard way to do that, rather than all the other tools available to do things. It's possible, but it's work.

Use <Cntrl><]> or shut down the VM to disconnect the connection from your terminal session.

---

### Post by Dennis N on 2023-03-22
Just a couple of comments here:

For a user new to virtual machines and looking for a nice GUI to install and manage one, the tutorial:
[https://linuxhint.com/install-kvm-ubuntu-22-04/](https://linuxhint.com/install-kvm-ubuntu-22-04/)
comes up short in the package list.
Nowhere in this tutorial is there a mention of the GUI installation and management tool, **virt-manager**. That should at least be a suggested package (I would consider it essential).

Also **bridge-utils** is not a 'necessary package' to access the internet or the host from the guest and could be omitted (along with step 6).

Added comment:
The target article of post #1 and the thread title link makes it clear in step 3 it is installing an Ubuntu Server VM and uses virt-install terminal command. That is not a Desktop system. To its credit, at the end it does mention Virtual Machine Manager (virt-manager)  as a GUI tool for managing virtual machines.

---

### Post by MAFoElffen on 2023-03-22
+3 to both ajgreeny and Dennis N 

Why? In the Linux World, there are hundreds of ways to do the same thing. As I said in my last post, even though it is "possible" to install, start, run, manage Qemu/KVM from the command line... and working with Qemu & KVM for over 15 years, I know of many ways to do that... The question remains: Why put yourself through that? Just because something is *possible,* does not mean it makes sense. 

I can see the value in a "learning experience"... You can learn what happens in the background at the ground level. But do that a few dozen times and you will see that it can be a challenge and taxing on time.

Personally, Virtual Machine Manager is still my day-to-day go to. Most users only touch the edges into what you can really do with that tool. Get to know how to use the toolsets available to you, and make your own informed, educated decisions.

My time is better spent *using* VM's to do the things I really need to do. My goal is not limited to creating VM's or to making things into a challenge. (Although that is sometimes entertaining.) 

Time Management = Time is a valuable and rare asset.

---

