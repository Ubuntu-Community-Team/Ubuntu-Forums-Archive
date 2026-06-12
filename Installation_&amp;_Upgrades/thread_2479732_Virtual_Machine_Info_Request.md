---
title: "Virtual Machine Info Request"
date: 2022-10-04
forum: Installation &amp; Upgrades
---

### Post by drumone on 2022-10-04
Thank you for reading this! Before I begin down the rabbit hole of learning about Virtual Machines, I want to ask the community for suggestions. Can anyone recommend current/recent articles, tutorials, videos, etc. on creating and using Virtual Machine environments? Yes, I know I can do a search for this information, but I would prefer not to waste a lot of time reading inaccurate or outdated information, considering I wouldn't know it was wrong. I would like to learn as much as I can about VMs so I can save time and hassle and not have to ask for help a thousand times. 

Specifically, I currently run a dual-boot system. Ubuntu is my main OS on a 1 TB SSD. I run Windows 11 Pro on a second 1 TB SSD. I would like to keep Ubuntu as my main OS and run Windows in a VM and still utilize both SSD, if possible. I will be running some RAM heavy programs in Windows (Sibelius, various Neuratron software, Ableton Live, and a few other things), if that makes any difference. Again, I'm hoping to make my learning as pointed and accurate/up-to-date as possible. Consider me a novice that is comfortable with using the terminal, provided someone can give me the lines of code. I've just started learning C++ and I don't know anything about coding for Linux OS yet. Any information you can provide is greatly appreciated! Thanks!!!

---

### Post by TheFu on 2022-10-04
Technology keeps moving.  By the time anything is written down, it is already out of date.
Overall, virtual machines all work the same way, so if you look at anything from the last 15 yrs, that will be close enough on the big ideas. Just ignore any detailed commands.

Each hypervisor has different strengths and weaknesses, pros and cons.  Only you can do the research to decide which, if any, can fill your needs.  If you don't have $10K, then you'll not be looking at some of the enterprise, paid, hypervisors.  Never fear, the fastest, most flexible, hypervisor available today is built into the Linux kernel already. However, that usually isn't the first one selected because for that flexibility, there is a price in complexity.  Most beginners with virtualiation would pick a hypervisor like virtualbox or VMware Player or VMware Workstation, or Gnome Boxes or whatever Canonical was pushing ... think is is a snap package called Multi-Pass.  I tried and failed to get multipass to work at all.  Gnome Boxes wasn't flexible enough for my needs.  

I've used about 10 different hypervisors over the years.
If you plan to run MS-Windows as a guest machine under Linux, then you are limited to HVM - Hardware Virtual Machine - hypervisors.  There are PVM - ParaVirtual Machines, and there are some things that are not hypervisors at all, but Linux Containers.

If you have 2 or more hardware devices that you'll dedicate to virtualization 100%, it would be smart to look at Proxmox. This is a nice management tool over Linux containers and KVM/QEMU VMs, but I understand you cannot use the system as a workstation with it.  Probably not what you want.

Oracle's Virtualbox is a place to start.  Be certain to read and understand the 2 different licenses, so you know you can actually agree to follow them.  There is a F/LOSS version of virtualbox too, but most of the recommendations I see in these forums is to use the one from Oracle with the more restrictive licenses.  The manual for virtualbox is easily found with any search engine.  

Using lots of RAM inside a VM isn't usually an issue. Using lots of CPU is.  And using any high GPU stuff is very complex, not recommended for most people.  While the video will be more than sufficient for typical office programs, even snappy,  even light games will show the limitations of the virtual GPU provided by the hypervisor.  If you intend to do video editing or gaming at all, then you'll likely want to stay dual booted.

---

