---
title: "How to permanently disable Ubuntu upgrades 22.04 desktop"
date: 2024-01-11
forum: Installation &amp; Upgrades
---

### Post by foxsquirrel on 2024-01-11
Please let me know if their is some way to totally shut down the upgrades for 22.04 desktop. We get the info box about it and I really need to eliminate that too so it cannot be clicked. Why, several of our critical machines running VMware workstation pro 17 are down after allowing an upgrade.
All we are getting is finger pointing from VMware with the issue and no solutions. It appears the kernel update is ahead of VMware and that will not allow the kernel modules to be built, hence all our vm's are down. In  software and updates I cannot find an option to shut it off completely.

---

### Post by #&amp;thj^% on 2024-01-11
It is a good practice to include the Warning!
[COLOR="#FF0000"]WARNING[/COLOR]
Disabling automatic updates comes with a security risk. Once automatic updates are disabled, use the following two commands to keep your system updated manually.

Link here: [https://linuxconfig.org/disable-automatic-updates-on-ubuntu-22-04-jammy-jellyfish-linux](https://linuxconfig.org/disable-automatic-updates-on-ubuntu-22-04-jammy-jellyfish-linux)

---

### Post by ajgreeny on 2024-01-11
To clarify the situation, is Ubuntu 22.04 the host or the guest system of your VMs?
If guests, I wonder if this is a problem of the VM's kernel versions being ahead of VMware's ability to run them, as happens sometimes with older versions of VirtualBox, usually solved by updating VirtualBox.

I do not know VMware at all so have no idea if your version is old or new so please give us all the detail that you possibly can.  Most importantly don't forget that running any guest OS that is not fully updated is certainly going to be insecure so you need to make sure you do not continue using the VMs if they are not fully updated.

---

### Post by foxsquirrel on 2024-01-11
It is the host, not sure if the any of the vm's have an issue because it will not start. 

They said to revert the kernel version, I am not going to do that. That seems like a bigger mess than what we have going on now with VMware.

Vmware workstation Pro 17.0

---

### Post by deadflowr on 2024-01-11
> **foxsquirrel said:**
> It is the host, not sure if the any of the vm's have an issue because it will not start. 

They said to revert the kernel version, I am not going to do that. That seems like a bigger mess than what we have going on now with VMware.
Why would reverting cause you issues?
Rebooting into the old kernel shouldn't be any kind of issue.

Linux systems, like Ubuntu, keep the old kernel there for precisely this situation.

---

### Post by webaake on 2024-01-11
Or, you can stop Grub from booting into the newest kernel. 


Edit /etc/default/grub

> GRUB_SAVEDEFAULT="true"
GRUB_DEFAULT="saved"

then command: sudo update-grub

Booting into an older kernel would probably fix all your present problems very easily. The above method will prevent any future update problems with kernels. No new kernel will be booted until you decide, after careful consideration, to boot a newer kernel.

I've been using Ubuntu since 2007 and not all updates are fully functional.

---

### Post by foxsquirrel on 2024-01-11
Am I safe to assume this will back peddle the kernel and be safe?

```
sudo apt remove linux-image-$(uname -r) linux-headers-$(uname -r)
```


Update: Was testing this on different machine and this is the warning message:

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Removing linux-image-6.5.0-14-generic &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; You are running a kernel (version 6.5.0-14-generic) and attempting to     &#9474; 
 &#9474; remove the same version.                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; This can make the system unbootable as it will remove                     &#9474; 
 &#9474; /boot/vmlinuz-6.5.0-14-generic and all modules under the directory        &#9474; 
 &#9474; /lib/modules/6.5.0-14-generic. This can only be fixed with a copy of the  &#9474; 
 &#9474; kernel image and the corresponding modules.                               &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; It is highly recommended to abort the kernel removal unless you are       &#9474; 
 &#9474; prepared to fix the system after removal.                                 &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Abort kernel removal?                                                     &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                    <Yes>                       <No>                       &#9474; 
 &#9474;                                                                
```

---

### Post by webaake on 2024-01-11
Completely unnecessary and furthermore, useless for coming updates.

Follow advice and go into Grub menu at boot and chose an older kernel. Boot and evaluate. Then edit grub default to use a good and saved kernel.

---

### Post by ian-weisser on 2024-01-11
"I want to remove everything..." seems overkill.

You can simply apt-hold the kernel metapackage until your VMware is ready for the upgrade.
This will permit unrelated (non-kernel) upgrades...like security upgrades...to continue.
Let apt work the way apt is intended to work, It's intended to do the heavy lifting for you.

---

### Post by #&amp;thj^% on 2024-01-11
> **ian-weisser said:**
> "I want to remove everything..." seems overkill.

You can simply apt-hold the kernel metapackage until your VMware is ready for the upgrade.
+100
You took your time to reply, I thought you'd be here sooner. :)
```
sudo apt-mark hold <package-name>


```

---

### Post by ian-weisser on 2024-01-11
Indeed. 

Since the CURRENT metapackage points to a kernel you cannot use, use the GRUB solution to keep booting into a working kernel.

When the kernel works with VMWare again, shift from GRUB to the less-fragile apt hold solution:

```

sudo apt-mark hold linux-image-generic-hwe-22.04      // Stop kernel upgrades
sudo apt-mark unhold linux-image-generic-hwe-22.04    // Resume kernel upgrades

```

---

### Post by foxsquirrel on 2024-01-11
Thank you for that, it seems like the best solution at this point.

What is the exact name for the kernel meta package that should be inserted into @1fallen reply

```

sudo apt-mark hold <package-name>
```

Did manage to stop the last machine here to have not been upgraded to 6.5. It is on 6.2 so VMware was installed on it, opened and vm's were copied and that went good. However, doing a couple open and closes of vmware the host locked up and had to be power cycled. I am able to get into the vm's and get the important stuff out of them, that was a serious concern. Had to put the vm's on an HDD because the NVMe's were out of space. Not sure if the HDD latency was messing something up or not. 

I do need to disable kernel upgrade on the 6.2 machine

Is this the correct one to use?
```

sudo apt hold linux-image-generic-hwe-22.04
```

---

### Post by #&amp;thj^% on 2024-01-12
From the working kernel use:
```
uname -r
or
uname -a
```
Better yet:
```
$apt list --installed | grep linux-image
```

---

### Post by foxsquirrel on 2024-01-12
I would like to thank you and all the others that have helped me with this issue.

My solution: 

Went back to 20.04 on the older kernel and VMware workstation 17 would build the kernel modules for the older kernel.
I did save the boot nvme for when VMware gets it fixed it can go back to 22.
Did shut off the upgrade to 22.04 notice, so I am assuming that 20.04 will not be updated to 22 or the 6.1++ kernels.

Fortunately, all the vm's are on nvme drives and they transferred over to the player just fine. 
However 20.04 just crashed and had to reboot running 17.5 workstation, seems like vmware has several issues going.

---

