---
title: "installing internet explorer on ubuntu"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by bdws1975 on 2009-12-09
hi all,

Ok, be VERY, VERY gentle as as of 10 minutes ago, I'd never touched Linux.  I managed to download ubuntu through unetbootin and am now using it.

Here's the thing:  I HATE microsoft, ie, etc, but I have to have IE for two work applications that require IE.  Is there anyway to install IE on ubuntu?

Again, please, please speak very s-l-o-w-l-y as I'm SUPER new at this and have no programming background.

i'd greatly appreciate any help.

Thanks,
Brett

---

### Post by MelDJ on 2009-12-09
can you tell what programs you have that need IE?
ubuntu programs do not need it.

---

### Post by aysiu on 2009-12-09
This should help you:
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

Are you absolutely sure you need Internet Explorer, though? User Agent Switcher on Firefox doesn't help at all?

---

### Post by bdws1975 on 2009-12-10
HI all,

I am pretty sure I need IE.  The two programs are proprietary programs for my company.  I've tried over and over to run them on firefox and just can't make it happen.

What is agent switcher?

Thanks,
Brett

---

### Post by bdws1975 on 2009-12-10
Ok, don't think agent switcher will work.


is there a way to get IE?


Thanks,
Brett

---

### Post by bdws1975 on 2009-12-10
shoot, it helps if I read the posts entirely.  Thanks and I'm installing ies4 right now.

thanks and I'll report back.

Brett

---

### Post by bdws1975 on 2009-12-10
ok, I downloaded ie4linux and it works like a charm, however....

when i try to run the proprietary software it says, '.net 3.5 service pack 1 is required to run LM program'

any chance I can use that in linux also?

thanks,
Brett

---

### Post by Ginsu543 on 2009-12-10
I think your best bet is to create a Windows virtual machine within Ubuntu using VMware or VirtualBox. I personally recommend VirtualBox since that is what I use and it's free. I'm not sure if this is a perfectly accurate description but it's like having a Windows emulator. You can run Windows inside a window in Ubuntu (no pun intended).

Just go to [www.virtualbox.org](www.virtualbox.org), download the appropriate .deb file, and install it by double-clicking on the icon. Once you've installed the program, it will allow you to install Windows in a virtual environment (you will need a Windows install disk). I have Windows XP service pack 3 running smoothly this way and I have the .net 3.5 service pack 1 installed on it through Microsoft Windows Update. Perhaps this will help you get your proprietary software up and running.

If you need help, there are extensive user guides available from Sun on the website. You can also get help by reading through the "Virtualization" section of the forums here.

---

### Post by underquark on 2009-12-10
Do you mean Net Framework, Service Pack 1?  I run at least one program (Terracrosser) requiring Net Framework 3.5 from a virtual Win XP machine using VirtualBox.  Install VirtualBox, create a virtual machine, install Win XP, install Net FRamework 2.0, upgrade it to 3.5 SP1.

---

### Post by bdws1975 on 2009-12-10
thanks folks!

I'm downloading virtualbox right now.

Here's a follow up:

If I get all my programs to work in ubuntu through the virtualbox installation, can I then ditch my windows totally?

Currently, i'm given the choice to boot either ubuntu or windows on startup.  Can I ditch windows and just have ubuntu with the windows application for when I need it?

That would do away with shutting down and rebooting everything I need to switch.

thanks,
brett

---

### Post by bdws1975 on 2009-12-10
I got an error when after it finished downloading.  It said, 'error:  wrong architecture i386'.  

Since I'm running ubuntu on a machine where windows was first installed, which should I use?

Brett

---

### Post by bdws1975 on 2009-12-10
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-ObJlOAswS6: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-ObJlOAswS6: Connection refused)

Any idea why i'm getting this?

Brett

---

### Post by Ginsu543 on 2009-12-11
Which version of Ubuntu are you running? Karmic? Jaunty? Which architecture? 64-bit? 32-bit? You should install the 64-bit version of VirtualBox (host) if you are running a 64-bit kernel. Once you have VirtualBox set up, you can install a 32-bit guest like Windows XP. From your error message, it appears you downloaded the 32-bit version (i386). The 64-bit version is under AMD64.

---

### Post by bdws1975 on 2009-12-12
Thanks all.  I think I figured it out.  

Brett

---

### Post by strruner on 2009-12-23
j

---

### Post by Claus7 on 2009-12-25
Hello,

> **aysiu said:**
> This should help you:
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

Are you absolutely sure you need Internet Explorer, though? User Agent Switcher on Firefox doesn't help at all?

Thanks, this worked very nice for me too. I had some issues with some of my modems configurations. This fixed the problem.

Regards!

---