### Post by drumone on 2022-10-05
Thanks Fu!!! It sounds far more complicated than I originally thought it would be. Thank you for getting me started in the right direction. I am assuming some of your terminology will make more sense when I start reading up on things. I'm using an AMD Ryzen 9 CPU, so I think I should be ok with that. I do plan to get back to writing music and using music production software at some point in the future. However, I believe this is more RAM heavy due to the heavy use of all of the sample files. My past systems have had a tendency to lag, but this system, that I custom built, is far superior in every respect to my past systems. 

I do have an additional question. I prefer Ubuntu as my OS and it's what I use daily. However, I will have to use Windows in the future for all of my music creation/production needs. In addition, I'm working on a degree in software development right now. My university only supports Windows and Mac and I will be using Windows for all of my assignments that I can't do on Ubuntu (Eg. Visual Studio for my current C++ class). Then there is my future career in software development. Considering all of this, would I be better off using Windows as the host and Ubuntu in the VM? I'm looking to have flexibility with my set-up so I can easily switch back and forth as needed. I'm honestly not even sure what a VM looks like, how it operates, or how to access it yet. Now that I know what to start looking into, I should have a better idea soon.

Thank you again for your help!

---

### Post by thebearak on 2022-10-05
Be prepared for a performance hit.  I've used, pretty extensively, Parallels, VirtualBox, and server based ones like Xen and KVM.  I also tried out Microsofts VM engine.

For your purposes, the free VirtualBox might be the right solution to get into it and check it out, but I think you'll be disappointed with the performance.   The $$$ Parallels is quite a bit better and offers easier tools, but I believe it only works on Windows and MacOS as the host OS.

Xen (free version) is a bit more complicated and really meant for a server environment (no GUI), but has some really great features like being able to run redundant VMs on different servers and easily switch between them.   It can do Windows VMs, but you would access them via Remote Desktop or VNC.

I'm currently using KVM on a server environment.  I have 2 Windows VM's machines that I can either access via virt-manager or through Remote Desktop.  Both work really well and are fairly quick.  Not as quick as Parallels running on a Mac with a Windows VM, but quick enough.

So given what you said, I'd have to agree with TheFu, VirtualBox might be the best solution to try out.

---

### Post by ajgreeny on 2022-10-05
As a Linux only user I have used only two hypervisors, VirtualBox and KVM/QEMU, the latter of which is usable on Linux only, both for full GUI systems of Windows and Linux distros,  and would most definitely suggest that the performance of KVM/QEMU is very much better than VBox, though perhaps a bit more complicated until you are used to using it.

I can not comment on either hypervisor's usage on server systems as I have never needed to run a server but certainly I found Linux distros as well as Windows 7 and 10 to run very much smoother and faster in KVM/QEMU than when using VBox.

