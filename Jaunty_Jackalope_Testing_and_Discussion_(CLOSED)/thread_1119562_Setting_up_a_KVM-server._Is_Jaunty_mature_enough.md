---
title: "Setting up a KVM-server. Is Jaunty mature enough?"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by meulie on 2009-04-08
Hi all!
 
I'm about to install a KVM-host server and got pointed towards Ubuntu 9.04. Normally I am quite the Gentoo-profet, but even I can see that Jaunty looks very promising as host OS for my new box:
[LIST]
[*]support for RAID10
[*]EXT4 support
[*]KVM GUI's support, like virt-manager
[/LIST]

But... Jaunty is still in beta. The schedule says it will be released at the end of this month, but I prefer not to wait that long...
Is Jaunty in its current state ready/stable enough for a KVM-host installation?

---

### Post by wirelessmonkey on 2009-04-08
I just setup KVM on my Jaunty test box a few days ago. I've had a number of issues with virt-manager being unable to stay connected to VNC with both a WinXP and Gentoo VM. Oddly enough, on a fedora 10 vm, I've not had any issues.

---

### Post by meulie on 2009-04-08
> **wirelessmonkey said:**
> I just setup KVM on my Jaunty test box a few days ago. I've had a number of issues with virt-manager being unable to stay connected to VNC with both a WinXP and Gentoo VM. Oddly enough, on a fedora 10 vm, I've not had any issues.

Hmm, if that's all that doesn't work-quite-right, then it's good enough for me. In the last year or so I always used KVM via cli, so I can live with some instability in a GUI...  ;-)
 
As soon as I don't lose any data on my RAID10/ext4 partitions I should be able to handle any/most/all(?) other issues that appear...  :cool:

---

### Post by Yashiro on 2009-04-08
Jaunty is not mature, no.

---

### Post by Polygon on 2009-04-09
if you want my opinion, no. I have gotten tons of crashes, whether its a bug in the kernel, or something to do with nvidia. the amount of crashes i have gotten is staggering, and a deal breaker for me. It was crashing more then windows xp ever did back in 2006

also, ext4 is NOT something you want to be using right now. Sure it has improvements, but a ton (read: most) programs have not updated themselves to properly sync their changes to disk when needed, and instead are just relying on ext3's 5 second delay which is....not there anymore. So therefore if you are running anything critical with a ext4 filesystem, and the program has not updated itself, there is a very good chance you will at least lose some data.

maybe you will have better luck then i have on the freezing issue, but i highly recommend that you stay away from ext4 ...at least for now

---

### Post by antiram on 2009-04-09
the vnc disconnected error and virt-manager crashes doesnt happen with metacity compositor or compiz.

---

### Post by meulie on 2009-04-09
Oh, I have no problem with most kinds of crashes... As long as the basic linux system, ext4, raid10 & KVM stay up and running, I'm happy :-)

---

