---
title: "VirtualBox, run installed OS?"
date: 2013-11-28
forum: Installation &amp; Upgrades
---

### Post by Niemil on 2013-11-28
I have dual boot on my computer (Windows 7 and Ubuntu).
Only reason I even use Windows 7 is just for some video editing (sony vegas and after effects) and for bank usage.

I really start to like Ubuntu and want to use it 100% when surfing.

I been trying out VirtualBox, but then I installed Windows on the virtualbox.

However, I wonder if I can run my Windows 7 from the virtualbox?
And I wonder if that's really slow and bad to do?

I think it would be quite faster to do some bank jobs etc.

But to render videos etc, will it be very slow and lagging?

Also I think of trying out a game I tried before (Cabal online), and do it via virtualbox. But not very sure.

Anyway, how do I even setup so I can run my already installed Windows 7 in virtualbox if possible? Or is it better to just boot to my Windows 7?

---

### Post by Mark Phelps on 2013-11-28
> However, I wonder if I can run my Windows 7 from the virtualbox?

As far as I know -- NO -- you can not point VB at another installation of Windows and run that; instead, you have to install Windows in VB.

---

### Post by Niemil on 2013-11-28
Well, I found this one for a few mins ago and read some of it and also started to go through it:
[http://geekery.amhill.net/2010/01/27/virtualbox-with-existing-windows-partition/](http://geekery.amhill.net/2010/01/27/virtualbox-with-existing-windows-partition/)

However, I somehow just don't understand, seems to be quite complicated. I got some error on the command: 
[B]VBoxManage internalcommands listpartitions -rawdisk /dev/sda[COLOR=#F8F8F8][FONT=Monaco]
[/FONT][/COLOR][/B]
and the error says:
VBoxManage: error: Cannot open the raw disk: VERR_ACCESS_DENIED

---

### Post by electrohandyman501 on 2013-11-28
My guess on the error is that the disk is available to your Host os. As far as I know if you are assigning the entire drive as being available to the host, it can't be available to the guest at the same time. 
It may be possible to setup a single folder on the disk that you could possibly enable for sharing with both systems at the same time. 
I've run into the same issue having W7 host with VMWare. If I assign the data drive to the guest session, I cannot access it from the host till the guest is shut down.

---

### Post by VMC on 2013-11-28
Niemil, You need this topic moved to [virtualisation]("http://ubuntuforums.org/forumdisplay.php?f=308") forum. Hopefully they will spot this topic here. I only have one or two programs that I need for Windows.  vbox works using one of them right now. I'll have to see about the other at the end of the year. 

I have a spare hard drive for video editing. I don't think a VM will work very well.

---