See [https://ubuntu.com/blog/kvm-hyphervisor](https://ubuntu.com/blog/kvm-hyphervisor) for a bit more detail.

---

### Post by TheFu on 2022-10-05
Audio processing seems like it should be easy inside a VM, but VMs are about cooperative sharing of limited physical resources. That means giving up slices of the hardware for other OSes running on the same system.  For that reason, I wouldn't recommend any audio processing that isn't pure math - i.e. if you want to listen - be performed inside any VM.  Run the OS on the real hardware for that. It doesn't matter than you have a Ryzen 9. Sorry.  The required context switching between different OSes, even with hardware support for it, just isn't sufficient.

How tied to MS-Windows your course work is, depends completely on the professors involved.  It is hard to learn MS-Windows C++ programming without being tempted and forced into using MS-Only extensions.  You may want to discuss this with all your professors to see if you can use Linux with C++ and either GTK+ or Qt libraries which are cross platform instead of MS-proprietary libraries. For about a decade, I earned my living as a cross-platform C++ developer on 12+ platforms, including MS-Windows and MacOS, but also including a number of Unix and mainframes too. If you stick with POSIX C++ calls and avoid the dotnet/mono libraries, you'll have a better chance of creating cross-platform code that will actually work.  We had a saying, port early and often.  At my job, we built the complete systems, all programs, all tools, on every platform we supported 2x a week. This way, tiny issues on 1 platform didn't become use architecture failures for the products being sold.

Anyway, for most programming classes, running an OS inside a VM is the same as running on the real hardware, just without all the stupid hardware compatibility issues.  Programming needs are why I first started using virtual machines.  The virtual hardware provided by all VM hypervisors is all very standard, well supported stuff.  There will not be any need to hunt down drivers for any OS running inside a VM.  Remember that the hardware presented to a guest OS running inside a VM is all virtual and not connected at all to what the real hardware is.  That fancy $1000 nVidia GPU - doesn't matter inside a VM.  To the VM, it is a 128MB VGA GPU which may or may not have 2D or 3D GPU instructions.  Same for network cards and storage - 100% virtual.  In fact, there are virtio devices for those that are very low overhead and latency between the guest VM and the real hardware ... but still 100% virtual.  For example, my physical NICs are 1Gbps and get about 920-940 Mbps transfers.  But the virtio NIC in my VMs routinely see 25 Gbps between 2 VMs running on the say physical hardware.  Virtual NICs rock.  Of course, when a VM sends traffic that has to use a real ethernet cable and switch, it drops to 920-940 Mbps. There's no beating physics.  Same for disk controllers. Choose the virtio disk controller.

Today, I know better than to run MS-Windows directly on hardware. I have the flexibility NOT to need it in that way.  There are excellent audio processing and editing tools for Linux, but probably not as point-n-clicky as for other OSes.  I've been using Linux for my simple audio processing needs since the 1990s. My needs are very simple, so probably nothing at all like what you need.

Sorry if I'm all over the place here.

Oh ... and just to be clear, I use kvm+qemu with libvirt and virt-manager on my VM host machines.  I switched away from using virtualbox, Xen, ESXi and other toy hypervirsors for desktop-on-desktop needs over a decade ago.  KVM is what almost every one of those commercial VPS providers use, except the ones that sell hypervisors and feel the need to inflict their work "dog food" on themselves and their customers. MSFT does this.  OTOH, Amazon switched to using KVM about a decade ago. Previously, they were using a version of Xen.

All the hypervisors have a GUI control center available. It is usually a webapp for the enterprise hypervisors, but virt-manager, also known as VMM, is a desktop application that can control hundreds of VMs and hundreds of VM host machines over the network.  In general, servers don't have any GUI/desktop, so we use ssh to manage Linux servers anywhere in the world.  If you need a desktop, load a desktop and setup x2go for remote access. Don't use VNC or RDP. Those aren't secure.  x2go is 2-3x faster and uses ssh tunnels.

---

### Post by MAFoElffen on 2022-10-06
I taught college students CS courses as a Teaching Assistant and as a Student Tutor (because of my past experience)... I also prepared programming examples for lectures, tutorials to setup virtual class environments, and departmental infrastructures for courses.

Which course are you taking that you are learning C++? (Title and description?) Are you taking it as OOP for a math or science degree... or for Computer Science? If CS, which direction in CS: IT, Database Management or Programming?  If IT, then which branch of: System Admin, Networking or Desktop Support? If CS, then what is the infrastructure of your CS Department? (MS Window Servers or Linux Servers)

Next is what formats they require your homework and projects to be turned in as... Because most colleges and universities here require Microsoft Word, and MS PowerPoint slideshow, then Adobe PDF. 

I know as a CS student, you have access to some academic licensing that is invaluable. I downloaded all my SPARK account programs just for the licensing.

To me, it doesn't matter with hypervisor you run. Thought some need to be additional dedicated hardware accessed as a server. But setting up a VM for each are *basically* and *logically* going to be about the same. Once you learn how to do one, the basic concepts transfer over to creating VM's on other systems.

For me, I'm a fan of Dual Booting Windows and Linux. Though for a student, some times you are going to need to cut and paste thing from one thing to another... There are ways to do both...

The answers to the questions I asked above is going to drive any recommendations from  me. You can see that without the answers to those questions, that  recommendations are fairly broad and general.

---

