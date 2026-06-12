---
title: "How to import Vurtual box"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by Kaizoku001 on 2012-04-28
I'm planning to try out the new Ubuntu 12.04 on a new Hard disc this weekend.

the problem i have is: in my present 11.04, I also installed Win 7 in vurtualBox.

How can I transfer the virtual Box Windows to a new Ubuntu 12.04?

Thanks

---

### Post by dino99 on 2012-04-28
inside your /home you have .VirtualBox folder (ctrl+h to unhide it), so copy & paste it

---

### Post by SeijiSensei on 2012-04-28
You might also want to use the Virtualbox export function to create a portable snapshot and put it in a safe place just in case.  Moving a Windows 7 snapshot to another machine will cause Windows to complain about licensing issues, but reloading it on the same machine shouldn't be a concern.

One way to avoid problems like this in the future is to devote a separate partition on your hard drive to /home.

---

### Post by Kaizoku001 on 2012-04-28
> **SeijiSensei said:**
> 
One way to avoid problems like this in the future is to devote a separate partition on your hard drive to /home.

Actually, if i'm not mistaken I think I did. I remember reading a page about creating diff partitions for home root and such when I first Installed 11.04 (I'm new at this, as you can see)

**How can i verify if home is on a diff partition? And if it is how can this help?**
I'm planning on installing 12.04 on a diff Disk so i can give it a test drive.
If all works out I'M planning on hooking up the old disk and transferring all the data.

Thanks


PS @Dino99   I like your solution. simple is usually best, 
sill just want to know what all my options are. learning experiences and all.

Thanks

---

### Post by SeijiSensei on 2012-04-28
To see how your partitions are mounted, just type "mount" from a command prompt.  If you see a line like

```
/dev/sda7 on /home type ext4 (rw)
```

then /home is mounted separately.  In that case you shouldn't need to do anything with your virtual server images.  VBox should run them with the new version just as it did before.

During installation, choose manual partitioning, then select the partition where /home resides now and configure the installer to mount it as /home again with the new version.  Make sure you tell the installer not to format the partition!

---

### Post by Kaizoku001 on 2012-04-28
Thanks Seiji.
The problem is that I'm using a diff Hard disk.
How can i go about moving/copying my home partition onto a new disk.

---

### Post by Kaizoku001 on 2012-05-03
Ok I just moved the "VirtualBox VMs" and ".VirtualBox" folders to the HOME fouler in 12.04.
I start VBOX, Add Win From the Virtual Box VMs folder,  and try to boot up Sin, but,,,,
I get the following message:
> Failed to open a session for the virtual machine W7.

Implementation of the USB 2.0 controller not found!

Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' or disable USB 2.0 support in the VM settings (VERR_NOT_FOUND).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

If I can't boot up the machine how do I Install the Extension Pack??

EDIT############################

Sorry..

found it, did it,,, All seems good

---

### Post by CharlesA on 2012-05-03
You need to install the extension pack from the virtualbox website.

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Kaizoku001 on 2012-05-03
> **CharlesA said:**
> You need to install the extension pack from the virtualbox website.

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)


Thanks!

---

